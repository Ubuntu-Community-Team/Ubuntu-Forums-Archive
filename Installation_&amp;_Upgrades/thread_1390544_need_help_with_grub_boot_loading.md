---
title: "need help with grub boot loading"
date: 2010-01-25
forum: Installation &amp; Upgrades
---

### Post by panterus on 2010-01-25
i am completely new to ubuntu/linux/unix, in other words i dont know bash commands. now the problem, i downloaded and installed ubuntu on an external drive as my internal is dying but has vista installed on it, im using the near dead hard drive to carefully install ubuntu on the external before it locks up. anyway, the install went fine and i downloaded wine 1.2 and the needed ubdates and even git ?? before that, then it needed to reboot before the updates would take effect, so i rebooted. when it booted back up i selected ubuntu in the list and it partially loaded then left me with the grub command line and saying it would accept limited bash commands and typing help or pressing tab gets me a list of commands all of which i am unfamiliar with from my old days in DOS, so i cant tell it to boot without a kernel name apparently right? what are my options from this grub...place...thing...stuff? can it at least show me a list of bootable "kernels"?:-s

details: installed ubuntu 9.10-desktop-i386 using the windows install method as i dont currently have any empty dvds or large thumb drives just a few r/w cds

---

### Post by panterus on 2010-01-25
bump: need info soon if possible:popcorn:

---

### Post by audiomick on 2010-01-25
> **panterus said:**
> details: installed ubuntu 9.10-desktop-i386 using the windows install method as i dont currently have any empty dvds or large thumb drives just a few r/w cds

Do you mean a wubi install? That would be: windows is running and you install from the CD

or

You booted the computer with the CD in the drive and installed from the Ubuntu menu that appears?

If it is a wubi install, I think you might be headed in the wrong direction.

I haven't done one, but as I understand it, a wubi install is within the windows install. That means, if your windows is dying, the wubi ubuntu will die with it, I think.

---

### Post by panterus on 2010-01-25
it was a wubi install therefore ubuntu is second in the boot list but it still boots from the external hard drive when ubuntu is selected, its the internal hard drive that is dying actually. but it installed and ran fine it was only after updating and rebooting that i ran into the problem.

---

### Post by panterus on 2010-01-25
bump

---

### Post by panterus on 2010-01-25
i may have a solution to this not sure yet but i may have installed the new wine 1.2 before getting the updates neccasary for samba. running new updates now will see if wine will install after reboot

---

### Post by audiomick on 2010-01-25
> **panterus said:**
> it was a wubi install 

I am afraid I won't be much help to you then. I have never even seen a wubi install.

---

### Post by Leppie on 2010-01-25
> **audiomick said:**
> I am afraid I won't be much help to you then. I have never even seen a wubi install.
you are a lucky man, wubi installs can get ugly...

---

### Post by meierfra. on 2010-01-25
> That means, if your windows is dying, the wubi ubuntu will die with it, I think.
Actually not. Even if the internal drive dies, one can use Grub2 to boot    Wubi on the external drive. 


Anyway, the OP might be hid by a bug in Grub2. So try this:

[https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)


If this did not solve your problem, lets have a closer look at your system:Follow these [instruction]("http://bootinfoscript.sourceforge.net/") to run the boot info script and post the RESULTS.txt.

---

### Post by panterus on 2010-01-26
thanks for the info that does look like it might be the issue trying another fresh install so i willl try and replace that file before updating grub which btw did cause the boot error;)

---

### Post by panterus on 2010-01-26
aslo having another problem it seems last install i was trying to run a game in wine and it would not recognize my graphics card or at least wasn't running it to its best potential the game crashed at one point saying my system wouldnt run shader model 2 and i have a 945 gma intel integrated card with 256 mb dedicated it used to run dx 10 and very close to specs for shader 3 (i wished there was some driver update that would push it over the hump heheh:p) later it would crash after some wine updates from another source it would crash with a report from wine saying a serious error had occurred, basically same thing i think just came with the updated wine report instead.

---

### Post by presence1960 on 2010-01-26
> **panterus said:**
> it was a wubi install therefore ubuntu is second in the boot list but it still boots from the external hard drive when ubuntu is selected, its the internal hard drive that is dying actually. but it installed and ran fine it was only after updating and rebooting that i ran into the problem.

when wubi is used the windows bootloader is used and the Ubuntu entry is added to the windows bootloader. When the windows bootloader presents the option of windows or Ubuntu & you choose Ubuntu the windows bootloader passes to GRUB so you can boot Ubuntu.

Now think this thru: The windows bootloader is on the MBR of your internal disk, once that disk goes you will not be able to boot anything because in wubi the windows bootloader controls the boot process. 

I would agree with audiomick. You need to do a full install of Ubuntu by booting the Live CD and installing to your external disk. At the Ready to install window click the Advanced button and choose to put GRUB on external disk MBR by using the drop down box (see pic below). If you only have the one internal and one external disk select /dev/sdb to put GRUB on MBR of external. When install is complete reboot and go into BIOS and set the external disk to boot before the internal. This will allow you to boot with or without the external plugged in. When plugged in GRUB will take over and you can boot to Ubuntu. When the external is unplugged it will boot to windows.

P.S. you can operate with ubuntu installed to the external. But it would be best to buy a new hard disk because the speed of an external disk is not as good as an internal disk. Then install Ubuntu to the internal disk either by itself or as a dual boot. I would go for dual boot because the things you want to run will run better in windows than in wine. Wine is crap really! Everything does not run in it or it doesn't run as good as it does in windows.

---

### Post by meierfra. on 2010-01-26
> The windows bootloader is on the MBR of your internal disk, once that disk goes you will not be able to boot anything because in wubi the windows bootloader controls the boot process.

Yes, but the Windows boot loader is not needed to boot Wubi.  You can just install Grub2 to the MBR of the external drive and boot Wubi. So this is not really a problem.

Anyway, while I disagree with audiomick and presence1960 on this matter, I do agree with their conclusion.

You should not use Wubi to install Ubuntu to an external drive:

1)  A regular install is just a easy, since no partitioning involved.

2)  A  Wubi install lacks in performance.

3)  You will get better help in the  Ubuntu forums.

So as long as you are reinstalling, you should do a regular install.

---

### Post by panterus on 2010-01-26
i dont have a dvd to download the full install onto atm nor a large enough usb drive do you think a cd is large enough. already have the third install in place btw and its working good so far with the updated wubildr file. the main thing im trying to figure atm is the graphics card driver or access issue in wine 1.1.37 (1.2 beta). the game i used said it dont have the hardware for shader 2 and i do :s

---

### Post by panterus on 2010-01-26
bump still looking to resolve graphics problem on intel 945 gma adapter

---

### Post by meierfra. on 2010-01-26
Please do not  bump a thread more than once  every 24 hours and please start a new thread. It's unlikely that somebody  with experience in graphic problems will look at a thread titled  "need help with grub boot loading"

---

### Post by meierfra. on 2010-01-26
> a cd is large enough
A cd is enough for a regular Ubuntu install.

---

### Post by panterus on 2010-01-26
ok thanks for the info and sorry about the bump, heheh.

---

