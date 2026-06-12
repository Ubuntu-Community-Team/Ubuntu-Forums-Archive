---
title: "How do I create a bootable system image with ClamAV or similar installed?"
date: 2011-07-28
forum: Installation &amp; Upgrades
---

### Post by houldsworth1 on 2011-07-28
All of my PCs are set up to either run Ubuntu directly, or are dual boot Ubuntu and some variant of Windows.  One of the things I like about this is that in the rare instances that I get a virus I can simply boot into Ubuntu and run ClamAV to remove the virus from there.  

I have a friend who recently picked up a nasty virus and we are having a hard time getting his machine to boot at all without all sort of strange behaviors.  Under that scenario I can't trust Wubi to work correctly.  Soo....

**Is it possible for me to create a bootable CD, DVD or USB drive from my machine?  I'd like to use my machine because I can update the virus definitions before I create the image and then use that to clean his machine.**

Any help much appreciated.

Thanks!

---

### Post by oldfred on 2011-07-28
I have not used any of these, but they may be what you want.

Sites not verified but look useful:
[http://www.avg.com/us-en/avg-rescue-cd](http://www.avg.com/us-en/avg-rescue-cd)
[http://www.askvg.com/download-free-bootable-rescue-cds-from-kaspersky-bitdefender-avira-f-secure-and-others/](http://www.askvg.com/download-free-bootable-rescue-cds-from-kaspersky-bitdefender-avira-f-secure-and-others/)
[http://www.techmixer.com/bitdefender-rescue-cd-with-auto-update-virus-definition-features/](http://www.techmixer.com/bitdefender-rescue-cd-with-auto-update-virus-definition-features/)
[http://www.rarst.net/software/drweb-livecd/](http://www.rarst.net/software/drweb-livecd/)

---

### Post by houldsworth1 on 2011-07-29
Thanks Oldfred - I will take a look at those.

---

### Post by westie457 on 2011-07-29
Another way is to create a LiveUSB with a persistence file. Boot into that and install clamav. This works.

---

### Post by houldsworth1 on 2011-07-29
Thanks Westie.  You wouldn't have a link to how to do that handy would you?

If you have t search then don't worry, I can do that later.  

Thanks!

---

### Post by westie457 on 2011-07-29
Either from a LiveCD or your normal Ubuntu system go to System > Administration > Startup Disc Creator. Starting from the top of the window working down. Choose the ISO file you wish to use. Select the USB stick -already plugged in- and hopefully the only one to save any confusion. Click on Erase Drive. Answer yes to the pop up question. When that has finished the optopns in the lower part of the window can be adjusted, The 'Stored in reserved extra space' will allow you to create the persistence file. Just move the slider to the size you want. The maximum possible is the size of the USB stick less the space needed for the ISO. The bigger the space the longer it takes to create. When you are happy click on Make Startup Disc and wait. Follow the prompts as they appear. The final message will say something like "You may boot a computer using this USB Drive.
Look at the screenshot for guidance.

When all that has done. Reboot into the LiveUSB and select 'try'.
When you have a desktop you can now install things to the persistence file just like a normal hard drive and installation.

So to install clamav open a terminal and run ```
sudo apt-get clamav
```

The sudo part might not be necessary as you are already root. It is a live system remember. Enjoy saving your friends Windows installations from the nasties that us Linux/Unix users rarely catch.

---

### Post by houldsworth1 on 2011-07-30
Westie

That sounds just like what I was looking for - thanks!

---

### Post by houldsworth1 on 2011-07-30
Westie - I tried that and it worked perfectly - thanks!

I now have a thumb drive ready to cure PCs the world over...well, in my town anyway.  :)

---

### Post by houldsworth1 on 2011-07-30
> **oldfred said:**
> I have not used any of these, but they may be what you want.

Sites not verified but look useful:
[http://www.avg.com/us-en/avg-rescue-cd](http://www.avg.com/us-en/avg-rescue-cd)


Oldfred - the AVG site likes very good.  Provides a bootable image in either CD or USB formats.  This would be very helpful for my friend who's PC is too old to boot from the USB. 

Thanks!

---

