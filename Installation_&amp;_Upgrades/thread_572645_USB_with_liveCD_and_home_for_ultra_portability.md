---
title: "USB with liveCD and /home for ultra portability?"
date: 2007-10-10
forum: Installation &amp; Upgrades
---

### Post by bliffle on 2007-10-10
Seems to me that I could create a USB thumb drive, say 2 or 4 gb,  with the liveCD of my favorite distro as well as most, if not all, of my best data on it. Then I could plug it into a computer almost anywhere in the world and be in pretty good shape: a system I'm familiar with and the data I need on that trip. I could use a friends PC or one in an internet cafe.

All I have to do is rig the BIOS to read the USB.

Surely someone must be doing this already. In fact, there's probably a well-worn path to doing this, right?

Of course, it would be nice if there was encryption for the data, in case my ultra-portable slips out of my pocket onto the floor.

Someone must have done this. I'd even guess there's an application ready-made to do it.

---

### Post by bliffle on 2007-10-11
I was just over at MicroCenter where I bought a 1gb micro SD which is about as big as my little fingernail and goes into a SD sized caddy. With that a guy could carry his entire system in a little dinky package, maybe in a carrier on the key chain.

---

### Post by picopir8 on 2007-10-11
Yes, there are numerous tutorials on the topic:

Here is a windows tool that will do everything for you:
[http://www.pendrivelinux.com/2007/09/21/usb-ubuntu-704-persistent-install](http://www.pendrivelinux.com/2007/09/21/usb-ubuntu-704-persistent-install)

If you want to customize things more to your liking, you can follow one of these tutorials instead:
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
[http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar)

Keep in mind, that persistent file support is broken with feisty.  The above mentioned tool will correct the problem, but if you choose to do things yourself, you will need to do the fix yourself as well.  That can be found in post #157 of the following link:
[http://ubuntuforums.org/showthread.php?t=427312&page=16](http://ubuntuforums.org/showthread.php?t=427312&page=16)

---

### Post by bliffle on 2007-10-11
So all I have to do is follow those instructions and when I'm done I just copy my "/home" over from the HDD on my computer, right?

Thereafter, whenever  I leave the house I pocket the pendrive and if I happen to go somewhere that I use the local PC computer for my own work, when I arrive back home I just copy from the USB "/home" to the HDD?

This looks like hotstuff!

Of course I might expect a bumpy road with wifi, but feisty seemed to roll over those pretty well.

---

### Post by kb5lnx on 2008-01-03
> **picopir8 said:**
> Yes, there are numerous tutorials on the topic:

Here is a windows tool that will do everything for you:
[http://www.pendrivelinux.com/2007/09/21/usb-ubuntu-704-persistent-install](http://www.pendrivelinux.com/2007/09/21/usb-ubuntu-704-persistent-install)

If you want to customize things more to your liking, you can follow one of these tutorials instead:
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
[http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar)

Keep in mind, that persistent file support is broken with feisty.  The above mentioned tool will correct the problem, but if you choose to do things yourself, you will need to do the fix yourself as well.  That can be found in post #157 of the following link:
[http://ubuntuforums.org/showthread.php?t=427312&page=16](http://ubuntuforums.org/showthread.php?t=427312&page=16)

Great links!
I hope you might help further with customization? I know this forum is about Ubuntu, but I got to your post googling "pendriveLInux" so... I hope you don't mind the side-stepping; or,  If you can't address the subject for that distro, maybe you could let me know how to do it on Ubuntu, and I'll try to adapt this...? I'm using Gnome desktop

I installed pendrivelinux on a USB flashdrive but I really do not like the sound file it plays when Liinux boots up, on that distro.  

Please locate that file and let me know how to prevent it from being played? I do need sound to be on otherwise,  so it's only that file that is the problem.  
I need to :
1)-identify the file played during boot up (at least, find out its directory; then I could test the solution until found)
2)- prevent it from being played.

---

### Post by ~LoKe on 2008-01-03
Hm...I've been having trouble finding a reason to buy a flashdrive or anything of the sort.  Thanks for making this post.  I should really try other distributions...maybe I've spent too much time in Ubuntu? :D

Let me know if any of those guides works out for you....so I can do it myself. ^^;

---

