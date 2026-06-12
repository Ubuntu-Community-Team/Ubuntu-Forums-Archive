---
title: "no text status messages in 6.10 splash screen"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by mykmelez on 2006-10-27
After upgrading from 6.06 to 6.10, usplash stopped working (Ubuntu started displaying a blank screen during startup and shutdown), although my system starts up fine, and gdm displays the login screen once the system finishes starting up.

Adding vga=791 (1024x768 resolution) to my grub configuration file as per [step 6 of the usplash customization howto]("https://help.ubuntu.com/community/USplashCustomizationHowto#head-3f1a5b3bcea03e357b466d0f04f41bfe01d1f8bc") got things partially working again, as the Ubuntu logo and progress meter now appear on startup and shutdown.

But the scrolling status messages still don't.  Did 6.10 do away with those messages, do I need to do something else to get them to appear, or is this a bug?

---

### Post by maino82 on 2006-10-27
I have the same problem, with the added problem of the loading screen being offset. The image says "Ubun" on the right hand side of the screen and wraps around to the left side where it continues with "tu." Any ideas as to why this may be happening?

---

### Post by skymt on 2006-10-27
Edgy disabled the status messages in Usplash, but you can get them back easily enough. First, open your menu.lst (gksudo gedit /boot/grub/menu.lst). Then remove any mention of "quiet" from the file. You should get the messages again next time you boot.

---

### Post by spd106 on 2006-10-28
I have the same problem as maino82. The splash image is offset. My monitor has native 1024x768 and before changing the menu.lst to vga=791, it showed the resolution as 1600x1200 and said "out of range". 

Has anyone tried editing the /etc/usplash.conf?

Mine looks like this
```

# Usplash configuration file
xres=1600
yres=1200

```

If I change these values to 1024 and 768, do you think it will work better?

---

### Post by spd106 on 2006-10-28
I threw caution to the wind and tried the changes.

Good news - The shutdown splash is ok now.
Bad news - The startup splash wasn't any different.

---

### Post by DJ Wings on 2006-10-28
I'm using Xubuntu Edgy, and I have the exact same problem, except that the word "xubuntu" doesn't even appear. Weird.

---

### Post by brouche on 2006-11-01
I use Ubuntu Edgy, and I have the same problem with this offset splash image.
The half-solution given by spd106 works on my widescreen laptop (WXGA+).

---

### Post by spd106 on 2006-11-01
I think I've found a way to sort it.

I remembered while watching the update process that the initrd.img was regenerated several times. This got me thinking that the boot process happens while the kernel is being started and the file system isn't actually loaded until later. This suggests that the /etc/usplash.conf file can't or isn't being read during boot. If a little digging I found that a small initramfs is loaded, this probably has the resolution settings in it.

So basically we need to regenerate the initrd.img to take the new resolution settings. I did this by reinstalling usplash, though there's probably an easier way.

I'm not sure about the reasoning, but we're all learners here and it worked for me anyway.

---

### Post by brouche on 2006-11-02
It worked for me too. Thanks a lot.
But I wouldn't search a easier method to fix this issue, as it's hard to find simpler than clicking on "select for reinstallation" in Synaptic.

---

### Post by spd106 on 2006-11-02
Actually I already did.

1) Change the /etc/usplash.conf file to your resolution.
3) Backup the current initrd (just in case) **sudo cp -v /boot/initrd.img-2.6.17-10-generic /boot/initrd.img-2.6.17-10-generic.old**
2) Then generate the updated one **sudo update-initramfs -u**

There are other options for the command (see man pages), but this works ok.

---

### Post by mykmelez on 2006-11-07
This discussion has veered off course, but FWIW I figured out why the scrolling status messages weren't showing up: the kernel was booting with the "quiet" flag.  Rebooting without that flag caused the messages to reappear.

---

### Post by jan247 on 2006-12-23
is there any way for the splash image to revert to text mode (no splash) when something is taking a long to process. I often find it useful in dapper's splash when it shows me a screen in the normal black and white text showing me when i've remounted 30 times and it requires some scanning.

---

### Post by teaker1s on 2006-12-31
:-k disabling text in splash isn't progress in my book

---

