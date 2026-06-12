---
title: "Can't install Toshiba Satellite E205"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by linuxlovinwarren on 2010-02-24
Hi I've been trying to figure this out all day, I just got a new Toshiba Satellite E205, and I can't install ubuntu or any other linux os out there that I have tried so far. I've read a lot of things on the forms about changing out the different options but nothing I've tried worked such as graffic safe mode, deleting the quite and whatever the other command was off the end. The closest I've got was when I tried with Debian in text mode I could at least see what was happening, and according to that it can't find my dvd-rom I checked the \dev but I can't find it either. So any help what so ever would be appreciated, I really don't want to be stuck with windows 7!
 
Ohh BTW, it comes with the following: intel graphics media accelerator HD ACPI x64 DVDRAM ga10f

---

### Post by mörgæs on 2010-02-25
Does it work if you boot with a 10.04 live CD?

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by galley3175 on 2010-02-28
I just purchased the same laptop and with the 10.04 imaged using the no acpi option on boot I was able to boot and install.  I could not boot once the install completed, but this was due to the fact that I need to set the same option for the grub boot loader.  I hope this helps.

Thanks,

Gary

---

### Post by linuxlovinwarren on 2010-03-02
I eventually got 9.10 to install, but no luck getting to see the login screen, I'm downloading 10.04 right now so hopefully this will fix my problem!

---

### Post by darkod on 2010-03-02
> **linuxlovinwarren said:**
> I eventually got 9.10 to install, but no luck getting to see the login screen, I'm downloading 10.04 right now so hopefully this will fix my problem!

It sounds like video driver related. Do you know which video card do you have?

Also, you can try this: Boot the computer but at the grub menu don't hit Enter to boot ubuntu. Highlight the ubuntu option but hit 'e'. That will show the boot commands. In the line starting with linux.... at the end add:

vga=771

That should be basic video mode. Hit Ctrl + X and see if it will boot the desktop that way. If it does, and once you tell which video card you have, we can sort out a driver.

---

### Post by linuxlovinwarren on 2010-03-02
it's a intel gma hd card in it, I'm going to try this 10.04 to see if it works with the no acpi option for me like it did for galley on the same laptop, but otherwise it's a video problem for sure. Because I can see the circle of friends come up and the kernal and stuff all loading underneath them but it looks bad, then it blanks out,btw I have to use the i915.modeset=0 to get that

---

### Post by linuxlovinwarren on 2010-03-02
alright tryed the vga=771 it said something about gfxpayload but didn't do anything, back to downloading

---

### Post by linuxlovinwarren on 2010-03-03
THANK YOU EVERYONE!!!!!!!!!!
Alot of work to find out that 10.04 works perfect with the acpi=off statement!

---

### Post by mörgæs on 2010-03-05
Congratulations. Do you feel like writing a brief summary on 
[http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/) ?

---

### Post by kwunderlich on 2010-06-01
By the way, you will need to press the F6 key during the boot process and the Ubuntu menu will at some point appear.  Then be sure that the acpi=off has an "X" next to it under the F6 boot options.

---

### Post by Mochi on 2010-06-08
Hi, guys
 
I also bought Satellite E-205 and was trying to have Windows 7 and Ubuntu 9.10 dual boot. I managed to installed Ubuntu 9.10 through Safe Mode and acpi=off on F6 (otherwise just black screen after pressing "installation"), however I cannot get any internet (no wired or wireless) once log into Ubuntu 9.10.
 
Does Ubuntu 10.04 solve all these problem, black screen in installation, internet connection etc.?
 
Thanks a lot!

---

### Post by linuxlovinwarren on 2010-06-09
Well there is still ACPI problems, so I manually turn it off everytime I boot, being too lazy to change it permanently :). Since I've loaded 10.04 I haven't had any problems with the my network card, none of the lit up "touch buttons" on the side work which can be kind of annoying and the fact that I can't see how much battery life I have left has kept me kinda dependent on windows but I'm glad to say everything else works great!

---

### Post by dimpet on 2010-06-14
Hi All

I have got my toshiba e205 working with ACPI enabled.

This allows the following to work
- battery monitor 
- CPU scaling (battery will last longer)
- Function keys 
- Lit up keys on the right of the keyboard.

Definitely worth doing. Just install the following kernel patchs (which were made for the Toshiba **L505-ACPI,[B])** [/B]See [http://ubuntuforums.org/showthread.php?t=1301101&page=27](http://ubuntuforums.org/showthread.php?t=1301101&page=27)

[http://www.coxei.com.ar/Cosas/linux-...stom_amd64.deb]("http://www.coxei.com.ar/Cosas/linux-headers-2.6.32.11+drm33.2-l505-acpi-rtl8191se-64bits-generic_2.6.32.11+drm33.2-l505-acpi-rtl8191se-64bits-generic-10.00.Custom_amd64.deb")
[http://www.coxei.com.ar/Cosas/linux-...stom_amd64.deb]("http://www.coxei.com.ar/Cosas/linux-image-2.6.32.11+drm33.2-l505-acpi-rtl8191se-64bits-generic_2.6.32.11+drm33.2-l505-acpi-rtl8191se-64bits-generic-10.00.Custom_amd64.deb")

sudo dpkg -i linux-headers-2.6.32.11+drm33.2-l505-acpi-rtl8191se-64bits-generic_2.6.32.11+drm33.2-l505-acpi-rtl8191se-64bits-generic-10.00.Custom_amd64.deb

sudo dpkg -i linux-image-2.6.32.11+drm33.2-l505-acpi-rtl8191se-64bits-generic_2.6.32.11+drm33.2-l505-acpi-rtl8191se-64bits-generic-10.00.Custom_amd64.deb

Then following commands (after install the packets):
[I]sudo update-initramfs -c -k 2.6.32.11+drm33.2-l505-acpi-rtl8191se-64bits-generic
sudo update-grub[/I]

---

### Post by dimpet on 2010-06-14
Don't forget to remove acpi=off after you install the new kernel.

---

### Post by linuxlovinwarren on 2010-07-01
I'm trying to use this fix but it won't install the package, very confused on why it wont what kernal were you running when you used this?

---

### Post by linuxlovinwarren on 2010-07-02
Alright I followed the instructions on the thread you pointed out, and made my own custom kernel. I couldn't use the patches that you posted because it required AMD, and I have I386. It worked to get ACPI working I can use my side buttons turn off the mouse everything, but in order to use it I have to start it in recovery mode and put it in low graphics mode. Any ideas to get it fully working?

---

### Post by dimpet on 2010-07-15
I have uploaded my kernel config here, maybe that will help.

[https://docs.google.com/leaf?id=0B1f4ID6k5EJ-NWZhNmM4MzgtODA2OS00OGZlLWEyNDQtNjIwMDkzYTFkYTRh&hl=en](https://docs.google.com/leaf?id=0B1f4ID6k5EJ-NWZhNmM4MzgtODA2OS00OGZlLWEyNDQtNjIwMDkzYTFkYTRh&hl=en)

---

### Post by linuxlovinwarren on 2010-07-16
Alright thank you Dimpet, to finish of this thread for good to get this laptop up and running with Ubuntu, you have to use the AMD64 version of Ubuntu which the ISO can be found here: [http://releases.ubuntu.com/lucid/ubuntu-10.04-desktop-amd64.iso](http://releases.ubuntu.com/lucid/ubuntu-10.04-desktop-amd64.iso) When installing select to use the ACPI workaround, and when first booting hit e to edit the boot options and acpi=off then hit control-x to start up. Afterwords download the patches Dimpet posted above and follow his instructions, after that boot from the patched kernel and all should be well. Once again thank you a ton Dimpet.

---

### Post by myers.pa on 2010-07-20
Hey so between dimpet and linuxlovin I got this to work. However last night for whatever reason I removed ubuntu from my laptop. Came back today and the the links to the Kernel patches were dead. Can someone either send them to me or maybe know of another link?

Thanks!

---

### Post by linuxlovinwarren on 2010-07-21
Alright I uploaded them to google this should hopefully stay open for download.

[https://docs.google.com/leaf?id=0B13mGDYo6R1xMWM5OTk1MWEtNWI5ZS00YTFiLWI2YzItNjkzMzZkOTlmYTEz&sort=name&layout=list&num=50](https://docs.google.com/leaf?id=0B13mGDYo6R1xMWM5OTk1MWEtNWI5ZS00YTFiLWI2YzItNjkzMzZkOTlmYTEz&sort=name&layout=list&num=50)

[https://docs.google.com/leaf?id=0B13mGDYo6R1xMGZjYWY4OTctNjc2ZC00ZWIzLWEwNDgtMzg2ZjI0ZjMzYmFl&sort=name&layout=list&num=50](https://docs.google.com/leaf?id=0B13mGDYo6R1xMGZjYWY4OTctNjc2ZC00ZWIzLWEwNDgtMzg2ZjI0ZjMzYmFl&sort=name&layout=list&num=50)

---

### Post by myers.pa on 2010-07-21
Sweet. Thanks very much. I've got them saved on an external hard drive now as well just in case :D

And thus, Ubuntu flourishes once more. Thanks everyone!

---

### Post by hayvanAdam on 2010-08-14
Thanks for great thread.
I have a problem. I changed my kernel but keyboard backlight function does't work.

---

### Post by linuxlovinwarren on 2010-08-25
Does your backlight not work at all or is it only on? Mine is stuck on all the time but I kinda like it on all the time, so I never worried about it.

---

### Post by kwunderlich on 2010-08-28
Anyone know when the patch will appear in the official kernel or where to look as to when it is scheduled to be included?

---

### Post by linuxlovinwarren on 2010-09-15
I have no idea, but if you find out I think we would all like to know. I would love if one of these days I could start using the most current again.

---

### Post by KushedVapors on 2010-09-15
> **kwunderlich said:**
> Anyone know when the patch will appear in the official kernel or where to look as to when it is scheduled to be included?

Im assuming you're talkin about the patch that you have to use acpi=dsdt or whatever at the end of the boot line(dont kno if thats what its called). If so its implemented in the .35 kernel.. Im usin that kernel on Archlinux and everything seems decent except the power managment(doesnt squeeze out the same hours that windows does). Dont kno what kernel Ubuntu is usin right now since i left a while ago.

Oh and has anyone got the backlit key on the right to work. The one that turns it on and off? i kno people got there apple laptops that have a backlit keyboard to turn off and on. Forget what the packet they use is called.

---

### Post by maheshk1102 on 2010-09-25
Hi,
I want to install 10.04 with usb stick on the Toshiba Satellite E205 
Please help
I am not able to install with CD 
Please  help

---

### Post by mörgæs on 2010-09-25
Please write exactly what happened when you tried installing from CD and what you have done to solve the problems. Noone can help you without a detailed description.

---

### Post by maheshk1102 on 2010-09-26
Hi,
I want to install 10.04 with usb stick on the Toshiba Satellite E205
Please help
I am not able to install with CD
The last command seen on the page is kernel_help
I tried with my usb pen drive to install but it could not be started and the diplay message was could not find the sislinux.
I am new to linux so need step by stepp process for installation.As I went thorugh sveral threads, I learned that it is difficult to install on Toshiba E 205.
But I want to run my system on linux.
Please help

---

### Post by mörgæs on 2010-09-27
What happens if you try booting from CD? Please write all error messages.

---

### Post by tec_know_joe on 2010-10-12
This post helped me install 10.04 on my E205 just great but when I upgraded to 10.10 the new kernel did not load.  Has anyone had any luck with this?

---

### Post by mörgæs on 2010-10-12
How does it work when booted with a live CD?

---

### Post by linuxlovinwarren on 2010-10-20
The only way to boot from the live CD is to change the settings so that it disables ACPI, this will allow you to see what is actually happening but should only be used for your initial installation of Linux, after that you need to follow the instruction found at the beging of the forum to install the custom kernals which you will use to boot after words. If you need more info I'll check back in over the next week or so.
 
On another note, I never turn off my back lit key board so it doesn't bother me but any information on kernal updates that work better for our machines is appreciated.

---

