---
title: "Meerkat - repair or remove ?"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by grey1beard on 2010-10-14
Having briefly tried the live cd for meerkat on my amd64 desktop, I tried to do an install of 10.10 with the amd64 iso alongside an existing xp pro system.
I set it to repartition my 80gb drive to 20gb for the xp and ~60gb for the meerkat.
After a reported error during the language packages install - 
"Sub-process/usr/bin/dpkg returned error code 1"
 - the instalation almost immediately crashed, and as requested I sent an error report.
However, as the sceen had frozen it was impossible to attach  /var/log/syslog and /var/log/partman, and could only add what iso I had been trying to use.

I then started again, and discovered that the partitioning has occurred, and if I run the live cd, I can see the two file systems, and can access /var/log, but neither /syslog nor /partman exist in the /log file.

On the meerkat desktop I can see the "Install Ubuntu 10.10" icon, but what should I try to do now ?
Should I be trying to remove the partial installation, so that I can start again, or repair it ?
I have only a little experience of 8.04, and am only just starting to learn my way around the terminal etc, so I'd be grateful for a roadmap of what next.
John

---

### Post by mikewhatever on 2010-10-14
What do you mean by repair? I don't remember such an option exists on the installation cd, which leaves you with reinstalling.

---

### Post by grey1beard on 2010-10-15
> **mikewhatever said:**
> What do you mean by repair? I don't remember such an option exists on the installation cd, which leaves you with reinstalling.

When I re-inserted the live cd, and started to reinstall, the partitioning choice I was faced with was of two 10.10 partitions.
This was how I found that the first attempt had already partitioned the hdd.
While I didn't try to set one to zero, which I suppose might have overwritten the first attempt, I went on to find that I had access to it.
Perhaps it was naive of me to think that I could repair what had not installed correctly. I certainly had no idea if it was possible or not, hence my question here.

If it's not possible to repair, how do I get rid of the previous attempt, bearing in mind that I wish to keep the xp partition intact ?
John

edit - I have an online connection for the the desktop, if it helps.

---

### Post by garvinrick4 on 2010-10-15
Put the install cd back in and choose Try Ubuntu. When it boots up
the desktop to Applications/Accessories/terminal when terminal opens:copy and paste
```
sudo fdisk -l
```
Find the linux install you want to use or reinstall to.
If it is sda5 for example.
Hit the install Ubuntu on desktop and choose manual install.
When it comes to where you want to install click on the sda5 (use yours) check format ext4 and choose / 
If was a small partition already made it is for swap.
So click on that partition and choose swap.
Do not need swap if over 2 gigs of RAM so if it tells you that you
have no swap and you have over 2 gigs ignore,
Make sure you put grub (bootloader) in sda not sda1 or sda5 but sda
the drive and it will put grub in mbr (master boot record) where it belongs. Install and when it is done boot into your Ubuntu and
copy and paste this.
```
sudo update grub
```
Makes a new grub-config and puts all your installs in grub menu.

You can see your partitions in gparted if you need to.
System/Admin/gparted in Live CD (install cd)

---

### Post by grey1beard on 2010-10-15
Many thanks for the road map.
I'll get some breakfast under my belt, and have a go.
John

---

### Post by grey1beard on 2010-10-15
May your pot never empty.

Meerkat is now happily blinking in the new dawn.
John

Edit
It may be significant(or not) that for my first attempt I had ticked the "update during install", and the "proprietary drivers" boxes, and that I was working online with my laptop at the same time.
Second time around I left them unticked, and kept the laptop offline.

---

