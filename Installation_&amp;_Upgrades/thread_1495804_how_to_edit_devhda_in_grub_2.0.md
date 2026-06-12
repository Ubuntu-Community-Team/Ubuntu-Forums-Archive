---
title: "how to edit /dev/hda in grub 2.0"
date: 2010-05-28
forum: Installation &amp; Upgrades
---

### Post by sayantandas on 2010-05-28
I had windows 7 installed on my system prior to the installation of Lucid Lynx. The boot loader for windows is installed in /dev/sda1. The main windows installation is in /dev/sda3
Ubuntu is installed in /dev/sda5.
The grub update has added a loader for windows 7 for /dev/sda3 instead of /dev/sda1.
How do i change that to /dev/sda1 in grub 2.0 as it says that it is not recommended to edit grub.cfg in grub 2.0.
I know i can add something in custom section but  I am not a pro in linux hence i'm not sure how to add that. 
if anyone here knows how to edit /add the windows installation link please let me know.

thanks

---

### Post by Martje_001 on 2010-05-28
Which version of Ubuntu are you using?

Anyway, try the following:
```
sudo update-grub
```

---

### Post by garvinrick4 on 2010-05-28
> **sayantandas said:**
> I had windows 7 installed on my system prior to the installation of Lucid Lynx. The boot loader for windows is installed in /dev/sda1. The main windows installation is in /dev/sda3
Ubuntu is installed in /dev/sda5.
The grub update has added a loader for windows 7 for /dev/sda3 instead of /dev/sda1.
How do i change that to /dev/sda1 in grub 2.0 as it says that it is not recommended to edit grub.cfg in grub 2.0.
I know i can add something in custom section but  I am not a pro in linux hence i'm not sure how to add that. 
if anyone here knows how to edit /add the windows installation link please let me know.

thanks You will have 3 primarys in Windows 7 usually. One for mbr
 in sda1 usually labeled system then one for OS and one for recovery. The last primary
is an extended partiton where linux exists. That would be your 4 primarys. In boot window the recovery is called Vista that is just how Linux reads it. When you install Ubuntu grub go's in sda in advanced tab in last page of install. If you need to reinstall grub no problem just ask in this thread. If you installed in sda1 or sda2 or sda3 might be a problem but fixable with a few lines of code usually. In boot selection booting Windows 7 OS will be in first Windows selection, kind of confusing.

---

### Post by sayantandas on 2010-05-29
Thanks everyone for the inputs. I have got it working by manually editing grub.cfg. This is what my os prober shows. Notice that Windows 7 loader is being set to /dev/sda3. I have manually edited that to set to /dev/sda1 and changed the UUID as well. 


### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3A98D7D998D791AD
    chainloader +1
}

My question is how do I make the grub to set windows 7 boot to  /dev/sda1 permanently?  
Doing a sudo update-grub  or during kernel upgrade it will again set it back to /dev/sda3


This is my output for fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xccaeda49

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        5222    41840640    7  HPFS/NTFS
/dev/sda3            5222       12373    57439022    7  HPFS/NTFS
/dev/sda4           12373       19458    56906753    5  Extended
/dev/sda5           12373       19163    54537216   83  Linux
/dev/sda6           19163       19458     2368512   82  Linux swap / Solaris

---

### Post by kansasnoob on 2010-05-29
You add custom entries to "/etc/grub.d/40_custom":

```
gksudo gedit /etc/grub.d/40_custom
```

Then to make the entries in "/etc/grub.d/30_os-prober" no longer appear you make it non-executable by running:

```
sudo chmod -x /etc/grub.d/30_os-prober
```

Should you ever desire to make "/etc/grub.d/30_os-prober" executable again just "sudo chmod +x" to revert that change.

More info in the **Adding Entries to Grub 2** section here:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Edit: it sounds like you may already know, but always follow up any changes by running "sudo update-grub".

---

### Post by garvinrick4 on 2010-05-30
Given my ubuntu install with grub is in sda5 and it is labeled as maverick.
Use whatever yours are. My mbr is in sda1 labeled SYSTEM. As you see I am putting it 

into sda and never sda1, sda5 alway, always sda.



Make directory for mbr if there is a seperate partition for mbr. 

```
sudo mkdir /media/SYSTEM
```Make directory OS

```
sudo mkdir /media/maverick
```Mount OS

```
sudo mount [/dev/sda5]("file:///media/dev/sda5") [/media/maverick]("file:///media/media/maverick")
```Mount mbr partition if one.

                                   ```
sudo mount [/dev/sda1 ]("file:///media/dev/sda1")[/media/SYSTEM]("file:///media/media/SYSTEM")
```Install grub to sda. 

                                    ```
sudo grub-install --recheck --root-directory=/media/maverick [/dev/sda]("file:///media/dev/sda")
```unmount

```
sudo umount /media/maverick
```unmount

```
sudo umount /media/SYSTEM
```

---

### Post by sayantandas on 2010-05-31
Thanks so much for your input guys. It worked well....

---

