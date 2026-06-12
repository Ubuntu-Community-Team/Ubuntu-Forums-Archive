---
title: "Black Screen on after loading bar in live cd or installation."
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by Jholder29 on 2008-05-27
I am trying to run a install or a live cd of Ubuntu 8.04 x64 and after the ubuntu loading bar on either I get just a solid black screen... everything is still running. 

I imagine it has something to do with the graphics card, Nvidia 9600GT and I could just use some assitance in getting this going. 

Thanks.

---

### Post by iaculallad on 2008-05-27
> **Jholder29 said:**
> I am trying to run a install or a live cd of Ubuntu 8.04 x64 and after the ubuntu loading bar on either I get just a solid black screen... everything is still running. 

I imagine it has something to do with the graphics card, Nvidia 9600GT and I could just use some assitance in getting this going. 

Thanks.

Just be sure that you are using a 64-bit architecture processor/system. In case you truly do, try checking the LiveCD for error using the "Check CD" on the menu for installation.

---

### Post by Jholder29 on 2008-05-28
I am on the x64 architecture and I have ran the Check Cd which came up with no problems. I also created a 32 bit version cd and just tried to use the live cd with the same results. Whenever the black screen is up, the keyboard still responds if your press num/caps/scroll. 


Any other ideas?

---

### Post by iaculallad on 2008-05-28
Had u tried installing using the Alternade CD? Or tried installing the LiveCD in low graphics mode?

---

### Post by Jholder29 on 2008-05-28
I haven't given either of those a try yet, I will do that tonight and let you know. 


Thanks.

---

### Post by Jholder29 on 2008-05-28
Well, using the alt cd I was able to get it installed. However, I have the same exact symptoms when it loads up.


After the Ubuntu loading bar a black screen, keyboard responds to num lock/caps lock nothing shows up.

:lolflag:

Just for reference:
   Proc: AMD 64 X2 5600+
   MB: Asus M3A
   VCard: Geforce 9600GT
   Memory: 4gb Corsair DDR2 800

---

### Post by Pumalite on 2008-05-28
You will need the Nvidia driver found here:
[http://www.nvidia.com/object/linux_d...32_173.08.html](http://www.nvidia.com/object/linux_d...32_173.08.html)

---

### Post by Jholder29 on 2008-05-29
Ok. Well I can't figure out exactly how to go about installing it. I can't get to any run level using the ctrl + alt + fkeys or anything to show up on the screen.

---

### Post by iaculallad on 2008-05-29
Try to press Alt+F1 key when your screen goes blank.

Try to shutdown gdm

```
sudo /etc/init.d/gdm stop
```

Press Alt+F1 key again if the screen goes blank again to bring you back to the console.

Run the NVIDIA installer script (if you already downloaded it)
```

sudo sh (NVIDIA-Installer_Script).run
```

Try restarting gdm

```
sudo /etc/init.d/gdm start
```

---

### Post by Jholder29 on 2008-05-29
No luck. I don't get anything when I press alt+f1 or hold it in, just the same black screen. I waied quite a while, but still nothing comes up. 

It is responding to the keyboard however. If I hold ctrl + alt + del it restarts the pc/ the num/caps/scrollock work light up. 

Thanks for all of your help so far guys

---

### Post by WirlWind on 2008-06-30
I'm getting identical issues, but with an older version.

I'm running the same GFX card and have seen quite a lot of issues with it, so I'm assuming the latest install won't be any different.

---

### Post by upchucky on 2008-06-30
im not sure if hes getting busybox, is the cursor there on blank screen? perhaps blinking?

if so get supergrub to fix bootloader.

if no cursor then a default/jumper setting on graphics card or motherboard may need changing, google the card and board for settings.

---

