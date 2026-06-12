---
title: "Problems with Edgy Usplash"
date: 2006-11-02
forum: Installation &amp; Upgrades
---

### Post by Sentinel83 on 2006-11-02
Hello Everyone,

I am currently having a problem after upgrading my laptop (Dell C400) to edgy where the machine boots (and shuts down) to a blank screen with a blinking cursor in the upper left hand corner.  After about 30 seconds the machine loads gdm and everything is fine.  

I have searched the forums and found some things to try and none of them have worked, hence me opening this thread to see if there are any other ideas.

I have tried so far to:
-  Add the VGA setting into my grub menu.lst file.  I use a 1024x768 resolution and setting the vga to 791 (16bit) or 792(24 bit) just give me an error on startup telling me that I have specified an incorrect mode.  Then it asks me to pick a mode or type 'scan.'  This seems to work for some other people on the forum, no idea why it doesnt for me at this point.

-  Reinstalled the ubuntu usplash theme.  I did this by running
```
sudo aptitude reinstall usplash-theme-ubuntu
sudo dpkg-reconfigure linux-image-$(uname -r)
```
Still no luck.  

-  If I run usplash from a terminal prompt it displays the edgy usplash graphic, so I know the files are there. 

](*,) 

This seems like it would be a silly setting somewhere, and I know that a lot of other people are having this type of issue after the upgrade.  Anybody have any other ideas or found something that works?

Thanks in advance!

---

### Post by tebibyte on 2006-11-03
I was having the exact same problem on a Dimension 2350 running Edgy Edubuntu. Any Ideas?

P.S. I just found a duplicate post at [http://ubuntuforums.org/showthread.php?t=291025](http://ubuntuforums.org/showthread.php?t=291025)

---

### Post by just4free on 2006-11-14
i have a same problem here.
i'm using dell latitude d500 and doing a fresh install.

---

### Post by DFLiddle on 2006-11-17
I have the very same problem on my Dell Latitude C400 as well. Is it certain that the new usplash will support higher resolutions on all hardware, or is it possible that -- in this case, perhaps -- it still requires a 640x480, 16-bit resolution at boot?

When I first installed Edubuntu 6.06, it took me a few tries before I realized that I had to dumb down the display for it to succeed. My upgrade to 6.10 did not go well at all, so I wound up reinstalling from scratch, and I didn't try leaving the display setting at "VGA" -- I automatically bumped it down.

Since I don't have a lot of experience editing the menu.lst file for GRUB, may I ask what a line might look like that specifies a particular resolution and mode?

---

### Post by Jimmy_r on 2006-11-23
> Since I don't have a lot of experience editing the menu.lst file for GRUB, may I ask what a line might look like that specifies a particular resolution and mode?

[http://ubuntuforums.org/showthread.php?t=258484](http://ubuntuforums.org/showthread.php?t=258484)

You may also want to try SUM(see signature)

---

### Post by DFLiddle on 2006-11-23
Thanks for the GRUB resolution help. When I added 'vga=0x311' to the end of the line, the blinking cursor now no longer appears in the corner of the blank screen where the splash should be. Resolution plays some role, I think.

There is a file, /etc/usplash.conf, that specifies a 1024x768 resolution. I tried to edit this file, but it was marked read-only. Could this setting be a factor? How might I configure this?

It would also help me to know whether or not the fact that GRUB is controlled from my SUSE 10.1 installation influences the splash problems. My instinct tells me that it does not, since once it passes the boot process on to the Ubuntu kernel, it's finished its work.

---

### Post by DFLiddle on 2006-11-23
Since my last post, I figured out how to open and edit /etc/usplash.conf. I changed the resolution to 640x480, and now the splash screen appears when Edubuntu shuts down. However, it still fails to show up at boot. Any ideas?

---

### Post by Jimmy_r on 2006-11-23
Try this:
```
sudo update-initramfs -u
```

---

### Post by Steve S. on 2006-12-17
I'm still figuring out the usplash thing with edgy, but I did a few things that may be noteworthy to get the 1024x768 to work.

Run this:
```
sudo gedit /etc/usplash.conf
```

and make sure your res. is 1024x768.  So it looks like this:
```
# Usplash configuration file
xres=1024
yres=768
```

Then run this:
```
sudo gedit /boot/grub/menu.lst
```

The key seems to be this: at the end of the grub list line it should read
```
ro vga=791 splash
```
I removed the "quiet" comment as I wanted to see what was going on during start up and shut down.  It also seems **significant** that the "splash" word be the very last word in that line.

```
Here is my /boot/grub/menu.lst
title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=7cf36988-ae97-45cb-ae7c-927b70b2ffa8 ro vga=791 splash
initrd		/boot/initrd.img-2.6.17-10-386
savedefault
boot
```

Oh, and don't run this:
```
sudo dpkg-reconfigure linux-image-$(uname -r)
```

after you change /boot/grub/menu.lst or it will reset it and you'll have to go back in and change it again.

Perhaps this information only helped me, but I hope it saves someone else the effort I put into figuring some of this out.

---

### Post by anubhavrocks on 2006-12-18
just remove the 
VGA=791 

from the line and then try

---

