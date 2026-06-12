---
title: "Need help booting from USB after failed Ubuntu install"
date: 2010-09-06
forum: Installation &amp; Upgrades
---

### Post by naboreum on 2010-09-06
Hello there,

Obviously I am new to the Ubuntu community and am having some problems getting it to work on my IBM Thinkpad R40 laptop. I chose the Netbook edition because that seemed to fit my laptop requirements perfectly. I tested it out using unetbootin and decided to install. While trying to install I got an error that it could not unmount /cdrom. After seemingly resolving that issue I tried to install again and restarted my computer. After restarting it does not load Ubuntu and will not boot from a USB or from a CD-RW.

I am not sure what the problem is and have tried everything I can think of/searched for on the internet to fix it and have finally come here.

Thanks

---

### Post by naboreum on 2010-09-06
I created the bootable usb in OS X as well as the CD-RW could this be a contributing factor? Could the speed at which the CD was burned be an issue?

If you need any other info, please, let me know.

---

### Post by stee1rat on 2010-09-06
Do you mean it doesn't load at all?

---

### Post by naboreum on 2010-09-06
I mean the IBM screen appears with the option to hit the blue Access IBM button then the screen turns to black and there is just a blinking cursor at the top left corner.

---

### Post by wilee-nilee on 2010-09-06
If your relying on the boot order set in bios this can be also done with a f-key prompt to get choice of boot, mine is f-12, I have seen it be others as well as esc. Start the computer and try the key prompts to get to this post bios boot from menu.

---

### Post by naboreum on 2010-09-06
f12 for me asks what I could like to boot from but i get the same blinking cursor after choosing cd/room or the bootable usb which is recognized as a hard drive rather than a removable drive . I have also tried changing the boot order with the same results.

---

### Post by naboreum on 2010-09-06
bump

any other thoughts?

---

### Post by stee1rat on 2010-09-07
There could be only 3 reasons, i think: you didn't made your usb stick and cd/rom bootable (live), your usb port and cd/rom drive is broken or unplugged (o_O), you didn't save the changing to bios after you change the boot order.

---

### Post by naboreum on 2010-09-07
What specifically would make the usb and/or cdrom bootable (live)?

---

### Post by stee1rat on 2010-09-07
A software that records it! :)

---

### Post by ronparent on 2010-09-07
To give you a more explicit answer - what you download from the Ubuntu site is an iso image. This in of itself is not bootable. It has to be burned to a cd as an image (complete with bootloader and individual files you need to boot) not as an .iso file. Unetbootin will do that to properly install the iso to a memory stick so the stick will boot and run the installer on the stick. Most contemporary burn software will ask you if you want to burn the image to the cd (yes of course) otherwise you end up burning one big .iso file which is not bootable. Its hard to tell with everything that has been going on, but I think that what you have to do is to get a bootable image either on the cd or the stick so that you can run a live cd session. Once booted to a live session you can follow the instructions for reinstalling grub to your computer to make it bootable. The instructions are here: [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

I hope this solves your problem. Good luck. Keep posting if you need more help.

---

### Post by naboreum on 2010-09-07
I wish that was the answer to my problem but the CD and USB are both set up to be bootable with all of the files out rather than the one large .iso file. The USB and CD were both made on a MacBook Pro. Could this is a part of the issue?

---

### Post by ronparent on 2010-09-07
I'm unfamiliar with Mac conventions. The iso probably has a DOS MBR. Unless the Mac substitiutes a Mac MBR in writting the cd? It seem unlikely but possible.

---

### Post by naboreum on 2010-09-07
Such as I thought.

---

### Post by naboreum on 2010-09-07
bump for any other thoughts? 

please.

---

### Post by 0N3 on 2010-09-07
[http://www.youtube.com/watch?v=iDr-rnz1WTQ](http://www.youtube.com/watch?v=iDr-rnz1WTQ) My tutroial on how to make USB HDD Drive bootable theres also one there for making Burning Ubuntu to CD. Change your boot priorty in your make your first choice CD/DVD if using CD/DVD and make USB HDD your first choice if using USB Drive hit F10 to save to the changes.

---

### Post by naboreum on 2010-09-07
Okay I give up.

Thanks to everyone that responded.

---

