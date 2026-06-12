---
title: "Installation help: Ubuntu only sees fake raid"
date: 2010-01-30
forum: Installation &amp; Upgrades
---

### Post by sunshineacid on 2010-01-30
Here is my problem:

I have 2 drives (WD 160 blacks SATA)
Originally, I installed these with win 7 x64 in a RAID 0 config. Due to craptacular read/write "improvements", I have reimaged my PC to use both drives normally - Native IDE mode.
I reinstalled win 7 on a single drive and have been trying to install ubuntu 9.10x64 on the other, but it only sees a single 320g hdd in a raid 0 stripe (my old config)
Now, from all of the posts I have been reading though, I gather that the empty drive still has the fakeraid settings on it from the old config. How do I correct this?

---

### Post by sunshineacid on 2010-01-30
more searching.

found some code... will this remove the raid information without wiping windows?

sudo dmraid -E -r /dev/sdd
sudo apt-get remove dmraid

Im hesitant to try, as I dont want to wipe my existing windows installation. 

Thanks in advance.

---

### Post by phillw on 2010-01-30
Hi,

in the absence of any specific comfirmation -- hold tight. Grub 1.97beta that shipped with Ubunutu 9.10 is not 'best of friends' with RAID.

I'm no expert on grub, but I would advise caution -- people like presence, drs305, bean123 would be better placed to help you. (Sorry if I've missed someone out)

Assuming you're running Grub 1.97beta ```

grub-install -v
``` Will tell you. If you are on the 1.97beta, then you may want to consider putting burg on
(like grub, just spelled differently) bean123 is active with it, you can bump into him over at --> [http://ubuntuforums.org/showthread.php?t=1371288&page=16](http://ubuntuforums.org/showthread.php?t=1371288&page=16)  
It is not his posting on RAID, I'm sorry I cannot find it, just that I know he
has back-ported RAID support via BURG into 9.10 - If you just say "Hi" on that thread 
he'll be able to tell you the posting you need.

Regards,

Phill.

---

### Post by bean123 on 2010-01-31
> **sunshineacid said:**
> more searching.

found some code... will this remove the raid information without wiping windows?

sudo dmraid -E -r /dev/sdd
sudo apt-get remove dmraid

Im hesitant to try, as I dont want to wipe my existing windows installation. 

Thanks in advance.

Yeah, that should do it, and it's relatively safe. dmraid would save the original content in devicename_{copy_}formatname.dat and devicename_{copy_}formatname.offset, which can be used to restore in case something is wrong.

---

### Post by sunshineacid on 2010-02-06
Thank you for your responses.

I was tinkering around with this before I got your responses, and ran a format on the second drive while in windows. Once It was done, ubuntu was able to see and install on that second disc. Because my drives are identical, and I couldnt tell the difference between them in the installer, i unplugged (while off) the windows hdd and installed ubuntu on the blank drive. Success finally.

Now I am faced with a new problem.
Grub doesnt see my windows 7 install. Actually, let me rephrase. It does, but I am getting an error when running sudo update-grub

```

jason@boomstick:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sdb1
grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

done

```

I googled this and found a few things concerning bootable flash drives, and the only significant information I was able to glean was to make sure the drive is bootable. According to Palimpsest both drives are marked as bootable.

Can anyone help with this new problem?

Thank you in advance.

---

### Post by darkod on 2010-02-06
Because you unplugged the windows drive, ubuntu didn't include it in device.map file. Recreate a new file with:
sudo grub-mkdevicemap

Run sudo update-grub after and it should be fine.

Also, even if the format got rid of the raid meta data from the ubuntu disk, you might still have remains on the windows disk which might interfere later with ubuntu detection of windows.
After using the drives in raid you should have run the commands you quoted in post #2, for both drives, something like:
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
sudo apt-get remove dmraid

PS. For future reference, in the installer in step 4 you notice a colored bar at the top and bottom. They represent the partitions on the disk before and after the install. Even if you have drives of same capacity but they would usually have different partitions on them, you can easily tell them apart. The problem with unplugging is that sometimes it's better ubuntu to know what hardware is present when installing.

---

### Post by sunshineacid on 2010-02-08
Thank you for your help guys. Everything seems to be working now =)

---

