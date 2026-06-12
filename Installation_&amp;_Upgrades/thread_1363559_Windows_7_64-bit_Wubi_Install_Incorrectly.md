---
title: "Windows 7 64-bit Wubi Install Incorrectly"
date: 2009-12-24
forum: Installation &amp; Upgrades
---

### Post by jgatkinsn on 2009-12-24
Hi,

I'm trying to run wubi to install kubuntu 9.10 64-bit on my Windows Professional 7 64-bit system.  The problem I'm running into is that when I go to start the install, wubi tries to download the 32-bit version of Kubuntu even though I have the 64-bit (kubuntu-9.10-desktop-amd64.iso) iso file in the same directory as the wubi.exe.  I do have the exe setup in Vista compatibility mode.

Any ideas what could be wrong?

---

### Post by Greenbean209 on 2009-12-24
Did you download the ISO and the wubi exe separatly? If do then wubi might not even be looking for your ISO. If thus is what you did, I would suggest mounting the ISO or buning it to a CD and then navigating to the wubi exe within the mounted ISO or within the CD.
 
Oh and just wondering is this your first Linux experience?

---

### Post by jgatkinsn on 2009-12-25
I haven't tried burning to CD, because in the past I never had to do it.  Downloading worked fine.   No, it's not my first Linux experience, but this is my first time trying to install Wubi on Windows 7, and it is behaving as from past experience.  I'll try the burn method and see what happens.

Thanks.

---

### Post by jgatkinsn on 2009-12-25
I burned the CD, but it's still doing the same thing: tries to download the i386 (32-bit) version of the desktop. Goofy.  I don't know what to do now.

---

### Post by Greenbean209 on 2009-12-25
That is strange.... Are you sure you are using the wubi within the CD, not one you may have downloaded separately?

---

### Post by jgatkinsn on 2009-12-25
Positive.  When I inserted the CD, it ran autorun and popped up the installer from the CD.  I told it to install Kubuntu in windows, and it ran Wubi.  It extracted all the files from the CD, then started doing the i386 desktop torrent download.  I let it go ahead and install.  I verified that the 32-bit version was installed.  Of course, it couldn't quite completely install because of some weird GRUB error that only allowed me to boot back into Windows 7.

---

### Post by garvinrick4 on 2009-12-25
When you download Ubuntu it is either 64 bit or 32 bit. They are not both on the same
download. Recheck what .iso version of Uubuntu you are downloading. Here is page with
64 bit or 32 bit. Just pick country and which version.



[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by jgatkinsn on 2009-12-26
I know it sounds crazy, but the only kubuntu .iso that I have on my hard drive is ...

kubuntu-9.10-desktop-amd64.iso

That is what I burned and that is what I tried to install to no avail.  Again, when I run the wubi install from either a downloaded version or off the 64-bit version CD, it is the one downloading the i386 iso.  I never requested it.

---

### Post by jgatkinsn on 2009-12-26
I tried a second download .amd64.iso image.  Same thing.  It extracts the files from the CD drive (takes 4.5 minutes), then goes right into an hour download of i386.iso.torrent of the desktop image.

---

### Post by garvinrick4 on 2009-12-26
If it is on the CD it takes about 5 to 12 minutes to install.

---

### Post by efflandt on 2009-12-26
Isn't Wubi in Win7 asking for trouble?  Someone else had trouble after they said Win7 went into standby (I think it actually hibernated), and then had grub issues.

Why not shrink Win7 using its own utility (in Administration) and use gparted from the install CD to create a partition for Linux?  If you have enough RAM for Win7 you probably do not even need swap, unless you want to hibernate.  That is what I just did with a new Dell laptop (64-bit 9.10).  I did not tamper with the Windows mbr, I put grub2 on the primary Linux partition and marked that as the boot partition with gparted from the CD before shutting down after installation.  Works great.

---

### Post by Sircoelho on 2010-01-17
I can confirm this, Wubi installation do not complete and insists download kubuntu i386 torrent.

---

### Post by Greenbean209 on 2010-01-20
Ok Ive been gone for a while but I can tell you how I installed wubi on my 64 win7 machine. I got the installer from the wubi website. there is only one choice of installer. Then I ran it in vista compatibility mode with no service packs and ran as admin. Those settings should fix the booting problems. As far as i know the installer will chose the bit format appropriate for your machine and download extract and install. Try it this way and it should be fine.

---

### Post by Senuf on 2010-03-18
Hello. Greenbean209, I tried what you suggest, but to no avail. Some friends' parents, who have been using windows for quite a while (now using Win 7 64 bit on a Core2Quad PC) want to give a try to some linux distro. Since they're accustomed to some "bells & whistles", I decided to go with Kubuntu (although I use Ubuntu). I wanted to go the *Wubi way*, even tried what you suggested on your latest post in this thread, but it keeps downloading the i386 version.

I am about to give up on this. Should I?

---

### Post by Senuf on 2010-03-18
OK, never mind. I gave up already. I'll return them the PC tomorrow. I tried EVERY single method I could find around here and in other sites & forums, but could NOT install Kubuntu/Wubi in 64 bit in their PC with Win 7 (64 bit too).

I feel kinda frustrated, but, hey, such is life.

Ta-da!

Senuf

---

### Post by picdome on 2011-04-29
same thing happen for me with ubuntu 11.04 , but here my laptop is 32 bit and i downloded 32 bit version but when i tried to install it start downloading 64 bit version, so i disconnect internet and tried again .. now it showing this error "Cannot download the metalink and therefore the ISO"

---

