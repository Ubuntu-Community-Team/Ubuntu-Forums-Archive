---
title: "Dapper destroys LVM's?"
date: 2006-07-30
forum: Installation &amp; Upgrades
---

### Post by dizm on 2006-07-30
I just made it from breezy to dapper.  After giving up on a standard upgrade, I did a fresh install on a clean drive.  But somewhere alone the way my original breezy drive's LVM got damaged.

How can this happen, and how to fix it?

Here's what happened:  I started with a fairly robust, stable and up-to-date breezy install on a 200GB SATA drive in an Intel P4 with 1GB ram.  I had one physical 10GB boot partition and the rest an LVM with four logical partitions.

I first tried clicking 'upgrade' on the default update manager, but got some-or-other complaint.  So I looked around more and then did 'apt-get update', 'apt-get upgrade' and then 'apt-get dist-upgrade'.

Several MB later (and detail omitted) I had what looked like a nice clean dapper. Until I rebooted.  Grub (I think it was grub) said it couldn't find my root partition.

So I dropped down to the earlier kernel (2.6.15-23 vs 2.6.15-26).  This kernel could see the (logical) root partition, but the boot froze up somewhere around LVM load time.

Thereafter that drive would never boot!

I then did a fresh install on a clean drive, and of course dapper is great.  But my logical partition on the other drive is unreadable.  I can mount the boot partition (under dapper), but qtparted sees the lvm as "unformatted".  fdisk does report it as 'Linux LVM', so there seems to be something there.

I also tried booting the breezy live CD, but breezy sees the same thing as dapper.

Is it all gone?  Could I repair the partition table somehow?

(yes, I did back up all my critical stuff, but what is life without non-critical stuff?)

---

### Post by keithweddell on 2006-07-30
I don't think qtparted can read LVM partitions so it just tells you they are unformatted.  Try another livecd - something like Systemrescuecd - which includes LVM support.  It sounds as if the partitions are still there so you just need to find a way to access them.

If you need to do future Ubuntu re-installs, bear in mind that the default installer doesn't handle LVM - you need to download the Alternate Install CD.

Keith

---

### Post by dizm on 2006-07-30
thank you keith.  

but... 

i do have LVM installed; perhaps it came in with kubuntu?

i have now made a system cd, and still qtparted reports unformatted.  i continue to poke and prod blindly!

any more tips would be appreciated!

---

### Post by keithweddell on 2006-07-31
Ubuntu supports LVM but AFAIK the default installer/upgrader doesn't.  That's why you need to use the Alternate Install CD when you have an LVM filesystem. 

OK Try this (commands need to be entered as root):

Boot from your liveCD - eg SystemRescueCD or RIP

Enter at Command Line "vgscan" (without quotation marks)
This should find your LVM Volume Group if it is still working.
(If the command is not found your livecd doesn't support LVM and you need to try another one).

Enter at Command Line "vgchange -a y" (again w/o quotation marks)
This should activate the Logical Volumes

Enter at Command Line - "lvscan" (w/o ...)
This should find and display the Logical Volumes

If all is OK so far, it should simply be a case of making mount directories and mounting the LVs. eg

mkdir /mnt/test1
mount /dev/mapper/VolGp-LV /mnt/test1

You should then be able to copy off any data you want.  If the LVs are screwed and you can't get this far, I'm afraid you're going to need more expert help than I can give.  Good luck.

Keith

---

### Post by dizm on 2006-07-31
Ok, I recovered my lost lvm's!
Here's how:

lvscan revealed that all of my LV's were marked INACTIVE. ???  So there were no corresponding /dev/'s, and of course they could not be mounted.

I bounced lvm (thanks Joe): 
 sudo /etc/init.d/lvm stop
 sudo /etc/init.d/lvm start

Now vgscan showed ACTIVE lv's.  So for my one volume group (vg0) and each logical volume (lv-n) i could do (as root):
 mkdir /mnt/lv-n
 mount /dev/vg0/lv-n /mnt/lv-n

Then I copied everything over to a safe (non-LVM) drive, and in future I'm going to learn more about stuff like LVM before I use it!

Of course I should have used the Alternate Install CD, but who was to know?

My fresh install (then update, then install kubuntu) had full LVM support.  I did make a SystemRescueCD but I didn't have to use it.

Thanks Keith, and also my nephew Joe.
Yay Dapper!

---

### Post by dlane on 2006-09-19
Just a quick note - I found this thread when I was trying to figure out how to recover after a Dapper update left me in the same boat (hang at "mounting root filesystem").  The difference between my setup and most that are discussed on this forum, is that the system uses software RAID 1 (mirrored disks) with LVM on top of that.  So I have md0 and md1 devices, with /boot being on md0, and an LVM group "ubuntu" being on md1.  The ubuntu group has root, var, swap, and home volumes.  

I found, after using the **alternative** Dapper boot install CD (which is what I used to install the software RAID and LVM in the first place) in rescue mode (selected the "rescue mode" option rather than "server install" or "LAMP install", etc. at boot time).  I mounted the root volume, which the rescue mode system offered to me as /dev/ubuntu/root, and then I ran /target/sbin/vgscan (note: /target is the directory under which the rescue mode shell mounts the desired volume) and confirmed this was the right volume.  I then mounted /dev/md0 (my boot partition, not managed by LVM) - mount /dev/md0 /mnt - and used nano to edit the /mnt/grub/menu.lst.  For some reason, during the most recent upgrade (which included installing a new linux kernel, etc.), it changed the root device in the kernel boot line to "/dev/hda1" and I didn't know what it had previously been.  When I simply changed - root=/dev/hda1 -> root=/dev/mapper/ubuntu-root - everywhere it occurred in the menu.lst file, saved the file, and rebooted. All was well!!

So to summarise: used rescue mode on a bootable CD to determine the logical  volume names on the system - including my root volume: /dev/ubuntu/root - I translated that name (not sure if this is necessary) to the more generic LVM mapping lingo: /dev/mapper/ubuntu-root - and then replaced the kernel boot line which incorrectly listed root=/dev/hda1 with /root=/dev/mapper/ubuntu-root, saved, rebooted.  Voila.  

If you happen to know the LVM volume names on your system, then you can do this all from the grub prompt simply by hitting ESC and editing the kernel   line in the grub configuration and then fixing /boot/grub/menu.lst after your system boots normally...

Hope that helps someone.

---

