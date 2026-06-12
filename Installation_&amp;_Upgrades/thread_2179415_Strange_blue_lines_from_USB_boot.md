---
title: "Strange blue lines from USB boot"
date: 2013-10-08
forum: Installation &amp; Upgrades
---

### Post by maslacher on 2013-10-08
Hi, i'm trying to install ubuntu on my pc (G1610 with intel HD graphics) but i have a big issue. Currently i'm using manjaro linux and it's works but i would like to give a ubuntu a try. I don't have cd drive so i install from 4GB pendrive using dd bs=4M if=(direction to iso) of=/dev/sdb and when i try to boot i've got strange vertical blue lines and there is nothing i can do about it.  I'm thinking this is some driver compatibility issue but i don't now how to solve this. I tried earlier install ubuntu on virtual machine from oracle and works perfectly.

---

### Post by sudodus on 2013-10-08
I think it is a problem with the graphics driver. You might succeed with a boot option, for example ***nomodeset***. See this link

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Am I right, that this is a new system (bought this year)? If so, you should try a new version of Ubuntu, 13.04 or the not yet released 13.10 to get the appropriate drivers.

---

### Post by maslacher on 2013-10-08
I have partialy solve this. I have to install in nomodeset mode but this works only for me in uefi install. In legacy/normall mode i can't choose nomodeset because after pinky screen with keyboard i have black screen. And i can't install in uefi because i have MBR.
@sudous i bought G1610 recently and i'm trying to install 13.04 but i propably try to install 13.10 if this will not work.

---

### Post by sudodus on 2013-10-08
If it works in UEFI mode you will be able to make work also in classic BIOS mode (booted live from syslinux and also booted from grub when installed).

At the  pinky screen with keyboard you should press a key to get to a menu, where you can add the boot option.

---

### Post by maslacher on 2013-10-08
Thank's sudodus you're great. It's working.
After install can i solve this issue with that?
sudo add-apt-repository ppa:tjaalton/ppa
sudo apt-get update 
sudo apt-get dist-upgrade
Edit: I've just downloaded 13.10 final beta and everything for now works nice and easy so it's solved.

---

### Post by sudodus on 2013-10-08
I don't know about that ppa. Maybe it will help you. (If not you can always remove it and try something else.)
And you can add ***nomodeset*** to grub in the installed system. See this link

[https://help.ubuntu.com/community/Grub2/Setup](https://help.ubuntu.com/community/Grub2/Setup)

for example text about [FONT=courier new]**/etc/default/grub**[/FONT] where you can add boot options according to 

> ***GRUB_CMDLINE_LINUX*** 


[LIST]
[*]Entries  on this line are added to the end of the 'linux' command line (GRUB  legacy's "kernel" line) for both normal and recovery modes. It is used  to pass options to the kernel. 
[/LIST]

***GRUB_CMDLINE_LINUX_DEFAULT=***"quiet splash" 

[LIST]
[*]This  line imports any entries to the end of the 'linux' line (GRUB legacy's  "kernel" line). The entries are appended to the end of the normal mode  only. 
[LIST]
[*]To view a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash". 
[/LIST]

[/LIST]


Good luck :-)

---

