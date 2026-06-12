---
title: "How to dual boot over windows..."
date: 2008-10-27
forum: Installation &amp; Upgrades
---

### Post by comingbackdown on 2008-10-27
Howdy y'all.
I've got two computers running. One is a Dell Dimension 2400, the other is custom built.

Mine is the custom built one, my parents have the dell.
So, here's the situation.

There's a 100gb HDD in the dell, and a 160 and a 40 in the custom.

The 100 is slow, the 40 is fast. I want to wipe the 100 in my parents' computer, swap it out with my 40 (which is my secondary)

Here's the deal.

I want to install Ubuntu on my machine on the 100gb HDD.

Here's the problem. I already have XP installed on my main HDD on my machine. I've been told that it's difficult to install Ubuntu after XP. Can anybody walk me through it? I'm running XP Home SP2 on my machine, on my primary 160 GB HDD. I'd be installing Ubuntu on the 100, which would be my secondary.

So, walk me through this. I really don't want to rebuild a perfectly good XP installation just to double-boot.

Many thanks,
-Trillium

P.S., I'd be installing 8.04 for Ubuntu. :guitar:

---

### Post by Elfy on 2008-10-28
Swap the hardware - boot with the livecvd - either a boot menu or make sure that bios is set to boot cdrom first.

Once you get to the partition part of the procedure - choose use whole disk - choose the correct one, likely that it will be labelled sdb- it will format and create the partitions it needs.

If you prefer make the partitions with the editor - system admin menu and choose manual - it's what I do, you have more control.

Making sure that you have picked the right drive - delete existing partitions.

Swap size - if you need to hibernate then swap must equal or be greater than RAM - otherwise 1.5XRAM if less than 1Gb, or 512MB if greater than 1Gb

Create 3 partitions

ext3 - 15Gb
ext3 - remainder - swap
swap - see above for size

Once the partitions have been created close the partition editor and start the install.

Once it reaches the partition stage choose manual - you will be given a list of all partitions on bothe drives - again don't touch the windows drive.

Pick the 15Gb partition - edit - pick ext3 from the Use As menu and / from the Mountpoint menu

Pick the other ext3 partition - edit - pick ext3 from the Use As menu and /home from the mountpoint menu.

Continue with installation.

---

### Post by caljohnsmith on 2008-10-28
I would definitely follow forestpixie's advice, but just one small caveat: Grub will by default be installed to the MBR (Master Boot Record) of (hd0), also known as /dev/sda, which will most likely be your Windows internal drive. The advantage of this is you don't have to do anything special to get the Grub menu on start up after you reboot, if all goes well. The big disadvantage is that your drives are dependent on each other for booting, so if anything happens to either of them (including simply disconnecting the Ubuntu drive), you will not be able to boot either Windows or Ubuntu.

Personally I would recommend installing Grub to the MBR of your Ubuntu drive, leaving your Windows drive untouched, and then set your BIOS to boot the Ubuntu drive on start up instead of the Windows drive. And of course you can add an entry in your Grub menu to boot your Windows drive. This has the advantage that if anything happens to either drive, you can still boot the other one. If you want to do it this way, then when you get to the last stage of the Ubuntu installation, click the "advanced" button, and tell Grub to install to /dev/sdb or whichever is the Ubuntu drive. That's all there is to it. 

Good luck and let us know how it goes. :)

---

### Post by Elfy on 2008-10-28
Which is all well and good assuming that a boot from option is available easily without having to enter bios to edit it - not all pc's have the option.

I've never had a problem with grub - that I didn't cause myself:)

---

### Post by comingbackdown on 2008-10-31
> **caljohnsmith said:**
> I would definitely follow forestpixie's advice, but just one small caveat: Grub will by default be installed to the MBR (Master Boot Record) of (hd0), also known as /dev/sda, which will most likely be your Windows internal drive. The advantage of this is you don't have to do anything special to get the Grub menu on start up after you reboot, if all goes well. The big disadvantage is that your drives are dependent on each other for booting, so if anything happens to either of them (including simply disconnecting the Ubuntu drive), you will not be able to boot either Windows or Ubuntu.

Personally I would recommend installing Grub to the MBR of your Ubuntu drive, leaving your Windows drive untouched, and then set your BIOS to boot the Ubuntu drive on start up instead of the Windows drive. And of course you can add an entry in your Grub menu to boot your Windows drive. This has the advantage that if anything happens to either drive, you can still boot the other one. If you want to do it this way, then when you get to the last stage of the Ubuntu installation, click the "advanced" button, and tell Grub to install to /dev/sdb or whichever is the Ubuntu drive. That's all there is to it. 

Good luck and let us know how it goes. :)

Ummm.... I'll try it... If anything screws up, I'll be back, guaranteed. If nothing goes wrong, I'll obviously mark it solved... If something makes it go to hell in a handbasket, I'll be back... I also have an Nvidia GPU to deal with... Now, my friend said he got his 8 series to work with 8.04 no problem... I hope I have the same luck. :) If not, I shall return...

---

