---
title: "new installation doesn't load"
date: 2007-09-06
forum: Installation &amp; Upgrades
---

### Post by Nzer24 on 2007-09-06
I just overcame one boot problem and now I'm stuck on a new one.

I just installed Ubuntu 7.04 and grub is working, but when I boot it, the loading bar completely stops at the very start, and won't continue. However, after a while it starts something called BusyBox and gives me a command line and can access my Ubuntu partition.

I'm fine with completely reinstalling Ubuntu, but it would be helpful to know how to fix this in case that doesn't work...

I am running a dual boot on i386 with Windows XP, which boots fine, but may be running a triple or quadruple boot in the near future.

---

### Post by Pumalite on 2007-09-06
May be is your xserver.
sudo dpkg-reconfigure xserver-xorg
Accept most defaults, choose 'vesa' as your driver, then: startx
On the other hand maybe Grub cannot see your partition. Is there an error message anywhere?
What are your specs, and what did you install with?

---

### Post by Nzer24 on 2007-09-06
Should I type this into the BusyBox command line? It seems to not have a sudo command...

Also, I found that when I start up in recovery mode, it also freezes. The last thing it lists is 

[ 11.284426] sr 5:0:0:0: Attatched scsi generic sg2 type 5

I'm not sure if this reveals anything, because it might be frozen on the process after that.



P.S. I like your signature quote!

---

### Post by Nzer24 on 2007-09-06
Oh and my specs are:

Processor : Intel Core 2 Quad Q6600
Mobo: Intel DP35DP
Hard Drive: Seagate 500 GB
Install Disk: Ubuntu Feisty 7.04 Kernel 2.6.20-15-generic (a bit outdated)
I do have an ethernet card, but I have to install a special driver and can't without Ubuntu running
And just in case you're wondering, it's a homebuilt.

But I've had Ubuntu installed for a couple weeks before this and had no problem, so I doubt it's a hardware compatibility problem.

---

### Post by Pumalite on 2007-09-06
A command line (if you have one(Ctrl+Alt+F1)), should allow you to run a sudo command, What about your specs?

P.S. I'm afraid of my signature.

---

### Post by Nzer24 on 2007-09-06
I just tried putting in those commands in the live CD's command line. It said that it wasn't installed though. If I need a command line within Ubuntu, I'm out of luck because it really won't start up.

Any other ideas?

---

### Post by Pumalite on 2007-09-06
Well, it looks like this thing didn't install at all. How come you have to install a special driver for your ethernet card and you 'cannot do it unless Ubuntu is running'?. Can you explain that a little bit more?. Any Ethernet Card usually runs fine with Ubuntu without any additional drivers. Also is best to be connected to the Internet during install And ideally through a router that provides DHCP.

---

### Post by Nzer24 on 2007-09-06
First of all, I just reinstalled and it completely fixed it... I have no idea why it didn't work at first. (Although I have been doing a lot with the bootloader and MDR just a little while ago)

Second of all to answer your question just because:
I have a ethernet card built into my mobo. Turns out that neither linux nor windows have a generic driver that works with it, so you have to install it from a download. Although this does generate a catch 22, the mobo conveniently comes with a driver install disc for windows, but not linux. 

Thanks for your help!

---

### Post by merlinus on 2007-09-06
Magic!  Ain't life grand!!!

Glad things are so easily fixed with ubuntu.  It should be so easy in so-called real life.

:)

-merlin

---

### Post by Pumalite on 2007-09-06
What do you mean 'magic'?. What about all my help?? AH...AH?

---

