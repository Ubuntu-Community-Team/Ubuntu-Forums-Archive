---
title: "tri boot configuration question"
date: 2008-11-28
forum: Installation &amp; Upgrades
---

### Post by graysky on 2008-11-28
I'm about to resize/create a new 20 gig partition for Intrepid Ibex and am looking forward to playing with it.  My question deals with the correct way to install/partition my disks to keep my existing two O/S's intact.

I have two disks:

Disk1 contains two NTFS partitions for my XP system and one EXT3 partition (/boot).

Disk2 contains my three Debian Lenny partitions (root, home, and swap) and a large NTFS partition.

I installed my /boot (grub) to disk1 so that if disk2 ever crashed, I could still boot into XP.  My plan is to shrink the NTFS partition on Disk2 by 20 gigs to use as my root for Ubunutu 8.10 (have to delete it, make an extended and several logical partitions, but it's doable).

Question #1: I'm assuming I can keep my /home and /swap that Lenny uses to share with Ibex.  Is this correct?

Question #2: Does the the Ubunutu installer ask me what I'd like to do with grub like the Lenny installer does?  If so, is it best to segregate Lenny's /boot from Ibex's /boot?  I can just put Ibex's /boot on Ibex's / partition.

Question #3:  What's unclear to me is what I should actually do with grub via the Ibex install.  Should I have it take no action and manually add some entries for Ibex or will the installer handle it just fine, writing to Lenny's menu.1st on Lenny's /boot?

Question #4: Do I need to add a bootable flag to the Ibex boot partition, and if so, can one have two partitions flagged as bootable on the same disk?

Suggestions are welcomed and thanks in advance!

---

### Post by confused57 on 2008-11-28
> **graysky said:**
> I'm about to resize/create a new 20 gig partition for Intrepid Ibex and am looking forward to playing with it.  My question deals with the correct way to install/partition my disks to keep my existing two O/S's intact.

I have two disks:

Disk1 contains two NTFS partitions for my XP system and one EXT3 partition (/boot).

Disk2 contains my three Debian Lenny partitions (root, home, and swap) and a large NTFS partition.

I installed my /boot (grub) to disk1 so that if disk2 ever crashed, I could still boot into XP.  My plan is to shrink the NTFS partition on Disk2 by 20 gigs to use as my root for Ubunutu 8.10 (have to delete it, make an extended and several logical partitions, but it's doable).

Question #1: I'm assuming I can keep my /home and /swap that Lenny uses to share with Ibex.  Is this correct?

Question #2: Does the the Ubunutu installer ask me what I'd like to do with grub like the Lenny installer does?  If so, is it best to segregate Lenny's /boot from Ibex's /boot?  I can just put Ibex's /boot on Ibex's / partition.

Question #3:  What's unclear to me is what I should actually do with grub via the Ibex install.  Should I have it take no action and manually add some entries for Ibex or will the installer handle it just fine, writing to Lenny's menu.1st on Lenny's /boot?

Question #4: Do I need to add a bootable flag to the Ibex boot partition, and if so, can one have two partitions flagged as bootable on the same disk?

Suggestions are welcomed and thanks in advance!

1.)Probably not a good idea to share your Lenny /home with Intrepid, but sharing the same swap is a good idea.

2.)During the installation of Intrepid, you can click on the "Advanced" button in the lower right & change the location of where grub's IPL is installed.  Make a note of how the installer recognizes your / partition(/dev/sdbx), you'll want to type in /dev/sdbx in place of the default (hd0).

3.)I would recommend adding a chainloader to Lenny's menu.lst to boot Ibex:
```
title  Intrepid 8.10
root (hdx,y)
chainloader +1
```
replace (hdx,y) with your partition designation, e.g. /dev/sdb3 would probably be (hd1,2).

4.)No, you don't need the bootable flag on Intrepid.

---

### Post by graysky on 2008-11-28
> **confused57 said:**
> 1.)Probably not a good idea to share your Lenny /home with Intrepid, but sharing the same swap is a good idea.

2.)During the installation of Intrepid, you can click on the "Advanced" button in the lower right & change the location of where grub's IPL is installed.  Make a note of how the installer recognizes your / partition(/dev/sdbx), you'll want to type in /dev/sdbx in place of the default (hd0).

3.)I would recommend adding a chainloader to Lenny's menu.lst to boot Ibex:
```
title  Intrepid 8.10
root (hdx,y)
chainloader +1
```
replace (hdx,y) with your partition designation, e.g. /dev/sdb3 would probably be (hd1,2).

4.)No, you don't need the bootable flag on Intrepid.

#1 - Not a good idea... why not?  (Honestly don't know, not trying to be impossible).

#2 and #4 - Thanks for the suggestion, I'll try this when I do the install.

#3 - Why did you suggest that I chain load it?  Can you elaborate on this?  I figured I would just add a few entries under my Lenny lines for Ibex... no?

For reference, here is my working /boot/grub/menu.1st (I edited out most of the commented lines):

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		8

# Pretty colours
color cyan/blue white/blue

splashimage=(hd0,2)/grub/splashimages/debsplash.xpm.gz

title           Windows XP Professional x64 Edition
root            (hd0,0)
#savedefault
makeactive
chainloader     +1

### BEGIN AUTOMAGIC KERNELS LIST

title		Debian GNU/Linux, kernel 2.6.26-1-amd64
root		(hd0,2)
kernel		/vmlinuz-2.6.26-1-amd64 root=/dev/sdb2 ro quiet vga=792
initrd		/initrd.img-2.6.26-1-amd64

title		Debian GNU/Linux, kernel 2.6.26-1-amd64 (single-user mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.26-1-amd64 root=/dev/sdb2 ro single
initrd		/initrd.img-2.6.26-1-amd64

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by confused57 on 2008-11-29
This thread may give more insight into sharing a home partition:
[http://ubuntuforums.org/showthread.php?t=871240&highlight=share+home](http://ubuntuforums.org/showthread.php?t=871240&highlight=share+home)

This also should explain how chainloading works for booting a different distro:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

---

