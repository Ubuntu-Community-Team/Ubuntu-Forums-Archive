---
title: "Installing Ubuntu on External Drive"
date: 2012-05-24
forum: Installation &amp; Upgrades
---

### Post by Coastalguy on 2012-05-24
I just installed an external SATA drive (tried USB by BIOS wouldn't recognize it. I want to install Ubuntu on it, along with Grub2, so that I can leave it on to boot to Ubuntu, or turn it off to boot to Windows. In my BIOS, I have my DVD first, this new drive with Ubuntu second and my main drive with windows MBR third.

My question is, as this new drive is 500gb, I don't want to waste all of it with just Ubuntu. I want to split it between ubuntu and Windows storage (no windows boots on it).

Am I correct that all I need to do is partition it into 2 partitions, with the first one large enough for ubuntu, and the second one as NTFS so windows sees it. If so, then I understand the Ubuntu installer, allows you to take free space (from the first partition) and assign it for swap, root, home and boot?

thanks,

---

### Post by irv on 2012-05-24
When you said, "tried USB by BIOS wouldn't recognize it" is your computer not able to boot from USB? or is it just not recognizing it? It has to be able to boot from it to run Ubuntu off of it.
I have my BIOS set to boot first USB, CD, then HD. This way I can setup OS' on USB drives and boot from them when I plug them in and boot up.

Yes you can setup two partitions on the hd to NTFS and one for Ubuntu. The partition for Ubuntu you want to set the boot flag using gparted. I do this all the time and it works great.

---

### Post by oldfred on 2012-05-24
You should not need a separate /boot unless an older system that has issues booting beyond 137GB, although some BIOS settings may emulate that problem on newer systems.

You can partition any way you want. I like to only use 1 or two primary partitions and then put everything else into the extended partition. That leave a primary or two incase some system need only primary. 

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

