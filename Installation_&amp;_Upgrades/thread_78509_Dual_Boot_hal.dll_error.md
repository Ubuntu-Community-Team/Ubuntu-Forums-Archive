---
title: "Dual Boot hal.dll error"
date: 2005-10-18
forum: Installation &amp; Upgrades
---

### Post by pperk97 on 2005-10-18
i installed 5.10 RC as a dual with XP pro.. grub comes up to the multiboot screen but when i select XP i get a HAL.DLL missing error... ubuntu works fine, just can't get back to XP...
HELP

---

### Post by thomsuey on 2005-10-20
See my response at the bottom of [this thread]("http://www.ubuntuforums.org/showthread.php?t=73254").

---

### Post by leezer3 on 2005-10-20
Hiya,
What appears to be happening is that you have installed Ubuntu on a partition before Windoze on the HDD. Quite typicaly, Windoze is unable to cope with this, and throws its toys out of the pram :rolleyes: 
I presume you have access to the Ubuntu termminal, so do this:
1st, run:
```
lsparts
```
to give you a list of the partitions on your drive. Find the number of the Windoze partition (It should be either FAT32 or NTFS if you're not sure), I will assume NTFS.
Next, you need to edit the Windoze boot.ini, so download CaptiveNTFS from:
[http://linux-ntfs.sourceforge.net/status.html#ntfstools](http://linux-ntfs.sourceforge.net/status.html#ntfstools)
and install it with 
```
./configure
make
install
```
 (This may throw up some missing libraries messages, if so search for these and install in Synaptic.)
Now, you need to mount the Windoze partition, so take the number you found earlier, and run:
```
cd /mnt
mkdir windows
mount -t ntfs /dev/hda**PARTITION NUMBER** /mnt/windows
```
Next, you want to make a copy of the Windoze boot.ini file, so that you can modify it, so do:
```
cd /mnt/windows
cp boot.ini /home/**YOUR USER**/boot.ini
cp boot.ini /home/**YOUR USER**/boot.ini.bak
cd /home/**YOUR USER**
gedit boot.ini
```
Now, find the lines that look like this:
> default=multi(0)disk(0)rdisk(0)partition(1)\WINDOW S
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows
You need to modify the number in brackets after **partition** to the partition number you found earlier PLUS one, as Windoze starts counting from 1, while Linux starts counting from 0.
Now save the modified boot.ini file, and run:
```
sudo unmount /dev/hda**PARTITION NUMBER**
sudo ntfscp /dev/hda**PARTITION NUMBER** /home/**YOUR USER**/boot.ini boot.ini
```
You should now be done :D
However, if everything is still the same after rebooting etc, you will want to restore the second copy of the boot.ini file with:
```
sudo unmount /dev/hda**PARTITION NUMBER**
sudo ntfscp /dev/hda**PARTITION NUMBER** /home/**YOUR USER**/boot.ini.bak boot.ini
```

Hope this helps, and is simple enough for a non-tecchie to understand :)

Cheers

-Leezer-

---

### Post by kpt_hadok on 2008-06-27
Thanks alot. This worked for me on Ubuntu 8.04 with XP sp3 on the other partition.
Used gparted to find the partition number.

---

