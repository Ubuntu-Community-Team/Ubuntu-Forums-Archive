---
title: "'MBR'  text shows before boot. how to delete?"
date: 2012-08-05
forum: Installation &amp; Upgrades
---

### Post by akaisuisei on 2012-08-05
Hi i'm a linux novice and

I attempted to dual boot an ubuntu 12.04 with windows 7 on an hp mini 210 netbook

long story short i got messed up with the process and made windows 7 running again to be able to shrink before starting installing ubuntu 12.04 again

below are the codes i tried from this site [http://robert.penz.name/221/mini-howto-restore-windows-mbrbootloader-with-linux/](http://robert.penz.name/221/mini-howto-restore-windows-mbrbootloader-with-linux/)

**1. Solution**
 
sudo apt-get install syslinux

 if the package got installed use following to write the MBR.
 
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda

 **2. Solution**
 
sudo apt-get install mbr

 if the package got installed use following to write the MBR.
 
sudo install-mbr -i n -p D -t 0 /dev/sda

he didnt mentioned to replace sda with the partition to put which is in my case its sda1

the result is an 'MBR' text shows up with blinking cursor below

how can i remove this?

i've used the codes 

```
sudo dd if=/dev/zero of=/dev/sda bs=440 count=1
```

```
sudo dd if=/dev/zero bs=446 count=1 of=/dev/sda
```

but no luck

Any help is appreciated

---

### Post by darkod on 2012-08-05
You have to be very careful with those commands.

Did you run the install-mbr on /dev/sda or /dev/sda1? I think /dev/sda is the correct because the bootloader goes to the MBR of the disk (which is only /dev/sda without any number) and not to a partition like /dev/sda1.

So, what is the current status, can win7 boot or not?

---

### Post by coffeecat on 2012-08-05
> **akaisuisei said:**
> 
he didnt mentioned to replace sda with the partition to put which is in my case its sda1


Quite right that he didn't suggest replacing sda with your partition. You will break things if you dd code into the first 440-446 bytes of sda1!

> **akaisuisei said:**
> 
i've used the codes 

```
sudo dd if=/dev/zero of=/dev/sda bs=440 count=1
```

```
sudo dd if=/dev/zero bs=446 count=1 of=/dev/sda
```


You've blanked out the mbr with that code.

From an Ubuntu live CD, run this:

```
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
```

That will restore the Windows mbr code. You don't need the "sudo apt-get install syslinux" first - it's already installed.

---

### Post by akaisuisei on 2012-08-05
> **darkod said:**
> You have to be very careful with those commands.

Did you run the install-mbr on /dev/sda or /dev/sda1? I think /dev/sda is the correct because the bootloader goes to the MBR of the disk (which is only /dev/sda without any number) and not to a partition like /dev/sda1.

So, what is the current status, can win7 boot or not?

It can boot.

But the annoying 'MBR' shows up before it boots

---

### Post by akaisuisei on 2012-08-05
> **coffeecat said:**
> Quite right that he didn't suggest replacing sda with your partition. You will break things if you dd code into the first 440-446 bytes of sda1!


Oh really? I didn't know that. I've executed the code with 'sda1' instead of sda coz the annoying 'mbr' just showed when i did the 'solution' suggestions. XD But my netbook boots and fortunately its fine.

> **coffeecat said:**
> 

From an Ubuntu live CD, run this:

```
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
```That will  restore the Windows mbr code. You don't need the "sudo apt-get install  syslinux" first - it's already installed.

The windows is fine. It boots up. I would like to know what causes "MBR" text to show 

same thing happened to this guy here but in his case its "GRUB"
[http://ubuntuforums.org/showthread.php?t=1246095](http://ubuntuforums.org/showthread.php?t=1246095)

> **produnis said:**
> thanks, I tried this one, and it leaves only the entries "Boot from Partition 3" and "OSX".

But:
If I try to boot from Partition 3, it just leaves a black screen with the word "GRUB" and a blinking cursor....

After reinstallation of the bootloader with the Ubuntu live-CD
(boot from live-cd, open a terminal and type in:```

sudo mount /dev/sda3 /mnt  # sda3 is my ubuntu-installation
sudo mount -o bind /dev /mnt/dev 
sudo mount -t proc /proc /mnt/proc 
sudo chroot /mnt /bin/bash 
grub-install /dev/sda 
update-grub 
reboot
```)

..rEFIt shows again 3 boot-option:
1) OSX
2) Boot Linux from HD
3) Boot Linux from Partition 3

The crazy thing:  both Linux-Options work!!
But after trying to delete the HD-option with your code 
```
sudo dd if=/dev/zero of=/dev/sda bs=440 count=1
```it again  leaves the "Boot Linux from Partition 3" which is not able to boot
and again ends up showing a black screen with the word "GRUB" and a blinking cursor...

any suggestions?

In my case i havent installed ubuntu yet so i dont have GRUB. Or should I proceed on installing ubuntu to correct the problem?

---

### Post by coffeecat on 2012-08-05
> **akaisuisei said:**
> The windows is fine. It boots up. I would like to know what causes "MBR" text to show 

Sorry I misunderstood you. I've never seen "MBR" text showing. All the 440 odd bytes of Windows code in the mbr do is to find the partition with the boot flag set and hand the boot process over to the boot sector of that partition. I'd assumed that the code contained in the mbr.bin file that you've copied to the mbr was byte-for-byte identical to Windows mbr code. Maybe it's only functionally the same and puts "MBR" to the screen, although if so I can't see what the purpose would be.

When you install Ubuntu and hence grub to the mbr, the Windows code will be replaced. If you still see "MBR" on screen when booting Windows that *may* therefore be to do with the fact that you copied the mbr code to the sda1 partition. In which case I don't know what the fix would be.

---

