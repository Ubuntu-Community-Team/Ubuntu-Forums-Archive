---
title: "Botched Upgrade to Dapper"
date: 2006-06-06
forum: Installation &amp; Upgrades
---

### Post by sambram on 2006-06-06
Hello. I chose to upgrade from Kubuntu Breezy to Dapper via apt. I started the process in a Konsole window and when KDM asked if I would like to close the current X session I accidentally answered yes instead of no.

Now I can boot as far as a tty prompt, but am unable to start X, as i think it didn't get installed fully thanks to my fumbling fingers.

Any suggestion of how to remedy this? I use wifi on that machine for my net access (which i would have a hard time making work from the command line). 
I could physically move the machine to an ethernet jack although I would like to avoid this. 

Should I download the alternate CD? If so, can I run it without destroying my home directory? Any help greatly appreciated.

---

### Post by sdalley on 2006-06-06
It depends how far your upgrade got. Network stuff (including wireless) is at a lower level and likely to be upgraded early on, so it could still be functional and using your previous settings. If the commandline cmd "host www.google.com" works, then net access is ok. During my upgrade, I was left with a command prompt as well. Having an nvidia video chip based display card, I did "sudo apt-get install nvidia-glx"and the next reboot came up OK with a graphical login. YMMV.

You can certainly use the alternate cd to do a local upgrade using the cdrom as a repository. (You will need to run the "apt-cdrom add" command - see manpage or apt-cdrom --help, and possibly comment out all online repositories in /etc/apt/sources.list if you are still offline, before doing apt-get update && apt-get dist-upgrade). This should not affect your /home directory - only actually running user programs and setting preferences on your own desktop, or repartitioning the disk itself with a full reinstall, should affect that.

---

### Post by sdalley on 2006-06-06
Forgot to mention the **apt-get check**, **apt-get -f remove** and **apt-get -f install** commands, see manpage, they can untie a lot of funny knots.

---

### Post by sambram on 2006-06-06
[QUOTE=sdalley]You can certainly use the alternate cd to do a local upgrade using the cdrom as a repository. (You will need to run the "apt-cdrom add" command - see manpage or apt-cdrom --help, and possibly comment out all online repositories in /etc/apt/sources.list if you are still offline, before doing apt-get update && apt-get dist-upgrade). This should not affect your /home directory - only actually running user programs and setting preferences on your own desktop, or repartitioning the disk itself with a full reinstall, should affect that.[/QUOTE]

Aw man, I tried this method and everything looked good, but now I get as far as the (new) boot screen and "Checking Root Filesystem" (I think) before the boot screen disapears and throws an error at me. My dilemma now is I can't get to the command line, even. 

(Even though I'm stuck again, thanks anyway.)

Edit for further elaboration:
Also, when I attempted to complete the upgrade from the CD, I got the Samba problem described here: [http://www.ubuntuforums.org/showthread.php?t=190613](http://www.ubuntuforums.org/showthread.php?t=190613)

After that, I absentmindedly rebooted and that's how I got where I am now.
I have figured out how to get to a prompt, with the "rescue" via booting from the CD. Need to figure out how to finish the upgrade, though.

---

### Post by sambram on 2006-06-07
I am running a shell from the alternate CD, because the botched upgrade won't boot as far as a prompt.

dpkg shows that the remainder of the upgrade is selected for install, but my dilemma now is trying to run dselect throws up an error about BTerm not being installed.

anything to help me complete my upgrade at this point would be greatly appreciated.

---

### Post by sdalley on 2006-06-08
Hmm. Ahh. Ummm...

There's so many things it **could** be. There's enormous threads on this forum [http://www.ubuntuforums.org/showthread.php?t=186115](http://www.ubuntuforums.org/showthread.php?t=186115) and [http://www.ubuntuforums.org/showthread.php?t=187318](http://www.ubuntuforums.org/showthread.php?t=187318) about your kind of problem, which I daresay you've looked at. It could be that the kernel initrd or bzimage files got corrupted (maybe youre reboot corrupted the filesystem and it needs an fsck from rescue mode?  maybe you ran out of disk space at a critical point and some files got silently truncated? This would indicate a reinstall of the corrupted (eg kernel) packages.

I note that there is a recently-updated comprehensive thread about sorting out broken packages in the sticky section: [http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672) , esp. the bit about **What if you can't boot into a terminal at all** That might get you sorted. Anyway, the best of luck in your endevours.

---

