---
title: "Grub won't boot"
date: 2011-11-06
forum: Installation &amp; Upgrades
---

### Post by si-jockster on 2011-11-06
Dear All. I suspect I have deleted my ubuntu partion and now I can't boot to windows 7 or ubuntu.

OS's: 11.10 and Windows 7 (64-bit) dual boot
Machine: HP G61
* Does not have option to boot from USB

I have tried booting various boot utilities from web with no luck i.e.
11.10 Live CD
Super-Grub
Hiren'sBootCD

With all of these it starts to boot, give me the initial text of the bootloader then give me the following error:
"Cannot open CD driver FDC0000. SHCDX33A cannot load!"

I am at loss what to do next. Any all help/suggestion gratefully received. Many thanks, Simon

---

### Post by oldfred on 2011-11-06
You need to have a working liveCD. Have you correctly burned it, not copied it and burned it at the slowest speed you can? If you look in BIOS what boots first?

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Once you get a liveCD working post this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by bluexrider on 2011-11-06
So let me get this straight. 

You are unable to boot ANY live distro?

You have checked your BIOS settings to boot from CD/DVD?

If you can boot a live distro chances are you can fix it.

---

### Post by darkod on 2011-11-06
I will just add be careful with SuperGrub. It's not the same grub as in ubuntu as far as I know, and it might complicate things more.
All you need is the ubuntu desktop cd to boot into live mode. You can fix the boot with that.

And not being able to boot any CD has nothing to do with ubuntu. If that is the case, you might have another problem too.

---

### Post by si-jockster on 2011-11-06
OldFred - you are a star - used ImgBurn and it is now booting into live CD.

How do I reinstall grub etc.

Many, many thanks, Simon

---

### Post by cogier on 2011-11-06
There is this wonderfull tool that will sort this out for you. Go to [http://sourceforge.net/projects/boot-repair-cd/files/]("http://sourceforge.net/projects/boot-repair-cd/files/") and download the Boot Repair ISO file.

Use Brasero to "Burn an image" to CD. Then boot from the CD and when prompted use the "Fix usual problems....." option.

It's the easiest fix I have found for Grub problems.

Keep the CD in a safe place...

---

### Post by si-jockster on 2011-11-06
Many, many thanks Cogier - all sorted now by running Boot-Repair and using ImgBurner.

Kind regards, Simon

---

