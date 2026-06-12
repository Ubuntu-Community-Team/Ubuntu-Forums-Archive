---
title: "New ATI graphics card installation problems"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by arlw2008 on 2008-07-10
Hi, I have been using ubuntu on my desktop computer for about 6 months now and really do like it. I recently upgraded my monitor to a 22in, as my graphics card couldnt output at a high resolution and use compiz, i decided to upgrade to a Sapphire ATI Radeon HD 3450 with a PCI Express interface. When i put the card in to my computer and booted up, the computer booted up as normal then got to just before the ubuntu loading screen and then the screen just turned off. I tried booting from the live CD, but that didnt work either. I tried re-installing and that didnt work. My guess is it a driver issue as the computer outputs to the monitor in vga mode on start up but as soon as it gets to the loading screen (which uses a driver  with the graphics card...i think) the screen goes blank.

The motherboard that im using is a Asus A8N-E Deluxe, with an AMD athlon 64 3000+ venice core. Im not sure on the exact spec of ram and hard drive but i assume that doesnt matter for this problem. 

Any help will be gratefully recieved, pls let me know if you need any more information inorder to help.

Thanks in advance.

---

### Post by chalewa on 2008-07-10
did you try getting the fglrx drivers from the ati website?



edit: [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-6-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-6-x86.x86_64.run)

you can get the new 8.6 driver there, and follow these instructions:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

---

### Post by arlw2008 on 2008-07-10
Thanks for the quick response i have but i have having a few problems with them. But i think that i may be able to resolve them with abit of playing about. If these drivers are correctly installed, when i put the new graphics card in, will it work straight away even though i would have installed the drivers using my old graphics card? sorry if this is a stupid question.

---

### Post by chalewa on 2008-07-10
> **arlw2008 said:**
> Thanks for the quick response i have but i have having a few problems with them. But i think that i may be able to resolve them with abit of playing about. If these drivers are correctly installed, when i put the new graphics card in, will it work straight away even though i would have installed the drivers using my old graphics card? sorry if this is a stupid question.

um i can't say with 100% certainty. i would like to think yes, if you had two different xorg's but i can't be sure. 

if i were you, i would probably download the driver to your computer somewhere, you would be able to do everything from the command line before you actually boot into x

---

### Post by arlw2008 on 2008-07-10
One of the thing that i have been trying to do is get to a command line before the graphic card driver kicks in but i have been unsuccessful, how do you do that?

---

### Post by chalewa on 2008-07-10
> **arlw2008 said:**
> One of the thing that i have been trying to do is get to a command line before the graphic card driver kicks in but i have been unsuccessful, how do you do that?

in grub, before you even click on the kernel you want to boot into, there should be a failsafe option. that will give you just a command line to work from

---

### Post by wpshooter on 2008-07-10
I think the first 2 things that I would try would be to #1 try to install Ubuntu using the safe graphics mode.

If that does not work, then I would try installing from an ALTERNATE CD version of Ubuntu.

---

### Post by chalewa on 2008-07-10
> **wpshooter said:**
> I think the first 2 things that I would try would be to #1 try to install Ubuntu using the safe graphics mode.

If that does not work, then I would try installing from an ALTERNATE CD version of Ubuntu.

yea but i think that he already has hardy installed, and even if he did that, isn't he still going to have to install ati drivers at some point?

---

### Post by wpshooter on 2008-07-10
> **chalewa said:**
> yea but i think that he already has hardy installed, and even if he did that, isn't he still going to have to install ati drivers at some point?

I think by the time it takes them to figure out how this might be fixed that they can re-install the O/S "properly" from scratch and be done with it.

---

### Post by arlw2008 on 2008-07-10
I have already tried re-installing ubuntu, using the gui install and using the alternative cd. Unfortuntly neither worked.

---

### Post by chalewa on 2008-07-10
well it is ultimately your choice as to what route you want to go, i would try to install the drivers from the command line and see if you can get it to work. once you have the drivers downloaded it is pretty step by step.

---

### Post by 73ckn797 on 2008-08-26
My son has the ATI Radeon HD 3450 card also. We have installed Hardy Studio 64 on that machine. It runs but if I enable the restricted driver and reboot the system stops just before fully loading and I get the "Out of range" message and system freezes. I have to run the recovery mode on boot to fix the xserver. Then it boots fine but I am back to square one.

I have been browsing the forum and will follow the instruction on the "How To" link. Will this allow the "Extra Visual Effects" to work through Compfiz?

I have a nVidia card and do not have to deal with this issue.

---

