---
title: "Screen Resolution LOST"
date: 2008-09-03
forum: Installation &amp; Upgrades
---

### Post by ivikas on 2008-09-03
Hello all,

         Iam using ubuntu 8.04 and it was all going well,then i came upon a software called "EnvyNG" that installed ATI driver.I used it for automatic and it could not detect ati 1650 pro and there is another option for EnvyNG that is manual install.I done it and finally i was asked to reboot the computer.But now i find my earlier screen resolution is lost.

After this i plugged my video display to the graphics card,but there is blank(dark) screen.So when i remove my graphic card and put the video in ordinary pc slot.My earlier screen resolution is lost.


Please give me a fix,

Thanks in advance

---

### Post by Amarsingh0793 on 2008-09-03
Which Graphics Card do you have? Is it ATI Radeon or NVidia? If it is NVidia, install a program called "NVidia X Server Settings" (via synaptic). When installed, go to System > Administation > NVidia X Server Settings. From there, on the left, click X Server Display Configuration, choose your suited resoltuon and click apply.

Hope this Helps :)

---

### Post by ivikas on 2008-09-03
Iam using ATI 1650 PRO

---

### Post by ivikas on 2008-09-03
Now it shows in XORG FILE AS

```

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:0:2:0"
	Driver		"ati"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"

```

---

### Post by Mark Phelps on 2008-09-03
You've got a lot going on, and I'm not sure what you're doing, so I have to ask some questions.

You talked about plugging in the video card. I'm guessing this means your PC has both onboard video and you have a video card as well, and that you installed using the onboard video.  You then downloaded EnvyNG, ran it, it detected the ATI card (which you were not hooked up to) and installed for it.  Then when you rebooted, you did not get a high res screen -- but you were still hooked up to the onboard video.

Right so far?

Then, you said you moved your video card to another slot.  So, I'm guessing it's a PCI card, not AGP or PCI-X.  Then, after moving the card, you get no display.

Right again?

Here's what I think happened.  When you installed using EnvyNG, it created a new Xorg.conf file with settings for the detected ATI card. Since you weren't hooked up to the ATI card when you rebooted, of course, you didn't get the correct display.  If you had then hooked up to the ATI card and rebooted, everything should have been OK.

But instead, you moved the video card.  When EnvyNG created the Xorg.conf, it put the address of the video card (at that time) into the file.  So now, with the card in a different slot, the Xorg file has the wrong address.

What should fix it is returning the video card to the slot it was in when you installed envyNG, and hooking the monitor video cable to that card. Also, to safe, disable onboard video in your BIOS settings.

---

### Post by ivikas on 2008-09-04
Hello Mark,

            Firstly,iam running ubuntu 8.04 LTS Desktop and a windows XP in dual boot system.I have an onboard video card and a seperate video card that is ATI 1650 PRO.[COLOR="Red"]I downloaded the EnvyNG and run it.It Could not detect my ATI CARD,so there is a manual install option,i clicked it and the driver was installed.Leter i was asked to reboot the computer.I then done this,but before it i reconnected computer monitor video output to the ATI CARD.There is no display--Just a blank dark screen[/COLOR].So i was evident ,a new xorg file has been created and so resolution is lost.i don't have backup of earlier file so i was at despair.Today i just booted to live cd and was planning to replace the live cd's xorg file with my local ubuntu installation.But i needn't have to do this as ubuntu autoconfigured the screen resolution for me.Iam on a LAMP development system so do not want to risk again :-D

However,if there's a perfect guide you can link me,i will definetely go for it as i am crazy about compiz graphics

Thanks for your time and help dude

---

### Post by Mark Phelps on 2008-09-04
If you go to the AMD/ATI site for the video drivers, when you select Linux, you will see that they provide a downloadable installation guide.  This  walks you through the steps to be done to install their drivers in various ways.

Also, my experience in 8.04 is that modelines and resolution settings in the xorg.conf are pretty much ignored.  I had to end up using the screen resolutions settings panel to set my resolution to greater than 800x600, regardless of what was in the xorg.conf.  So, if your resolution resets, you may have to resort to that method as well.

---

