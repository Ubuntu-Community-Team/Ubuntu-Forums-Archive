---
title: "Need help installing guys!"
date: 2007-01-14
forum: Installation &amp; Upgrades
---

### Post by drjekyll452 on 2007-01-14
Hey guys,

Firstly, thank you to all who help me out! 

Secondly, my issue! 

I have installed Ubuntu on every computer in my house without an issue, but when I try to install it on the following computer:

AMD64 3200+
1GB DDR-400
160GB Hdd (Partitioned 127GB and 21GB) 127 for WindowsXP and files, 21GB for iTunes
250GB RAID array 1+0
200GB RAID array 1+0
DVD-RW
ATI AIW 9800 Pro

The issue that I am having is when booting with the LiveCD in my drive...
I choose the first option and it starts to load everything and then the screen goes black and never changes. It never reaches the desktop or anything. Just a black screen and the computer is frozen! I have left it to do its "thing" for 2 hours with the same result. (just making sure).

Now, I have no idea what to do. I have successfully installed Ubuntu 6.10 on the following computers with no issues:

IBM T40 (Bought a new HDD)
Compaq Evo
AMD AthlonXP
Pentium D 820

I am just wondering why this would happen with this computer. Oh also, I removed the array and that was not the issue. I bought two new DVD-RWs just to try it out and they did not work. Any advice or solutions are greatly appreciated!

Please oh please won't somebody think of the children! I mean my poor computer...


Lastly, thanks in advance to all that help me out. I love Ubuntu but this is a serious thorn in my side.

Dr. J

---

### Post by icefaerie on 2007-01-14
To start, when the options first come up, hit F6.  You will see a list of the boot options.  Delete "quiet" and "splash".  Then let us know what errors you see before your screen goes blank.

---

### Post by drjekyll452 on 2007-01-14
I will do that right now and let you know. 

Thanks,

---

### Post by drjekyll452 on 2007-01-14
There weren't any errors when I followed your instructions. It loaded everything (Kernel, Gnome, etc)...then the screen went blank. 

Hmmm?

---

### Post by icefaerie on 2007-01-15
> **drjekyll452 said:**
> There weren't any errors when I followed your instructions. It loaded everything (Kernel, Gnome, etc)...then the screen went blank. 

Hmmm?

Hmm, weird.  I'm really not sure then. :/  Hopefully someone else can offer some advice...

---

### Post by drjekyll452 on 2007-01-15
Thanks for your effort ice.

---

### Post by aberry5555 on 2007-01-16
ok, press F6 again and delete the "quiet" and "splash" options, but also add on to the end "break=bottom". This will give you a command line half way through the boot. I have a feeling that the reason your screen is going blank is the same reason mine goes blank, because the wrong drivers are loaded at boot. 
  Once you have a command line type in "chroot /root nano /etc/X11/xorg.conf. Doing this will open up your xorg.conf file in a command line editor called "nano". Scroll all the way down until you find a heading called "device", under this should be info about your graphics card and what driver it uses (probably ati). If it says ati then change it to "radeon" then press ctrl+O and ctrl+X, this will bring you back to the command line. From there type "exit" and see if it boots. If it doesn't it might mean the radeon drivers don't work either (I don't know if they do as I went straight to the fglrx closed source drivers) so you will have to do the same thing again but, instead of typing radeon, type in "vesa" (this is the most basic driver available to linux, it's the same as running windows with no drivers for the gfx card).
  I'm pretty sure this is the reason but if not then I don't know, you'll have to fiddle some more :p

---

### Post by drjekyll452 on 2007-01-16
Thank you Aberry!

It definitely was the drivers. I appreciate your help a lot! 


Thanks,

Dr. J

---

### Post by aberry5555 on 2007-01-17
no problem :)

---

