---
title: "Getting thrown to Grub 2 console, boot not working"
date: 2020-04-13
forum: Installation &amp; Upgrades
---

### Post by savique on 2020-04-13
Hi everyone,

Recently built a new PC for machine learning work, and so have the following setup:

1x SSD = Windows 10
1x SSD = Ubuntu 18.04
1x 4TB = Windows work data
1x 4TB = Ubuntu work data

These are all internal drives. When I bought the PC last week, the shop helped me load Windows 10 on the first SSD, and then I installed Ubuntu 18.04 myself on the 2nd SSD. All was working well -- Grub would load upon startup, and Ubuntu was the default, whilst I could pick Windows 10 if I wanted. 

However today everything broke -- Grub auto-loaded Ubuntu after turning on, and then at the login screen I just clicked the restart button because I wanted to access Windows. However I got thrown to the Grub console, and nothing seems to be working to get back into either OS. 

Here is the output from Boot-Repair (I used a live USB to "Try Ubuntu") to install it:

[http://paste.ubuntu.com/p/W2jWXJfsW3/](http://paste.ubuntu.com/p/W2jWXJfsW3/)

Some notes:

1. I didn't change anything recently, the only thing I can think of was that I restarted Ubuntu from the login screen *without* logging in first
2. I tried following some Stack Overflow answers:
[https://unix.stackexchange.com/questions/329926/grub-starts-in-command-line-after-reboot](https://unix.stackexchange.com/questions/329926/grub-starts-in-command-line-after-reboot)
But that didn't work -- after typing "normal" or even trying "boot" after setting prefix and root gives me "you need to load the kernel first"
3. Ctrl Alt Del and holding F12 doesn't work
4. Changing the boot order in the BIOS (holding DEL) to put the Windows HD first doesn't work, still end up at the Grub Console*
*Short note about this, my BIOS is a little confusing, and it's unclear which is my Windows HD or even if it is showing up there. I've moved things around but I can't confidently say "this doesn't work" because even though I have shuffled the drives around, it doesn't seem to be loading.
**Second note about this, booting into Ubuntu from my USB ("Try Ubuntu") and browsing the file system does show all 4 harddrives there, so it doesn't seem like a HD failure
5. Running "Boot Repair" gives me an alert: "GPT detected, Please created a BIOS-Boot partition....then try again"
6. The /boot folder on my Ubuntu SSD partition is empty (sdb2/boot)
7. The Grub folder is on a different Ubuntu SSD partition (sbd1/Grub)
8. The shop folks installed Windows 10 using Legacy Bios instead of UEFI, so when I installed Ubuntu, I did legacy as well (first attempt at Ubuntu installation worked but Windows 10 didn't show up on Grub so I had to switch boot orders in Bios to access each one. Since that seemed inconvenient and it was a new install I just reinstalled Ubuntu again on legacy and all was well, Grub showed both Ubuntu and Windows 10, and everything worked until this morning)

As much as possible, I would prefer not re-partitioning anything, since everything was working fine until today -- could something have corrupted or move some files around? I did install some packages yesterday for a code repo on Github on their requirements.txt: [https://github.com/AliaksandrSiarohin/first-order-model](https://github.com/AliaksandrSiarohin/first-order-model)

Thanks in advance for any assistance -- and sorry if the questions are a little basic, I'm quite new to all this.

---

### Post by savique on 2020-04-13
Some other findings from the Grub 2 command shell (using some tips from here: [https://www.linux.com/training-tutorials/how-rescue-non-booting-grub-2-linux/](https://www.linux.com/training-tutorials/how-rescue-non-booting-grub-2-linux/))

ls (hd1,1) results in:
lost+found/ grub/ and some files including vmlinuz-5.3.0-28-generic and initrd.img-5.3.0-28-generic plus other similar files

ls (hd1,2) results in:
lost+found/ boot/ swapfile/ etc/ media/ var/ and ALSO has some files called vmlinuz (no extension) initrd.img.old initrd.img and vmlinuz.old

ls (hd1,2)/boot/ is empty

ls (hd1,1)/grub has grub.cfg and other files in it

Plus another update: Restarting and pressing F11 gets me to "Please select boot device", but none of the 4 selections (my 4 drives) do anything but bring me back to the Grub console -- so it doesn't seem like a direct boot to Windows is working either.

---

### Post by yancek on 2020-04-13
>  5. Running "Boot Repair" gives me an alert: "GPT detected, Please created a BIOS-Boot partition....then try again"

The message above indicates that you have Ubuntu installed in Legacy mode on a GPT partition.  In that case, you need a "BIOS-BOOT" partition un-formatted, 1-2MB is enough.  See boot repair beginning at line 942.  After doing this, you could install Grub to the MBR of sdb where Ubuntu is installed and then boot Ubuntu and run sudo update-grub. Your windows install on the other drive is also a Legacy install. Also, you will note at the very beginning of the boot repair output that you have Ubuntu Grub code in the MBR of sda which is the windows disk.  Did you mean to do that.  This is the default on almost any Linux install but can be changed during the install.

---

### Post by oldfred on 2020-04-13
The shop did not do you a favor by installing Windows in the old legacy/MBR configuration.
Microsoft has required vendors to install in UEFI/gpt mode since Windows 8 released in 2012. Not sure why they would use legacy?
Windows only installs in BIOS mode to old MBR partitioning and only in UEFI mode to newer gpt partitioning. You would have to totally reinstall Windows to convert to UEFI. But since new system, it may be worthwhile?

Since you have BIOS, you have to maintain a Windows boot loader in the MBR of the Windows drive. And then you want grub in MBR of Ubuntu drive. 
Boot-Repair's autofix installs grub to every MBR, which you do not want. But you can use advanced mode and choose operating system and MBR/drive to install into. 

With newer gpt partitioning, you have to have a bios_grub partition for grub to install into that drive. 
The bios_grub is only 1 or 2MB unformatted with bios_grub flag. Use gparted to shrink any partition by a bit and add the bios_grub partition.
Then use Boot-Repair & advanced mode to install boot loaders.

I started converting my drives to gpt in 2010. All new drives & most larger flash drives are now gpt.
I also added bios_grub originally, but when Windows started using UEFI/gpt, I automatically added both an ESP for UEFI boot and a bios_grub for BIOS boot. Now all my systems are UEFI, except very old laptop, so I do not add bios_grub anymore.

---

### Post by savique on 2020-04-14
@yancek & @oldfred, thank you both for your quick and detailed replies!

I first reset to the original Windows boot loader using the Windows 10 image (steps 1-11 here: [https://askubuntu.com/questions/429610/uninstall-grub-and-use-windows-bootloader/654913#654913](https://askubuntu.com/questions/429610/uninstall-grub-and-use-windows-bootloader/654913#654913)), so I could access Windows 10 at least -- of course doing that, there was no way to access Ubuntu unless I fixed the Grub issue.

Managed to fix it using both your instructions (I'm being extra explicit for my own learning, and also for anyone who might find this as part of their troubleshooting in the future):

1. Have a live USB with Ubuntu image loaded on it 
2. Boot the PC using this USB, selecting "Try Ubuntu" instead of Install
3. Once logged in, connect to wifi, and then open up terminal
4. Type `gparted` and let it scan
5. Once loaded, select /dev/sdb (top right dropdown)
6. I have two existing partitions, /dev/sdb1 and /dev/sdb2
7. I click on /dev/sdb2 and right click, and click "Resize/Move"
8. Followed this for resizing: [https://www.howtoforge.com/partitioning_with_gparted](https://www.howtoforge.com/partitioning_with_gparted)
9. Clicked my new partition (I set it for 5mb), right click, "Manage Flags", and checked "bios_grub"
10. Followed this for boot-repair: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
10a. Installed boot-repair via terminal, and used "Advanced Options", did NOT install grub into all master boot records (mbrs), but rather chose "sdb" (which is where my Ubuntu lives. sda is where my Windows 10 is.)

This is the final output:
[URL="http://paste.ubuntu.com/p/x96GmnMHNr/"]
http://paste.ubuntu.com/p/x96GmnMHNr/[/URL]

It said there was an error, but when I restarted it, I managed to boot into Ubuntu directly.

Finally, I went into my BIOS (Holding DEL on my computer upon starting), went to the Motherboard Settings, and changed the boot priority so that my Windows drive is first, and Ubuntu drive is second.

Now, when I turn on the PC, Windows is default, and if I want to use Ubuntu, I can restart and hit F11 when starting to pick the different drive that Ubuntu lives on.

@oldfred, I had considering completely wiping both drives since they are still new, and reinstalling Windows 10 using UEFI and then Ubuntu again, so still might do that before this month is over. I guess there's a long term downside to keeping it on legacy BIOS? 

@yancek, the reason grub was on /dev/sda was that when I installed Linux, that was the default selection on "where to install the bootloader" section, and I found a Stack Overflow post that said not to change that, so left it as is. I now know that was perhaps not the right decision. Is it fair to say that in a case like this (2 separate physical drives, one operating system per drive), the best case is to install the bootloader onto the drive with Ubuntu?

Any thoughts on why this happened? Seems like Windows might be the culprit, I thought I had disabled automatic updates, but looks like it tried and failed to install something yesterday per the update logs (4/13). It's unlikely Ubuntu did something on it's own to mess up Grub? Though I am curious why my (hd1,1) had two vmlinuz and initrd: [COLOR=#000000]vmlinuz-5.3.0-28-generic & [/COLOR][COLOR=#000000]vmlinuz-5.3.0-46-generic and [/COLOR][COLOR=#000000]initrd.img-5.3.0-28-generic & [/COLOR][COLOR=#000000]initrd.img-5.3.0-46-generic and if there was an Ubuntu update that was downloading/installing and got interrupted somehow. 

Thank you both again for your help![/COLOR]

---

### Post by savique on 2020-04-14
I'm reading and trying to understand the latest output in the paste I shared, just for my own learning: [http://paste.ubuntu.com/p/x96GmnMHNr/](http://paste.ubuntu.com/p/x96GmnMHNr/)

1. Seems like the error was because it couldn't mount the USB drive with the linux image? That seems fine
2. The two linux and memory images seem to be referenced in the menuentry for "Advanced Options for Ubuntu", so the older version (28) can be accessed?
3. Windows didn't end up getting added to the Grub menu, that's ok for my purposes since I'm using F11 myself, but would be good for me to understand why. 
4. Grub timeout style in grub.cfg is set to "hidden", I think I've changed this before to `menu`, which should get the menu to pop up automatically, unless I keep it as hidden, and seems like I can get the menu to show anyway if I type a key upon loading
5. grub_timeout in grub.cfg also seems high, since I'm not using it to access windows anyway, might as well reduce the time to 2 seconds or something?

---

### Post by oldfred on 2020-04-14
Windows updates turn fast start up back on. And the Linux NTFS driver will not see the NTFS partitions, so grub will not add Windows to boot menu. With Windows best to set Windows system partition as read only and mount in fstab, and create a separate shared data NTFS partition for read/write access from both systems. But fast start up sets hibernation on all NTFS partitions, so you must keep that off.
Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

You add Windows to grub menu with this:
sudo update-grub

Boot-Repair is running a variety of Linux commands. Those often do not like the live installer, especially if the hybrid DVD/flash drive configuration that does not have partitions. And if partitions, they are usually not typical. So those errors are normal.
Grub install showed error code 0 or no  error which means it installed correctly. 

Ubuntu now keeps two kernels. So when upgraded, if you have some sort of issue with new kernel you can still choose older one in grub. It used to keep all kernels, unless you manually housecleaned. And some configurations with a small /boot partition then had issues.

You can reset time in grub boot menu to 2 or 3 seconds.  But then have to be quick to press shift key to get into grub.
With BIOS install, you press & hold shift key to get grub menu, right after BIOS screen. And with UEFI you press, usually multiple times, the escape key. Timing can be an issue. Do not set to 0, as then you may never get into grub menu.

Also UEFI has fast boot, required by Windows as well as Windows own fast start up. That is because Windows boots so slow. New systems with SSD have resolved a lot of those issues, its still slow but not as bad as hardware overcomes the slow boot.

If BIOS works, you can use it. Its just that new hardware is UEFI and that offers some advantages. And gpt partitioning has advantages over the old MBR. But those are not really major, unless your partition table breaks. MBR has no backup, gpt does. But if you have good backups of both systems, then you do not have to worry.

I saw several years ago Intel was going to suggest elimination of CSM by 2020. Obviously not happened. But just saw again the Intel says next generation should be UEFI only. Current systems would not be affected. But If you install new hardware, the drivers for BIOS & UEFI are different. At some point, new hardware may not work with BIOS systems.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

You should not have to reinstall Ubuntu since already on gpt drive. You need ESP - efi system partition 100 to 500MB FAT32 with esp &/or boot flags. And then total reinstall of grub, which replaces BIOS grub - grub-pc with UEFI grub - grub-efi-amd64.

With BIOS install, you get option on where to install grub boot loader, default is always first drive. The UEFI install screen is the same, but the option on where to install boot loader does not work, always first drive. Bug in Ubuntu Ubiquity installer. There are work arounds, or reinstall grub with manually or with Boot-Repair.

---

### Post by savique on 2020-04-17
Thanks for the help! Will continue tinkering and learning.

---

