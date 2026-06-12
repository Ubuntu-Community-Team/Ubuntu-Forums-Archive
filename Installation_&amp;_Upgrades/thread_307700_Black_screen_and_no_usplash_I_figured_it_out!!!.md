---
title: "Black screen and no usplash I figured it out!!!"
date: 2006-11-27
forum: Installation &amp; Upgrades
---

### Post by Chazall1 on 2006-11-27
I have been working on this for weeks,(on and Off) I had upgraded to Edgy and had no Usplash, just a black screen with a blinking curser in the upper left corner. I have a Dell Dimension 3000, with a i82865G graphic card and a Dell E176FP monitor. Its all in the resolution, Here is what I did:

1.  sudo gedit /etc/usplash.conf set the resolution to 640x480
then run  sudo update-initramfs -u

2.  sudo gedit /boot/grub/menu.lst
FIRST: Check the line that looks like this   #defoptions=quiet splash    I had made changes to the setting from what I read, This is the default setting
SECOND: go to the end of Kernel line and it sould be   ro quiet splash

    sudo update-grub

3.  sudo dpkg-reconfigure linux-image-$(uname -r)

This worked for me, I did not think I would ever see Usplash, Hope this works for you!!!!!!

---

### Post by sanelx09 on 2006-11-27
Hello, I have the same problem, it says GRUB on the upper left hand corner, so I am guessing its pretty similar.

The first step worked, but the 2nd didn't work.
It opened menu.lst but it was completely blank.

Then, I went on and did the last step, and this is what I got: 
> ubuntu@ubuntu:~$ sudo dpkg-reconfigure linux-image-$(uname -r)
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.17-10-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.17-10.33 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.17-10.33 was configured last, according to dpkg)
ubuntu@ubuntu:~$ 


Is this what I am supposed to be getting or what?

---

### Post by -Phi- on 2006-11-28
I had a blank boot screen and tried the steps but it didn't work (though oddly shutdown still had the logo). What did work was to fix a broken link from /etc/alternatives/usplash-artwork.so to the appropriate theme file in /usr/lib/usplash/ manually.

- Phi

---

### Post by Steve S. on 2006-12-24
> **-Phi- said:**
> I had a blank boot screen and tried the steps but it didn't work (though oddly shutdown still had the logo). What did work was to fix a broken link from /etc/alternatives/usplash-artwork.so to the appropriate theme file in /usr/lib/usplash/ manually.

- Phi

Could you instruct on how you did that, Phil?  I think I may have the same issue....

---

### Post by ZeroThree on 2007-04-05
Question for any of the previous posters.. I have a Dell Dimension 3000 box at home with the same setup. Windows XP & Ubuntu Edgy Eft.. using GRUB to dual boot.. which works SOMETIMES..

Its really the strangest thing ever. Windows boots 100%  of the time. Ubuntu, maybe about 70% of the time. When it doesn't boot into the actual Ubuntu OS, it reboots altogether, in some kind of a loop. If I just leave it on for a while, it will eventually boot into Ubuntu (default option in GRUB) but its annoying as all hell. 

I've looked on a couple of other posts.. tried modifying the video buffer in the bios (which doesn't really apply because I already had the thing installed and working for some time) and I've tried tweaking with a ton of bios settings to see if it changes anything.

Because its erratic, I have a feeling it might be a hardware problem, but I'm not completely sure... any help is greatly appreciated.

---

### Post by adohall on 2007-06-06
Thank you so much. Your method worked for me. I now I have a usplash (so that's what it's called - I got used to talking about a bootup logo).

By the way - I didn't have to edit my grub menu list or update it.

I suspect I'm only in 16 bit color depth. what's the best way to increase it to 24?

---

### Post by adohall on 2007-06-06
answered my own Q - I just backed up /etc/X11/xorg.conf then edited it - replacing 16 with 24 after 'default depth'

now the banding (streaks) is gone from the title bars of windows

---

### Post by Baryon on 2007-07-24
If you have this problem, how do you access a command prompt, or load X, so that you can do these commands? The other VTs are not giving any login prompt.

---

### Post by joemilx on 2007-08-09
Congrats on solving my problem with the splash disappearing after updates applied on August 8, 2007.  Your solution cut two minutes off my boot-up time.  Very clear, stepwise solution.  Thanks!

---

### Post by darksmurf on 2007-10-21
Just a quick update, this method fixed my usplash for Kubuntu Gutsy 7.10...tried suggestions from 20 other posts but this one worked very easily.  You truly are a god among men!

---

