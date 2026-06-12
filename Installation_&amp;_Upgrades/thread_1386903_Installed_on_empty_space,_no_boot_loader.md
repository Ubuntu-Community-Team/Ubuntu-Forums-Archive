---
title: "Installed on empty space, no boot loader"
date: 2010-01-21
forum: Installation &amp; Upgrades
---

### Post by crasius on 2010-01-21
After checking the install disk is error free, I installed 9.10 on half a HD that was unused, unformatted, completely empty.  The other half has a windows XP Pro install on it.

I had to use safe graphics mode to avoid a black screen on install. I have a Nvidia card in a MB with onboard graphics.  Bios is set to use graphics card.  Safe graphics worked, and the install was uneventful.  Under the advanced tab, I left the defaults for the boot loader.  It looked like it was defaulted to install the boot loader, but I may be wrong.

On boot up now, windows comes up, bu no boot loader.

I tried booting from the live distro to make sure/reinstall bootloader, but I need to be able to start that up in safe graphics mode to be able to see anything on the screen.  How can I do that?

Any other ideas?

Am I even on the right track.  Isn't installing on an empty partition setting up for dual booting?

---

### Post by darkod on 2010-01-21
Yes, you did right installing into the unallocated space. I'm very confused too. And I don't know how to solve the graphics problem which is needed to boot the live desktop and install grub on the MBR.
A temporary solution might be to set in BIOS your onboard card to be used, it might work better with ubuntu livecd. After you install grub on the MBR you can put things back in BIOS.

PS. Don't forget to plug the monitor into the onboard card connector. :)

---

### Post by presence1960 on 2010-01-21
At this screen hit F4 and select safe graphics mode.

---

### Post by crasius on 2010-01-21
Thanks for the fast reply.  I will drag out the old vga  monitor and give that a try.  I wanted to make sure I going down the right path before the heavy lifting began. ;)

---

### Post by presence1960 on 2010-01-21
It would be best if we can see your setup & boot process before you make any adjustments. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by crasius on 2010-01-21
Thanks for the showering of help.  I tried something else and learned something new.

I have two HDD with two windows installations... an old XP install I'm keeping for while in case I find I need a file that I thought I already transferred to the new install, and a new XP install on a new hard disk on which I only formatted and used half of anticipating the other half for Ubuntu.

I have the boot sequence set to boot the new windows install on the new disk, but because it is not on the first SATA connector, it is not the C drive.

So what happened was Ubuntu installed onto the C drive.  It didnt have any "unused space"..... the whole disk was one partition for windows.  So I guess what it did was take the largest unused space of that windows partition and repartition to make two.

Booting from that disk by changing the boot sequence brings up the boot loader perfectly.  I don't want it that way, but no harm done.

The new disk is 500 GB.  I used 250 for one partition for the windows install.  I want Ubuntu to install on the remaining 250 GB.

I will change the SATA connections to make the new hard drive the "C:" drive, or first hard drive.

If I select the Guided - Use the largest continuous free space option, is it going to install on the empty part of the disk, or is it going to repartition the windows partition... something I don't want because although it would work, I'll run out of room.

---

### Post by presence1960 on 2010-01-21
> **crasius said:**
> Thanks for the showering of help.  I tried something else and learned something new.

I have two HDD with two windows installations... an old XP install I'm keeping for while in case I find I need a file that I thought I already transferred to the new install, and a new XP install on a new hard disk on which I only formatted and used half of anticipating the other half for Ubuntu.

I have the boot sequence set to boot the new windows install on the new disk, but because it is not on the first SATA connector, it is not the C drive.

So what happened was Ubuntu installed onto the C drive.  It didnt have any "unused space"..... the whole disk was one partition for windows.  So I guess what it did was take the largest unused space of that windows partition and repartition to make two.

Booting from that disk by changing the boot sequence brings up the boot loader perfectly.  I don't want it that way, but no harm done.

The new disk is 500 GB.  I used 250 for one partition for the windows install.  I want Ubuntu to install on the remaining 250 GB.

I will change the SATA connections to make the new hard drive the "C:" drive, or first hard drive.

If I select the Guided - Use the largest continuous free space option, is it going to install on the empty part of the disk, or is it going to repartition the windows partition... something I don't want because although it would work, I'll run out of room.

Glad you got it sorted out!

The boot info script would have showed which disk has GRUB on it and what boot # that disk is. If you want to learn about your setup and the relationship of your devices to booting then run it on your machine and go over the contents of the RESULTS.txt file. it contains a plethora of info about your setup & boot process.

---

### Post by darkod on 2010-01-21
> **crasius said:**
> 
I have two HDD with two windows installations... 

If I select the Guided - Use the largest continuous free space option, is it going to install on the empty part of the disk, or is it going to repartition the windows partition... something I don't want because although it would work, I'll run out of room.

Crucial piece of advice you should have told us. :)

Yes, Use Largest Free space .... will install ubuntu into the largest unallocated space on the hdd, what you want. It will not touch your windows partition at all. At least it shouldn't.

---

### Post by presence1960 on 2010-01-21
> **darkod said:**
> **_Crucial piece of advice you should have told us. :)_**

Yes, Use Largest Free space .... will install ubuntu into the largest unallocated space on the hdd, what you want. It will not touch your windows partition at all. At least it shouldn't.

That is exactly why I insist on running the boot info script prior to giving suggestions to fix a boot problem. Whether unintentional or not most people's description of their setup a lot of times is not what is actually on their machine.

---

### Post by crasius on 2010-01-21
> **darkod said:**
> Crucial piece of advice you should have told us. :)

Yes, Use Largest Free space .... will install ubuntu into the largest unallocated space on the hdd, what you want. It will not touch your windows partition at all. At least it shouldn't.

Then why did it?  I thought it was impossible that it installed on the old hard drive.  There was no free unused space there.  There was blank space inside a windows partition, but that is not free disk space... and it did not leave the windows partition untouched, it would not have had enough room without resizing the windows partition.

---

### Post by darkod on 2010-01-21
> **crasius said:**
> Then why did it?  I thought it was impossible that it installed on the old hard drive.  There was no free unused space there.  There was blank space inside a windows partition, but that is not free disk space... and it did not leave the windows partition untouched, it would not have had enough room without resizing the windows partition.

I really can't say. I haven't been able to try, but I think the following would work:
If the ubuntu installer is "suggesting" different hdd than the one you want, temporarily select the Erase and use whole disk option, that will enable a drop down list under it. Select the correct disk in that list. After that change the option to the one you want, like Use Largest Free space, or Install Them Side-by-Side, etc.

Except for the above idea, I don't know how to switch to another disk if the one you want is not selected by default.

---

### Post by crasius on 2010-01-21
Well thanks for the help.... I'm leaning toward just biting the bullet and scrapping the old XP installation, and let Ubuntu take the whole disk.  That was the plan in the long run, I just have to get over the fear that there is something on that old install I need.

I know it is done all the time, but I am not comfortable with Ubuntu resizing my existing windows partition....  to much risk.

---

### Post by presence1960 on 2010-01-21
> **crasius said:**
> Well thanks for the help.... I'm leaning toward just biting the bullet and scrapping the old XP installation, and let Ubuntu take the whole disk.  That was the plan in the long run, I just have to get over the fear that there is something on that old install I need.

I know it is done all the time, but I am not comfortable with Ubuntu resizing my existing windows partition....  to much risk.

Partitioning is not done by Ubuntu, it is done by gparted. 

As with any OS installation/partitioning operations it is suggested you back up your data prior to doing so. If you have the time you can make an image of your OSs with clonezilla prior. But as with any installation/partitioning operation there will be errors from time to time. That is just the nature of the beast. Stuff happens, but MOST of the time those operations are uneventful and go as planned. It is not Ubuntu's fault. 

If you have windows Vista or 7 you should not resize your windows partition with a third party partitioning software due to a yet unresolved [bug]("http://bugzilla.gnome.org/show_bug.cgi?id=379482"). It is best to resize Vista/7 partition with windows disk management utility.

---

