---
title: "Installation troubles!!!"
date: 2008-10-10
forum: Installation &amp; Upgrades
---

### Post by vpdtri on 2008-10-10
I have just started using Ubuntu. At the moment, I am using a CD live. I would like to have a permanent installation into my desktop and I did install it but there are some troubles.

There are 2 seperated disks in the computer. One is used for Windows XP and another one I would like to install Ubuntu. The installing process was done carefully and no error message appear during the installation.

However, when everything is done and the computer needs to be restarted to run Ubuntu, at the beginning the error message appear:

GRUB loading, please waite...
Error 21

and it stopped the computer working further.

Could you please advice on this issue?

Best regards,

---

### Post by Elfy on 2008-10-10
Can you open a terminal from the accessories menu and paste in this command

```
sudo fdisk -l
```
This will give you an output _similar_ to:
>    Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1302    10458283+  83  Linux
/dev/sda2            2676        9889    57946455    5  Extended
/dev/sda3            9890       10011      979965   82  Linux swap / Solaris
You will have aline for ntfs as well, note the line that says Linux - likely that it's after sda1

You need to know the /dev for it later, now make a folder 
```
sudo mkdir /mnt/recovery
```
Now we can mount the linux partition and access the files - replace xy with the partition number you get from the fdsik -l command
```
sudo mount -t ext3 /dev/sdxy /mnt/recovery
```

That shoudl not give any errors - if it does stop and post back, now run these commands and post both of the outputs here please.

```
cat /mnt/recovery/boot/grub/menu.lst
sudo fdisk -l
```

---

