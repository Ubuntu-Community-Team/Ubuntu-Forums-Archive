---
title: "grub.cfg missing after punch of updates??"
date: 2010-10-02
forum: Installation &amp; Upgrades
---

### Post by jjaakkol on 2010-10-02
I installed yesterday punch off updates to 10.04. Now Linux does not work as selected from multiboot. I have installed Ubuntu with windows installer. (Vista+ Ubuntu)

Gives only error *NTFS5: No wubidlr*
and new reset. 

Hitting INSERT right after selecting Ubuntu does not give any extra.

wubildr, wubilr.cfg and wubildr-mbr exists on C:\ubuntu\winboot

Under C:\ubuntu\disks exists root.disk and swap.disk

Directory C:\ubuntu\disks\boot\grub is empty. It should not?

---

### Post by garvinrick4 on 2010-10-02
wubildr is in the bcd of Vista bcd is its boot manager. If it is not an entry in
bcd then ubuntu will not boot.
You can look at it by going into Vista and at a command line:
```
bcdedit
```
There should be an entry with wubildr in it. Here is a link for Wubi.
[WubiGuide - Ubuntu Wiki]("https://wiki.ubuntu.com/WubiGuide")

---

### Post by jjaakkol on 2010-10-02
bcdedit gives this, so Ubuntu is there as I I said earlier, but when I choose Ubuntu I get 
that error NTFS5: No wubildr

C:\Windows\system32>bcdedit

Windows Boot Manager
--------------------
identifier              {bootmgr}
device                  partition=C:
description             Windows Boot Manager
locale                  en-US
inherit                 {globalsettings}
default                 {current}
resumeobject            {7ed1980a-e1ec-11de-94cf-ffbfc56c7ab8}
displayorder            {current}
                        {084fde22-171b-11df-8a92-001e330c25bf}
toolsdisplayorder       {memdiag}
timeout                 10
resume                  No

Windows Boot Loader
-------------------
identifier              {current}
device                  partition=C:
path                    \Windows\system32\winload.exe
description             Microsoft Windows Vista
locale                  en-US
inherit                 {bootloadersettings}
recoverysequence        {572bcd56-ffa7-11d9-aae0-0007e994107d}
recoveryenabled         Yes
osdevice                partition=C:
systemroot              \Windows
resumeobject            {7ed1980a-e1ec-11de-94cf-ffbfc56c7ab8}
nx                      OptIn

Real-mode Boot Sector
---------------------
identifier              {084fde22-171b-11df-8a92-001e330c25bf}
device                  partition=C:
path                    \ubuntu\winboot\wubildr.mbr
description             Ubuntu

C:\Windows\system32>

---

### Post by bcbc on 2010-10-02
Do you get an error about loadfont or does it just reboot?

Do you remember if there was an update to grub-pc? I've seen a few of these issues recently but it's unclear what the solution is. But there may be workarounds that involve booting a live CD and editing grub.cfg by hand. (The actual problem seems to be because of errors processing the existing grub.cfg, not that it is missing)

---

### Post by jjaakkol on 2010-10-02
Laptop just restart again to Boot menu where I can choose Vista or Ubuntu.

I am not 100% sure if there was any grub. Maybe as amount off updates was 79. :]

---

### Post by garvinrick4 on 2010-10-02
It is there that is a good thing. Now to get it recognized when you try to boot into Ubuntu?
The only thing you can do is look in launchpad.net to see if it is a known bug and there is a fix. (upper right corner of Ubuntu Forums) and or wait for WUBI users that have had this problem to post in your thread. Take a peak at launchpad and look around, you will not be only one with this problem.

---

### Post by bcbc on 2010-10-02
Boot from a live cd, mount your windows partition, loop mount your root.disk, copy the existing grub.cfg and then edit it. Just remove everything except the entry you wish to boot.

e.g. if wubi install is on /dev/sda2
```
sudo mkdir /media/win 
sudo mount /dev/sda2 /media/win
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
sudo cp /mnt/boot/grub/grub.cfg /mnt/boot/grub/grub.cfg.copy
gksu gedit /mnt/boot/grub/grub.cfg
```

Just remove everything other than the menuentries you want.

e.g. you can have just this in grub.cfg and it will work (this is just an example, use your own entry).
```
menuentry "Ubuntu, Linux 2.6.35-22-generic" {
 insmod part_msdos
 insmod ntfs
 set root='(hd0,msdos2)'
 search --no-floppy --fs-uuid --set ea5cc2095cc1d10d
 loopback loop0 /ubuntu/disks/root.disk
 set root=(loop0)
 linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro quiet splash
 initrd /boot/initrd.img-2.6.35-22-generic
}

```Good luck. 

Long term fix... no idea. But it might be a good idea to start thinking about creating a partition and migrating your wubi install to it.

---

### Post by jjaakkol on 2010-10-02
So this grub.cfg should exists under windows c:\ubuntu or under its subdirectories? I can say that it does not. :)

---

### Post by bcbc on 2010-10-02
> **jjaakkol said:**
> So this grub.cfg should exists under windows c:\ubuntu or under its subdirectories? I can say that it does not. :)

No it's on the root.disk which you cannot view under windows unless you install some special software (which allows read only view and is therefore not very useful). If it were under windows it would be simple to fix.

---

