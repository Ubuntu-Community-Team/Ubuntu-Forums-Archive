---
title: "Installation Problem"
date: 2017-12-26
forum: Installation &amp; Upgrades
---

### Post by wbee on 2017-12-26
For Christmas,somebody gave me an HP Compaq 8000 Elite Ultra Slim Desktop that had Windows 7 Professional installed.

I have a DVD of the 16.04 64 bit lts Ubuntu system that I have used before to install on another compter with no problem.

So,I went into the BIOS (F10) and changed the boot order to boot from the installation DVD. I restated and it took me to the preinstalled Windows 7.

I went into the Windows 7 OS and tried to play a CD,which the OS would not recognize or play.

As best I can tell,the computer is not  recognizing the Disk player.

Yes,I know this is an Ubuntu site and not an HP site but among this knowledgeable group,do you have any ideas how I should proceed to install the 16.04 long term support Ubuntu OS on the computer?

Thank you.

---

### Post by ajgreeny on 2017-12-26
See **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 

**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system as at present we do not have enough information to know what is needed.
If the computer boots using UEFI you must also install Ubuntu using UEFI in order to boot both OSs from the grub boot menu.

---

### Post by wbee on 2017-12-26
ajgreeny,

Only the Windows 7 Professional was installed on the computer in question. 

Even with the bios set to boot the dvd,it will not do so and will only take me to Windows 7 Professional. So,I can't download boot-repair unless there is a way to download it using the Windows 7,much less be able to copy and transport the pastebin link.

The optical drive is not communicating with much of anything,as it will not even play music cds.

Sorry I could not be more help following your directions. :-)

---

### Post by oldfred on 2017-12-26
Some newer systems require a UEFI/BIOS setting to allow USB or DVD boot. That is for security to prevent someone else from booting your system. Do not know if yours has that setting but check UEFI/BIOS.

---

### Post by ubfan1 on 2017-12-26
From the BIOS/UEFI settings, is the DVD listed?  If not, look for other settings to enable it.  If the DVD may be popped out, remove it and reinsert it, maybe it's just loose.

---

### Post by wbee on 2017-12-27
ubfan1,

Thanks for the response. I went into the bios(UEFI is not listed) and yes,the burner is listed. The DVD was installed correctly. There is a linkage broken or non existent between the player and everything else. It won't play CD's or recognize a blank disk either.

---

### Post by wbee on 2017-12-27
Thanks all. Flashing the bios resolved the issue. Solved.

---

