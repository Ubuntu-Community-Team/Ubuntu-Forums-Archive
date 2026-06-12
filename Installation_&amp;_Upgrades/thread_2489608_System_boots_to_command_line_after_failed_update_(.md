---
title: "System boots to command line after failed update (Dual boot)"
date: 2023-08-04
forum: Installation &amp; Upgrades
---

### Post by jimboslice7 on 2023-08-04
Hello everyone, I will try to explain as best as possible.

I went into software updater as ubuntu was saying I had updates. After updates started and system needed restart, system was stuck for 15 minutes on restart.
I go to manually restart system and when restart is complete now ubuntu will only load up to command line after stating "[FAILED] Failed to start process"

Steps I have taken to attempt to fix:

1. Make sure fast boot is still off.
2. Make sure secure boot is still off.
3. Make sure ubuntu is still first in boot order
4. Doing manual update, "sudo update" in command line  Received multiple "fail to fetch" and "could not download the upgrades" errors. System restored to original state.
5. Attempted to reinstall GNOME, received several errors stating "failed to fetch" and "temporary error resolving".
6. Attempted GNOME reinstall again with --fix-missing and received. "Updating from such a repository cant be done securely".
7. Attempted to fix broken files in ubuntu recovery mode and received once again "Could not download upgrades" and "Restoring original system state"

I am at quite a loss right now I had many important files that would quite honestly devastate me to lose if I had to reinstall ubuntu clean. I did not believe a recommended update would cause my system
to falter so heavily.

---

### Post by oldfred on 2023-08-04
Boot with current version live installer & backup anything you think is important.
I backup /home, list of installed apps & my data partition(s). I have just a few settings in /etc, so just copy those into /home, otherwise you may want /etc also. If any server apps (database, web, etc) those usually are in / & need separate backup.

Can you boot older kernel?

What does this show. If not from booted system, you may have to mount / & show it from that.

Post this in code tags, shows repositories & ppa. If upgrading best to remove all ppa.

cat /etc/apt/sources.list; for X in /etc/apt/sources.list.d/*; do echo; echo; echo "** $X:"; echo; cat $X; done

---

### Post by jimboslice7 on 2023-08-04
When attempting to boot from older kernal it still boots only to command line.

I have attempted a few things

I removed /etc/apt/sources.list 

After this I attempted sudo apt update

Encountered errors saying

 "Please use apt-cd-rom to make this CD-ROM recognized by APT"

"The repository 'cdrom://ubuntu 22.04.1 LTS _Jammy Jellyfish -Release amd64 does not have a release file"

"Updating from such a repository can not be done securely and is therefore disabled by default"

I am not sure why it is trying to update from a CD-ROM as I currently have no CD loaded.

---

### Post by oldfred on 2023-08-04
You cannot remove  /etc/apt/sources.list  as it is where it looks for updates. You need to restore that file & fix any issues in it.

So it has to use CD-Rom as that would be only place to look for updates.

I have this old info in notes, not sure if still valid.
reset /etc/apt/sources.list 
[https://ubuntuforums.org/showthread.php?t=2414194&p=13843080#post13843080](https://ubuntuforums.org/showthread.php?t=2414194&p=13843080#post13843080)
Ubuntu Sources List Generator
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by tomber57 on 2023-08-05
I had the same problem no gui after update. After sudo apt install --reinstall ubuntu-desktop.
After reboot everything worked again as usual.

---

### Post by donratcliff on 2023-08-06
Worked like a champ!!   Thanks for your help!!

---

### Post by donratcliff on 2023-08-06
Tomber57:  Worked like a champ!!   Thanks for your help!!

---

### Post by MAFoElffen on 2023-08-06
EDIT: Nevermind. Started this post before I left. Sent it upon return. Looks like he figured out his problem already...

--- Old Post ---
He cannot reinstall "anything" until he get his networking working. That is where he is getting the "failed to fetch errors".

Since you are ow console / cli, go through the checklist:
```

ip a # Check to see if you have an IP address, and check to see if the device is UP or DOWN.
ping -c 4 192.168.1.5 # <--- Change that to your IP address, and see if you can ping yourself.
ping -c 4 192.168.1.1 # <--- Change to your LAN gateway IP address
ping -c 4 8.8.8.8 # <--- See if you can ping Google's DNS Server
ping -c www.google.com # <--- See if you ca resolve a DNS address to Google

```
That is a progressive set of networking tests. Where it fials, fix from there.

Or... Mount your system from a LiveUSB, chroot into the installed system, then diagnose and repair.

---

