---
title: "Dual-boot, 3 HDDs, GRUB and Windows - Windows' bootloader hangs"
date: 2008-07-19
forum: Installation &amp; Upgrades
---

### Post by roomcays on 2008-07-19
Hi there,
I have been a GNU/Linux user for some time now, recently I have had two IDE hard disks, configured as follows:
[LIST]
[*]1st IDE/ATA HDD with Windows XP - let me call it **Disk1**
[*]2nd IDE/ATA HDD with Linux + GRUB boot manager - I shall call it **Disk2**
[/LIST]
However, in BIOS I swapped boot sequence, so my computer was always booting from **Disk2** as the first disk. I had then GRUB to choose which operating system I'd like to work on.
Of course, Windows XP cannot boot properly when is not on the Primary Master, but that was easy to fix using common workaround with GRUB hard disk mapping:
```
(...)
map (hd0) (hd1)
map (hd1) (hd0)
(...)
```
This worked all fine, until I connected third hard disk, throught SATA controller:
[LIST]
[*]3rd SATA with Linux (Gentoo) and GRUB as well - I will call it **Disk3**
[/LIST]

OK. Disk3 is SATA disk and thus is recognized as **last** disk available in **GRUB** (hd2) but as **first** disk in **Ubuntu** (/dev/sda).

Now the problem:
Suppose I have done nothing with /boot/grub/menu.lst, so it looks now just like when I had only two disks:

```
title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=8f7669c5-a3bc-4532-ac2c-d6ec1df721ea ro quiet splash
initrd		/initrd.img-2.6.24-19-generic
quiet

title           Windows XP
rootnoverify	(hd1,0)
chainloader     +1
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=8f7669c5-a3bc-4532-ac2c-d6ec1df721ea ro single
initrd		/initrd.img-2.6.24-19-generic


```
Now the weirdest part:
[LIST=1]
[*]On the very beginning, when I just connected fresh, clean, unformated **Disk3** to my computer Windows XP started one or two times. Then I did some nasty partitioning and formating on Disk3 (so I could install there Gentoo AND have two additional cross-system partitions with NTFS) and...
[*]...Windows XP stopped to boot! It was showing no errors, just blank black screen (...of death). It was just like when you try to boot Windows XP from second hard drive without mapping workarounds. So I tried thousands of configurations and looked through million of web pages to find the solution. I've found nothing, but...
[*]...**Super Grub Disk**. When I boot from SGB-CD I can boot windows normaly AND - which I discovered reading all of its GRUB configuration files - it **does not** do hard drive mapping! It just:```
rootnoverify (hd0,0)
chainloader +1
boot
```
That's it! The other thing is that SGB boots Windows from (hd0), however this is a cause of BIOS I supose, because when it finds bootable CD-ROM it does not swap hard drives later on.
[*]the BONUS: after booting Windows XP once from SGB (the one which uses C:\boot.ini to display on windows start) something changed. Now (without SGB, booting from **Disk2**) after selecting Windows XP from GRUB's menu I can see Windows bootloader menu and even countdown timer is running, but if I press Enter (or wait for timer to go off) computer hangs and only hard reset can help...
[/LIST]

So now I have absolutely no idea on what to do...
I've tried some tricks with Windows' boot.ini file, but I don't know how to boot other disks (not partitions) this way.
I am thinking about putting GRUB on **Disk1** (so on the disk where Windows is installed), but I'm not too sure of effects of this. I don't want to mess with my disks, I have important data on both of them (the SATA one is for now almost clear).
Could anyone help me?
Maybe some of you have experienced this kind of weird behaviour of stupid Windows? And maybe this idea of putting GRUB on Windows' disk isn't bad?

Please, any comments are welcome.
Thanks in advance!

---

### Post by cdtech on 2008-07-19
I had the same setup (windows on first drive/Ubuntu on second) and used my bios to select the drive. In my menu.lst I just named the windows drive as (hd0,0) and my Ubuntu as (hd0,0), I know it sounds a little weird but it just worked.

Ubuntu see's the drive that it's on as (hd0,0) when you boot from bios. Then by setting your drives accordingly within the grub menu.lst you should be ok with the selections within the list (hd0,0 as windows hd2,0 as your Gentoo install.

Hope this helps.......

---

### Post by roomcays on 2008-07-19
Thanks, **cdtech**.
I am now using this kind of solution - I switch booting sequence in BIOS to get to the right operating system. Is this what you mean?

However I am so confused about GRUB/Windows, because it worked (and still does work) fine when only two disks are connected, and messes up when I connect third disk, which is seen by GRUB as last disk, so it should have no influence...

Even NTLDR from WindowsXP loads properly (I can see Windows' boot menu) - something wrong happens after thou...

Cheers,
Roomcays

---

