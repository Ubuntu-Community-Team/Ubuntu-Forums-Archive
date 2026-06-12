---
title: "X server (error: no screens found)"
date: 2007-02-20
forum: Installation &amp; Upgrades
---

### Post by bergsore on 2007-02-20
/* see next post for problem update. */

I have an installation problem that I strongly suspect has something to do with my
graphics card.

AMD Athlon64 X2 3400+
Abit KN8 SLI (no onboard video)
Radeon X800 XL (PCI express)
SATA HDD

when I boot from cd and select "Start or install Ubuntu" 

6.06.1: everything goes fine (though there is no ok next to PCMCIA) until the X server. 

6.10: displays a grayscale spash and no text but keeps loading things until it hits the X server.

Once they hit the X server, I get a blue and grey screen saying that it can't start the X server and it may not be configured properly.  When I say I want to see the output it gives me:

X windows System Version 7.0.0
X protocol version 11, Revision 0, Release 7.0
Build OS: Linux 2.6.15.7 x86_64
current OS: Linux ubuntu 2.6.15-26-amd64-generic #1 SMP
...
Module Loader present
...
(II) Primary Device is: PCI 01:00.0
(II) ATI: Candidate "device" section "ATI Tecnologies, inc. R430 UM [radeon X800 XL] (PCIe)
Fatal server error: no screens found

6.06.1: dumps me to a prompt.  Says to restart GDM.
If I try safe graphics mode the monitor stops receiving a signal at the same point.

6.10: no prompt but I can enter text on the screen.  Hitting the power button will cause ubuntu to exit, display the (grayscale) splash screen and eject the cd.  Hitting a key does not shut it of however.  Safe mode the same.

Can anyone help me?  I have Ubuntu on my laptop and I love it.  I would really like to get in working on my main comp as well.

---

### Post by taurus on 2007-02-20
I suggest you use the alternate CD to install it since it uses text mode instead of the graphic mode.  Should be real easy to follow.

---

### Post by bergsore on 2007-02-21
Ok, I successfully installed Ubuntu using the alternate install CD, but it has a serious error on boot up.

...
booting the kernel
PCI: can't allocate resource region 0 of device 0000:05:08.0
PCI: Error while updating region 0000:05:08.0/0 (00009001 != 01009001)
Root-NFS: No NFS server available, giving up.
VFS: Unable to mount root fs via NFS, trying floppy.
Kernel Panic -  not syncing: VFS: Unable to mount root fs on unknown-block(2,0)



I used QTparted in Knoppix to partition the drive, I already had 3 primary partitions so I made an extended partiton with two logical partitions, one for / and one for swap.  The root is formated with ext3.

Any ideas?

---

### Post by taurus on 2007-02-21
Are you trying to mount nfs in /etc/fstab?  Can you boot into recovery mode from GRUB menu?

---

### Post by bergsore on 2007-02-21
when I run in recovery mode I get much the same just more output:

kernel 2.6.13-15.10-smp Default (recovery mode):
Boot options:
root (hd1,0)    //my windows partition!?  Is this just referring to the MBR?
kernel /vmlinuz root=/dev/sda6 ro single
boot

VSF: Cannot open root device "sda6" or unknown-block(2,0)
Please append a correct "root=" option

kernel 2.6-17-10-generic (recovery mode):

manages to boot up okay, runs fsck and oks my root fs (sda6.)  Complains about one of my data partitions (Originally had SuSE, reformated as ext3 but some reifer blocks are still there and I don't know how to get rid of them.)  I get to a root prompt and if I try startx I get the same blue-grey screen as before. 

I tried to check /etc/fstab but gedit can't open it ("Cannot open display").  Any commands I could use to read it without an x server?

Thanks again for your time and your prompt responses.

---

### Post by taurus on 2007-02-21
If you want to edit /etc/fstab in the recovery mode, then you need to use nano.

```
nano -Bw /etc/fstab
```
And when you are done, exit with <Ctrl>x, Y, than then Return.

And if you need to reconfigure X again, run

```
dpkg-reconfigure xserver-xorg
```

---

### Post by bergsore on 2007-02-21
I looked in /etc/fstab and apparently my boot partition is reiserfs and one of my data partitions is vfat (defaults,utf8,umask=007,gid=46) (dump 0) (pass 1).  I don't know if either of those is a problem.  My root partition is ext3 (defaults,errors,errors=remount-ro) (dump 0) (pass 1).

as for the x server I went through the configuration, mostly just accepting defaults but I still get the same error.  Do I have to restart after I reconfigure?

When I run lspci I see my video card on 01:00.0 and 01:00.1 but the xorg setup forces me to do something like PCI:1:0:0, is this equivalent?

---

### Post by taurus on 2007-02-21
Make sure you pick **vesa** as a driver for your graphic card.  Then, reboot and see what happens.

---

### Post by bergsore on 2007-02-21
Hmm.  I tried vesa and all other options the same.  As soon as I type startx the moniter stops reciving any signal, similar to the safe graphics mode of 6.06.1.

Any ideas?

---

### Post by bergsore on 2007-02-22
I appear to have networking capability (at least, I can ssh into remote computers.)  Might it be possible for me to download different drivers such as the proprietary one from ATI?
Is this a good idea?

Would trying X org instead of xfree86 make any difference?

---

