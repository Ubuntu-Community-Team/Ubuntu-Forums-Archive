---
title: "Can I uninstall Ubuntu 14 when dual booted with Xubuntu 16?"
date: 2018-02-12
forum: Installation &amp; Upgrades
---

### Post by Richard_York on 2018-02-12
Thanks to recent help here I've successfully installed Xubuntu16.04 alongside Ubuntu 14.04 on an old laptop. This is an exercise prior to installing 16.04 alongside existing Windows10 on our new 2nd hand desktop. I don't mind if I crash this laptop, but if I louse up the desktop I'm lost, as I'm way out of my depth; I just like Ubuntu and intend to go on using it even though I don't understand it!

Having worked the dual boot on the laptop, I'd like to try removing Ubuntu 14.04 and let the poor beast concentrate on Xubuntu. This also means I'll practise un-installing one OS if my installation of 16.04 goes wrong on the desktop.

I see a recent thread here asking about uninstalling 16.04 on a Windows10 machine, but there it appears that reinserting the boot flash drive brings an option to uninstall, and when I stick my 14.04 flash drive in and start up, it's not offering me that option. I got as far as the "something else" option, but that only takes me to partition setting.

Any comments will be gratefully received, especially if you're able to put them in language I can understand! I get quickly lost with terminology.
Many thanks.

---

### Post by RobGoss on 2018-02-12
Is this a fresh installation of Xubuntu 16.04? if so why not just do a clean installation and save your self some time

---

### Post by Richard_York on 2018-02-12
That's what I could easily do, certainly.
I was, however, looking to try removing an Ubuntu installation without disturbing what's already there, as described in my original post, by way of a trial run in case it becomes necessary with the desktop machine I've recently acquired. If the installation of 16.04 there goes wrong, I want to be able to take it off without messing up Windows10, so this was a sort of stepping stone to that.

---

### Post by oldfred on 2018-02-12
First you have to know what is MBR if BIOS/MBR, or boot order if UEFI/gpt.
You have to make sure correct system is the booting system or first in boot order. Or else you delete the system that you are using to boot and have to run repairs.
But you always need an Ubuntu live installer and a Windows repair/recovery flash drive with the current version of every system you have installed.

If BIOS and first entry in grub is you new install, which would be normal they you should just be able to remove the partition that has 14.04.
But just looking at partition may not tell you which ext4 partition is which.

What does this show:
       lsblk -o NAME,LABEL,PARTLABEL,SIZE,UUID,MOUNTPOINT 
And to confirm which system you have booted into:
cat /etc/lsb-release

After I install/format a partition I like to label it to help know which is which.

---

### Post by RobGoss on 2018-02-12
You can remove the **14.04 **partition if needed but as Fred stated if the 16.04 does not have the boot loader your system will not boot correctly. You will have to run the live desktop and use the Boot repair in order to install the boot loader. If Windows is installed it will be a bit more complicated

---

### Post by Richard_York on 2018-02-13
> **RobGoss said:**
>  If Windows is installed it will be a bit more complicated

Thank you both Fred and Rob.  I think this last sentence settles it for now - if the process is different with Windows, there's no point in me bashing my head round trying to do this exercise for the sake of it on the laptop, when this won't inform me about how to do it on a Windows machine if the meed arises

So with thanks again, I'll just take the initial suggestion of wiping the whole thing and reinstalling Xubuntu on the laptop. If I crash when it comes to working on the Desktop I'll just have to ask you helpful people again! 

Incidentally, following on from that that - the desktop  machine doesn't come with reinstallation disks, but I'm told its chip is registered with the Windows 10 OS, so that "all" I'd have to do is apply online to download it, when it would be recognised, and supplied with a download to re-install. I hope the shop has told me correctly here.

---

### Post by RobGoss on 2018-02-13
I haven't used Windows for a few years now so I'm not sure about the download process. I did see this **MS** website were you can download the** Windows 10** ISO file [https://www.microsoft.com/en-gb/software-download/windows10ISO](https://www.microsoft.com/en-gb/software-download/windows10ISO) I would think as long as you are a registered user and payed for your Windows copy you should not have any problem

---

### Post by oldfred on 2018-02-13
Still better to have backup.
While I think the Windows ISO may work, it will not include the drivers unique to your system that the vendor's version does include. Then you have to go thru the reboot multiple times to install each driver.
It used to be only the vendor's version would work.

 Product key now in UEFI/BIOS
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c) 

I did get one Dell system with Windows a couple of years ago.
It wanted Windows backup, Dell backup & I made a full image backup with Macrium. 
Multiple DVDs & flash drives required.

 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)
Microsoft Windows 8.1 reinstall/refresh
[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media)

---

### Post by Richard_York on 2018-02-13
I'm going to have to learn about EUFI, I suspect, I've only ever used BIOS machines.
Meanwhile this laptop from 2009 is now running Xubuntu17 quite happily,  and of course faster than Ubuntu 14 was going on it. Busy week coming up, but I suspect I'll be posting for help when I do  get onto working with the desktop machine. For one thing I've not used Windows since Vista!
Thanks all again.

---

