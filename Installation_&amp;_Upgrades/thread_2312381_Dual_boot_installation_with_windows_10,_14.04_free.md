---
title: "Dual boot installation with windows 10, 14.04 freeze on logo"
date: 2016-02-04
forum: Installation &amp; Upgrades
---

### Post by Aleksandar_Stevano on 2016-02-04
Hey everyone,

I got a problem with installing ubuntu 14.04.

I got a new laptop( [https://www.asus.com/Notebooks/N552VX/](https://www.asus.com/Notebooks/N552VX/) ), and it already has preinstalled windows 10. I already use dual boot with windows 8 on my other laptop, installed it withoud a problem two years ago.
On new one, I have disabled fast and secure booting, as suggested, and got a ubuntu installation on usb and dvd also(just in case).
Whenever I try to "Try ubuntu", it starts loading, and then freeze on boot screen with ubuntu logo and those orange circles bellow.
Also, I tried installing ubuntu, without 'trying it', and the same happens. After then I have to power it off completely by pressing power button for a few seconds. I spent all day yesterday trying to fix it, and no luck. I also had powered it off like this for a dozens of times, but I would not like to torture it like that anymore by trying :)


I only found one topic about this ([https://askubuntu.com/questions/678623/stuck-on-logo-cannot-install](https://askubuntu.com/questions/678623/stuck-on-logo-cannot-install)) , and it sounded similar to this situation.
The guy suggested to:
> [COLOR=#111111][FONT=Ubuntu]Change the SATA config to IDE and (for any reason.. do not ask me why) I had to set the windows mode to windows 7 in bios. [/FONT][/COLOR]

But I don't have these options in my BIOS. As for the SATA configuration, I only have one SATA mode selection (AHCI), and it's chosen...

If someone could help, I would really appreciate it.

Hey, sorry for double posting. I used nomodeset parameter and got ubuntu to run, and afterwards installed it. But it came with a lot of issues...
My touchpad is not working, and I couldn't shut down the computer, it would freeze when I click on shut down or restart.
And beside that, my fan would not stop working, althought my temperature was bellow 30 C...
Then I found the solution to add acpi off and grub update. It helped with shut down issue and with the fan, but now I have to find a way to install the touchpad...

Back to the lab...

---

### Post by oldfred on 2016-02-04
The instructions on IDE mode is wrong, It only should be AHCI which most new systems default to.
Even newer is NVMe, which some small SSD on motherboard now use.
IDE was for compatiblity with the now 10 year old PATA/IDE drives booting in BIOS mode.

And some UEFI have Windows and "other". Which really is secure boot. And Windows 7 does not have secure boot, so it also needs the "other" setting.

Have you updated UEFI to newest from Asus?

This has other boot parameters also:
[http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters](http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters)

---

### Post by ceejazz on 2016-05-28
Hi Aleksandar,

did you finally succeed? And how did you do it.

having the same problems here.

Chris

---

