---
title: "New PC but Ubuntu can be downloaded but not installed"
date: 2013-08-22
forum: Installation &amp; Upgrades
---

### Post by viriatovigo on 2013-08-22
Good morning/afternoon/evening every one.

Here I go again, the useless Mediterranean donkey with a new problem.

I've just bought a new PC, a Lenovo IdealCentre B340 because the old IBM Lenovo ThinkCentre was packing up and I believe that all the problems that I have were, in part, due to that machine. At least this one already comes with wireless keyboard and mouse and it works because I am using them just now. It comes with Windows 8 what I don't want at all. As I did always before, I did download Ubuntu -it shows up in my Computer file- but when I did try to install Ubuntu by clicking on "Install Ubuntu" the bloody Microsoft says that can not be installed because the software is faulty (????).

I did download Ubuntu several times and the Microsoft crap always says the same.

Also, when starting, the PC gives me the choice to start with Windows or Ubuntu. If I choice Ubuntu,again, says that can not be started because the software is faulty.

In the past, when downloading Ubuntu, did come the typical  Ubuntu install window where I used to click on "Install Ubuntu" and then "Replace Windows with Ubuntu", but this time the install window doesn't show up but gets downloaded automatically. 

I hate, hate, hate Microsoft...

Please, help. Thank you.

Tino

---

### Post by 3246251196 on 2013-08-22
You are trying to install Ubuntu through Windows?

You have tried to download an image of Ubuntu and boot into that image (DVD/CD/FLASH) rather than through Windows?

Be aware that are freedoms are constantly being attacked: New motherboards are coming with a new "technology" called Secure Boot. This essentially holds a key: If an operating system is not signed by that key then your hardware will not allow this "unsecure" software. Everyone, from now on, should ask whether or not the hardware they are buying (motherboard, currently) comes with Secure Boot technology; if it does, you should ask if you have the ability to switch this off.

I cannot find the article on stallman.org.

---

### Post by mastablasta on 2013-08-22
are you talking about wubi?

the way you install is download the iso, burn the iso to DVD or USB and boot from the media with the os and then install.

---

### Post by grahammechanical on 2013-08-22
Installing Ubuntu using wubi.exe in Windows 8 should not be attempted. The two are no longer compatible.

> Windows installer is not compatible with Windows 8 or UEFI firmware, and is not available for Ubuntu 13.04.


[http://www.ubuntu.com/download/desktop/install-ubuntu-with-windows](http://www.ubuntu.com/download/desktop/install-ubuntu-with-windows)

wubi.exe is still part of the ISO image but should not be used with Windows 8 or UEFI boot systems.

Regards.

---

### Post by Bucky Ball on 2013-08-22
*Thread moved to **Installation & Upgrades**.*

---

### Post by viriatovigo on 2013-08-22
3246251196: "You are trying to install Ubuntu through Windows?". It is what always did and it worked so far, thought some times I made a disc, I'm  keeping the disc and in  the last 2 times I did install it from the disc, but it doesn't work this time in any way. I will ask to the seller about the secured issue, thanks.

mastablasta: Yes, I mean wubi but I have already the DVD as per my answer to 3246251196.

grahammechanica: I suppose that you mean that it is not point to do it for the reason that you say later in your answer -and I didn't know- but _*should not be attempted*_... Why not? Could I  be killed? Right, jokes aside, then How to do it? Should I format the HD and try to install Ubuntu from the disc? Should I buy another older PC and give this one to a charity? Or I should buy a Shuttle v50 that comes without memory, HD nor OS and install a clean HD?

---

### Post by Bucky Ball on 2013-08-22
If you are installing Wubi in Windows, then continue to sort out. If you are wanting to install Ubuntu and only Ubuntu to the hard disk, wipe the hard drive (by booting to an install DVD desktop and launching Gparted) and install Ubuntu to the hard drive. 

Please clarify. Are you now attempting to install Wubi while running Windows or you are trying to do a clean install to the hard drive? As you are probably aware, Wubi will only install in Windows, it is not standalone. You cannot install it to a partition like an OS, only into Win as a program, more or less. It is not considered a permanent solution and more 'try before you buy', or in this case, install Ubuntu proper to a hard drive.

---

### Post by 3rdalbum on 2013-08-22
> **viriatovigo said:**
> I will ask to the seller about the secured issue, thanks.

Not really any point in asking them about it. All PCs that come with Windows 8 have Secure Boot enabled by default. It's a condition of Microsoft giving the PC the sticker that says "Certified for Windows 8".

> grahammechanica: I suppose that you mean that it is not point to do it for the reason that you say later in your answer -and I didn't know- but _*should not be attempted*_... Why not? Could I  be killed?

It's possible you'd lose access to Windows and would have to reinstall Windows.

> Right, jokes aside, then How to do it? Should I format the HD and try to install Ubuntu from the disc?

No need to format the hard drive beforehand. Just boot up the DVD and install Ubuntu. If you want to wipe out Windows 8, you'll be given the option to. If you want to dual-boot, you can resize Windows (you may need to download and run Boot Repair on the DVD afterwards, if you can't get access to Ubuntu after installing it.).

If the DVD still won't boot, you can go into the computer's BIOS and switch off Secure Boot. But Ubuntu 13.04 and 13.10 should be able to boot and install even with Secure Boot turned on.

---

### Post by Mark Phelps on 2013-08-22
> but should not be attempted... Why not? 

Because ... it has been dropped and will NOT be supported anymore. The introduction of PCs with UEFI has seriously complicated the situation.

Just because something USED to work in the past, is no guarantee that it will continue to work in the future.

You would do better abandoning the Wubi approach and going with the more standard dual-boot.

---

### Post by viriatovigo on 2013-08-22
Thank you all.

I can see that the best way is going to be a dual-but, but I am lost on Windows 8 (in reality I have not a clue after XP...) and I don't know how to get into the BIOS as before.

The old Lenovo pressing F8 at start took me to the BIOS but in this new one doesn't work and takes me directly to a window where it gives me the option of - I said in the beginning- to start on Windows or on Ubuntu but, again as I said before, if I chose Ubuntu says that can not be started because the software is faulty. 

And again, as I said, if I try to boot directly from the disc, again, says that the software is faulty.

I going to stop it for a couple of days because I've just got a new translation assignment that I can see that is going to take at least 2 days. I am doing business with Apple Mac Mountain Lion. 

See you then.In the mean time have a nice one all of you. I'll be back in 2 days or so.

Tino

---

### Post by oldfred on 2013-08-22
UEFI install is a lot more complicated as now you have UEFI with secure boot, UEFI without secure boot, and BIOS/CSM/Legacy boot modes. But with Windows in UEFI mode you need to install Ubuntu in UEFI mode.

Please review the link in my signature which will lead you to several install examples with screen shots and lots of detail. But it is not exactly easy. But some systems seem a lot more complicated than others. A few have just used Windows to shrink the Windows partition, turned off fast boot in Windows/UEFI, kept UEFI on, and installed. Others have lots of issues and they vary by vendor & model.

---

### Post by viriatovigo on 2013-08-29
Hi everyone.


  Problem resolved in my way. 


  Got fed up and I bought a Shuttle X50V2 that comes without RAM, HDD and OS.


  I did install the RAM that I pleased (2Gb), one of the HDD from one the former PCs (80Gb) and did install Ubuntu from the disc that I have since the first time. End of the problems.


  &#8220;Problems&#8221; because now I have no problem anymore with the wireless keyboard either, so I infer that was due to the PC itself and not to Ubuntu.


  80Gb are enough because I have an external HDD Fujitsu Siemens of 1Tb connected all the time where I have all my documents. In the Shuttle itself there is only the OS, so if the PC packs up I lose nothing.


  Thank you all for your help.


  All the best.


  Tino

---

### Post by Bucky Ball on 2013-08-29
Glad everything's working. Please mark thread as solved by following the link in my signature. Thanks and good luck. ;)

---

