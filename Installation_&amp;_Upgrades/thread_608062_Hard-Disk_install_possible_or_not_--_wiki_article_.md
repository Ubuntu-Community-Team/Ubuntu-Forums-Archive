---
title: "Hard-Disk install possible or not -- wiki article supposed it works"
date: 2007-11-09
forum: Installation &amp; Upgrades
---

### Post by bbruecker on 2007-11-09
Hi folks,

I've got an old but fine notebook. I'd like to give Ubuntu (xubuntu or server) a try because I'm not happy with Damn-Small-Linux which I'm currently running on that machine (old kernel, impossible to "make configure", language problems...). 

Unfortunately the notebook doesn't boot from CD-ROM, network, and the Ubuntu-Installers (ubuntu server 7.10 and xubuntu, both alternate-install) doesn't recognize my PCMCIA-CD-Rom.

I've found this article
[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

I've followed this article step-by-step, except my notebook has not have 1 Gig memory -- so my virtual hard disk is only 65 Mgbs large. The install process ist starting, but it stops because it want's to install from a CD-Rom. (I think the amount of Memory is not the point, because there is no failure message.) The author of the article does not describe how to convince the Ubuntu-installer to load the files from the hard disk. But this is the tricky point.

So, dear professionals... Do I need a Gig of Memory to install from Hard Disk? (A description called "Install from 1Gig -memory" would be suitable in this case.) Or is it simply not possible to install Ubuntu from Hard disk, as some posts say? It hat would be true, the article should be removed.

If last is true, I'd be very happy to hear some suggestions suite to my difficult situation.

Thank you for reading this and writing down useful tips.
Benjamin

---

### Post by logos34 on 2007-11-09
> **bbruecker said:**
> The install process ist starting, but it stops because it want's to install from a CD-Rom. (I think the amount of Memory is not the point, because there is no failure message.) The author of the article does not describe how to convince the Ubuntu-installer to load the files from the hard disk. But this is the tricky point.

Yes, but notice that it uses the live cd.  So you need the xubuntu-7.10-**desktop**-i386.iso. (min. 128 MB RAM to run or 192 MB RAM to install.)

Or try this method ('hd-media') with the alternate cd (min. 64 MB RAM to run):

[URL="http://ubuntuforums.org/showthread.php?t=316093"]'HOWTO: Install Edgy 6.10 / 7.04 / 7.10 from an .iso file (hd-media)'
[/URL]

---

### Post by oldos2er on 2007-11-09
What are your machine's specs?

---

### Post by bbruecker on 2007-11-10
Thanks for your answers,

to oldos2er: here are the specs of my "toshiba portege 3020ct"[LIST]
[*]Pentium I 300 Mhz,
[*]96 MB Ram,
[*]40 GB Harddisk (new one),
[*]No-Card-Bus PCMCIA/16 Bit
[*]No build-in modem or nic[/LIST][INDENT]Two 16 Bit PCMCIA Nics -- both cards are recognized on a newer notebook with xubuntu 7.10:[/INDENT][LIST]
[*]Aterm WL11CB (same chipset as orinoco classic gold)
[*]xircom Ethernet 10 compact card via xircom card caddy[/LIST]I've read about memory specs before [here]("https://help.ubuntu.com/community/Installation/LowMemorySystems"). So my plan is first to install ubuntu server, and install a lightweight window manager later. I've tryed out the "HOWTO: Install Edgy 6.10 from an .iso file", but the Installer doesn't recognize the Ubunut-server-iso-file. I've posted a question there.

Any ideas?
Benjamin

---

### Post by logos34 on 2007-11-10
Did you use the vmlinuz and initrd.gz from gutsy archive:
[http://archive.ubuntu.com/ubuntu/dists/gutsy/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/installer-i386/current/images/hd-media/)

Or...

Does laptop have floppy drive?  If so you could try [Smart boot manager]("https://help.ubuntu.com/community/SmartBootManagerHowto")--it might be able to boot your cdrom.  Basically all you do is copy 'sbm.bin' (~1.4MB) file from /install directory on ubuntu CD to floppy (it may be in a different folder on xubuntu or ubuntu server cd)

(linux method)
insert floppy (do not mount) and format, then copy:

sudo mke2fs /dev/fd0
sudo dd if=/path/to/sbm.bin of=/dev/fd0

(ex. in my case the last line is 
sudo dd if=/media/cdrom0/install/sbm.bin of=/dev/fd0

boot from floppy drive and choose 'cdrom' from menu

---

### Post by oldos2er on 2007-11-10
I doubt if you'd be happy with Ubuntu's performance with those specs. Have you tried Puppy Linux?

---

### Post by logos34 on 2007-11-10
It just occurred to me you may have the paths wrong. vmlinuz and initrd.gz are in the **'install**' folder on the Ubuntu alternate cd, NOT the 'casper' folder as on the live/desktop cd.
Xubuntu alternate and server cds may be different still.

Leave the CD in the tray this time and edit the entry on DSL grub menu:

> title installer
        root (hd0,0)
        kernel **/install/**vmlinuz boot=**install** root=/dev/ram ramdisk_size=1048576 rw
        initrd **/install**/initrd.gz

Or try this one from the [Installation/FromWindows]("https://help.ubuntu.com/community/Installation/FromWindows") (-->'**CD approach**')

> title Install Ubuntu
kernel   (hd0,0)/install/vmlinuz **root=/dev/ram0 devfs=mount,dall ramdisk_size=17000**
initrd   (hd0,0)/install/initrd.gz

Hopefully the difference in the 'kernel' lines and/or the paths will do the trick.  

Basically, all you're trying to do is boot the kernel and initial ramdisk image from the hard drive and continue the install from the CD. I just tried the second with a Feisty alternate CD I had laying around.  After selecting entry in grub menu it boots the kernel and then starts grabbing stuff off the cd. (can't say for sure, though, if it will work for xubuntu or server).

Of course, oldos2er may be right about your specs.  96 MB RAM is probably enough to run Xubuntu ok but I just noticed your cpu-- might not cut it.  Maybe Puppy would be a better iidea than Xubuntu, or DeLi or some Fluxbox-based distro.  Or maybe just resign yourself to the server with CLI only.

Good luck.

---

