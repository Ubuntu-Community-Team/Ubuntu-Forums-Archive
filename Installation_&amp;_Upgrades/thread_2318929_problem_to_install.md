---
title: "problem to install"
date: 2016-03-30
forum: Installation &amp; Upgrades
---

### Post by lucao-orsi on 2016-03-30
I'm trying to install 14.04, I'm using my USB to do that. Everything is ok untill I select Install or Test Ubuntu on the boot with my pendrive.
After selecting this I just have a black screen and nothing happens.
I've used this same pendrive in other PC and worked very well.
This PC that I have this problem has an Nvidia card.
What to do to solve this?

---

### Post by Bashing-om on 2016-03-30
lucao-orsi; Hello,

What results when booting the liveUSB to the boot options menu, selecting F6 and setting "nomodedset" as a boot parameter ?
If this parameter permits you to boot "try ubuntu" we can do something similar for the install and at a later time install a graphic's driver.

[INDENT]one of those times the kernel
[INDENT][INDENT][INDENT]needs a bit of help
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by lucao-orsi on 2016-03-30
Hello,

The boot options just show to me this F6 options when I hit help.
I need to tipe "nomodeset" afer hit Help and F6?

Tks,
Lucas

---

### Post by Bashing-om on 2016-03-30
lucao-orsi; Hey !

Making progress:
> 
I need to tipe "nomodeset" afer hit Help and F6?

Nope, that ' nomodeset' is a preset and available in a drop down menu from the F6 screen .

Boot the liveUSB;
At the purple splash screen (stick figure keyboard emblems at bottom of screen) -> hit any key ->
Language screen -> escape key to accept the default ->
Booting options screen -> F6 key (other options) -> arrow down to the preset option(s) space or enter to accept and then the escape key to exit; 
Try "nomodeset" at this time; for other additions the boot options kernel boot line is now available, one may append "other" desired boot parameters to the end of the line that are not present in the "presets".
Enter key to continue the boot process to the GUI desk top; Degraded graphics is OK at this point.
Additional Drivers, location varies depending on the version, ->locate the Additional Drivers utility and install the recommended driver. This will not persist a re-boot.

If this is successful in the liveUSB we can install the operating system under these conditions and in a similar manner install the graphics driver in the actual install.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by lucao-orsi on 2016-03-30
I'm getting this boot screen when boot from LiveUSB.

[ATTACH=CONFIG]268072[/ATTACH]
I don't have options, even hitting Advanced option (nothing there).
I used the Universal USB Installer to create this LiveUSB.

---

### Post by Bashing-om on 2016-03-30
lucao-orsi; Ho Kay ..

That screen is of UEFI as the hardware firmware, 
In this context it is the escape key that grub looks for . There is but a small window - 3 seconds - of opportunity for grub to recognize the escape key, As soon as the firmware screen clears repeatedly depress/release the escape key. All else remains the same.

Please advise, are you going to dual boot ? If so ,,, how ubuntu is installed may be critical .

UEFI is a horse of another color .

[INDENT][INDENT]but doable
[/INDENT][/INDENT]

---

### Post by lucao-orsi on 2016-03-30
Yes, I'll have dual boot. I already have dual boot with ubuntu and windows 10. But I need to make a fresh ubuntu install. I have an HD with windows and other HD dedicated to Ubuntu. To select the boot source I need to hit F8 key while my computer starts, after that I select the USB drive.
If I understood well, after selecting my boot source I should start depress/release escape key, right? Or should I don't press F8 and press escape key before grub runs?

Tks!!!

---

### Post by Bashing-om on 2016-03-30
lucao-orsi; Yes .

> 
after that I select the USB drive.

Immediately begin pressing/releasing the escape key as soon as the USB begins to boot .

Mind you I am not familiar with EFI and each and every manufacture implements the firmware different.

sometimes:
[INDENT][INDENT]I just have no need to know
[/INDENT][/INDENT]

---

### Post by lucao-orsi on 2016-03-30
I was reading about UEFI, but my computer doesn't seen to be in this mode. My MotherBoard isn't so new to have this feature.

---

### Post by Bashing-om on 2016-03-30
lucao-orsi; Welp;;

That black screen from the image you provided rather than a purple screen says this is a EFI system.
Be aware, how you boot the installer is how it will install . EFI/legacy/CCSM or what not.
see:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by lucao-orsi on 2016-03-31
I pressed escape key, on the screen, and tried the command nomodeset.
Happen this, see the picture.
[ATTACH=CONFIG]268092[/ATTACH]

The only thing that works is memtest... heheh at least this works....

---

### Post by Bashing-om on 2016-03-31
lucao-orsi; Sheeshhh ...

I am lost as to where you are .
Assuming this is a legacy firmware ..
Boot the installer, and as soon as the bios screen clears, depress and hold a shift key .
Is the next screen you see the language selection screen ?

Also, did you verify the .iso file that you "burned" ? Maybe we have a corrupt image ?

sometimes
[INDENT][INDENT]I do wonder
[/INDENT][/INDENT]

---

### Post by lucao-orsi on 2016-03-31
Nothing happens when I hold a shift key.
What I think that is happening (my video card is not correctly loaded):
When I select to try Ubuntu or Install a gray screen appears, after that appears 2 lines of codes at the top, after that a black screen flashes (my monitor tell me that is no signal - power management mode). I can hear the cooler of my video card slowing down (maybe wrong drivers are been loaded). After this at the keyboard the numlock light turn on and after turns off, and my USB devices are powered up (at this point I think that ubuntu is fully loaded, but I have no image, the reason to think this way, is because this is the same at my notebook).

Yes, I`ve checked this .iso whit my other 2 notebooks, the option to try Ubuntu worked correctly.

And yes, this is a Legacy firmware.

Thanks

---

### Post by Wayne_Anderson on 2016-03-31
[COLOR=#000000][INDENT]If you have the option, change the option os windows 8.x to windows 7 in the bios.

See 2nd pic here: [http://www.guruht.com/2014/09/how-to...sus-x200m.html]("http://www.guruht.com/2014/09/how-to-install-windows-7-on-asus-x200m.html")[/INDENT]


[/COLOR]

---

### Post by Bashing-om on 2016-04-01
lucao-orsi; Hello;

That " What I think that is happening (my video card is not correctly loaded): " is what the boot parameter is all about. Take the Graphical driver out of the equation and boot with the fall back kernel's graphic's driver.
That 1st step is to get you to the installer's boot menu and make that adjustment. At that point, the only driver loaded is that of grub's . It is very simple and reliable in this context.

Should not be such a big deal .

[INDENT][INDENT]it is all in the process
[/INDENT][/INDENT]

---

