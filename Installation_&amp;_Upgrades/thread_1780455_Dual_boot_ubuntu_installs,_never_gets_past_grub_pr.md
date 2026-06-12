---
title: "Dual boot ubuntu installs, never gets past grub prompt"
date: 2011-06-12
forum: Installation &amp; Upgrades
---

### Post by JH0009 on 2011-06-12
ASUS AMD e-350, trying to set up dual boot ubuntu side by side with win7. 1st time linux
Live usb ok, / boot/ swap home/ partitions seem to setup ok
Installed with grub to boot/, seems ok, then easy bcd.

Rebooted, got grub prompt.
Never got past this stage with multiple tries.
Used ubuntu doc guide for grub prompt and it looks like vmlinuz and initd arent where theyre supposed to be and dont point to the proper files anyway, didnt know how to fix.
Boot-repair and reinstalling grub2 from terminal didnt fix
Reinstalling completely with grub2 to MBR broke everything and got dead end grub rescue prompt.
Had to recovery

Is there something Im not doing right?  How do I fix vmlinuz and initrd?  I'd like to not have to load grub2 to MBR if possible
EasyBCD never seemed to recognize anything other than the windows partitions, and never got past GRUB4DOS prompt

---

### Post by YesWeCan on 2011-06-12
I understand why you do not want Grub in the MBR of the XP disk.
I know that EasyBCD works with Vista/Ubuntu. Not sure about XP.

Alternatively, you can save yourself a headache or two by using a USB stick to boot from. Install Ubuntu to the USB stick (you never use the USB Ubuntu, just boot from it to the HD Ubuntu) and then boot it and run 'sudo update-grub' to add XP and HD Ubuntu to the menu. Always boot from the USB. This way you keep the MBR untouched on the XP disk and you don't need EasyBCD.

---

### Post by JH0009 on 2011-06-12
Im using win7, not xp.  
Unfortunately EasyBCD does not work for me... after "autoconfiguring" and rebooting, all it does is go into GRUB4DOS prompt.  ls does not see the linux partitions, and other commands like set don't work

I'm wondering if it is a UEFI issue but other people with the same laptop seem to install it fine via installer

---

### Post by dino99 on 2011-06-12
please read:

[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

### Post by YesWeCan on 2011-06-12
> **JH0009 said:**
> Im using win7, not xp.
Oops, Win7 sorry. I have set this up before. I assume you have a separate installation of Ubuntu, not a Wubi thing, and that you installed Grub to the root partition of Ubuntu? Honestly, it isn't worth the hassle. With Win7 especially it is easier and causes no problems to just to install Grub to the MBR. Or install grub to another disk's MBR if you have another disk.

---

### Post by Frogs Hair on 2011-06-12
There may be something helpful at the link.[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by oldfred on 2011-06-13
Best to post this, so we can see what is where:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

