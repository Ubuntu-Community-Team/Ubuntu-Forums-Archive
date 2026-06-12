---
title: "radeon 7200 and xorg.conf"
date: 2008-09-08
forum: Installation &amp; Upgrades
---

### Post by flux242 on 2008-09-08
Hi,

I'm trying to make the xubuntu 8.04 working with the old sony crt monitor. The problem is that as far as I login into the system it hangs on. So I tried to reconfigure the xserver-xorg with the dpkg-reconfigure. But it asked me only keyboard related questions so the monitor specific entries in the /etc/X11/xorg.conf are missing. What shall I do to reconfigure the monitor and graphics card?

BTW I managed to make it working with the 20" samsung tft monitor. But when system is loading it switches to some mode with is not supported by the monitor so I see a black screen untill the login promt appears. Where do I configure the monitor mode during system loading?

Thanks

---

### Post by Partyboi2 on 2008-09-08
To reconfigure the xserver you can boot into recovery mode and choose xfix. If you are having a black screen from grub to login then have a look at your /etc/usplash.conf file to make sure you have the correct settings for your screen resolution.
so if it has something like
xres=1024                                                                                                                    
yres=768 
means you are using 1024x768. Make sure you have the correct screen resolution for what your monitor supports.

---

### Post by flux242 on 2008-09-08
> **Partyboi2 said:**
> To reconfigure the xserver you can boot into recovery mode and choose xfix. 


actually this was the fist thing I tried. Didn't help. So how do I make dpkg-reconfigure xserver-xorg detect my monitor and gr.card?

> **Partyboi2 said:**
> 
xres=1024                                                                                                                    
yres=768 
means you are using 1024x768. Make sure you have the correct screen resolution for what your monitor supports.

ok I'll take a look, but I'm afraid the resolution should be ok. The tft supports all resolutions upto 1600x1200. Something wrong with the timing or refresh rates I suppose (I do see the splash screen on my older crt monitor which supports upto 1280x1024)

---

