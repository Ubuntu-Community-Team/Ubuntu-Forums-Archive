---
title: "how to re-mount /dev/sda"
date: 2014-05-29
forum: Installation &amp; Upgrades
---

### Post by lemonoid on 2014-05-29
Hi all. I have just a slight problem. It has been since 11.04 since I have installed Ubuntu, due to an upgrade in hardware and being lazy with a UEFI system. Anyways, I am getting a different option than I ever had before and I need a little help. When trying to Install, I am told that /dev/sda is mounted and I cannot create, resize, or .__.. new partitions unless I unmount /dev/sda. I had never been presented with this option in older installations, and I was not quite sure what to do. So I selected the option to 'unmount' and then when I got to the next menu with the options to Erase Disk, use LVM, something else, and...... 'Something Else' I was taken aback. I am used to just selecting 'Install Alongside WIndows' or 'Dual-boot with Windows' or whatever that option is. So what I did is I cancelled installation and rebooted back into Windows. I was hoping that would mount /dev/sda back. So I rebooted again, went to Boot Menu and selected my SanDisk Cruzer USB device, which took me back to Ubuntu. I went to Install again, and it went straight to the menu without asking about /dev/sda. I do not know what to do, as I do NOT want to delete Windows. Could someone point me in the right direction? Thanks in advance for your assistance.

---

### Post by westie457 on 2014-05-29
Follow the advice in the posted link here. [http://ubuntuforums.org/showthread.php?t=2208965&p=12945249#post12945249](http://ubuntuforums.org/showthread.php?t=2208965&p=12945249#post12945249)

When you get to install Ubuntu go for the 'something else' option otherwise there is a good chance you will accidentally wipe Windows.

---

### Post by lemonoid on 2014-05-29
> **westie457 said:**
> Follow the advice in the posted link here. [http://ubuntuforums.org/showthread.php?t=2208965&p=12945249#post12945249](http://ubuntuforums.org/showthread.php?t=2208965&p=12945249#post12945249)

When you get to install Ubuntu go for the 'something else' option otherwise there is a good chance you will accidentally wipe Windows.

okay, so you're saying, I don't need to remount /dev/sda partition? and I should simply go into windows mmc to see WHAT size I should shrink it to, then shrink it??Then I go back to Install Ubuntu and create a new partition, now that I will have space? is there anything i should know when creating the new partition? (ie boot flags or anything)   I don't know much about creating partitions (what kind/etc). I have messed with partitions before in Ubuntu but it was a LONG time ago and I really don't like having to do so. I guess I'm scared I'll mess up my system, as I don't know what all the different partitions are when I'm looking at a table. and I guess the /dev/sda partition is the only one I would need to shrink?

---

### Post by oldfred on 2014-05-29
Your sda is your first drive, the first partition on sda would be sda1. Windows in BIOS mode uses two and vendor uses 2 more and that is all the primary partitions you have.
If Windows 8 pre-installed you have gpt partitioning and there is no limit on partitions, but Windows has all the new secure boot, SRT (if you have it) and UEFI or BIOS options.

If Windows is BIOS, you must install Ubuntu in BIOS mode.
If Windows is booting with UEFI, you can install Ubuntu in UEFI or BIOS mode but better to be UEFI.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

If you have BIOS and used all 4 primary.
      
 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.

If UEFI see link in my signature for lots of useful links with screen shots.

---

### Post by lemonoid on 2014-05-29
I do apologize, but that was just a little bit confusing. I think it was mainly the wording. I have read all about UEFI and EFI, I was actually following a AskUbuntu explanation of installing Ubuntu on a UEFI system, that actually finally enabled me to even boot or attempt to install Ubuntu. I went into BIOS and changed boot settings, disabled Secure Boot, disabled FastBoot, I don't have SRT. But after doing that, I was able to boot from flash drive by selecting Boot Order(F12) when rebooting. I have a Gateway 1TB HDD, 8gb RAM, Windows 8 preinstalled, upgraded to 8.1. I guess now, what I'm basically asking (now that I know I do not have to mount /dev/sda again, is do I need to CREATE or CHOOSE from the partitions listed (such as those in your second and third screenshots. For example, I DO plan on allocating about 50GB at least to Ubuntu, so I guess I need to go into MMC and Shrink my Windows, because the main partition for Windows fills up all but about 17GB of the HDD. You did clear up a couple things (I was wondering what the 300MB and a couple other small partitions were). I will take a screenshot really quick of what my partitions look like.

---

### Post by lemonoid on 2014-05-29
sorry the pictures here were too big. so I attached them below.

---

### Post by lemonoid on 2014-05-29
...........

---

### Post by lemonoid on 2014-05-29
here they are.

---

### Post by westie457 on 2014-05-29
Sorry about my last post, that was for something different.
This is the link I should have posted. [http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

Fastboot must be disabled and all forms of sleep/hibernation must be disabled as well,otherwise the Ubuntu installer will get things wrong.

Choosing the 'Something Else' option will give you full control of which partitions you install to.

The Windows partition must be adjusted while Windows is running.

---

### Post by oldfred on 2014-05-29
Best to use Windows to shrink the Windows partition and immediately reboot so it can run chkdsk. Make sure fastboot and secure boot are off as just about any maintenance in Windows and it resets to its defaults which are always on.

Also best to fully backup Windows.

I prefer to create partitions in advance with gparted (never use Windows) and then in something else I choose change to reformat and choose mount such as / or /home. But you can use the + button to add partitions or - to delete them. 

Do not use any auto install options if reinstalling, as then you may really need to backups I suggested above.

---

### Post by lemonoid on 2014-05-29
Thanks to both of you. westie, the post wasn't totally off haha, I still need to edit the size of windows. I think pretty much at this point I know what to do, but just one last thing, when I go to create my partitions for Ubuntu, could you recommend size per partition? and do I need to name the partitions anything in particular??? Like for instance I plan on having at least 50gb of Ubuntu space, should I make a separate partition for that and just call it /home? I guess I need three partitions at this point: the root partition (which I don't know what size to make it), SWAP, and extra home space.

---

### Post by oldfred on 2014-05-29
I made some suggestions in post #4, but it is up to each user to determine how he may use system and that can greatly change partitioning. Even my own optimal partition plan a few years later is not very good as my needs have changed.

---

