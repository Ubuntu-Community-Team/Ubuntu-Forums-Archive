---
title: "Ubunto on nVidia G-FORCE 5200 PCI"
date: 2006-08-01
forum: Installation &amp; Upgrades
---

### Post by Michael Boutros on 2006-08-01
Hello,

I am trying to install Ubuntu on my desktop PC, which has a nVidia G-FORCE 5200 PCI graphics card. When I put in the CD and load it up, I get to the last stage where it trys to load X, but then it never works, it just says that loading X failed. However, I tryed it on my sisters laptop and it worked fine, so I know for sure it is my computer. It is either the graphics card, or the CD drive. I have had some problems before with the CD drive. Unfortunately, I don't have another drive in my PC tower to test it with. Can anyone please help me?

Thanks,
Michael Boutros

---

### Post by zxee on 2006-08-01
> I get to the last stage where it trys to load X, but then it never works, it just says that loading X failed. 
If the Xserver is failing then perhaps it's only that and not your optical drive's fault.
So before we look for other problems try > dpkg-reconfigure xserver-xorg from the commandline you find yourself in after you get the xserver failed to load message. In that configuration program enter the driver for your card. You'll get a chance to select one. The open source driver for your card is nv. If you know the values for the other questions the set up program asks you can enter them; if you don't leave those values blank. Hope that helps.

---

### Post by tseliot on 2006-08-01
Does your computer have also an integrated graphic card?

If so, please post the model of the card

---

### Post by Michael Boutros on 2006-08-01
> **zxee said:**
> If the Xserver is failing then perhaps it's only that and not your optical drive's fault.
So before we look for other problems try  from the commandline you find yourself in after you get the xserver failed to load message. In that configuration program enter the driver for your card. You'll get a chance to select one. The open source driver for your card is nv. If you know the values for the other questions the set up program asks you can enter them; if you don't leave those values blank. Hope that helps.

I tried that, and I chose nv and it didn't work, so I just left all the values from automatic discovery, and it still didn't work. I took a picture of the error screen after I was done with the settings and typed in "startx":

[(Linked because it's big)](http://www.michaelboutros.com/screen.jpg)

Also, I do have on board graphics, but Windows is configured to use the nVidia chip and I am not sure what the model number is.

Thanks,
Michael Boutros

---

### Post by zxee on 2006-08-01
> Also, I do have on board graphics, but Windows is configured to use the nVidia chip and I am not sure what the model number is.

The image you supplied gets very fuzzy after the "Fatal Server Error No screens found" part 
I'm not sure but it doesn't seem to be complaining about the driver-although it could still be that. What did you select for screen resolutions? If you know the specs of your monitor you can put those in. Running that dpkg command again you can also select fbdev or try other drivers to see if that will get you a useable xserver.

---

### Post by Michael Boutros on 2006-08-01
> **zxee said:**
> The image you supplied gets very fuzzy after the "Fatal Server Error No screens found" part 
I'm not sure but it doesn't seem to be complaining about the driver-although it could still be that. What did you select for screen resolutions? If you know the specs of your monitor you can put those in. Running that dpkg command again you can also select fbdev or try other drivers to see if that will get you a useable xserver.

I didn't change anything, the only screen resolution that is already selected is the first one, 640 x 480, and I don't know how to select anything else. What other drivers do you think would work, other than nv? fbdev? Anything else?

Thanks,
Michael Boutros

---

### Post by Michael Boutros on 2006-08-01
Also, for some reason, the on-board graphics chip does not work at all, but this has nothing to do with Ubuntu.

---

### Post by zxee on 2006-08-01
> **Michael Boutros said:**
> Also, for some reason, the on-board graphics chip does not work at all, but this has nothing to do with Ubuntu.

But the ubuntu installer might have detected it anyway-which I think is the reason tseliot asked about an onboard graphics card.

You can try vga for your driver. I don't actually remember all the possible drivers, but I know from past experiance that sometimes experimenting will get a workable xserver.

Another thing to try is doing lspci -v and post the results. That may show your onboard card but since you've specified that the graphics card you're using is pci NOT agp you probably need to give the location of your card in the dpkg-reconfigure xserver-xorg set up.

---

### Post by Michael Boutros on 2006-08-02
> **zxee said:**
> But the ubuntu installer might have detected it anyway-which I think is the reason tseliot asked about an onboard graphics card.

You can try vga for your driver. I don't actually remember all the possible drivers, but I know from past experiance that sometimes experimenting will get a workable xserver.

Another thing to try is doing lspci -v and post the results. That may show your onboard card but since you've specified that the graphics card you're using is pci NOT agp you probably need to give the location of your card in the dpkg-reconfigure xserver-xorg set up.

I think you are right, because when I choose auto-detect it detects the onboard chip. However, when I do "lspci -v", it shows my nVidia card. Any ideas?

Thanks,
Michael Boutros

---

### Post by Michael Boutros on 2006-08-02
Sorry to bump, but I really want to install Ubuntu.

---

### Post by Michael Boutros on 2006-08-07
Anyone at all? Ubuntu looks great and I really do want to use it.

---

