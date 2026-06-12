---
title: "Can't Access Ubuntu After Win10 Update"
date: 2016-10-16
forum: Installation &amp; Upgrades
---

### Post by justin.m.kincaid on 2016-10-16
After much difficulty, I managed to get my new Acer Aspire E15 to dual boot Windows 10 and Ubuntu 16.04 a little over a week ago. Things were great, I was able to access GRUB during the boot cycle and choose which OS I wanted to run. 

Then three days ago Windows 10 forced their latest update on me. I was mildly annoyed, but didn't think much of it. Today I tried to access my Ubuntu install for the first time since the Windows 10 update and my laptop acts like GRUB doesn't exist. I've spent the past hour googling possible solutions, but everything I've found either references an older version of Windows, a different flavor of Ubuntu, or is a year plus old. 

What information do I need to provide in order for others to help me with this issue? I'm very comfortable with Windows, but fairly Linux illiterate and installed it so that I could learn how to navigate it a bit better, so please use small words.

---

### Post by gdesilva on 2016-10-16
Looks like Windows update has replaced grub with its own bootloader (used to be ntldr in Win 7). 

If you are using the old BIOS and not UEFI the following should fix your issue. I have not reinstalled grub in an UEFI environment so DO NOT follow the following instructions!! You have been warned!

Try booting the machine off a liveCD of Ubuntu and run gparted to make sure all your partitions are in tact. Note down the name of the ubuntu partition.

Open terminal in the LiveCD session and run sudo -s to gain super user access.

Now mount the linux partition, eg

# mount -t ext4 /dev/sdaX /mnt  (-t option tells the linux file system type. sdaX - here X is the partition number of your linux and /mnt is where the partition will be mounted)

then reinstall grub on your hard disk

# grub-install --boot-directory=/mnt /dev/sda (this will use the grub image files in your linux partition and install them on your hard drive boot sector)

Reboot the machine from the HDD and you should now see the grub menu.

---

### Post by justin.m.kincaid on 2016-10-16
Thank you for the reply. I'm currently using UEFI, so I didn't follow your instructions, but the following seemed to work. Grub now loads appropriately.

Here's an update of what I tried (in chronological order):

1. Confirmed that Fast Boot is off.
2. Booted via USB and clicked on Try Ubuntu Without Installing. Ran BootRepair's Recommended Repair option. Everything seemed to check out and I was given a link, but the link doesn't work for some reason.
3. In Windows 10, I ran Command Prompt as an Admin and ran the following command:
--a. bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
--b. It echoed "The operation completed successfully"

Here's additional information:
1. During boot up, when I go to my BIOS, there's the following information:
--a. Boot Mode: UEFI
--b. Secure Boot: Disabled
--c. Boot Priority Order: HDD1, HDD0, Windows Boot Manager, USB FDD, USB HDD

---

### Post by gdesilva on 2016-10-16
This might be of use...

[http://askubuntu.com/questions/349526/how-to-set-grub-default-not-windows-boot-manager](http://askubuntu.com/questions/349526/how-to-set-grub-default-not-windows-boot-manager)

---

### Post by gdesilva on 2016-10-17
Hi, great to see that you solved the problem. Curious to know what the solution was....it might help others with similar issues. Thanks

---

