---
title: "Not installing/working"
date: 2010-08-29
forum: Installation &amp; Upgrades
---

### Post by Cptn Krunch on 2010-08-29
Alright, so I'm an avid windows fanboy, but I wanted to check Ubuntu out, and dual boot it.

First, I tried Wubi, and all is fine, but when I choose Ubuntu on the boot menu, it shows some dialog, then just blank. its stays blank forever, so I had to shut the computer off.

Then, I burned the Ubuntu iso to a CD and botted from it at startup. This at least showed the purpl-ish install screen. After I pressed enter over install, it went to the blank screen again. just black, nothing appeared.

I'm not sure what the problem is. My laptop is fairly new, it shouldnt be having an issue to run it.

I have 4Gb RAM, plenty of space on the hard drive, and a 1Gb video card...

I have no clue what to do, as this is my first encounter with an Linux distro ever. help?

---

### Post by mr clark25 on 2010-08-29
sounds like a graphics driver issue. try using the VESA driver. press any key when it first starts loading ubuntu. (while the little picture at the bottom of the screen is present) and then press f4 (i think its f4...) i believe its under the "other options" option. select the VESA driver and then boot from the cd.


if my directions are a little vague/wrong, feel free to correct me.

---

### Post by Cptn Krunch on 2010-08-29
f6 was other options. Anyways, there was no option for "VESA" anything. thanks for the suggestion though.

---

### Post by Rubi1200 on 2010-08-29
Take a look here for some possible workarounds:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

But, we really need to know what graphics card you have to offer solutions.

Hope this helps.

---

### Post by oldfred on 2010-08-29
I thought f4 was the choice for minimal video.

I have nvidia and had to use f6 and use nomodeset. That setting also works for some other video cards but there are other settings also. What video card do you have?

---

### Post by Cptn Krunch on 2010-08-29
I have a Nvidia GeForce 9400. Its sitting in an Alienware M-17x laptop, running Windows 7... if any of that helps.

---

### Post by oldfred on 2010-08-29
I had to do this for my nvidia 9600:
boot from the cd, press F6 and then select the nomodeset option.
(I actually edited my grub.cfg as I use grub to boot ISO on USB, or in USB's syslinux.cfg or text.cfg)
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
After I installed nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.

---

