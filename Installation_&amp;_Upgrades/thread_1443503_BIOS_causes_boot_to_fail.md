---
title: "BIOS causes boot to fail?"
date: 2010-03-31
forum: Installation &amp; Upgrades
---

### Post by G-forze on 2010-03-31
I have just bought a new system (specs below) and tried to install Ubuntu 9.10 but so far have not even gotten to starting the installation. Using a Live CD, after the first menu (where you pick language, settings, etc.) the computer freezes with a black screen and only a blinking underscore. Thereafter nothing happens and I have to push Reset.

Using the ordinary 32 bit Live CD I was able to perform the boot by choosing Safe Graphics Mode and choosing all the F6 alternatives (I don't know which one did the trick). With only Safe Graphics it still froze, but displayed a text about a BIOS error and recommended using pnpbios=off.

My problem now is that I want to install to RAID 1 and thus need to use the Alternate installation CD. This CD has no Safe Graphics Mode, and nothing I do seems to give me anything other than the blinking underscore. What's going on, and is there anything I can do to get my dear Ubuntu working for me again? :)

The specs, as promised:
Motherboard: Asus P7H55 Intel H55 LGA1156 ATX 
Processor: Core i3 530 
RAM: 4 Gb (2x 2Gb) DDR3 1066
Gfx: Asus ENGTS250 DK/DI/1GD3 nVidia GeForce GTS250 1GB
HDs: 2x Western Digital Caviar Green SATA II 1.5 Tb

---

### Post by dstew on 2010-04-01
The Alternate Install CD uses a text-based installer, so "safe graphics mode" is not available or needed. What happens when you try to use the Alternate Install CD? Does it boot? Do you get an error message of some kind? Are you sure the CD is good (works normally in other computers -- bad burn?)

---

### Post by linux_lux on 2010-04-01
I am having the similar issue. It may have something to do with the Icore3 processor and the bios we are using. I am using a Acer with a ICore 3. 

Here is what happens:

1.) Using WUBI or LIVECD I am able to get into the installation to setup the language, keyboard preferences and the partition setup.
2.) Once the system reboots, right before the splash screen appears, a screen flashes up and then disappears.
3.) Once this happens the system just hangs on a black screen, sometimes this screen has a flashing curser.
4.) I have tried running in different modes, used WUBI, 32 bit and 64 bit installs (LIVE CD) and tried the server build and have the same result. 

Once the machine reboots I notice that the windows boat loader is still in tact. So it seems that the GRUB loader isn't installed at that point, which I thought installed during the initial part of setup.

I am at a loss and need to get a linux install on my machine for work, however I refuse to use anything but unbuntu.

Any insight to this would be appreciated. Has anyone had success installing 9.10 on a ICORE 3???

Linux_Lux

---

### Post by dstew on 2010-04-01
It's not the processor. See [this blog]("http://www.phoronix.com/scan.php?page=article&item=intel_corei3_530&num=1") for an Ubuntu system running an iCore 3 processor. There could be some issue with BIOS and/or motherboard settings, but first make sure the Alternate Install CD is good.

---

### Post by linux_lux on 2010-04-05
Thanks. I am downloading the Text-based installer and will see what that brings me. The blog mentioned in the other post doesn't really give me too much to go on. They didn't even specify which Linux distro they were using. I am going to hope that the text-based installer will allow me to install on the Icore 3. Apparently the integrated chipset graphics are the root of the problem. Otherwise I will wait until 10.04 is released for this machine.

---

### Post by oldfred on 2010-04-05
Note that Phoronix used Lucid to test and made this comment:

but it will work  with recent Linux distributions and should work particularly well with the distributions  coming around in H1'2010 that are using the Linux 2.6.32 kernel (or newer).

---

### Post by quadproc on 2010-04-05
> **linux_lux said:**
> ... Apparently the integrated chipset graphics are the root of the problem.
You might be having a problem with X windows not knowing which graphics hardware to use.  Do you have a BusID on your primary graphics device?

quadproc

---

### Post by G-forze on 2010-04-06
> **dstew said:**
> The Alternate Install CD uses a text-based installer, so "safe graphics mode" is not available or needed. What happens when you try to use the Alternate Install CD? Does it boot? Do you get an error message of some kind? Are you sure the CD is good (works normally in other computers -- bad burn?)

When I use the alternate install CD I get the same menu where I can pick the language, install settings and such. When I choose "install ubuntu" I get the blinking underscore and nothing else happens. Nothing at all. And no matter what choices I make in the previous menu this does not seem to change.

I agree that it seems logical it would be a chipset problem. Hopefully the good guys at Canonical are aware of the issue and working to fix it...

---

### Post by dstew on 2010-04-06
Are you sure the CD is good? Does it work in other computers? But, you are right, it could be that the kernel on the CD is not working with your hardware.

By the way, Canonical does not create Ubuntu, they only provide technical support. If you want to help the developers, you should create a [bug report]("https://bugs.launchpad.net/ubuntu/"). I searched the bugs for icore and ubiquity (the installer) and could not find anything. So maybe the developers need to know.

Be sure the CD is good though before submitting a bug report.

---

### Post by Slim Odds on 2010-04-06
> **dstew said:**
> Are you sure the CD is good? Does it work in other computers? But, you are right, it could be that the kernel on the CD is not working with your hardware.
...

The CD's have a built-in self test (checksums against a known value), so you don't even have to check it in another computer. Just run the test.

---

### Post by rustutzman on 2010-04-06
Some BIOS' contain a setting to protect the boot sector. I had one I could not get any operating system to install. Checked BIOS and there was a switch for "Install OS" mode with "On" and "Off" as the selections. I set it to "On" and the install went smoothly.

Russ

---

### Post by G-forze on 2010-04-08
> **Slim Odds said:**
> The CD's have a built-in self test (checksums against a known value), so you don't even have to check it in another computer. Just run the test.

Now I've done some checking and these are the results:

- I could not check the alternate Live CD with another computer, since I only have a macbook and it doesn't boot from the CD. The on-disc check didn't help much either, it only gave me the same blinking underscore.
- I kept trying the normal Live CD and found out that the combination of Safe Graphics Mode and No apic is what works (for booting from CD at least). Either one by itself just results in - you guessed it - a blinking underscore.

I'm really at a loss here, but I'll submit the bug at least. Thinking of staying with Windows 7. God forbid... ;)

Maybe if I tried Kubuntu or another distro alltogether? Anyways, thanks for all your input. It is much appreciated!

---

### Post by G-forze on 2010-04-14
Now I can confirm that the alternate CD is in fact ok. I used it to install Ubuntu yesterday on my girlfriends laptop and it worked without so much as a hick-up.

Must be my new hardware, then.

---

### Post by G-forze on 2010-05-05
So I managed to get Ubuntu installed, after all. Seems some settings in the BIOS were blocking, after I played around for a bit and turned some stuff on and off everyting worked just fine.

I can't be sure it's what did the trick, but my best bet would be that I enabled "Max CPUID value limit". No idea what that means but BIOS said it was disabled for Windows XP.

Hope this helps someone. I'll mark the thread as "solved".

Once again, thank you for all your help!

---

