---
title: "Ubuntu will not boot without USB plugged in"
date: 2011-01-06
forum: Installation &amp; Upgrades
---

### Post by Shival on 2011-01-06
After I select to boot Ubuntu (I dual boot Vista Ultimate 64.), it just sits at a black screen with the blinking dash.
Cannot enter anything and it will just sit there. But if I plug in my Flash Drive it will boot into Ubuntu either before starting the computer or while Im stuck in the black screen.
Plugging in the drive while I am in the black screen will make it boot right up. The drive will light up and a couple lines that quickly say something will show up on the screen and then it boots.
This Flash Drive contains Ubuntu and is what I used to Install Ubuntu.

---

### Post by presence1960 on 2011-01-06
With the flash drive plugged in:

Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

 This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by ajgreeny on 2011-01-06
When you installed ubuntu, where did you put grub?  In most cases it would be put onto the MBR of the internal disk, ie your Vista disk, and that isprobably where it is at the moment.  However, all the configuration files for grub are in the ubuntu install on the usb, so if that is not attached grub fails.

Download and install the boot-info-script shown in my signature and it will help sort out the problem.  Follow the instructions on the sute and post back the RESULTS.txt file here in code tags, ie, highlight the txt file and hit the # top right in the reply box.

---

### Post by Shival on 2011-01-07
Alright, got it

---

### Post by Shival on 2011-01-07
Alright, got it

---

### Post by Shival on 2011-01-07
Alright, got it

---

### Post by Shival on 2011-01-07
Alright, got it

---

### Post by Shival on 2011-01-07
Alright, got it. It didn't ask me anything about Grub when I installed.

---

### Post by Shival on 2011-01-07
Alright, got it. It didn't ask me about GRUB when I installed.

Edit] Forums were not working right so I kept trying to get my post to go through. Guess it worked....

---

### Post by oldfred on 2011-01-07
Forum went berserk and started double posting.

Your BIOS seems to promote the flash drive to sda. If you try to boot from your 120GB does it work? I have two 160GB drives and in BIOS have to sometimes try both. If looks like the windows will not boot as you do not have a boot flag on sdc1, so that drive may be the one not booting.

If not boot into Ubuntu and reinstall grub to sdb. Double check that it still is sdb, as you want grub2 installed to the MBR of the drive with Ubuntu.

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub
to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

Again confirm with fdisk that the windows drive is sdc.

set boot flag on for sdc1 (off on others)
sudo sfdisk -A1 /dev/sdc

Then in BIOS one 120GB drive should boot Ubuntu and the other 120GB drive should boot windows. Set default to boot Ubuntu drive and you can choose Ubuntu or windows, but if you ever have troubles with the Ubuntu drive you should be able to boot windows by changing BIOS.

---

### Post by Shival on 2011-01-11
I do have two hard drives and I have windows and Ubuntu on the same drive and the other hard drive is my media so int he event I loose my OS drive, all of my media goodies are still safe since the OS Hard-drive it ran the most it would be the most likely to fail.

[Sorry for the slow reply. I am going through a move.]

---

### Post by oldfred on 2011-01-11
That is fine, but some like to have an operating system on every drive, just in case to be able to boot. I have 4 systems (winxp, & 3 versions of Ubuntu) on three drives with each able to boot and each with some data. Of course I also have several repair Linux CDs & a full install on  a flash drive that boots. 

Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)

---

### Post by arch0njw on 2011-06-07
> **oldfred said:**
> 
if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub
to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

Again confirm with fdisk that the windows drive is sdc.

set boot flag on for sdc1 (off on others)
sudo sfdisk -A1 /dev/sdc


Good. Grief.

But this fixed exactly the same issue for me.  So why does the installer put GRUB on the USB stick and not on the HDD?


Thanks for the very helpful steps!!!

---

### Post by rubixcubix on 2012-05-01
Hello,
Please see my results file attached.  I have the same issue where I can only boot with usb drive on my Lenovo S10 netbook with Ubuntu 12.04.

Thanks all

---

### Post by Sabariesh on 2012-05-08
Use the commands given by Oldfred. It worked exactly for me

---

