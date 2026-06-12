---
title: "no internet, reinstall lucid on dual boot."
date: 2010-09-05
forum: Installation &amp; Upgrades
---

### Post by needastick on 2010-09-05
Hello,
      I've managed to break my box trying to install the latest ati catalyst for my new graphics card. I have managed to get the driver partially configured and was able to watch hi def before restarting.
      After a restart however I have lost my net connection and don't seem to be able to re gain it.
      I'm prepared to reinstall the os if that is the only way but I am unsure how.I have just changed from Karmic to Lucid which went easily enough but when I checked the download site it says not to use the desktop version if you are dual booting, which I am. The advice is to install the server version and then the desktop later.
      Is this the only way? seems a bit of a palaver, also I can't really decide whether the 64bit is worth it, I seem to have had a lot of grief trying to add printers scanners etc. Any advice for me please folks?

---

### Post by Ceedub2 on 2010-09-05
Install the server ver for a dual boot? Thats a new one. 

I have 64 bit 10.04 and the only problem I have faced is the printer trouble you have. Still not able to print to a printer hooked to a windows machine. You can always try the 32 bit version.

---

### Post by needastick on 2010-09-05
Apparently grub 2 overwrites the mbr.

---

### Post by garvinrick4 on 2010-09-05
> **Ceedub2 said:**
> Install the server ver for a dual boot? Thats a new one. 

I have 64 bit 10.04 and the only problem I have faced is the printer trouble you have. Still not able to print to a printer hooked to a windows machine. You can always try the 32 bit version.
Have to make a Windows Workgroup if from another computer in your small home network system and share printer and use a password to log-in with Windows machine. It uses that password when adding printer in Ubuntu. Then choose add printer choose window workgroup choose your printer then it looks for the driver choose your printer name and # and done.

---

### Post by garvinrick4 on 2010-09-05
> **needastick said:**
> Hello,
      I've managed to break my box trying to install the latest ati catalyst for my new graphics card. I have managed to get the driver partially configured and was able to watch hi def before restarting.
      After a restart however I have lost my net connection and don't seem to be able to re gain it.
      I'm prepared to reinstall the os if that is the only way but I am unsure how.I have just changed from Karmic to Lucid which went easily enough but when I checked the download site it says not to use the desktop version if you are dual booting, which I am. The advice is to install the server version and then the desktop later.
      Is this the only way? seems a bit of a palaver, also I can't really decide whether the 64bit is worth it, I seem to have had a lot of grief trying to add printers scanners etc. Any advice for me please folks? Have to make sure you have driver in your linux box for that device or see if it is in Synaptics and install it. Sometimes hardware does not have driver already installed in Linux. If not you have got to find it at source
from maker of hardware. Linux kernel and Ubuntu has a lot now but not all. Never had a problem using desktop version 64 bit or 32 bit, never had to install server and then install desktop. good luck.

---

### Post by garvinrick4 on 2010-09-05
> **needastick said:**
> Apparently grub 2 overwrites the mbr. Yes it does overwrite to grub2 last few versions before that grub legacy. Should just give you choice of windows install or linux install to boot into. Or for that matter all installs on machine will be in the choices to boot using grub2. Nice once you get used to it.

---

### Post by needastick on 2010-09-05
Just copied this from the ubuntu wiki, can't be the only way surely?


Warning: The Ubuntu Desktop edition LiveCD installer no longer allows a custom installation of GRUB, and it now uses GRUB2 (which is difficult to customize). DO NOT USE the Lucid Lynx Desktop edition LiveCD as an installer if you use a boot partition, use more than 2 operating systems, or chainload bootloaders. The Ubuntu installer will overwrite your Master Boot Record and you will later be forced to recreate it. This is a serious flaw in both Karmic Koala and Lucid Lynx Desktop edition installers. Use the Ubuntu Server edition instead (and then later add the ubuntu-desktop).
If you want to install more than 2 operating systems on a single computer, check out these tips.

---

### Post by garvinrick4 on 2010-09-05
> **needastick said:**
> Just copied this from the ubuntu wiki, can't be the only way surely?


Warning: The Ubuntu Desktop edition LiveCD installer no longer allows a custom installation of GRUB, and it now uses GRUB2 (which is difficult to customize). DO NOT USE the Lucid Lynx Desktop edition LiveCD as an installer if you use a boot partition, use more than 2 operating systems, or chainload bootloaders. The Ubuntu installer will overwrite your Master Boot Record and you will later be forced to recreate it. This is a serious flaw in both Karmic Koala and Lucid Lynx Desktop edition installers. Use the Ubuntu Server edition instead (and then later add the ubuntu-desktop).
If you want to install more than 2 operating systems on a single computer, check out these tips. If I have a bootloader I like and I am going to install a OS with a different bootloader I choose "do not install a boot loader" at install and then boot into OS with my boot in it and update-grub and all is fine. Worked with Ubuntu, fedora, redhat and OpenSuSe. I believe Ubuntu is just a check mark in a box where the others you got to look a little deeper to find do not install boot.

---

### Post by perspectoff on 2010-09-05
> **needastick said:**
> Just copied this from the ubuntu wiki, can't be the only way surely?


Warning: The Ubuntu Desktop edition LiveCD installer no longer allows a custom installation of GRUB, and it now uses GRUB2 (which is difficult to customize). DO NOT USE the Lucid Lynx Desktop edition LiveCD as an installer if you use a boot partition, use more than 2 operating systems, or chainload bootloaders. The Ubuntu installer will overwrite your Master Boot Record and you will later be forced to recreate it. This is a serious flaw in both Karmic Koala and Lucid Lynx Desktop edition installers. Use the Ubuntu Server edition instead (and then later add the ubuntu-desktop).
If you want to install more than 2 operating systems on a single computer, check out these tips.

No, it certainly is not the only way, and is not even the official way.

I wrote that advice (on Ubuntuguide.org and Kubuntuguide.org) only for people who want to use multiple partitions, each with a different OS.

If you only need Windows and Ubuntu, each in one partition, then you can use Grub 2 as the bootloader.

Grub 2 is like crabgrass to me, though -- it takes over the lawn as far as booting goes. Grub Legacy was much easier to use as the primary bootloader, IMO, especially for the simple task of chainloading secondary bootloaders (including the Windows bootloader, the Ubuntu Grub 2 bootloader, and the Mac bootloader).

It is bloody difficult to get Grub 2 to do this (chainloading) easily, hence my advice.

My computers have an average of 4 to 6 operating systems on them (not including virtual machines), including Windows XP/Vista/7 and Mac OSX. My advice is mainly for similar situations: multiple partitions and multiple OS, each requiring a unique bootloader of its own.

Having been burned more than 20 times by Grub 2, I continue to recommend Grub Legacy in its own small 100 Mb partition as the master bootloader. It is used in this fashion merely to chainload specific bootloaders (such as Grub 2) which remain contained within their respective partitions (for their respective OSs).

Using this method, Grub Legacy will live in its own isolated partition by itself, and the Master Boot Record will always point to it. The MBR will then never need to be changed again, and if it is changed (by Windows or Ubuntu or any other new OS), it is very easily reset. 

The instructions you are quoting is part of that scheme only. But I see the confusion and will re-write Ubuntuguide and Kubuntuguide to be a bit more clear.

I install Ubuntu servers and then the desktops because it is faster for me and because almost all my computers have server components on them, anyway.

I also like the option of a minimal server installation (available with the server installer but not the desktop version installers), which I recently have ended up using quite often (in the interest of speed, performance, usage in virtual machines, and avoiding some of the cutting edge nonsense that the Ubuntu masters of the universe love, but which I really don't need).

Lastly, the Ubuntu server editions have always had tools at installation for easily installing server-oriented packages. The desktop versions installers did not include these (until recently). 

In more recent versions of Ubuntu, there has been a gradual merge of server and desktop, so that all server packages are now pretty much easily installed in the desktop version as well. 

For this reason my advice may be a tad bit out of date and I apologize. Since many of my computers don't even run a desktop, I personally have always installed a server first and then added the desktop afterwards, when desired. (In the old days, I often had a mix of the Gnome desktop, the KDE desktop, the XFCE desktop, and maybe an LXDE and KDE3 desktop, perhaps on the same Ubuntu server.)

Nowadays, KDE works very hard to accommodate the bits of the Gnome desktop that aren't available for KDE, so that I don't need to have both Gnome and KDE desktop on the same computer any longer. In fact, I no longer install the Gnome desktop at all, (except on test versions of Ubuntu which I am reviewing). (If you haven't guessed, I am a KDE fan).

(BTW, I am not part of the official Ubuntu team, and Ubuntuguide.org is not the official Ubuntu wiki, so I would take it with a grain of salt and as only one opinion.)

Cheers.

---

### Post by needastick on 2010-09-05
Thanks guys for your prompt and considered replies. I did feel that the paragraph quoted was not the complete answer but those less experienced of us need it spelling out a bit.
  For now I'm going to try a little longer to resolve my net problem, and if that fails, download 10.04 to a thumbstick and install again.
  I shall re-read the replies tomorrow when I've gathered my strength, thankyou.

---

### Post by needastick on 2010-09-06
I've managed to resolve my connection problem this morning by re-configuring the dhcp server so no need for a fresh install just yet.

I'll mark this thread as solved as I think there are some good points on the op. Thanks for your help.

---

