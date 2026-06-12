---
title: "system hangs on first boot"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by RyanGT on 2005-10-13
I have Hoary installed on a USB hard drive.  I am trying to do the same with Breezy.  The main problem is that there are detailed instructions on how to do this for Hoary using mkinitrd (the boot image needs ehci_hcd module).  Breezy doesn't come with mkintird (I guess it uses mkinitramfs instead).  I think I have actually over come this part.  I will include what I did here in case someone sees a problem:
I used a list of modules from a Fedora post:
ehci-hcd
usb-storage
scsi_mod
sd_md

I added these to /etc/mkinitramfs/modules.  Hoary only needed ehci_hcd, but that didn't seem to work with Breezy.  The Hoary instructions had a place where a delay needed to be added, but I couldn't find any place to put it in Breezy (I think it went in mkinitrd.conf).  (The fedora module list was for mkinitrd).

I then did:
mkinitramfs -o /boot/initrd.img-2.6.12-9-386 /lib/modules/2.6.12-9-386
(from a shell off of the rescue CD).

After adding all of the modules listed above (to /etc/mkinitramfs/modules), I finally stopped getting the error that /dev/sda8 (the Breezy root) could not be found.

I now see a splash screen and Breezy appears to boot.  I see messages about mounting the root file system, configuring the network, syncing system clock...  All are OK.

The system then flashes the words Configuring Base System and then goes to a blue screen that says Installing Packages \\ Preparing for installation... and hangs at 0%.  (I don't know if this is related, but during the install, I said no to installing the remaining packages from the CD.  This seemed like it made installing Hoary take a really long time and I thought I could add packages one -by-one as I needed them.)

So, the system now sits at preparing for installation ... 0%.

Any Help?

Ryan

---

### Post by RyanGT on 2005-10-13
I think I am declaring victory.  I did another install not using the expert method and it did not give me a choice whether or not to install the extra packages from the cd.  It did hang once and I had to restart it, but I am now running breezy from my usb hard drive.  Unless someone else who knows more about mkinitramfs can point out something that should be done differently, I think this is a valid procedure.

I basically followed the steps from post #2 in this thread:
[http://ubuntuforums.org/showthread.php?t=20522](http://ubuntuforums.org/showthread.php?t=20522)
Quoting:
1) Install from CD 
>>(do a basic install hitting <enter> at the first prompt)
>>FYI: I set up all my partitions including /boot as logical - I wasn't sure this would work but couldn't add more primary partitions to the drive
>>It seems to have worked perfectly.
2) After installation, leave CD in drive and reboot with the parameter rescue
3) Pick your language and country
4) Wait for hardware detection to complete(was quite long on my system, seemed stuck for a while)
5) hostname: Ubuntu <enter>
6) Device to mount as root file system: /dev/discs/disc0/part2 (this may be different on your system. I have a boot partition in part1)
7) My system appears stuck here with a blue screen saying "Ubuntu Installer rescue mode"
>>my system was not stuck but I still needed to type Ctrl-AltF2<<
8) Ctrl-Alt-F2 <enter>
9) mount -tproc proc /target/proc
10) chroot /target
11) su (optional, gives you a few niceties in term of shell)
12) If you have a boot partition: mount /dev/sda1 /boot

From here it is slightly different for mkinitramfs (Breezy) as opposed to mkinitrd (Hoary):
A. edit /etc/mkinitramfs/modules to add the following:
ehci-hcd
usb-storage
scsi_mod
sd_mod

(nano didn't seem to come with Breezy, so use vim)

B. determine your kernel info:
ls /lib/modules

for the Breezy cd on 10/13/05 mine was 2.6.12-9-386, yours may be different.

C.  make the new image file:
mkinitramfs -o /boot/initrd.img-<kernel version>-usb /lib/modules/<kernel version>

so for me that was 
mkinitramfs -o /boot/initrd.img-2.6.12-9-386-usb /lib/modules/2.6.12-9-386
(if you use tab completion, it will find the default initrd, just don't forget to add the -usb or you will overwrite the existing initrd - which you may or may not care about since it is likely unbootable if it is on a USB drive but doesn't have the modules needed.)

From here, you can go back to the old how to:
17) If you have mounted a boot partition: umount /boot
18) Exit from chroot: exit
19) umount /target
20) reboot

You will likely need to edit your grub.conf file.  My usb hard drive comes up as the second hard drive so grub calls it (hd1).  Here is my grub.conf entry to boot off of sda7 with sda8 as root (you can probably figure out what partitions are what from fdisk -l in rescue mode).

title Ubuntu Breezy (2.6.12-9-386) USB
    root (hd1,6)
    kernel /vmlinuz-2.6.12-9-386 root=/dev/sda8 ro quiet splash
    initrd /initrd.img-2.6.12-9-386-usb
    savedefault

---

### Post by 11hjpphty76lkjj on 2005-10-14
Good job!!  I have confirmed that this works.  I get to use breezy now! hooray!!

YOU ARE MY HERO!!!!!!!!!!!!!!!!!!!

Aaron

---

### Post by andrewsawyer on 2005-10-18
Heya,

Quick question - if you have got this all up and running, and you have Ubuntu 5.10 running from a USB drive, is there any way to make it 'live'?

Thanks in advance,

Andy

---

### Post by RyanGT on 2005-10-18
I do have it all up and running.  What do you mean by 'live'?

Ryan

---

### Post by andrewsawyer on 2005-10-19
Hiya,

By 'live' I mean that it is bootable on more than one computer - like a LiveCD. I've looked through a good few of the threads, and posted in some of them too, however no-one has been able to help me.

Cheers,

Andy

---

### Post by DecIRC on 2005-10-27
Andrew,

I'm looking exactly the same thing.
But no way to find it :( :(

A way of thinking : install it on a hd. Install Slax scripts to make a live CD
and then make the iso file bootable on the hd, like damnsmall linux, I think....

---

### Post by andrewsawyer on 2005-10-27
There is a thread [here]("http://ubuntuforums.org/showthread.php?p=448906#post448906") about getting a LiveUSB, where there are some ideas floating around.  I don't think anyone has actually got it working yet, but still - there are some suggestions that might help.

---

### Post by RyanGT on 2005-10-28
I don't know if anyone has done it with Ubuntu, but I saw a blurb on Slahdot a while back about someone selling a 3 gig flash drive with Linux installed and marketing it as a portable personal computing environment.  So, someone, somewhere, on some distro has it figured out.

---

### Post by DecIRC on 2005-10-28
[http://www.pertec.com/](http://www.pertec.com/)

(sorry it's in french)

It's effectively done, with Ubuntu, but it's commercial :(
So hard to get the source....

Cedric

---

### Post by CHUCKYCHUCK on 2005-12-30
hi ! i just bought an external hard drive, and i 'm wondering if it is possible to just install the /boot folder in the internal disk, and all the others in the external one ?
maybe this would not cause any of the problems as the ones described above ?

thanks

---

### Post by RyanGT on 2006-07-11
I think installing just the boot folder on the internal harddrive should work.  Have you tried this already?  Did it work?

Thanks,

Ryan

---

### Post by hikeb on 2007-09-25
I would be so cool to have this up and running. I mean having a on the go ubuntu external hd. The problem i'm having when connecting my hd on other computers is that X11 is not starting correctly. I think that it wants to use the same settings from the computer from which i installed ubuntu on to my external hd. Does any one know how to make it go to some generic settings for X if it doesn't work with the default ones?

---

