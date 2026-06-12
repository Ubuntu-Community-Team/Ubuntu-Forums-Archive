---
title: "Gusty Install: after reboot, X not starting"
date: 2008-01-11
forum: Installation &amp; Upgrades
---

### Post by jofre on 2008-01-11
Hi guys,

I usually love linux, but in days like today... anyway, see if anybody out there can give me a hand.

I decided to install Gusty.
I use alternate CD because my stupid optiplex 320 needs lilo (grub does not work).

After install, my nfts partition (windows) was not there. I installed gparted, and a big warning symbol was beside the NTFS partition 

I download testdisk, which told me that everything was (or seems) OK. 

Nevertheless, my ntfs was still not being mounted.

Also, where the hell is fstab now? It is not in /etc/fstab !!!

Anyway, I went to synaptic and install several ntfs related packages. 
After that the warning symbol besides the NTFS partition was not there in Gparted, but still I could not mount it.

I decided to reboot, you never know, I thought.

And now X will not start! I installed the OS in french so the rough translation of the error message is:

Impossible to start X server (graphical interface) because of an internal error. bla bla bla 

and it freezes there.

Let me say that I did an update of the system, and I think that GDM was in the update, but it will be very strange that is that, as I log out and in a few times...

I am able to swtich console and shut down the computer. I could reinstall, as I just did it and is nothing to back up, but would be very annoying!!!

Any idea/ solution for any of my problems?

I know that the motto is, if you have a Linux working , don't upgrade. But the temptation was too big...

Thanks in advance,
Jofre

---

### Post by PmDematagoda on 2008-01-11
Could you please provide specifications about your PC, the most necessary is VGA information.

---

### Post by jofre on 2008-01-11
Do you mean the graphic card?
Ati radeon Xpress 1100

(Thanks for the fast replay)

---

### Post by PmDematagoda on 2008-01-11
Ok, now concerning your error, I am afraid I will need more than just "blah's". Could you please post the complete error message.

---

### Post by jofre on 2008-01-11
well just to
 "contact the system administrator", which is myself...who in turn is trying to obtain help in this forum. I am not a Linux guru by any means, but I have used enough to know that the rest is not important, believe me.

---

### Post by PmDematagoda on 2008-01-11
Try:-
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by jofre on 2008-01-11
by any chance you do know how to go to safe mode from lilo?

---

### Post by jofre on 2008-01-11
I do not know how to get to a safe mode console to do this. I know how to swithc alt+shift+F6, but when i start your command, a basic graphical interface starts, but does not responds to the keyboard.

---

### Post by jofre on 2008-01-11
ok, I am going nuts...

in lilo I put:

Linux init=1

and now it freezes when configuring the usb!!!

usb2-2: configuration #1chosen from 1 choice

this is the last line...

Ok this is a bit too much. I think on monday I will just reinstall again and just cross my fingers!!!

Good weekend to everybody.

---

### Post by Brimo2k on 2008-01-11
Jofre: I had this same exact problem.. too busy to deal with it. If youfind out the fix for it please let me know!!! :) I want to get back to ubuntu.

---

