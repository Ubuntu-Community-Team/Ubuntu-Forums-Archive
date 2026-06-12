---
title: "efibootmgr error during Ubuntu 18.04 Server installation"
date: 2018-04-28
forum: Installation &amp; Upgrades
---

### Post by kjg291 on 2018-04-28
I am running into a problem towards the end of a fresh install of Ubuntu 18.04 Server and it appears to have something to do with efibootmgr and the boot order. I have attached pictures of the log. I apologize for the poor picture quality, but I do not know how to take a screenshot while in the installation screen. Any help is appreciated. Thank you in advance!

[https://i.stack.imgur.com/am1tI.jpg](https://i.stack.imgur.com/am1tI.jpg)

[https://i.stack.imgur.com/fZIaI.jpg](https://i.stack.imgur.com/fZIaI.jpg)

[https://i.stack.imgur.com/84IMA.jpg](https://i.stack.imgur.com/84IMA.jpg)

---

### Post by oldfred on 2018-04-28
Note familiar with new live server installer.
Can you run Boot-Repair from it, or do you still need Desktop installer to run Boot-Repair.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Error seems to be related to invalid entry in boot order. You may be able to delete from within your UEFI or with this command line entry:

 # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr

---

### Post by kjg291 on 2018-04-28
Thank you oldfred.

I tried BootRepair and was unable to complete all the steps. Here is a screenshot: [https://imgur.com/a/21Nl8fM](https://imgur.com/a/21Nl8fM)

In the terminal, I also tried your suggestions with efibootmgr and here are those screenshots: [https://imgur.com/a/1AKva7k](https://imgur.com/a/1AKva7k) and [https://imgur.com/a/BmwRYss](https://imgur.com/a/BmwRYss)

Here is some background which may or may not be useful. I had been running Ubuntu 17.10.1 Server for several months with no issues on this laptop which is an HP Envy dv6-7247cl. Before a clean install of 18.04 Server, I replaced the 750GB HDD that came with the laptop originally with a brand new 256GB HP S700 Pro SSD.

I'm somewhat of a novice to Ubuntu, so I'm not sure if I have followed your suggestions correctly. Please let me know if I'm doing anything wrong. Thank you again in advance.

Edit: I am including a screenshot of my laptop's BOOT options for what it's worth: [https://imgur.com/a/LfqHqRs](https://imgur.com/a/LfqHqRs)

---

### Post by oldfred on 2018-04-28
You do not show 2003, now, so then you would not be able to delete it.
Not sure if that was error or not now.

Could not really tell on Boot-Repair screen.When you had Ubuntu working before, was it a BIOS install or an UEFI install?
How you boot install media UEFI or BIOS is then how it installs.

Can you manually boot the Ubuntu entry. You have a couple. Shim entry should work whether UEFI secure boot is on or off. Entry using grubx64.efi will only work if Secure Boot is off.

Can from Boot-Repair are you able to run the Summary Report?

HP is not particularly UEFI dual boot friendly. But many work arounds. Details in link in my signature on work arounds.

---

### Post by kjg291 on 2018-04-28
Thank you oldfred.

There is no important data on this new SSD, so I have no problem just starting all over from scratch. The reason is I have tried to install 18.04 more than once, sometimes with and without Legacy Support enabled under BIOS options and sometimes with and without Secure Boot enabled.

The very first installation was version 18.04 after installing the new SSD yesterday, but I cannot remember whether Legacy Support was enabled or not and I also think that I had used the BIOS and UEFI option when making the bootable USB in Rufus. That installation failed with the error message saying boot entry 2003 was missing as seen in the screenshot in the original post.

Is it possible to start a clean install from scratch all over again with Legacy Support disabled as well as Secure Boot disabled, as if the SSD had just been installed in the laptop? What steps would you recommend I follow to get rid of boot entries such as 2003, which are preventing the installation from completing successfully but cannot be found and removed by efibootmgr?

Before posting this, I did try a clean install again with Legacy Support and Secure Boot disabled and selected the MBR partition scheme for UEFI option in Rufus for the bootable USB and once again, the installation failed with the 2003 boot entry error. Do you have any suggestions on what I am doing wrong?

Thank you again for your help.

---

### Post by oldfred on 2018-04-28
My desktop motherboard requires UEFI only to let me boot flash drive in UEFI mode. Even UEFI or CSM/Legacy/BIOS mode only actually boots in CSM mode.
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  


Some have posted (mostly Dell) that CSM must be on, but you still can boot in UEFI mode. And for some reason it wants it on.
Most systems seem to need CSM/Legacy off to enable UEFI boot.

You can use gparted to delete partitions.
Or if you want same / (root) you can just select it as new / (change button) and use as / , ext4 and check format box.

Recently I have only installed in UEFI boot mode with Secure Boot off. And I make sure drive is gpt using gparted and partitioning in advance.

       It is recommended to use always GPT for UEFI boot as some UEFI firmwares do not allow UEFI-MBR boot. 
   For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap(prior to 17.10), but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]25-30+ GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical (not required with 17.04 and later uses a swap file, if no swap partition found)
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by kjg291 on 2018-04-29
Thank you oldfred.

Here is what I did to try to implement your suggestions. With Legacy Support and Secure Boot disabled, I booted with an Ubuntu 18.04 Desktop Live USB stick and used gparted to delete all the partitions on the SSD. I then created a FAT32 partition of size 512MB with boot and ESP flags and a second EXT4 partition with the remaining disk space. I rebooted and used another USB stick with Ubuntu Server 18.04 created by using the GPT Partition Scheme for UEFI in Rufus. And once again, the installation failed at the same location as seen in the image in my first post ([https://i.stack.imgur.com/84IMA.jpg](https://i.stack.imgur.com/84IMA.jpg)).

So I decided to give up and install the server version (size of 704MB) of 18.04 from this link: [http://cdimage.ubuntu.com/ubuntu/releases/18.04/release/](http://cdimage.ubuntu.com/ubuntu/releases/18.04/release/), which fortunately went from start to finish without any problems and I can log in to the terminal. I'm still really confused why the version from the main downloads page (size of 806MB) fails to install completely.

Thank you again oldfred for all your help. If you manage to figure out the problem, I would definitely like to know what it is. :)

---

### Post by oldfred on 2018-04-29
There are now two server installers.
The new subiquity version is the new graphical version, but may not have all the bugs worked out yet.
You maybe should file a bug report against the server install version you used.
They will want logs, but do not know if you still have any of those.

Was this your bug report?
If not post that it applied to you also.
[https://bugs.launchpad.net/subiquity/+bug/1767584](https://bugs.launchpad.net/subiquity/+bug/1767584)

---

### Post by kjg291 on 2018-04-30
Thank you oldfred.

Unfortunately, I don't have the logs anymore, but I have posted in that thread.

Thank you for all your help in trying to figure this out.

---

