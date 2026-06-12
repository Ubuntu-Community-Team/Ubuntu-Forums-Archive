---
title: "1 of 3 drives not detected when installing dual boot"
date: 2018-07-27
forum: Installation &amp; Upgrades
---

### Post by michael_krueger2 on 2018-07-27
I have 3 drives on PC and want to install Ubuntu on an empty SSD but it won't let me pick it.  But if I go into the advanced partitioning part I can see the SSD. I don't want to do the partitions myself cuz I don't know what I am doing.  Do I need to do something to the SSD before I try to install?

---

### Post by Autodave on 2018-07-27
You need to create at least one primary partition on that disk. Now you can let the installer do the work for you if all you are putting on that disk is Ubuntu. Let the partition be for the full disk size.

---

### Post by oldfred on 2018-07-27
You do need to know if system is UEFI or BIOS and then be sure to boot installer in that mode.
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

And autoinstall with multiple drives may not install to location you think, it really is better to use something else, choose partition on new drive with change button or create partition for / (root) as ext4. That is about the only difference.
[https://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](https://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
 
If BIOS you also want grub2's boot loader on new drive. It will default to first drive it sees otherwise.
      
 Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing) 
    
Another option is to just unplug other drives and then installer will only have the option to install to drive you want. You still need to be sure to match boot modes UEFI or BIOS of other drives.

---

### Post by michael_krueger2 on 2018-07-27
Ok, thanks I will try that.

---

### Post by michael_krueger2 on 2018-07-27
I must have done something wrong because ubuntu installed but when I restart just goes to windows.  I went into the UEFI to see if I could set the ubuntu drive to boot first.  But it is not in the list and it is also missing when I look at my drives while in windows.

---

### Post by oldfred on 2018-07-27
What brand/model system?
Some require work arounds.
Did you update UEFI, many work better now as vendors update UEFI.
If an Acer you need to set trust. If HP, they almost always seem to need a work around.
See links in my signature, if you want to read ahead.

---

### Post by michael_krueger2 on 2018-07-28
My PC:

ASRock Fatal1ty X370 Gaming K4
AMD RYZEN 7 1700
EVGA GeForce GTX 1080 Ti
SAMSUNG 960 EVO M.2 250GB (this has Windows on it)
WD Black 4TB (I use this for games and files) (I unplugged this drive because it was trying to install here)
Samsung 850 EVO 250GB (I want to put Ubuntu on this)

I didn't update my UEFI but my pc is not that old do you think I should still do this?
How do I take screenshots when I am installing Ubuntu? 
I had to google what a grub and a bootloader were so as you can tell I don't know anything. I did look at your links it is just hard for me to grasp how to apply to my situation.

---

### Post by oldfred on 2018-07-28
You need to regularly update UEFI, kernels (which both Windows & Ubuntu have done) and routers.
There are various virus and issues that need you to update. And recently some more varients  have been found and will require updates as soon as fixes are available.

With nVidia you will at least need nomodeset until proprietary driver is installed. And your Ryzen may need other boot parameters also.

       Asus B350M-A needs newer kernel that 18.04 default
[https://ubuntuforums.org/showthread.php?t=2391892](https://ubuntuforums.org/showthread.php?t=2391892)
MSI Tomahawk B350 with Ryzen R5 1600 New UEFI required
[https://ubuntuforums.org/showthread.php?t=2390475](https://ubuntuforums.org/showthread.php?t=2390475)
ASUS PRIME B350M-E major issues
[https://www.phoronix.com/scan.php?page=news_item&px=AMD-Raven-Ridge-Mobo-Linux](https://www.phoronix.com/scan.php?page=news_item&px=AMD-Raven-Ridge-Mobo-Linux)
ryzen acpi=off only 1 cpu, needs nomodeset & then nVidia driver instead
[https://askubuntu.com/questions/951630/fix-ubuntu-16-04-issue-with-gigabyte-ga-ab350-motherboard-and-amd-ryzen-cpu](https://askubuntu.com/questions/951630/fix-ubuntu-16-04-issue-with-gigabyte-ga-ab350-motherboard-and-amd-ryzen-cpu)
Asus Prime X399-A  with AMD Ryzen 1950X  Ubuntu 16.04.3
[https://ubuntuforums.org/showthread.php?t=2380798](https://ubuntuforums.org/showthread.php?t=2380798)

---

### Post by michael_krueger2 on 2018-07-28
Thanks for the help Oldfred but I think I will scrap the Ubuntu install.  It seems Ubuntu is not ready for my PC and I am not ready to do what it take to get it working.  It is just over my head.

---

### Post by oldfred on 2018-07-29
You still should update UEFI and probably best to update firmware on SSD. Both Windows & Linux have updated kernels.
That would be for Meltdown and Spectre CPU vulnerabilities from cpu speculative execution and caching. And they kept finding new variants so future updates probably required also.

---

