---
title: "Can't finish install of 13.04"
date: 2013-06-22
forum: Installation &amp; Upgrades
---

### Post by rickydia on 2013-06-22
Ok, please help me out. Here is what is going on. At the moment I am able to write this from the "try ubuntu without  installing" option. I installed 13.04 from my usb stick, everything went  fine, then at the end it said it needed to restart to finish the  installation. I clicked ok and it rebooted to the original screen with  the four options of 'trying ubuntu without installing,' 'install ubuntu'  and something for manufacturer install and then the last one of  checking disc for errors. I do not know what to do at this point. I have  clicked install again and going through the install again and removing  the usb stick after clicking restart at the end. this did not work and  appeared to freeze the screen until i hold down power button and restart  it. At the top it says GNU GRUB 2.00. My computer is a laptop and relatively new and had windows 8, I chose the option to remove windows and replace it with ubuntu... So I don't think windows is even in there anymore. When I try to turn on the computer without the usb stick in an error message comes up that says something like 'unable to find the image.' 
Help Please, I've been trying to find answers for hours now..

---

### Post by dino99 on 2013-06-22
you said: i install from the usb stick; so i suppose you now need to stop booting from the stick, and switch to the hdd where ubuntu is now installed.

---

### Post by rickydia on 2013-06-22
How do I do that??? Sorry I'm not that tech savy. It took all my tech know how just to put the thing on the usb and follow the setup instructions.

---

### Post by Bashing-om on 2013-06-22
[COLOR=#000000]rickydia; Hi !

See dino99's last.

Not knowing what machine and the bios that is installed thereto can not provide specific instructions.
General: there is an option in your bios to set the device boot priority. Accessing the bios routines varies with each machine and what bios is installed by the manufacturer. so again can not advise how to access it.

Just set in bios the 1st boot priority as the hard drive, and assuming that when you installed 13.04 you directed the grub installation to be to the hard drive -> you will boot into ubuntu.

Else: will have to install grub ( GRand Unified Bootloader) onto the hard drive's Master Boot Record. Not a great big deal.
[/COLOR][INDENT=3][COLOR=#000000]
just try'n to help

[/COLOR][/INDENT]

---

### Post by rickydia on 2013-06-22
I don't know how to access bios. Can I get to it from gnu grub menu??

---

### Post by Bashing-om on 2013-06-22
[COLOR=#000000]rickydia;

No, you can not access bios from grub.

When you cold boot your system, the first thing that loads is bios... most bios screens advise what key(s) to press to enter the "setup" routine. On some implementations of bios, pressing the space bar will halt the boot process and allow you all the time you need to scan the screen and maybe see a advisory for the setup key(s) ??

Until such time as you can advise us what machine you are running and what bios the manufacturer has installed, there is not much else we can advise.
[/COLOR][INDENT=3][COLOR=#000000]
still try'n to help

[/COLOR][/INDENT]

---

### Post by oldfred on 2013-06-22
If you unplug flash drive will it not boot hard drive?

This shows many vendors boot keys, one to get into BIOS and anther for a one time change. Normally best to have hard drive as first boot option in BIOS (quicker boot) and use one time boot key when booting flash drive or DVD drive.
 UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

---

### Post by rickydia on 2013-06-22
I have a hp pavilion g6 with intel core i3 and it came with windows 8.. hope that helps! thanks for helping!

---

### Post by rickydia on 2013-06-22
[INDENT] 					I have a hp pavilion g6 with intel core i3 and it came with windows 8.. hope that helps! thanks for helping! 				[/INDENT]

---

### Post by oldfred on 2013-06-22
If Windows 8 was pre-installed you have all the secure boot issues. Did you follow all the suggestions in the link in my signature?

Someone posted this for HPs.
 HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)

---

