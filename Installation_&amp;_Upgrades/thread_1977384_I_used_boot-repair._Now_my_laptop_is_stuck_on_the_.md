---
title: "I used boot-repair. Now my laptop is stuck on the grub screen. How do I boot?"
date: 2012-05-10
forum: Installation &amp; Upgrades
---

### Post by rockinruler on 2012-05-10
I have ubuntu 10.4 and win 7 installed. Because of a problem windows 7 wouldn't load but ubuntu would load.

I wanted the grub2 menu to be the default boot menu and i thought [boot-repair]("http://ubuntuforums.org/showthread.php?t=1769482") would do the needful for me. I just opened boot repair and clicked on 'recommended repair' with the default settings left unchanged and now I'm stuck on the grub menu with the black screen.

How do I get the previous config back?

---

### Post by xyzzyman on 2012-05-10
[http://ubuntuforums.org/showthread.php?p=11919924#post11919924](http://ubuntuforums.org/showthread.php?p=11919924#post11919924)

You dropped your computer from 3.5 feet in the air. Your HDD is shot and you're lucky nothing else is broken. You need to get a new HDD, and stop running this drive ASAP before it's too late to recover any data that may not be already backed up somewhere's.

---

### Post by mips on 2012-05-10
> **xyzzyman said:**
> Your HDD is shot and you're lucky nothing else is broken. You need to get a new HDD, and stop running this drive ASAP before it's too late to recover any data that may not be already backed up somewhere's.

Some people prefer not to listen. They will keep on working on a drive until there is no hope of any recovery.

---

### Post by rockinruler on 2012-05-10
> **mips said:**
> Some people prefer not to listen. They will keep on working on a drive until there is no hope of any recovery.

Some people could be more helpful if they'd not let being presumptuously self-righteous be their natural reaction to everything.
And even if I WAS planning to stick with the drive till there's no hope of any recovery, you don't know the first thing about the resources I have to deal with my problems, of course, since *it's none of your business.*

> You dropped your computer from 3.5 feet in the air. Your HDD is shot and you're lucky nothing else is broken. You need to get a new HDD, and stop running this drive ASAP before it's too late to recover any data that may not be already backed up somewhere's.

Yes, I'm lucky indeed. Before I get a new disk, I need to copy the things that are important, of course. Which is why I tried to get grub to be the default bootloader and got stuck with this.


Anyway, should anyone be stuck with the same problem and not want to see pseudo-judgemental comments and advice that weren't asked for in the first place, these are the instructions I followed :
[http://www.lancelhoff.com/restore-grub2-after-installing-windows/](http://www.lancelhoff.com/restore-grub2-after-installing-windows/)

---

### Post by flemur13013 on 2012-05-10
[http://www.lancelhoff.com/restore-gr...lling-windows/]("http://www.lancelhoff.com/restore-grub2-after-installing-windows/")

It's nice to have those instructions a bit more clear and concise:

+++
How to Restore GRUB2 after installing Windows:

    Boot from an Ubuntu Live CD/USB.
    Open a Terminal.
       $ sudo su 
       $ fdisk -l (Find Linux partition, ie /dev/sda1)
       $ mount /dev/sdx# /mnt  (x# = actual device and partition number)
       $ mount --bind /dev /mnt/dev
       $ mount --bind /proc /mnt/proc
       $ cp /etc/resolv.conf /mnt/etc/resolv.conf (copy from CD to HD).
       $ chroot /mnt
       $ grub-install --recheck /dev/sdx (x = actual device)
       $ reboot (to Linux w/o Live CD)

Upon reboot you should be presented with a GRUB2 menu, 
but with Windows missing:
    - $ sudo update-grub 

*If* it worked, Windows should show in grub.
+++

---

### Post by xyzzyman on 2012-05-11
In the future, instead of trying to repair a bootloader or data on a disk that is on its way out, you are best accessing it from a livecd, preferably mounted manually set as read-only, as any corruption can be made worse be even small writes depending on where the problem is. (I say this having dealt with hundreds of dying drives for customers over the years where I was their last hope as they wouldn't be able to afford a service like OnTrack that can remove the platters.)

---

### Post by rockinruler on 2012-05-12
> **xyzzyman said:**
> In the future, instead of trying to repair a bootloader or data on a disk that is on its way out, you are best accessing it from a livecd, preferably mounted manually set as read-only, as any corruption can be made worse be even small writes depending on where the problem is. (I say this having dealt with hundreds of dying drives for customers over the years where I was their last hope as they wouldn't be able to afford a service like OnTrack that can remove the platters.)

That's helpful. Thanks.

---

