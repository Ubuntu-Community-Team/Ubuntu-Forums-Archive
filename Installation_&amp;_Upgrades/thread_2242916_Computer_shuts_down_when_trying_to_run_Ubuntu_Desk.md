---
title: "Computer shuts down when trying to run Ubuntu Desktop 14.04.1 install"
date: 2014-09-04
forum: Installation &amp; Upgrades
---

### Post by dracojames on 2014-09-04
So, at the moment I've got Windows 7 64 bit installed on my PC. My plan is to have Ubuntu installed as dual boot. In the end, I hope to set this up so that rather than choosing my OS from a bootloader, I'll just select the Ubuntu drive in my BIOS when I want to use it, as my workflow requires Windows the vast majority of the time (unless there's a compelling reason not to - I just would prefer to have them entirely separate). I've run a Windows/Ubuntu dual boot on a computer in the past, so I'm not entirely new to this, but not a pro, either.

The problem that I'm running into right now is that every time I run the install media (have tried from both DVD and bootable USB created with Universal USB Installer), the computer will just shut itself down after a short time. If I'm not mistaken, usually the media should bring up a graphical interface allowing me to either try or install Ubuntu. When mine is loading, it sometimes will bring up a black screen with a flashing cursor, freeze for a few seconds (cursor stops flashing), and then shut down. Other times, it's gotten me to a language selection screen, and after choosing English, I get a simple text-based menu (no mouse support) to Try Ubuntu, Install, Check disk for errors, and a couple other options (memory check and something else I think). After choosing Install, I've gotten to an Ubuntu loading screen (Ubuntu with cycling orange dots under it), but again after a short time it freezes and then the computer shuts down. I get similar results from choosing Try Ubuntu or Disk check.

My system is running on a Core i5 760 (2.80 GHz overclocked to 3.81), with 8GB of RAM, and my temperatures stay within the safe range under heavy loads (I have a closed-loop commercial liquid cooler) so it shouldn't be a problem with system power, or an overheating issue (something I've run into on an old laptop in the past).

Everything above was with the 64 bit .iso file, but I've also tried the 32 bit install via USB and had the same results. I have no idea what could be causing this, so any help would definitely be appreciated.

---

### Post by grahammechanical on 2014-09-05
You might need to an F6 boot option. See section 6 - F6 in this wiki page.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

You do not mention your graphic adapter. Is it hybrid graphics? Does this machine have a UEFI boot system or BIOS? 

Regards.

---

### Post by kansasnoob on 2014-09-05
Did you check the md5sum of the iso before creating the live DVD and USB?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by dracojames on 2014-09-05
@grahammechanical: I'm running a GeForce GTX 460 graphics cards, and as far as I know, the system is BIOS, not UEFI (my main boot drive is partitioned as MBR, which to my understanding indicates a BIOS system, whereas EFI would indicate UEFI). Thanks for the suggestion - I'll take a look at those F6 boot options tomorrow, probably - I'm burnt out on troubleshooting right now after hours of trying to get this working.

@kansasnoob: Yeah, double checked the MD5s on both the 64 and 32 bit ISOs before creating the install media. Forgot to mention that in my post.

---

### Post by dracojames on 2014-09-05
@grahammechanical: Thank you! I finally got it to install after setting acpi=off, noapic, and nolapic (not sure if both noapic and nolapic were necessary, but acpi=off alone didn't seem to do the trick - I tried all three next, and it went through).

I was wondering, though - are there any long term effects to installing this way? Will performance suffer, or anything else, because I had to use those options to install? Are they still set as the boot options now, or will they have reverted since the install is finished?

---

### Post by christopher9 on 2014-09-05
Have you run the Software Updater yet ? At the pop-up screen choose Settings>Additional drivers and you might consider the video driver selection and load the correct one for your Nvidia card...

---

### Post by dracojames on 2014-09-05
Yup, I ran the updater and got the video drivers going already, everything seems to be working well now. I was just curious if having to set those boot options to install was something I needed to concern myself with, or if I'm good to go now.

---

### Post by christopher9 on 2014-09-05
If you are able to shudown/restart/boot at will and work with minimal error generation I'd say you're on your way...don't forget to install a backup app of some sort and routinely backup your home directory....that way if you have to reinstall the OS you can restore some of your personal settings...good luck with it...
 FWIW, I've got a GEForce GT740M in my Toshiba P50 running Lubuntu 14.10 beta and I'm experiencing random video tearing and reboots....I've updated to nvidia-343 driver and set the Nividia Server power setting to Maximum Performance as opposed to Auto or Adaptive....so far so good but I may need to regress to the nvidia-331 driver or back down to the Intel integrated graphics if these incidents don't settle down...

---

