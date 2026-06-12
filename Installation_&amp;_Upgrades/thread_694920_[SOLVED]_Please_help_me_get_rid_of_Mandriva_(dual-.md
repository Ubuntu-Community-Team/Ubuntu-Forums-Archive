---
title: "[SOLVED] Please help me get rid of Mandriva (dual-boot)"
date: 2008-02-12
forum: Installation &amp; Upgrades
---

### Post by abyssius on 2008-02-12
I have two linux versions on my 80-gig hard-drive (a) Madriva 2008 and (b) Ubuntu Studio. When I installed Mandriva (for some masochistic reason), it trashed my original Ubuntu install (probably because I messed up the boot-loader routine in Mandriva). Anyway, I eventually had to re-install Ubuntu Studio in order to get both Mandriva and Ubuntu to work properly (dual-boot).

I would like to get rid of Madriva entirely and dedicate the entire hard-drive to Ubuntu. However, I'm not confident that I can accomplish what I want to do without damaging my Ubuntu Studio install a second time. I've included a snapshot from GParted that shows my configuration. 

[IMG]http://www.cinesage.com/Gparted.gif[/IMG]

As it stands right now, 18.09 gigs is dedicated to the /dev/sda4 boot partition (I don't know how or why). Ubuntu is on /dev/sd3 with 20.12 GiB available. And, Mandriva is on /dev/sda1, using 32.60 GiB.

My desire is to make the entire hard-disk dedicated to Ubuntu, without having to re-install it again. Please can anyone help me? Ubuntu is so superior to Mandriva, I don't ever want to see that version of Linux again.

---

### Post by HappyFeet on 2008-02-12
this should be done with live cd
open terminal.
> sudo su
> gparted
> umount /dev/sda1
> umount /dev/sda4
then click on sda1 and delete partition
repeat for sda4.
click sda3 and choose resize.
hit apply after each step in gparted.

---

### Post by forestpixie on 2008-02-12
I had to do similar - although I didn't have 3 swap partitions :) , I used the livecd gparted rather than the buntu livecd

This is the order I dealt with mine using a [gparted]("http://gparted-livecd.tuxfamily.org/") livecd - it might also be worth getting [supergrub]("http://supergrub.forjamari.linex.org/") if you haven't got it

1 - delete partitions you don't want

move ubunut partition to the left

deal with the swap partitions - if you don't need 3 - which I don't think you do delete all 3 swap partitions and then delete or resize, (or not as the case maybe - can't remember with extended) the extended partition to the size you want the swap to be and create a swap partition inside the extended partition

at this point you should have your ubuntu partition on the left and the extended partition on the right with empty space in the middle - make a new partition in the middle, format to ext3

If not - delete the extended swap partitions so you have just the ubuntu partition

now you should have a big space - create your new partitions inside that - one formatted as ext3 then an extended with swap inside it

at that point you should have 3 which I assume is what you're after


When you reboot fstab is probable going to try to mount them and it won't be able to - I got an fsck error 8 I think - Ctrl+D got me in

then you can get the UUID information in order to get the partitions mounting properly

```
blkid
``` will get the UUID information you'll need to edit fstab

```
sudo cp /etc/fstab /etc/fstab.bak
``` to backup

```
gksudo gedit /etc/fstab
``` to edit fstab

If you do get a boot problem - use the supergrub livecd to reinstall grub, also might be worth changing the boot flag - but not sure about that

Hope that's of some help - even if it does take all night to read

---

### Post by abyssius on 2008-02-12
Thanks go to HappyFeet and forestpixie. I had to use both recommendations to get my system up and running with a single partition. HappyFeet's instructions allowed me to delete unwanted partitions and resize the partition as I requested. However, upon reboot, I was confronted with an [Error 20] message and a system halt. Luckily, I took forestpixie's advice and downloaded supergrub. I rebooted with the supergrub live CD and was able to fix the problem  (I chose the automatic process).

Strangely, it seemed to revert back in time to a setup I had a few days ago. The desktop showed a background image I set two days ago (and since replaced). The new image I created and assigned to the desktop was gone - as was some of my MIDI files I worked on yesterday. In addition, the update manager required me to install upgrades that I was sure I completed earlier today before the partition resize. 

Anyway, no great harm was done since I backed up all my data files before embarking on this. I think I am going to make a pledge to myself not to experiment any further with other Linux operating systems - until I learn more about Linux in general, and Ubuntu in particular. I'm a newbie from the windoze world - and so far, I'm thrilled with Ubuntu and the talented advisers on the Ubuntu forum. :guitar:.

---

