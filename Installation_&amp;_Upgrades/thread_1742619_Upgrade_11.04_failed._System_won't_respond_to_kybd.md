---
title: "Upgrade 11.04 failed. System won't respond to kybd or mouse. No gui or command line."
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by bikinbob on 2011-04-29
Keep getting alert notification box, with close button.  But get no response from keyboard or mouse. So I can't get past it. 

Alert =  
It seems that you do not have the hardware required to run Unity.  Please choose Ubuntu Classic at the login screen and you will be using the traditional environment.  

(Late model Dell, probably less than 2 years old.) 

But since I can't use the mouse to activate the close button, or use the keyboard (alt + x, or enter), I can't get past that point.  

Is there some control sequence I can use during boot startup and get to single user mode and modify something? 

Thanks, 

Bob Gruber

---

### Post by sikander3786 on 2011-04-29
Was the upgrade process successful and did it complete un-interrupted?

Things to try, press and hold down <Shift> key from Bios screen until you see the Grub menu. Then try booting with an older kernel.

If it doesn't help, choose Recovery mode from Grub menu, then 'Drop to root shell'. Follow the commands below.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

Note capital 'X' for X11. If there is an error like file not found, proceed to the next command anyways.

```
sudo dpkg-reconfigure xserver-xorg
```

```
sudo reboot now
```

Are you able to use your keyboard/mouse now? If not, let us see the output of these commands from your root shell.

```
lspci | grep VGA
```

```
glxinfo | grep Vendor
```

Or press Ctrl + Alt + F1 on your desktop. Can you see the tty1 Terminal?

---

### Post by bikinbob on 2011-04-29
Nope, the install did not go cleanly.   Power settings (30 minutes idle) took the system down early in the process.  It *appeared* to resume properly, well before the installation of packages started. 

I downloaded and burned a new 11.04 CD and am typing this via live boot. I think I'm looking a the Unity gui.    

I really like your suggestions and will try them.  I'm experienced in Solaris on SPARC, but fairly green on i386 / linux troubleshooting.

[B]I'd also like to know if I can kick off the install process from the live boot, and "repair" the upgrade without loosing my data. 
[/B]
Thanks for your help. 

Bob G.

---

### Post by sikander3786 on 2011-04-29
There is not much we can try to repair except any broken packages. But first, you need to try with graphics drivers as mentioned above.

---

### Post by bikinbob on 2011-04-29
I've held down the left shift key. I've held down the right shift key.  I've held down both shift keys.  Still haven't seen a grub menu yet. 

Just a blank screen, then the text box. 

Is there some other key combination that might activate the grub menu or break me out of the boot process? 

Still smiling... (and thx) 

Bob G.

---

### Post by sikander3786 on 2011-04-29
Grub legacy need you to press 'Esc' right after the Bios screen whereas Grub2 needs you to hold down Shift key from Bios screen. Not sure why it isn't working for you.

Are you sure your keyboard is working? Does it work in the Bios menu? I wonder if your hardware is causing some problems.

---

### Post by bikinbob on 2011-04-29
Keyboard and mouse working perfectly with live boot 11.04.  That's how I'm responding at this point.  

I'll try esc.

I also got a fresh copy of my 2 important data hierarchies (home and shares). 

So if esc doesn't get me there, the impacts from a fresh load won't be all that bad.   Samba, printer, and other utility configs primarily.  And a few packages.  

Thanks...

---

### Post by sikander3786 on 2011-04-29
Or you can also mount your drives in the Live Session environment and copy over your data to a safe location in case you decide to do a fresh install.

---

### Post by bikinbob on 2011-04-29
That's exactly what I did for making the copy of the data.  

Esc didn't work either, still got the blank screen followed by alert box. 

I'll make a few more tries later today. 

thx

---

