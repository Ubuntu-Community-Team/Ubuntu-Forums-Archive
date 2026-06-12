---
title: "No bootable device insert boot disc and press any key error [13.04 &gt; 13.10]"
date: 2014-01-16
forum: Installation &amp; Upgrades
---

### Post by Stephanie_Litchfie on 2014-01-16
So a few weeks ago, I made the switch from Windows 8 to Ubuntu 13.04.
Whenever I tried to boot my computer, the cursor in the top left corner would flash a couple times, then I'd get a screen saying "No bootable device insert boot disc and press any key".

Somehow, I managed to "fix" the problem using a combination of Boot Repair and something else (I don't remember what that something was). If I let my computer boot normally I'd still get the error, but if I brought up a menu to pick a device, I had the option of "ubuntu" as well as my hard drive and various paraphanalia, so I left it at that.

Fast forward to a couple of days ago, I decided to upgrade to 13.10, and now I'm back to square one. I still get that error message if my computer is left to boot on its own, and the option to choose ubuntu in the boot device menu is no longer there.

Here, have a pastebin:
[http://paste.ubuntu.com/6765350/](http://paste.ubuntu.com/6765350/)

---

### Post by tfrue on 2014-01-17
> GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       194,559       192,512 BIOS Boot partition
/dev/sda2         194,560 1,936,869,375 1,936,674,816 EFI System partition
/dev/sda3   1,936,869,376 1,953,523,711    16,654,336 Swap partition (Linux)

This is trouble. You have an EFI partition along with a BIOS partition. Since you had Win 8 on the computer first, I would say that you probably have a GPT disk and installed Ubuntu with MBR.

What I would do, since you obviously don't care about Window's, is live boot into Ubuntu, download gdisk, format the whole HDD as GPT, create a new partition, then reboot. I would also check your BIOS and make sure that Secure boot, and Fast Boot are disabled, but keep UEFI boot **ENABLED**.

So let's begin!

First, live boot into Ubuntu, easy peasy.

Second, open the terminal and type:
```
sudo apt-get install gdisk
```

Third, after it has finished downloading, type:
```
sudo gdisk /dev/sda
If it ask about using GPT, MBR, or some other option. Use GPT. Which should be 2
o
y
p (If no partitions present, create one)
n
enter
enter
enter
enter
w

```

Reboot into Ubuntu that you want to install, run the command:
```

[ -d /sys/firmware/efi ] && echo UEFI || echo BIOS
```
To make sure that you are booting EFI, or look to see if you have /boot/efi. So type: ls /boot.

Install, and choose "Something Else" select your partition that we created.

And we should be set!

Good luck,
Chris

---

### Post by Stephanie_Litchfie on 2014-01-19
So, no boot partition, no swap partition, just one big one?
I should have mentioned the bios partition is NOT the cause of my problems, I somehow ended up doing that the other day whilst trying to fix this.
I also should have mentioned I had 100GB of stuff on there, but bit late now.

---

### Post by tfrue on 2014-01-19
Back your all your important stuff up, if you haven't wiped the drive so we can simply move the files back over when we're finished installing.

When you run the installer and set the partition, if it's the entire disk or just 50GB, as "/", it will create all the directories needed. /, /boot, /etc, /home, swap, etc.. So we need not to worry about setting those manually.

A lot of people will do special partitions for different directories, which is fine, but I keep it simple most of the time and just have a single partition.

---

### Post by Stephanie_Litchfie on 2014-01-19
It's gone now, but no matter :). Yeah I tried that but it's still not showing up. I'll get another pastebin in about 10 hours, but right now it's bed time.

---

### Post by oldfred on 2014-01-19
You seem to be booting in BIOS/CSM mode, but have a boot flag on your main install. With gpt the boot flag is only on the efi partition to make it the ESP or efi partition with the files for UEFI boot. Not on a main data partition.

You may be able to remove boot flag from sda2, and then boot in BIOS mode. 

The efi partition without efi boot files may be confusing boot.

With very large drives like yours I do like to separate system from data. Or have separate /mnt/data partition or separate /home. Adding /home is a bit more advanced over default install of just / & swap. But offers some advantages. But you then do have to use Something Else or manual install not any auto install options.

I use data partitions, but that is a bit more advanced as you have to create partition separately from install, create mounts, add ownership & permissions and link folders back into /home to make it easy to use.

---

### Post by Stephanie_Litchfie on 2014-01-20
Well I reinstalled it following the instructions above, and then tried reinstalling wiping the disk and installing it, and it works now somehow. Close enough, thanks guys!

---

