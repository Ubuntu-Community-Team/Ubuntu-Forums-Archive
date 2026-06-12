---
title: "Laptop won't boot after an upgrade to Natty Narwhal"
date: 2011-06-05
forum: Installation &amp; Upgrades
---

### Post by LinuxStupid on 2011-06-05
I have a SONY laptop, PCG-7181M model. It came with Windows 7 but I changed the OS to Ubuntu.
Last night it asked me to upgrade to the new version called Natty Narwhal. I had to go to bed so I changed the sleep timer on the laptop to 2 hours, the time it would have taken the upgrade to complete. I woke up and the laptop was off, now only the grub menu shows up and the laptop won't boot. 

**I tried doing this: **
- When the machine boots up, press ‘Esc’ to get to the Grub menu
 - Select one of the “recovery mode” options. This will boot you up to a single-user root prompt.
 - Run “sudo fdisk /dev/sda” (this assumes that your hard drive is at sda)
 - Type “p” to see which hard drive partition is labeled “Linux swap”.  In my case the partition was /dev/sda5. Type “q” to exist fdisk.
 - Type these commands:


sudo swapoff /dev/sda5
 (Use whatever partition was labeled as “Linux swap” in fdisk. For me, this was /dev/sda5)
 sudo mkswap /dev/sda5
 sudo update-initramfs -u


However, it says swapoff failed: Invalid argument.


I know absolutely nothing about the sudo command (or anything else Linux for that matter) and would really appreciate some help!
Sorry this post is so long, I wanted to give as much details as I could.

---

### Post by Rubi1200 on 2011-06-07
Hi and welcome to the forums :-)

In order to get a better overview of the current state of the system please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

