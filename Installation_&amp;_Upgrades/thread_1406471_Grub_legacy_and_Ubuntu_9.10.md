---
title: "Grub legacy and Ubuntu 9.10"
date: 2010-02-14
forum: Installation &amp; Upgrades
---

### Post by bowbalitic on 2010-02-14
I searched through your forums and google but i haven't been able to find an answer for this. 

I was having difficulty with ubiquity (ubuntu installer on live cd) and dmraid on the Ubuntu 9.10 live cd, it kept reading my drives as raid and no matter what I did I couldnt install properly to my drives. So I removed one of my drives (the one containing windows) and installed that way. When I plugged my windows drive back in grub 2 wouldn't work. So I have given up with grub 2. I installed Ubuntu 9.10 on my drive with the /boot on a seperate partion. I then installed Ubuntu 9.04 (to install grub legacy, thought it would be a short cut)  with /boot overwriting 9.10s /boot partition. So now Ubuntu 9.04 works fine, but 9.10 can not be recognized by grub legacy. 

The /boot folder under Ubuntu 9.10 is empty, because I reformated the partition. So I was wondering what I need to put in it to make it boot properly. I'm pretty sure that I took an unusual approach to doing this, so if anyone knows of a better way to install grub legacy for 9.10 please tell me. 

Ubuntu 9.10 is on /dev/sda5 
this is my /grub/menu.lst (viewed from ubuntu 9.04) I added the 9.10 loader (probably wrong) I'm not sure if my root is setup properly, grub-probe didn't work. 


```

title        Ubuntu 9.04, kernel 2.6.28-14-generic
uuid        20c62759-3ad9-401f-b0cd-7633f35127d0
kernel        /vmlinuz-2.6.28-14-generic root=UUID=e2dfb6d4-d17a-4d46-9ec0-f5b203a6f66a ro quiet splash 
initrd        /initrd.img-2.6.28-14-generic
quiet

##  Ubuntu 9.10

title        Ubuntu 9.10
root (hd1,4)
makeactive
chainloader +1



## END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows XP Professional x64 Edition
rootnoverify    (hd1,0)
savedefault
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1
```Thanks in advanced for your help, I have spent 3 weeks trying to get 9.10 properly installed.

---

### Post by darkod on 2010-02-14
If you spent 3 weeks I guess you are already annoyed, and not sure if you want to keep trying. And yes, you took a very strange approach. :)

What I would do:
1. If you are sure your issue was dmraid, and you are not running raid on your system, the following commands will fully remove the raid meta data from both drives:

(you can run them from live desktop)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
sudo apt-get remove dmraid

You should be able to install correctly after that. I also suggest from Gparted in live desktop to delete the partition of your current 9.10 and 9.04 installs and install 9.10 again if the dmraid issue is resolved.

2. If you still have problems installing 9.10 (grub2), again I would suggest deleting the current partitions and install 9.10 again. Yes, it will install grub2 but you can remove it and install grub1, no need to install fully 9.04 for that and keep another ubuntu on your computer.
If section 1 doesn't help and you decide to do this, let me know and I'll find the commands to remove grub2 and revert to grub1.

In your current situation I'm not sure you can boot 9.10 with any commands because you formatted the /boot partition which was holding the kernel and initrd files. Now only 9.04 kernel files are there.
That's why I think the above is better, plus no need to keep two ubuntus just for grub.

---

### Post by bowbalitic on 2010-02-14
Well, thanks for the I did what you said, but the same thing happened as if I removed dmraid through the synaptic packet manager. It shows my drives as separate drives (but it still has the raid set-up as an option in the partition editor) and when I try to create a partition I get an error. (deleting partitions isnt a problem) 

Heres a save for the gparted error. 

```
GParted 0.4.5
 Libparted 1.8.8.1.159-1e0e
    **Format /dev/sda1 as ext4**  00:00:00    ( ERROR )             calibrate /dev/sda1  00:00:00    ( SUCCESS )             [I]path: /dev/sda1
start: 63
end: 314568764
size: 314568702 (150.00 GiB)[/I]          set partition type on /dev/sda1  00:00:00    ( SUCCESS )             *new partition type: ext4*          create new ext4 file system  00:00:00    ( ERROR )             ***mkfs.ext4 -j -O extent -L "" /dev/sda1***             [I]mke2fs 1.41.9 (22-Aug-2009)
/dev/sda1 is apparently in use by the system; will not make a filesystem here!
[/I]             ========================================

```Also here is a list of the objects in the ubiquity folder 

**activate-dmraid**  clock-setup-apply    install.pyc       pixmaps
apt-setup     console-setup-apply  localechooser-apply  summary
check-kernels     gtk              migration-assistant  tzsetup
clock-setup     install.py          netcfg-wrapper       ubi-restart-hal

I'm wondering if the activate-dmraid is the problem, assuming my problem is raid related at all. (I made activate-dmraid bold)

Again, thanks for the help. And although I am getting annoyed by all these problems i'm having I don't think I would enjoy it as much if everything worked properly... cuz then what would I have to do on my computer??

EDIT

Also, I was wondering if I was doing the /boot right. I want to have grub on its own partition without any direct relation to any os. (I like to reformat and try different os's) So should I be creating a separate /boot partition or should I do something completely different?

---

### Post by bowbalitic on 2010-02-14
So I think I've confirmed the problem. When I try to mount my 500 gb drives it tells me

One or more block devices are holding /dev/mapper/pdc_bcdbibc2

---

### Post by darkod on 2010-02-14
Yes, /dev/mapper looks like raid, but why doesn't it remove it? Make sure you have no raid settings enabled in BIOS, sometimes you can miss it looking. Then even after removal of the dmraid meta data, on every reboot BIOS is making it again.
Also make sure SATA Type is not set to RAID, it should be AHCI or Native IDE, or similar.

Making separate /boot doesn't matter much. If you install another OS over the current one, it will delete everything anyway. If you install another linux next to ubuntu, just make sure you go into Advanced settings and DON'T install bootloader for the new linux. Then just boot ubuntu and run update-grub which will find the new OS and add it to grub menu. That's the best way IMHO.

---

### Post by bowbalitic on 2010-02-14
My bios has my drives set to IDE. 

I was looking through some of the other threads and discovered the 

linux nodmraid 

cmd but it didn't help me either. I'll go through my bios again and see if there is some setting hidden somewhere that is setting my drives to raid.

---

### Post by bowbalitic on 2010-02-14
Wow...
Well I think I found the problem...

My MB has 4 sata connectors and an additional 2 which control Marvell raid. I had the Marvell connectors on for my front panel usb, firewire, and esat. Turns out Ubuntu saw the Marvel connectors were on and decided that all my drives were raid. I dissabled the Marvell and installation seems to be almost finished. Hopefully I can turn them back on after installation so I can use my external usb plugs. Ill let you know how it goes after installation.

---

### Post by darkod on 2010-02-14
> **bowbalitic said:**
> Wow...
Well I think I found the problem...

My MB has 4 sata connectors and an additional 2 which control Marvell raid. I had the Marvell connectors on for my front panel usb, firewire, and esat. Turns out Ubuntu saw the Marvel connectors were on and decided that all my drives were raid. I dissabled the Marvell and installation seems to be almost finished. Hopefully I can turn them back on after installation so I can use my external usb plugs. Ill let you know how it goes after installation.

I would use different connector for the esata if you can. Even if the install finishes OK, if it "decides" you have raid later, it might create issues again. I'm just making assumptions here... :)
How was the saying, better safe than sorry. :)

PS. Although those connectors should act as normal sata unless you have the Marvel raid enabled in BIOS. My board also has 6 connectors out of which 2 are for raid but only if you enable the setting in BIOS. Otherwise it's regular sata/ide mode.

---

### Post by bowbalitic on 2010-02-14
Of course it  the obvious... So that was the problem, 3 weeks only to realize its one of the simplest things possible... 

Thanks for help, I feel like an idiot now for not thinking about that.

---

