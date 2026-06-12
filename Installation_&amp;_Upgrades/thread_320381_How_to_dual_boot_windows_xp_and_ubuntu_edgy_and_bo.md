---
title: "How to dual boot windows xp and ubuntu edgy and boot from windows boot loader"
date: 2006-12-17
forum: Installation &amp; Upgrades
---

### Post by deekay on 2006-12-17
i have windows xp installed on my c drive ( Fat 32).

other drives are d ( Fat 32) and e ( Fat 32).

i tried to install ubuntu edgy on remaining free space and gave (hd5) (new linux root partition) as target to store grub boot loader.  

It was installing everything fine, untill it came to installing grub boot loader, when it said Fatal Error and then installation stopped. it had hapened before also.

it installs smoothly when i allow ubuntu to install grub boot loader to MBR of windows, but i dont want to boot from grub, i prefer booting from windows boot lodaer.

is there any way to install ubuntu grub boot loader on its own root partition   and then boot into ubuntu using windows boot loader. 

( OpenSUSE does it smoothly)

( I have read on web to do it via, floppy drive but i have Laptop with no floppy drive )

---

### Post by bulldog on 2006-12-17
Well if you want to do it the hard way,just be my guest :D 
Can't imagine what keeps you from using Grub as the bootloader,it's easy to use and very configurable,and you can erase it when ever you want.

But it's your choice to do it any way you want,

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by Herman on 2006-12-17
Hello deekay,
A good way to do what you want is to use [Wingrub]("http://grub4dos.sourceforge.net/"). You can leave your Windows IPL code in MBR and boot through Windows bootloader. You just need to configure boot.ini to use WinGrub, which is Grub for Windows. You download it in Windows and install it in Windows. So when the Windows bootloader menu comes up you either boot Windos directly with it's own bootloader or you go into WinGrub to boot any Linux installations. I have been using it for a while to test it out and works fine.

Another way is the old fashioned way to configure boot.ini,[Matthew J. Miller's HOWTOs: **Dual** Booting Ubuntu Linux and Windows **...**]("http://www.crhc.uiuc.edu/%7Emjmille2/howtos/dual-boot-linux-and-windows/")

But really I think you will find it a lot easier just to use Grub. You know, about 13000 people signed up to Ubuntu Web forums in the last 29 days according to the forum counter on the bottom of the main page. I don't know how many of those have installed, or how many have performed multiple installs. But for the number of people who have asked for help with Grub is a very small in proportion to the number of installations that are probably going on. And of the ones who ask for help, there are only a few who have a problem that is difficult to solve.

Why don't you just [back up your MBR with your Ubuntu Desktop LiveCD]("http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd"), and install the easy way, with Grub? (Like everyone else)? 
You can easily restore the MBR again afterwards if you have too many problems, the link tells you how.

Regards, Herman :D

---

### Post by Juan Largo on 2006-12-17
deekay -

Your question was the topic of one of my posts.  One of the options that Ubuntu should offer (but doesn't) is the option of installing Grub on / (root) instead of the MBR.  For example, MEPIS has that option.  Then you can use any number of 3rd party boot managers, such as GAG and Smart Boot Manager, to boot into Linux from the CD ROM drive (or a floppy drive if you have one) until you're ready to commit to letting Linux install Grub on the MBR.  Maybe Ubuntu will offer this some day.  For now, the "workarounds," such as modifying boot.ini, are clumsy at best and dangerous at worst.

Before doing ANYTHING with regard to the MBR, be sure to back it up.  There is a DOS program that does this called Disksave.exe that can be downloaded for free, but it's hard to use Disksave.exe unless you can copy it to a bootable disk with DOS on it.  (This is why I insist on spending the $20 to have a floppy drive on my computer, even though floppies are supposed to be "obsolete.")  

There may be other commercial MBR tools you can use as well.  But the main thing is that you need to back up your MBR.  Actually, this is good advice even if you don't mess around with the MBR, because there may be other ways for it to become corrupted.

When Ubuntu installed Grub on my MBR (without my permission), I was able to "undo" this by restoring the MBR I had saved ahead of time.

---

### Post by Juan Largo on 2006-12-17
deekay -

Your question was the topic of one of my posts.  One of the options that Ubuntu should offer (but doesn't) is the option of installing Grub on / (root) instead of the MBR.  For example, MEPIS has that option.  Then you can use any number of 3rd party boot managers, such as GAG and Smart Boot Manager, to boot into Linux from the CD ROM drive (or a floppy drive if you have one) until you're ready to commit to letting Linux install Grub on the MBR.  Maybe Ubuntu will offer this some day.  For now, the "workarounds," such as modifying boot.in, are clumsy at best and dangerous at worst.

Before doing ANYTHING with regard to the MBR, be sure to back it up.  There is a DOS program that does this called Disksave.exe that can be downloaded for free, but it's hard to use Disksave.exe unless you can copy it to a bootable disk with DOS on it.  (This is why I insist on spending the $20 to have a floppy drive on my computer, even though floppies are supposed to be "obsolete.")  

There may be other commercial MBR tools you can use as well.  But the main thing is that you need to back up your MBR.  Actually, this is good advice even if you don't mess around with the MBR, because there may be other ways for it to become corrupted.

When Ubuntu installed Grub on my MBR (without my permission), I was able to "undo" this by restoring the MBR I had saved ahead of time.

---

### Post by bulldog on 2006-12-17
The MBR with GRUB on it is easily restored with either the windows install disk or the Super Grub Disk.
So copying your old MBR to an floppy isn't necessary at all.

---

### Post by Juan Largo on 2006-12-17
bulldog -

> The MBR with GRUB on it is easily restored with either the windows install disk ... 

You're absolutely correct that the repair option on a WinXP install disk will restore a "generic" MBR that boots you into the C:\ drive.  So saving the MBR to a floppy isn't required for that simple task.  But would the WinXP repair also restore GRUB??  If GRUB is on the MBR, I think you would need to back up the MBR using disksave.exe or some similar way.  Of course, you could also install the "generic" MBR with WinXP repair and _then_ install GRUB.

---

### Post by bullinchinashop on 2006-12-17
> **Herman said:**
> Hello deekay,
A good way to do what you want is to use [Wingrub]("http://grub4dos.sourceforge.net/"). You can leave your Windows IPL code in MBR and boot through Windows bootloader. You just need to configure boot.ini to use WinGrub, which is Grub for Windows. You download it in Windows and install it in Windows. So when the Windows bootloader menu comes up you either boot Windos directly with it's own bootloader or you go into WinGrub to boot any Linux installations. I have been using it for a while to test it out and works fine.

Another way is the old fashioned way to configure boot.ini,[Matthew J. Miller's HOWTOs: **Dual** Booting Ubuntu Linux and Windows **...**]("http://www.crhc.uiuc.edu/%7Emjmille2/howtos/dual-boot-linux-and-windows/")

But really I think you will find it a lot easier just to use Grub. You know, about 13000 people signed up to Ubuntu Web forums in the last 29 days according to the forum counter on the bottom of the main page. I don't know how many of those have installed, or how many have performed multiple installs. But for the number of people who have asked for help with Grub is a very small in proportion to the number of installations that are probably going on. And of the ones who ask for help, there are only a few who have a problem that is difficult to solve.

Why don't you just [back up your MBR with your Ubuntu Desktop LiveCD]("http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd"), and install the easy way, with Grub? (Like everyone else)? 
You can easily restore the MBR again afterwards if you have too many problems, the link tells you how.

Regards, Herman :D

"Like everyone else"
I thought the whole idea of Linux was to not be like everybody else. Linux came about because of people like him thinking about things in a different way from everyone else. It's because of people who went against the grain that Linux exists at all. :p 
:-D

---

### Post by Herman on 2006-12-18
Posted by bullinachinashop:> "Like everyone else"
I thought the whole idea of Linux was to not be like everybody else. Linux came about because of people like him thinking about things in a different way from everyone else. It's because of people who went against the grain that Linux exists at all. :razz:  Okay. I guess you're right. Sorry deekay. I'll try to help without the extra comments this time.

Originally posted by deekay,
>  i tried to install ubuntu edgy on remaining free space and gave (hd5) (new linux root partition) as target to store grub boot loader.  
It was installing everything fine, untill it came to installing grub boot loader, when it said Fatal Error and then installation stopped. it had hapened before also.
it installs smoothly when i allow ubuntu to install grub boot loader to MBR of windows, but i dont want to boot from grub, i prefer booting from windows boot lodaer.
is there any way to install ubuntu grub boot loader on its own root partition   and then boot into ubuntu using windows boot loader. 
( OpenSUSE does it smoothly)Okay, you should be able to easily install Grub to the bootsector of your Ubuntu partition by specifying (hd0,5) I am guessing. You typed (hd5), which would mean hard disk number 6's MBR. I doubt if that's what you really mean. Probably your sixth partition of our first hard disk would be a good guess. 
If you are using the 'Alternate' CD to install with, as I presume ou would be , then you would type (hd0,5) on the line in this illustration,[IMG]http://users.bigpond.net.au/hermanzone/p6/10mbr.png[/IMG]

Here is a link for that part of an Ubuntu installation, "**Installing a Boot Loader for Ubuntu**...(click 'go')................[GO]("http://users.bigpond.net.au/hermanzone/p6.htm#Installing_a_Boot_Loader_for_Ubuntu")

I hope that helps,
Regards, Herman

---

### Post by lukskwldr on 2007-07-18
I had a similar problem as deekay. I was installing Ubuntu 7.04 on my laptop which already had Windows XP. I had BootMagic as the multiple OS boot manager and wanted to keep it. I used the Ubuntu alternative CD. When I came to the install Bootloader menu I tried to use the partition the root system was on, the partitioner utility said it was /dev/hda6 (as / ). I kept getting boot installer errors till I gave up and allowed Grub to be written to MBR to just finish the install. Now the laptop starts up with grub and shows both Ubuntu and Win XP and I can get into either fine. So what's  the problem? As I said, thats not what I wanted. I wanted to keep BootMagic. I have been able to install Red Hat and Mandriva on different partitions and those distros allowed me to put the Lilo bootloader on the / partition and still use BootMagic. I understood that Unbuntu's bootloader install would do the same so I'm supposing I did not do something right. Where did I go wrong? Thanks for anyone's help.

---

### Post by hh93 on 2007-08-29
> **lukskwldr said:**
> I had a similar problem as deekay. I was installing Ubuntu 7.04 on my laptop which already had Windows XP. I had BootMagic as the multiple OS boot manager and wanted to keep it. I used the Ubuntu alternative CD. When I came to the install Bootloader menu I tried to use the partition the root system was on, the partitioner utility said it was /dev/hda6 (as / ). I kept getting boot installer errors till I gave up and allowed Grub to be written to MBR to just finish the install. Now the laptop starts up with grub and shows both Ubuntu and Win XP and I can get into either fine. So what's  the problem? As I said, thats not what I wanted. I wanted to keep BootMagic. I have been able to install Red Hat and Mandriva on different partitions and those distros allowed me to put the Lilo bootloader on the / partition and still use BootMagic. I understood that Unbuntu's bootloader install would do the same so I'm supposing I did not do something right. Where did I go wrong? Thanks for anyone's help.

you can restore MBR-backup made during installation to the first 446 place ([http://www.users.bigpond.net.au/hermanzone/p18.htm);](http://www.users.bigpond.net.au/hermanzone/p18.htm);) this should give you back your Bootmagic.

---

### Post by jbuc89 on 2007-09-13
Hi lukskwldr,

I'm very new to Linux but am a very experienced Windows user.  I have yet to get Ubuntu 7.04 running off my hard drive.  I think it is an issue with an old BIOS and a 250 GB hard drive.  But enough about my problems.

Not sure which installation method you used but if you use the Live CD to do the install, one of the last screens that pop up before it starts formatting and copying files is a screen that tells the changes the Ubuntu installer is going to make to your hard drive.  There is an Advanced button at the bottom of the screen that allows you to install Grub to another location (e.g. /) instead of the MBR.

Hope this helps!  If you don't want to re-install Ubuntu, there are many posts that tell how to re-install just Grub to any partition from the Live CD.

---

