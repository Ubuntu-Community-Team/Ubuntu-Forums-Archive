---
title: "Install from USB, reboot, will not load."
date: 2014-10-03
forum: Installation &amp; Upgrades
---

### Post by scott70 on 2014-10-03
I am a newbie when it comes to Linux, and would love to start getting more familiar with it, but can not seem to figure out what to do.  I have a Lenovo B570 laptop that I would like to install Ubuntu on and can not seem to figure it out. 

Basically I downloaded the ISO, made a live usb drive, and clicked install.     The install completes and tells me to remove the install media and restart, and then nothing. Will not boot, brings up the boot menu, i select the HD and nothing. 

I tried to do the same install with Linux Mint and same issue. 

What am I doing wrong!!!

---

### Post by Bucky Ball on 2014-10-03
Welcome. Brings up the boot menu? You mean the Ubuntu grub boot menu, where you can choose an OS, or it brings up the computer's device boot menu, where you can choose a device to boot from?

Just wondering how you created the USB and which release are you using. 14.04 LTS?

When you choose the HD, exactly what happens? Black screen? Blinking cursor? A error message of some kind?

---

### Post by scott70 on 2014-10-03
I created the usb with UUI. As soon as the computer reboots, screen goes black for about two seconds, then I get a error screen, followed by the computers boot device menu.

Pictures
[URL="https://drive.google.com/file/d/0B0u__tf2RMyxTkF5ZHREUHotUFE/view?usp=sharing"]Error Screen 

[/URL]

---

### Post by yancek on 2014-10-03
The Ubuntu installation medium has several options.  Did you select Erase disk and install Ubuntu or one of the other options?  Did you accept all the default values during the installation?  If so, that would be pretty unusual on a system such as your with no other operating system.  Did you use GPT or MBR method to boot during the install?

---

### Post by scott70 on 2014-10-03
I selected "Erase Disk and install Ubuntu".  I accepted all default values and I am sorry but I dont understand the last. I booted with the live USB and ran the installer.

---

### Post by craig10x on 2014-10-03
Perhaps you get have someone download ubuntu and make a dvd iso of it, then set your bios to boot of cd/dvd drive and pop in the disc while in bios...it would then boot up off the iso and first go into live session (try ubuntu) and once it totally loads in, select the "install Ubuntu" icon from the desktop (double click) then select the option to wipe the disc and install ubuntu...
Might well have better luck doing it from a dvd iso then from the usb...just a thought in case others here can't get you straightened out with your current install...

---

### Post by scott70 on 2014-10-03
Figured it out!!!!

[COLOR=#000000][FONT=courier new]"
mount /dev/sda1 /mnt[/FONT][/COLOR]
[COLOR=#000000][FONT=courier new]cd /mnt/efi[/FONT][/COLOR]
[COLOR=#000000][FONT=courier new]cp -rfv ubuntu boot[/FONT][/COLOR]
[COLOR=#000000][FONT=courier new]cd boot[/FONT][/COLOR]
[COLOR=#000000][FONT=courier new]mv grubx64.efi bootx64.efi"


This fixed my issue! 
[/FONT][/COLOR]

---

### Post by Bucky Ball on 2014-10-04
Excellent work, thanks for sharing, and glad to hear all is good for now. Good luck and enjoy! ;)

---

