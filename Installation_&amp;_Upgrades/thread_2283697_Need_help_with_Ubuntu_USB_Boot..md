---
title: "Need help with Ubuntu USB Boot."
date: 2015-06-23
forum: Installation &amp; Upgrades
---

### Post by Stilian_Zagorov on 2015-06-23
I am trying to create a bootable usb withPenDriveLinux, but I cant find the iso file. I have never done anything like this before and all tutorials arent simple enough. Can someone send me a link to the easiest to understand and simplest tutorial? Or you could walk me trough here. Thank you in advance.

---

### Post by sudodus on 2015-06-23
Let us try here!

1. What computer is it? Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

and it will be much easier to give relevant advice.

2. What have you got and what do you want?

- Is there Windows in the computer now? Do you want to keep it? In that case which version is it?

---

### Post by Stilian_Zagorov on 2015-06-24
Well,

1.
Acer Aspire One D250
Intel Atom N270 at 1.60GHz
1GB ram card. (Planning to upgrade to 2GB)
[FONT=Verdana]Mobile Intel 945 Express Chipset Family
[B]This is what I found in the *Device Manager *program. I am not sure if it is correct or not.

[/B]Atheros  AR8132 PCI-E Fast Ethernet Controller (NDIS 6.20)
Broadcom 802.11g Network Adapter.

--------------------------------------  (I want Ubuntu 14.--)
I have Windows 7 and the minimum required specs are right on the edge of my specs (It is slow as hell)
I want to only have Ubuntu on my PC and have a copy of Windows XP so I can work on some XP only tasks.
But if dual boot is easier and will not make Ubuntu slower or if it takes a lot of HD space, then I would prefer a dual boot. 

[I]What I would like to know
[/I][/FONT][FONT=Verdana]Could I run Tiny7 (minimalised version of Win7) instead of XP?[/FONT]
[FONT=Verdana]If so, replace WinXP with Tiny7 in the criteria below.
 [/FONT][FONT=Verdana]
Is it easier to make a bootable flashdrive with Windows XP on it, or
is it easier to have WinXP and Ubuntu on my PC.
If I have both installed on my PC, will it perform slower.
If I have both installed on my PC, will WinXP take up a lot of space.
--

Thanks alot for the help! :D[/FONT]

---

### Post by Bucky Ball on 2015-06-24
Download the .iso from [here]("http://www.ubuntu.com/download/desktop") to your desktop. Launch Pendrive USB. Point it to the Ubuntu .iso you have just downloaded to your desktop.

This:

> **Stilian_Zagorov said:**
> 

What I would like to know
Could I run Tiny7 (minimalised version of Win7) instead of XP?
If so, replace WinXP with Tiny7 in the criteria below.
Is it easier to make a bootable flashdrive with Windows XP on it, or
is it easier to have WinXP and Ubuntu on my PC.
If I have both installed on my PC, will it perform slower.
If I have both installed on my PC, will WinXP take up a lot of space.
--


... is the stuff of another thread(s) as it has nothing to do with the title or subject of this one. You will greatly improve your chances of getting help by asking these things elsewhere. Attempting to answer all this on an unrelated thread when working on another issue will be nothing but confusing. Do you still want help getting the USB working? 

In a nutshell, if you can run XP, Xubuntu or Lubuntu will run absolutely fine on this box. Perhaps even Ubuntu, but I'd try one of the other two. 

Good luck. ;)

---

### Post by Stilian_Zagorov on 2015-06-24
Thank you. I was looking for the iso everywhere. I uderstand that you cant help me with the other stuff. Thanks, again.

---

### Post by Bucky Ball on 2015-06-24
> **Stilian_Zagorov said:**
> Thank you. I was looking for the iso everywhere. I uderstand that you cant help me with the other stuff. Thanks, again.

We can help you, but better off doing it elsewhere. The alternatives you mention I would only be worrying about if you can't get Xubuntu or Lubuntu, at least, running from USB, and there's no reason that can't happen. :)

Great you've got the .iso. If your machine is barely chugging along with Win7, Xubutu and Lubuntu are lighter and probably a better choice. Here's a link to the [Xubuntu]("http://xubuntu.org/") .iso and one for [Lubuntu]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu").

If you have any more issues creating the boot USB, let us know. ;)

---

### Post by sudodus on 2015-06-24
I agree with Bucky Ball. I would recommend that you download Lubuntu and Xubuntu 14.04.2 and [try them live before deciding what to install]("http://ubuntuforums.org/showthread.php?t=2230389").

The following link and links from it have a lot of tips how to create a USB boot drive.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

After reading it you can ask here. We have a lot of experience in creating USB boot drives and booting computers from them.

---

### Post by Stilian_Zagorov on 2015-06-24
I dont really like the other ones. I tried doing the USB thing, and it worked... But my laptop gets stuck on the boot logo. I dont know what to do.

---

### Post by sudodus on 2015-06-24
Standard Ubuntu might need more RAM and CPU horsepower, maybe also a better graphics chip to work.

---

### Post by Stilian_Zagorov on 2015-06-24
I checked the minimum required specs. My specs are over the minimum required. I just need help with the bootup thingie.

---

### Post by sudodus on 2015-06-24
Try with a boot option, for example **nomodeset**. See this link how to manage the boot options

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Stilian_Zagorov on 2015-06-25
I think that you misunderstood me... When I try to boot my laptop with the flash drive plugged in, I get the Acer logo, and nothing else. It says that I can tap **F2** for setup, but it doesnt work. It's like a still image. Nothing will happen if I pull the flash drive out, or if I tap buttons. I dont know what iis happening.

---

### Post by sudodus on 2015-06-26
If the computer is fast, you may need to press the F2 key all the time while booting. Sometimes cold booting works better than rebooting. You can also search the internet for alternatives to the F2 key (or simply try several key 'trial and error').

Sometimes another pendrive works better - if you have the possibility to borrow one.

Have you tried the pendrive in another computer?

---

### Post by Stilian_Zagorov on 2015-06-26
I will try later, but I just think that my laptop has gone obsolete. Its 5 years old. Do you think that it might be the problem. The last available BIOS update was september 2010.

---

### Post by sudodus on 2015-06-26
No, 5 years is old for some people, but we are running linux quite well in computers that are 10-12 years old. But not standard Ubuntu and Kubuntu, such old computers need lighter desktop environments. A 5 year old computer should definitely work, unless something is damaged, or there is some very special hardware.

Your Acer Aspire One should work at least with Lubuntu.

---

### Post by Bucky Ball on 2015-06-26
Nope, definitely not obsolete. None of my machines would be under five years old except for a netbook I just bought which has the specs of a flea anyhow. They are all running xfce4 desktop environment and some Xubuntu. I have an Odroid that runs the lighter Lubuntu fine. :)

---

