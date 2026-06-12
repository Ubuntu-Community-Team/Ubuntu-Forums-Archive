---
title: "Booting from external HDD w/partition, NTLDR error"
date: 2015-09-13
forum: Installation &amp; Upgrades
---

### Post by dan192 on 2015-09-13
So i've read through several threads, retried the steps numerous times, but i am still getting this error. 

I am using a Lenovo running W7. BIOS and using F12 to select boot choice. 8gigs of ram. Since i have a solid state HDD internal i am a bit pressed for space which is why i want to run the system from my external drive.  HDD is USB 3. 

I am running, and posting right now, through Ubuntu Live from a USB stick. I have run the instal procedure both from the ubuntu desktop and from the splash screen before the live trial. 

I set my swap area to 8gigs, and my ubuntu partition is 32gigs, (sdb3 formatted to ext4). The remainder of the 1tb is made up of backups etc. The bootloader drop down was also set to this location., 

When i look at the drives on the ubuntu desktop i can see that all files, including GRUNT, appear to have installed correctly. 

No matter what i try, i get the NTLDR error. I know i dont have a problem booting from USB devices both because i am running from a USB device right now, and also because i checked the BIOS settings and made sure that Legacy USB support was enabled (the closest thing i could find to USB bootability). 

Thanks for any help
dan

---

### Post by yancek on 2015-09-13
> The bootloader drop down was also set to this location., 

If you mean 'sdb3' as the location to which you installed the bootloader, that's your problem.  If you wanted to boot Ubuntu from the external you should have installed the boot code to /dev/sdb which would put code in the MBR pointing to sdb3, the Ubuntu partition.  Are you saying you get the "NTLDR is missing" error when you try to boot windows and Ubuntu?  That would be pretty unusualy as that is a windows boot file.  If you still have the Ubuntu Live/Install medium, boot it and go to the site below and download boot repair per instructions there and when you run it, select to Create BootInfo Summary to post here.  Do not try to make any changes.  If you are feeling adventurous, go to the second link below which explains several methods which can be used to repair the bootloader, one of them being to use boot repair.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by dan192 on 2015-09-14
I ended up just reformatting the partition, but in any event the bootloader placement fixed the problem. 

Thanks

---

