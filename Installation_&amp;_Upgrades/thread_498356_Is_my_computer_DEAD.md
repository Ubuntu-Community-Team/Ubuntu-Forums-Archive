---
title: "Is my computer DEAD?"
date: 2007-07-11
forum: Installation &amp; Upgrades
---

### Post by BigSteve on 2007-07-11
ohoh,

Last week I tried to install ubuntu on my Windows XP computer.  (HP Pavilion 7855).  FIrst few attempts did not work.  After reading posts and answers here, I purchased Partition Magic and made room for Ubuntu.  Installation succeeded.  COuld boot Ububntu doing nothing, or select XP from menu.

installed upgrades as suggested; installed a few apps like Monkey Bubble etc. , set up email and FTP.  all worked.

Was installing supprot for my printer (HP Photosmart 7150) when things went south.  System locked up.  Had to shut down using power button.  

Now if I turn the computer on with no CD in drive, I get "No Operating System Found" message.  If I start it with either a windows or a ubuntu CD in, I jsut get a blinking cursor, with no apparent response to keyboard or time.

DID I fry something?  At a loss as to what todo next.  Any ideas? :confused:

Is my computer DEAD? :(

Steve

---

### Post by poohbear1616 on 2007-07-11
> Any ideas?

First, do you have a floppy drive and is there a disk that was left in it?
If not, then it sounds like the hard drive might have crapped out.
Do you have a indicator light on the box for when the hard drive is busy?

Try booting the live disk and see if you can access the drive.

---

### Post by BigSteve on 2007-07-11
1.  No floppy in drive
2. Light on for HD continuously
3. When I try to boot from CD (yes it is the top priority in BIOS) is when I get the blinking cursor.
4. Without a CD in the CD drive, I get the "no operating sytem found" message.

Steve

---

### Post by dabl on 2007-07-11
> **BigSteve said:**
> 
Was installing supprot for my printer (HP Photosmart 7150) when things went south.  System locked up.  Had to shut down using power button.  


Unless there was something very funky with the printer installation process, it should not have been a cause of a system lockup.  There are very few software things that you can do to lock up Ubuntu -- I managed it once by running glxgears in full screen mode (actually just disabled all USB devices including my keyboard and mouse).

So, I'll speculate that your hardware chose that moment to crap out. With both hard drive and CD/DVD drive showing problems booting a bootable device, one could wonder about the IDE controller and bus ... you might want to reseat the IDE data cables, just to be thorough ... :(

---

### Post by confused57 on 2007-07-11
Left you a reply in your other thread:
[http://ubuntuforums.org/showthread.php?t=498373](http://ubuntuforums.org/showthread.php?t=498373)

---

### Post by Odrodzona-Sarmacja on 2007-07-11
So the crash happened after installing new hardware? yes?
Futhermore when you put ubuntu livecd in cdrom and start computer, then you get just a blinking cursor? yes?

Remove this hardware from your computer and start your computer with ubuntu lifecd again.

If ubuntu doesn't load from lifecd, then I think in bios is a setting allowing the bios to configure hardware configuration instead of plug&play operative systems. Then try lifecd again.

I hope you will be able then at least boot ubuntu from its lifecd at least. ;)

---

### Post by Panzor on 2007-07-11
That sounds exactly like a 'keyboard error' which is fixed by simply plugging in a keyboard. If that doesn't fix your problem, then open up the boot menu and select your partitions to open first. Those two ideas are all I can fathom. I'd guess that the first is correct since you had to response from the keyboard and it's a very rare time when a keyboard does not input while blinking.

---

### Post by Aramis on 2007-07-11
> **BigSteve said:**
> [...]
4. Without a CD in the CD drive, I get the "no operating sytem found" message.



I had this problem once when installed KUbuntu on my work PC, it was down to a faulty configuration of the Grub. I think - but please do verify this - that you can pop the ubuntu CD in, select the recovery mode... at some point you will be asked to re-install Grub, do it. You should not need to go any further.

Cheers,

Ar@mi$

---

### Post by BigSteve on 2007-07-11
Thanks for the resposnes... comments follow:

Panzor - keyboard responds as far and Ctrl-alt-delete causing restart, but then nothing (blinking with CD in, no op sysyem message if no cd)

Odrodzona... - remover hardware - no change
                       -reset config in BIOS - no change

Dabl - YOur analysis sounds correct, DAMN IT - that means what?  replace controller, replace ocmputer?

---

### Post by BigSteve on 2007-07-11
Aramis,  with the CD in, all I get is a blinking cursor, no opportunity to select ANYTHING!  :(

---

### Post by Odrodzona-Sarmacja on 2007-07-11
Try reseting bios to factory default settings.
Make in bios the cd-drive bootable before hd.
Then try starting computer with ubuntu livecd in.

Good luck!

---

### Post by BigSteve on 2007-07-11
> **Odrodzona-Sarmacja said:**
> Try reseting bios to factory default settings.
Make in bios the cd-drive bootable before hd.
Then try starting computer with ubuntu livecd in.

Good luck!

Thanks, tried those, and same results!

Steve

---

### Post by Odrodzona-Sarmacja on 2007-07-11
Well... next step would be to start removing other pieces of hardware and try to boot up... or like when you are putting up a computer from parts and you start with mothercard, cpu, memory, "a: drive :) " and try booting up on that with adding more hardware if it works together like cd-rom, hardrives, printers and etc.

---

### Post by BigSteve on 2007-07-11
> **Odrodzona-Sarmacja said:**
> Well... next step would be to start removing other pieces of hardware and try to boot up... or like when you are putting up a computer from parts and you start with mothercard, cpu, memory, "a: drive :) " and try booting up on that with adding more hardware if it works together like cd-rom, hardrives, printers and etc.

sigh, soudns right, and also sounds like it just progressed beyond me, time to get a professional involved.  Thanks alot.

Steve

---

### Post by 11hjpphty76lkjj on 2007-07-11
Just curious, but have you tried unplugging the photosmart printer?

Your system may be trying to boot from the usb harddrive in the printer (or flash drive) which will return the error no OS.

Either that or make sure to disconnect all your usb devices and try booting.

A

---

### Post by Gremlinzzz on 2007-07-11
disconnect printers and any other extra. then wipe the drive clean after check to make sure boot from cd then try to install. i use the cd version of this free disk cleaner .
[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

---

### Post by david_2001 on 2007-07-15
> **kalosaurusrex said:**
> Just curious, but have you tried unplugging the photosmart printer?

Your system may be trying to boot from the usb harddrive in the printer (or flash drive) which will return the error no OS.

Either that or make sure to disconnect all your usb devices and try booting.

A

That solved my problem :-)  Just got myself a nice shiny new HP PhotoSmart D6160.  Setup was easy with the Ubuntu supplied versions of hplip/hpijs but when I rebooted my PC would freeze during the BIOS POST.  This happened even if the printer was switched into power save mode.  Unplugging the usb lead from the printer got my PC booting successfully again and getting it to boot with the printer connected and switched on in my case involved delving into the BIOS and undoing the boot order changes I had made.  The AMI BIOS in the ASRock 775Dual-VSTA motherboard I'm using allows three different boot devices to be selected but I had only two enabled (the first HDD and DVD drives).  Enabling the third boot device and setting it to 1st Floppy fixed the problem!  (The BIOS doesn't have any PnP OS options and disabling USB devices from being used as boot devices didn't take.)

---

