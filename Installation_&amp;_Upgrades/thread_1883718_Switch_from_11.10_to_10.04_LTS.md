---
title: "Switch from 11.10 to 10.04 LTS"
date: 2011-11-19
forum: Installation &amp; Upgrades
---

### Post by Pen16 on 2011-11-19
Hello I am trying to install the 10.04 LTS ubuntu package because i like the simplicity over the new styles and i don't need the latest and greatest.

I have 11.10 installed on a 200 Gb hard drive that about to die so i backed up all my files on a another internal 100 Gb drive and i was wanting to install the LTS on there.

First I dont know if you can install it on another hard drive from the OS i have now (11.10) I tried from the disc but after the install it said restart and nothing happened there is no Linux hierarchy on the drive.

I tried from the boot but my computer has the nomodeset/nvidia card problem which i normally know how to fix (f6 mark nomodeset, replace quiet splash with nomodeset). But it keeps spitting out hard drive errors (I'm assuming cause it all pertains to sd0) when I try the install option or boot from disc option and after a while it just spits me out into terminal prompts.

Im wondering whats going on and if somebody could help me figure this out, i would appreciate it.

---

### Post by zvacet on 2011-11-19
No,you can not install 10.04 from 11.10 CD.Download 10.04 live CD and install with it.

---

### Post by oldfred on 2011-11-19
You can use your grub2 boot loader to loopmount an ISO file from a hard drive to install. If you partition in advance with gparted and install from a hard drive to another hard drive, the install goes very fast.

Hard drive:
Direct boot on hard drive:
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it should have to be different partition or
sudo umount -lrf /isodevice
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by Pen16 on 2011-11-19
Yes i know to use the 10.04 disc that is why I have one.

I will try these grub2 bootloader iso options it might take me awhile, im linux illiterate.
Thank You for the help!

---

### Post by Pen16 on 2011-11-20
Ok, so what all these threads are pointing at are telling me to change my grub (which i did, added the boot iso from disk option) which would only mean it would work through a restart.  That puts me in the same boat i was in before.

I was wonting a way that i could install the new OS and change the grub.cfg file right there so i can get it to boot because i cant get the 10.04 disk to boot properly.  All it does is spit me out in prompts when i want to install.

I wanted a little more power over whats going on because im not the terminal master yet.

If i install boot loader, is that a graphical program i can use within my 11.10 to install 10.04 on another disk?

---

### Post by oldfred on 2011-11-20
You cannot install while running another system.

If you are having boot issues with the liveCD or a liveUSB or directly booting ISO then that is usually a video issue, but may be another boot parameter that is required. When I add my boot stanza to directly boot an ISO I always add nomodeset to the linux line as direct boot does not give me the f6 options that the liveCD does.

Natty Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Pen16 on 2011-11-20
I'm not sure its a graphical anymore, every time I try and boot under my normal computer parameters which is usually only nomodeset but now if i look at the commands as its booting up its my hard drive.

Every time it runs smooth for the code until it tries to read from my hard drive and it sits there and spits out an I/O error when trying to read it.  I do have a hard drive that is dying but I unhooked that one and kept the good one plugged in.

It keeps trying to read different sectors but never works so it just stops moves on.

And I tried the grub iso boot by adding the lines to grub.cfg and putting the 10.04 iso in /boot/grub/iso.  Is it supposed to show up on the grub or boot on its own cause niether of those happened.

---

### Post by oldfred on 2011-11-20
Are you sure drive is good?

What does Disk Utility say about drive? I do not know details, but it shows green if it is ok.

---

### Post by Pen16 on 2011-11-20
yep it says its healthy and shows all green for disc utility.

Im gonna attempt to clarify the error just to make sure thats the problem, it says something to the fact the its trying to read sd0 ( my drive) and lists a different sector every time for about five times and then it skips it.

Is it possible that when i burnt the disc it went to fast of a burn rate that it missed some essential install files?  I have a great disc burner but the lowest speed it burns at or that ubuntu lets it burn at is 32x.

I've been wondering that cause most of my audio cd's will have millisecond skips.
I'm gonna try from a usb device and update.

---

