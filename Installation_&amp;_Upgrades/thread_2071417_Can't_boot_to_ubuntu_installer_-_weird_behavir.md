---
title: "Can't boot to ubuntu installer - weird behavir"
date: 2012-10-15
forum: Installation &amp; Upgrades
---

### Post by newlinux on 2012-10-15
Hi

Let's start with the background.

I've had some older hardware laying around, and I decided to get an old Socket 939 mobo off ebay to put it together. It's an X2 4200 proc, Asus a8nvm mobo. However I can't seem to get the installer to run with 12.04 64 bit or 32 bit. Twice I got it to screen where it lets me choose to install or try and i chose try and then it the installer froze. Other than that, I never get to that screen. I just get the moving dots ubuntu boot up screen, and it eventually freezes after a couple of minutes. Other key points of information:


[LIST]
[*]I've checksummed the install discs, and tested for defects - no issues. I've used this same disc for other installs.
[*]Another issue as that I can't get the internal IDE CD drive to even boot off of the ubuntu discs. It did however boot off of an old Windows XP installation disc, and I was able to complete an install of XP (just testing the hardware). The BIOS is set to boot off CD drive first. And I've entered the BIOS boot menu and manually selected the internal CD drive.
[*]I have an external USB disc drive I've been trying to install from, and that's where I'm getting this behavior.
[*]I also have an bootable 12.04 usb flash drive that exhibits the same weird behavior when I try to use it (freezes before I get to the install screen)
[/LIST]

Thinking there might be a problem with my internal CD drive (it's on the older side) But that doesn't explain the USB fails.
Things I will try next:
[LIST]
[*]Pick some of the different boot options (any recommendations?)
[*]Alternate 12.04 iso
[*]Install a different internal CD drive and try from there
[*]Try a different distro?
[/LIST]


Anybody had this problem before or know how I should proceed? I have installed ubuntu dozens of times over the last 6 years, and never had this happen before. I really would like to know why this is happening. Any help is appreciated.

---

### Post by darkod on 2012-10-15
You didn't mention the video card. If it's nvidia often you need to use the nomodeset parameter.

When you boot with the live cd/usb, if you hit Esc right away at the first purple screen, it should show the older style Main menu.

Hit F6 for advanced options, you can select nomodeset there.
After you are back to the main menu, select Try ubuntu to try it.

If that worked, you can install but note that on first boot you will need the nomodeset again, until it lets you boot once and activate the video driver. If you don't know how to add the parameter on first boot, you can ask.

Lets see first if it helps you.

---

### Post by newlinux on 2012-10-15
> **darkod said:**
> You didn't mention the video card. If it's nvidia often you need to use the nomodeset parameter.

When you boot with the live cd/usb, if you hit Esc right away at the first purple screen, it should show the older style Main menu.

Hit F6 for advanced options, you can select nomodeset there.
After you are back to the main menu, select Try ubuntu to try it.

If that worked, you can install but note that on first boot you will need the nomodeset again, until it lets you boot once and activate the video driver. If you don't know how to add the parameter on first boot, you can ask.

Lets see first if it helps you.

Nomodeset did not work for me (different looking boot up screen, same problems :)). That was the one boot parameter I did try last night (I almost always run nvidia cards since almost all my machines are HTPCs). The Asus mobo I mentioned has onboard nvidia 6150. But I also have a gt210 that I'll probably eventually put in for VDPAU capability. I took it out just in case it was causing problems and right now am staying with the onboard until I get things working to remove variables.

---

### Post by newlinux on 2012-10-16
Alright. Looks like at a certain part of the installation the mobo loses connectivity with the USB DVD/CD drive. The internal IDE CD/DVD drive was flaky and only worked sometimes. So, I installed another CD/DVD drive and was able to boot from it and installed from the alternate iso, but then I got lots of kernel panics and crashes every time I booted. Then I turned off ACPI in the bios aand reinstalled off the regular 64 bit disc from the new dvd/cd drive and all was well. So far the install has been stable with ACPI turned off.

so it was a combination of a faulty connection to a usb drive, faulty internal DVD/CD drive, and turning off ACPI that finally did the trick.

So it was

---

