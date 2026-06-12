---
title: "Install on server with just USB and Serial console"
date: 2022-10-30
forum: Installation &amp; Upgrades
---

### Post by hvdk on 2022-10-30
Hi,

I have a number of older appliance (Check Point Smart-1 410) that are no longer supported by the vendor but are good for lab stuff at home. The only have 2 USB ports and a serial console (RJ45).

I managed to get it to boot from USB and setup the serial console by removing `quiet flash` from the boot entry and adding `console=ttyS0,115200n8` and tehre I am running a server from USB. but I could not find a way to start the text installer. (And I have taken my time to search for it.)

For example [https://ubuntu.com/server/docs/install/general](https://ubuntu.com/server/docs/install/general) explains a bit about the serial console but I always go to the live image and never got a chance to do choose the installer.

So for now I would be looking for a few answers to questions like:
 1. How can I adjust my USB boot stick to enable Serial Console always?
 2. How can I start start the text mode install once the live image has started?

I m not sure wether it is me, google or some steps are simply never documented.
feel free to elaborate if you want to in your answer.

Just to get is straight I put Ubuntu server 22.04 on USB stick and tried 22.04.01 as well.

Any hints to get me going will be appriciated.

Regards, Hugo.

---

### Post by grahammechanical on 2022-10-30
The only thing that I can think of is that you are looking for a text installer when trying to install Ubuntu Desktop. You speak of running a server from USB. It is my understanding that Ubuntu Server edition does not have a live session and always launches a text based install session. I am not sure that we get a text installer version with Ubuntu Desktop. Is this the screen you are seeing?

[https://ubuntu.com/tutorials/install-ubuntu-desktop#4-boot-from-usb-flash-drive](https://ubuntu.com/tutorials/install-ubuntu-desktop#4-boot-from-usb-flash-drive)

If it is then follow the steps and you will get to the next section (5) - Installation-Setup. Select the Minimal Installation.

[https://ubuntu.com/tutorials/install-ubuntu-desktop#5-installation-setup](https://ubuntu.com/tutorials/install-ubuntu-desktop#5-installation-setup)

I have not tested the Minimal Install but I think that once you select it you get something like this:

[https://cloudinfrastructureservices.co.uk/how-to-install-ubuntu-minimal-desktop-tutorial-step-by-step/](https://cloudinfrastructureservices.co.uk/how-to-install-ubuntu-minimal-desktop-tutorial-step-by-step/)

Notice the section on the Installation Guide. There you see a text based installer.

Regards

---

### Post by hvdk on 2022-10-31
I used the ubuntu-22.04-live-server-amd64.iso image as base line. This is the one listed at the time as the latest LTS version. I know there now is also a 22.04.01 LTS version. but the name implies also it can run as live server. But I never get the question wether I want  install or run as live CD. This may be due to the time it takes to boot the machine with a serial console set to 9600n8 and then I have to adjust my terminal to a higher speed or watch for 2 to 3 minues to the boot messages on 9600. Either way I guess the question comes and goes due to all that extra time.

That is why I was looking for a way to adjust the USB drive to work directly on serial console instead of having to fight with emacs on a 9600 bps terminal and change the boot params to get a serial console active.

---

### Post by hvdk on 2022-10-31
Based on [https://github.com/AndiDittrich/debian-ubuntu-serial-install](https://github.com/AndiDittrich/debian-ubuntu-serial-install)
I have created a new USB drive with Ubuntu Server 22.04.01 LTS and then made a change to /boot/grub/grub.cfg as shown below.
After boot on a terminal on 9600 bps I could chooose the boot menu and had to change to 115200 bps to get the remainder. But now I have a normal installer choice.
So one can update the boot stick for this purpose.

menuentry "Try or Install Ubuntu Server" {
	set gfxpayload=text
	linux	/casper/vmlinuz  console=tty0 console=ttyS0,115200n8 nosplash ---
	initrd	/casper/initrd
}

---

