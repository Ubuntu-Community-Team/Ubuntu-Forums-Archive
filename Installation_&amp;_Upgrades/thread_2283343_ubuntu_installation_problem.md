---
title: "ubuntu installation problem"
date: 2015-06-21
forum: Installation &amp; Upgrades
---

### Post by alec11 on 2015-06-21
Yesterday I decided to install Ubuntu on my laptop (Medion Akoya, I3, 4gb RAM, HM76 chipset, Windows 8 pre-installed). Everything went great and it installed without a problem. However when it asked me to reboot and remove the installation CD, it rebooted into Windows and did not show this Grub menu it is supposed to apparently. So it was installed but just couldn't access it (It also didn't show up in the multi-boot window). I then ran the live CD version and installed boot repair disk and let it do its stuff, rebooted and I could finally pick Ubuntu from the multi-boot menu wich brought me to the Grub menu and I could boot Ubuntu. HOWEVER when I rebooted again too check if everything worked it didn't show Ubuntu anymore and I also couldn't boot into Windows anymore as my laptop said 'there is no media present'. I already did a fresh install of windows and tried the whole process again, but no luck so far.

Anyone able to help?

---

### Post by RobGoss on 2015-06-21
Hello and welcome, I'm assuming your machine is fairly new correct? There has been some changes with the bios that now incorporates UEFI

Please read the Ubuntu documentation that might give you a better understanding how to install a dual boot using UEFI     [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) 

I my self am a Windows user and have been for many years in fact, I did not think I would every switch to another OS, but! after using Ubuntu for about 6-months, and I have also love how Linux operates I'm am now a full time Linux and Ubuntu, user.  I have 5- machines at the moment and grant you this. They are all running Windows but now I only have one machine with Windows -8.1 and I never use it.

My point is this, I have the same problem as you with this one machine is does not give me the dual boot option it goes right into ether Windows or Ubuntu, depending how I set my Bios and it's a brand new PC but after using Ubuntu it does not matter to me because I am blown away with the performance of Ubuntu.

---

### Post by alec11 on 2015-06-21
Hi, and thnaks for the reply

My laptop isn't super new but it came with Windows 8 and has UEFI. The thing is that the boot repair disk will work, but only once. That means that I have to boot Ubuntu live CD and execute boot repair disk each time I want to boot either Windows or Ubuntu. So for some reason it seems that the fix applied by boot repair disk gets erased each time I reboot.

---

### Post by sudodus on 2015-06-21
Welcome alec11 :-)

You re-installed Windows. Can you do that also in the old BIOS alias CSM mode (as opposite to UEFI)? If that works, it will be fairly easy to also install Ubuntu and have a stable dual boot system.

Otherwise (in UEFI mode), you should turn off **fast boot** and **secure boot**. After that the dual boot system might survive. [COLOR=#696969]Unfortunately some manufacturers make it hard to install anything but the preinstalled systems. They tweak the UEFI systems beyond the UEFI standard.[/COLOR]

---

### Post by alec11 on 2015-06-21
Thanks for the help sudodus, 

however the only boot options I can find are UEFI, legacy and Dual-Boot

---

### Post by sudodus on 2015-06-21
I think **legacy** means BIOS (sometimes called CSM) in this case. Try it! If it does not work, you can reset it. **Dual-boot** is also worth trying.

*Edit:* You might find secure boot in another sub-menu, and fast boot is a feature in Windows - that should be turned off in Windows.

You find a lot of links if you search the internet for **fast boot windows**.

---

### Post by alec11 on 2015-06-21
I already had those two turned off but I havn't tried legacy yet so i'm checking that out right now!
thanks a lot

---

### Post by alec11 on 2015-06-21
Nothing so far worked so I decided to completly wipe Windows and only install Ubuntu, but the same thing has happend and it still only shows some sort of command prompt with 'shell' in it (I'm too new to understand all of this)

---

### Post by yancek on 2015-06-21
You indicated in one of your posts that you had tried boot repair.  It has an option to "Create BootInfo Summary".  Select that option when you run it and post a link to the output here.

---

### Post by alec11 on 2015-06-21
Here it is [http://paste.ubuntu.com/11752182/]("http://paste.ubuntu.com/11752182/plain/")

---

