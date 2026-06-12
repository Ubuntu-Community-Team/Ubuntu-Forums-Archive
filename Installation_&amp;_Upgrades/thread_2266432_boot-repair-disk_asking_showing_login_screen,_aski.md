---
title: "boot-repair-disk asking showing login screen, asking for username and password"
date: 2015-02-22
forum: Installation &amp; Upgrades
---

### Post by jsd014 on 2015-02-22
Hey, Everyone...  I recently brought back to life an old win xp/Ubuntu dual boot system that had been gathering dust at my place.   I'm giving it to a friend who doesn't need the ubuntu side.   The computer currently doesn't have a working CD/DVD drive, but can boot from USB.   It's an older system, and doesn't use EFI.   I used GRUB (yes, GRUB, not GRUB2) on it years ago, and would like to go back to the Windows XP MBR.
I downloaded boot-repair-disk from:
[http://sourceforge.net/projects/boot-repair-cd/](http://sourceforge.net/projects/boot-repair-cd/)
put it on a USB drive using unetbootin-windows-608, put the drive in the computer, booted up, and chose USB as the boot device.   UNetbootin started up with 4 options.   **It doesn't matter which option I choose, I end up at a lubuntu login screen asking for a username and password.**   This is probably really simple, but I have no idea what I should put in here.   All the tutorials I've seen online for boot-repair-disk don't show this login screen, and instead show boot-repair starting automatically.

I should add that simply hitting Enter here doesn't let me past the login box.   It seems to want a particular login/password combo...   Also, oddly, the login screen picture is green instead of the sunset like pic that I see in all the tutorials...

Anyone know what I should try here?

thanks for the help!

---

### Post by grahammechanical on 2015-02-22
There is more than one way to run Boot Repair then loading a Boot Repair image

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You could try running it from the installed Ubuntu or burn a Ubuntu ISO image to USB memory stick and run it from there. You may be better off using Lubuntu on that machine.

Are you sure that is the Boot Repair ISO on USB that is loading and not Lubuntu on the hard drive.

EDIT: I have Boot Repair on a CD. I have just run it to see what happens. Boot Repair live session is built on Lubuntu. This is what I get

1) Language selection screen
2) Black screen with "Boot Repair Disk" in large letters with 2 options - Boot Repair 64 bit and Boot Repair 64 bit failsafe.
3) Blue screen with "Boot Repair Disk" in standard letters and 5 moving dots
4) Boot Repair sunset back ground wallpaper and dialog saying "scanning systems."

What are the four options you see?

Regards.

---

### Post by jsd014 on 2015-02-23
Hello... I was going to describe everything I see during boot up, but then decided that pictures may be better.   Here's everything after the POST:
1) Boot device selection screen.   I choose "USB device" from this list.
[IMG]http://s7.postimg.org/igv9cq2zv/image002_Copy.jpg[/IMG]

2) UNetbootin starts, I can choose any option here (except "Help") and it will lead me to the same result.   In this case I chose "Default"
[IMG]http://s7.postimg.org/6t17i6duz/image003_Copy.jpg[/IMG]

3) Boot-repair-disk loading screen
[IMG]http://s7.postimg.org/ijf4zk6nf/image004_Copy.jpg[/IMG]

4) Boot-repair-disk login screen that I'm stuck at.   Here you can see the login box that I'm presented with...
[IMG]http://s7.postimg.org/aryf102i3/image005_Copy.jpg[/IMG]

I must be missing something very simple about this process...   Any ideas on what I can do?

Thanks for your help!

Edit: other things I should tell you about this computer... It currently doesn't have a working network connection.   That and the CD/DVD drive isn't functioning...

Edit2: I just tried building the boot USB with rufus-1.4.12 and booting with it.   While the startup looked different, I still ended up at the green login screen...

---

### Post by jsd014 on 2015-02-24
Well...   I tried several different combos and variations to get this to work, and I'm still unsure of why it doesn't (or at least why I keep getting this green screen).   I was able to replace the MBR using the MbrFix utility in Hiren's Boot CD on a boot USB drive ( [http://www.hiren.info/pages/bootcd-on-usb-disk](http://www.hiren.info/pages/bootcd-on-usb-disk) ).   Thank you, grahammechanical, for your help!

---

### Post by kent19 on 2015-10-16
A little late to the party but did you ever solve this ?
I tried various logins, then tried a blank password and that let me in.
Not sure what's going on there.

---

### Post by vitimiti on 2016-05-18
Apparently, this problem can happen when the CD is scratched. I'd try burning it onto a new CD or a USB drive, that should fix it.

---

