---
title: "Netinstall ?"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by WitchCraft on 2009-11-21
Question: I'm about to dump Arch Linux for Ubuntu, because the packagemanager of Arch Linux is horrible and because the network just doesn't work, no matter what I do.
 
Now, I want to install a server on this PC, but not LAMP!
I want to make an LLPM (Linux, LightHttp, PostgreSQL and Mono)  server.
My understanding is that the Ubuntu Server edition comes with LAMP preinstalled.
 
Is there anything like an Ubuntu Server netinstall cd ?
Or better, is there a way I can install a minimal Ubuntu, preferably without having to burn a CD (assuming the BIOS is sufficiently up-to-date) ?

---

### Post by MisfitI38 on 2009-11-21
> **WitchCraft said:**
> ...I'm about to dump Arch Linux for Ubuntu, because the packagemanager of Arch Linux is horrible and because the network just doesn't work, no matter what I do.

less /var/log/everything.log | grep PEBKAC

---

### Post by louieb on 2009-11-21
The default server install does not include LAMP. Its just one of many server software options available. 

There are net install CDs around don't know of one for the server edition. 

Take a look [https://help.ubuntu.com/community/Installation#Server%20and%20network%20installations](https://help.ubuntu.com/community/Installation#Server%20and%20network%20installations)

---

### Post by slakkie on 2009-11-21
With the netinstall CD you can create any kind of Ubuntu box: Desktop/Server/Everything else. You can create a minimal Ubuntu install and then start configuring the box as you see fit. 
My sig has the download URL for the minimal install CD, enjoy.

---

### Post by WitchCraft on 2009-11-22
> **MisfitI38 said:**
> less /var/log/everything.log | grep PEBKAC
 
Thank you, very nice of you, and so extremely useful...
but all my other Linux distros work very well, including a debian netinstall. So I don't think that the PEBKAC.
 
It's just that I accidentially installed VirtualBox OSE instead of PUEL.
For whatever reason, OSE contains the kernel modul for PUEL, and they are not comaptible. Now, I removed OSE via pacman, but it is still there, though not for pacman, and I still cannot install PUEL because it says OSE is installed.
 
It's all ****** up, the repositories have files in them that aren't actually on the servers.
Pacman fails regularely, and i have to change the repository source every now and then.
 
 
The wireless network fails randomly (notably every time you start pacman), probably due to a bug in udev, that is apart from eth0 being eth1 and vice versa randomly at evey bootup, and every attempt to resolve it by changing config files didn't work.
 
For using ssh, you have to remove everything from hosts.deny, obviously because reverse name lookup doesn't work. Now, I don't want to grant everybody ssh access to my machine.
 
The screen flashes at gnome startup, even after my second attempt of installation, after which I got OpenGL to work. Probably a bug in HAL. Reinstallation was necessary, because just like with virtualbox, pacman couldn't remove the intel driver, when I wanted to compile and install it from source.
 
You still need to authenticate to gnome, even when you did already login to the console. You cannot start gnome without gdm, for whatever reason.
Installing KDM f*cks up GDM.
 
I'm really a patient person, but enough is enough.

---

### Post by WitchCraft on 2009-11-22
> **slakkie said:**
> With the netinstall CD you can create any kind of Ubuntu box: Desktop/Server/Everything else. You can create a minimal Ubuntu install and then start configuring the box as you see fit. 
My sig has the download URL for the minimal install CD, enjoy.
 
 
mmh, I think PXE/netboot is what I search

---

### Post by WitchCraft on 2009-11-26
> **MisfitI38 said:**
> less /var/log/everything.log | grep PEBKAC

Interesting:
Bothered by your comment, I gave it a last try, and removed some system files manually.

After 15 minutes of guess-work removing, and a recompilation of pacman, I was able to run pacman again.
There were 500 MB of upgrades, including an intel firmware upgrade.

That solved all problems.

You should have said: PEBPAP:
Problem exists between pacman and permissions (even when run as root)...

---

### Post by WitchCraft on 2009-11-26
Another question:

Do I need a graphics card for doing a console-based net-install ?
I intend to install a webserver and mono, including using gdi+.

That would probably mean I have to install some xorg libraries.
I assume they also work without graphics card ?

---

### Post by WitchCraft on 2009-11-28
> **WitchCraft said:**
> Another question:

Do I need a graphics card for doing a console-based net-install ?
I intend to install a webserver and mono, including using gdi+.

That would probably mean I have to install some xorg libraries.
I assume they also work without graphics card ?

The answer to the question is: yes, unless it works at the first time and you can navigate to "ssh install" blindly.

But it is irrelevant in my case, since my atom 330 motherboard has an onboard graphics card.

The debian netinstall files you find here:
[ftp://ftp.debian.org/debian/dists/squeeze/main/installer-amd64/current/images/netboot/](ftp://ftp.debian.org/debian/dists/squeeze/main/installer-amd64/current/images/netboot/)


Along with various options:
[http://www.linuxquestions.org/questions/debian-26/how-i-did-it-diskless-netboot-with-debian-etch-468870/](http://www.linuxquestions.org/questions/debian-26/how-i-did-it-diskless-netboot-with-debian-etch-468870/)
[http://www.pcmech.com/article/how-to-install-ubuntu-linux-with-no-optical-drive/](http://www.pcmech.com/article/how-to-install-ubuntu-linux-with-no-optical-drive/)
[http://subvert-the-dominant-paradigm.net/blog/?p=26](http://subvert-the-dominant-paradigm.net/blog/?p=26)

---

