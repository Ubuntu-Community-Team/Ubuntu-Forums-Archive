---
title: "Black Screen / Login loop after changing display settings, fresh Ubuntu 20.04 install"
date: 2023-02-10
forum: Installation &amp; Upgrades
---

### Post by milesgx on 2023-02-10
I'm having some trouble with my new install of Ubuntu 20.04.

I've a dual monitor setup with a ROG PG279Q 165hz monitor plugged in via display port and a ASUS MG28U 30hz monitor plugged in via HDMI. My graphics card is an NVIDIA GeForce RTX 3080.

When I first log in after the installation, the display is wacky (see attached image) and the mouse's visual position does not match it's actual position. I'm able to adjust my display settings to match how my monitors are physically arranged, and coincidentally this fixes the mouse position issue as well.

[IMG]https://i.imgur.com/yU20Inw.jpg[/IMG]

(by the way, I took a phone pic because oddly, everything appears correct when taking a screenshot...)

After this things are fine, except when I restart the machine. When I login after restarting, it just becomes a black screen.

Doing some googling lead me to a solution:
Entering TTY by pressing Ctrl + Alt + F5 at the login screen, then
mv ~/.config ~/.config.old

Finally doing a sudo systemctl reboot, this brings me back to the original state - I can login fine again, but the visuals are back to being wacky with the mouse position bug as well.

I've also modified other settings without touching the display settings, and thus far they do not break anything with logging in - so, it seems that is  changing the display settings which causes it. Specifically, moving the monitor arrangement.

I tried Ubuntu 22.04, but it has the login problem immediately after installation - it just brings me to a black screen and I have no way of fixing it.

Any ideas what is happening here to cause the black screen on startup? I figure something that gets modified in those files when I change my display settings is causing a login loop, but I'm not sure why or how I can prevent this. Any logs I should look for / post here to help diagnose?

Cheers.

---

### Post by MAFoElffen on 2023-02-11
Please run the [UbuntuForums 'system-info']("https://github.com/UbuntuForums/system-info") script and post the URL of the pastebin it uploads to.

It has an extensive graphics section on the report which will answer a lot of things. A good place to start.

---

### Post by milesgx on 2023-02-12
Here is the system info script's results: [https://paste.ubuntu.com/p/WSpVBvXkvs/](https://paste.ubuntu.com/p/WSpVBvXkvs/)

---

### Post by MAFoElffen on 2023-02-12
You have a NVidia GPU and are running X11, but you are using the Nouveau driver, instead of the third party NVidia driver for your GPU...

What your screen looks like is what mine looks like if I try to use the Nouveau driver. Have you thought about going to the "Software and Updates" app, the Additional Drivers tab, and installing an NVidia Driver?

---

### Post by milesgx on 2023-02-12
Took a few tries to find the driver which worked for me, but nvidia-driver-510 has done the trick. Thank you for the help!

This is just a minor issue now, but I notice when I boot up / log in, the screen has a few logs which stream by (faster than I can read), and then flickers for a few seconds. After doing this for 3-5 seconds ish, it brings me to the login screen. Upon logging in, the screen flickers again for a couple of seconds before properly bringing me to my desktop. My main issue is resolved, so this isn't a big deal, just kinda curious why since that doesn't... look happy.

Cheers.

---

### Post by MAFoElffen on 2023-02-13
> **milesgx said:**
> This is just a minor issue now, but I notice when I boot up / log in, the screen has a few logs which stream by (faster than I can read), and then flickers for a few seconds. After doing this for 3-5 seconds ish, it brings me to the login screen. Upon logging in, the screen flickers again for a couple of seconds before properly bringing me to my desktop. My main issue is resolved, so this isn't a big deal, just kinda curious why since that doesn't... look happy.
LOL!

3-5 seconds? Count your blessings. Mine is 3-5 seconds from the last log messages to the login screen... Then after login, a black screen for 20-30 seconds until the Graphics Layer loads and the Desktop appears. I except that as my normal.

I got rid of the flicker to the login screen, by using a video set boot paramter for 1920x1080-32 in Grub so it sets KMS...
```

GRUB_CMDLINE_LINUX_DEFAULT="-- quiet splash video=uvesafb:1920x1080-32@60,mtrr:3,ywrap,noblank"

```

---

