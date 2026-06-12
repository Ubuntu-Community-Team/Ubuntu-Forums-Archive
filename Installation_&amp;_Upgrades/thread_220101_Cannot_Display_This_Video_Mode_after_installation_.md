---
title: "Cannot Display This Video Mode after installation is complete"
date: 2006-07-21
forum: Installation &amp; Upgrades
---

### Post by sfernand on 2006-07-21
I've been wrestling with this problem for a bit now .... Have an old AOpen PII MMX Pro 350 MHz with ~400MB RAM, 6 GB HD and a Dell 1704FPV that I decided to convert to a Ubuntu box. During the install from a CD, I needed to adjust the display using the F4 key from VGA to 640 X 480 X 24. (If I don't change this, I get the Cannot Display this Video Mode and the monitor become unresponsive, making the install hang.) Now the install proceeds beautifully and everything completes. When I reboot the system, it gets to "booting the kernel" and then I get the message "1. Analog Input: Cannot Display this Video Mode." Once I get this message, I can do nothing with my monitor ... so tried rebooting several times. My monitor autoadjusts to what the computer is sending it. During installation, when I hit the menu button on my monitor, it shows that the current resolution is 640 X 480 @ 60Hz refresh. Post-install, while the boot process is still ongoing, when I hit the menu button on my monitor, it shows that the resolution is now 720 X 400 @ 70Hz!!!! Don't know why it is changing. How can I get around this issue?

---

### Post by wieman01 on 2006-07-21
You can control the resolution in this file:

/etc/X11/xorg.conf 
or
/etc/X11R6/Xorg.conf

(I forgot... I am not in front of my Linux machine right now.)

There is a line for your monitor and graphic card that says "default". There you can define what default resolution the card/monitor ought to use from a pre-defined list (further below) of possible resolutions. Choose a number (1, 2, 3, 4, 5, ...) according to the resolution you want to pick. 

You can access the file system without entering the graphical mode by choosing "recover" or something similar when GRUB is loaded (very beginning of your boot process). 

Look on the web how to change text files in the terminal mode.

But that's the way to go I guess. You will have to mess around in the text mode until you have changed the settings in the "xorg.conf".

Good luck.

---

### Post by K.Mandla on 2006-07-21
> **wieman01 said:**
> You can control the resolution in this file. ...
(I was going to suggest that, but I wasn't sure the OPer had gotten all the way through a full installation. ;) Next time, I go for it!)

---

### Post by wieman01 on 2006-07-21
> **K.Mandla said:**
> (I was going to suggest that, but I wasn't sure the OPer had gotten all the way through a full installation. ;) Next time, I go for it!)

Hahaha... looking for "unanswered posts" then. ;-)

I am not sure either to be honest, but the header says "after installation...". If he hasn't then he will have to find a spare display. I have heard of such issues before and the common solution was to find a display that could deal with such kind of resolution.

Let's wait what the reply is. You are definitely NEXT! :-)

---

### Post by sfernand on 2006-07-21
Thanks for your responses. I believe the installation is complete unless the installation needs to complete stuff upon reboot (a la MS-Windows) which I seriously doubt. I was following someone's recommendation at this link and everything happened like a charm ... [http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p2](http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p2) (with the exception of the display change using F4). So on the reboot, I get stuck. I will follow wieman01's suggestions and let you know how I make out! Guess I was just tired of multiple installs late at night!:confused: 

Ta!

---

### Post by sfernand on 2006-07-30
Okay, so I decided to go with Ubuntu desktop instead of Ubuntu server. Everything installed like a charm. Except that the GUI stuff displaying during the install kept flickering. When I hit the Dell 1704FPV menu button, it showed that the refresh frequency was at 62Hz! (optimal recommended - 60Hz). Nevertheless, let everything complete and rebooted. Once the boot gets underway, for a portion I can see the linux kernel getting started etc. Then the screen goes back to the message "Analog Input: Cannot display this video mode". Went couple of times back to "recover" from GRUB and played around with the /etc/X11/xorg.conf file. All the right resolutions and frequencies are included. Still got the message. Then I just let it boot and got distracted by something. When I returned after about 15 minutes, lo and behold, the GNOME desktop had started, even though there was tremendous screen flickering. Entered id and password, went into System -> Preferences -> Screen Resolution and set the appropriate values that are optimal for my Dell 1704FPV. Voila!!! Screen doesn't flicker any more. Having an absolute beautiful experience with Ubuntu and GNOME - screensavers are quite breathtaking and my kids love to watch!!!! However, the problem hasn't completely gone away ... everytime I boot, there's a period between GRUB and GNOME starting up where I get the error message. Also, whenever I exit GNOME, I get the message too. Is there some way to permanently fix the issue, no matter where I am in Ubuntu? Would appreciate some help/advice!

---

