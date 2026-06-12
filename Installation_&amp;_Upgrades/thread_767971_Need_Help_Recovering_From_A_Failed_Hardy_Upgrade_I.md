---
title: "Need Help Recovering From A Failed Hardy Upgrade Installation"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by Gruss2 on 2008-04-26
Can someone out there help me???

I tried to upgrade from Ubuntu Gutsy to Ubuntu Hardy, but the installation failed. I now can know no longer boot into my operating system. When I boot my pc, the Ubuntu splash screen appears, and then it freezes at a light blue screen. The only way I can boot into my pc is with an older Ubuntu Live CD. 

Can someone one give me specific details on how I can login completely into my operating system without the Live CD and recover from the failed Hardy upgrade installation.

I don't want to do a clean install, because I have files and folders I want to save. I tried copying and backing them up while using the Live CD, but I keep getting permission denied errors. So again, PLEASE, can someone give me precise and clear details on how to solve this problem.

THANK YOU!

---

### Post by PmDematagoda on 2008-04-26
Boot Ubuntu in Recovery Mode and then execute the following commands:-
```
sudo apt-get install -f
```
```
sudo dpkg --configure -a
```
and 
```
sudo xfix
```

After they are all done, try starting the X-Server using:-
```
startx
```

If that works, then you should be able to use Ubuntu again.

---

### Post by chickendude on 2008-04-26
Hey, I think I've got a similar issue after trying to upgrade to Hardy Heron. It boots up nicely up until where I would usually login. I hit Ctrl-Alt-F1, followed those steps, and typed xfix and it said it was an unrecognized command. Then I typed in startx, and it told me to remove a file, which I did then retyped the command. It booted up and gave the same screen as before, only with a weird screen (it had stripes across the background). I hit Ctrl-Alt-F1 again and it brought me back to the terminal with the following info:
```
(II) Module "i2c" already built-in
(II) Module "ddc" already built-in
(II) Module "ramdac" already built-in
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
Atom 4, CARD32 4, unsigned long 4
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
```

Any help would be great! If there's anything else that would make the problem easier to diagnose, let me know too, thanks :)

EDIT: Oh! and about xfix I realized that I had run that from the Recovery Menu a few times before this and it spit out:
"xserver-xorg postinst warning: overwriting possibly-customized configuration film: backup in /etc/X11/xorg.conf.20080426833705"

Another thing is I once got the error message "The greeter application appears to be crashing. Attempting to use a different one." after hitting Ctrl-Alt-Backspace when it froze just before the login screen (although the login usually doesn't pop up unless there was a weird shutdown, as I had configured it not to request a password to login).

---

### Post by Gruss2 on 2008-04-26
PmDematagoda, I tried the info you gave, but it didn't work. It said the x-server appears broken.

I even tried to do a boot rescue from the Live CD, but I couldn't figure out how to enter the "boot" prompt. There are so many different options and steps.

There has to be a way to fix this. I can easily boot form the Live CD. I just can't boot from my hard drive, nor can I copy my personal files from my hard drive from within the Live CD. If I could do that, I would just copy them to my jump drive and just do a clean Hardy install. 

Does anyone else out there have any other suggestions?

---

### Post by chickendude on 2008-04-26
Try hitting Ctrl-Alt-F1 at the blue screen you get to. If you can log in from the terminal you should be able to mount your jump drive and copy files from within the terminal.

---

### Post by Gruss2 on 2008-04-27
> **chickendude said:**
> Try hitting Ctrl-Alt-F1 at the blue screen you get to. If you can log in from the terminal you should be able to mount your jump drive and copy files from within the terminal.

I tried that and all I got was a blank screen. So I did some googling and found a temporary solution by hitting the keys CTRL+ALT+BACKSPACE. 
I was then able to get past the blue screen and the login screen appeared. There, it gave me an option to login to either something called X something or GNOME. I chose GNOME. The OS did load, but my desktop looked corrupted and the icons looked like another OS. But I was still able to access my important files and folders, so I copied and burned them to a CD-R. Also, although I was able to login into the OS, It couldn't access the Internet. So that meant I couldn't upgrade to Hardy through the Update Manager or manually download the files. So I just did a clean install of Ubuntu Gutsy with a Live CD I had. After Gutsy was successfully installed, I immediately upgraded to Ubuntu Hardy. It downloaded and installed without any problems. So everything so far is working fine. 

Thanks for everyones suggestions.

---

### Post by chickendude on 2008-04-27
Hm, when I tried hitting Ctrl-Alt-Backspace it just took me to the same screen (it's a solid color and the screen just before loading my background picture) only this time instead of the pointer mouse it was the "busy" mouse.

---

