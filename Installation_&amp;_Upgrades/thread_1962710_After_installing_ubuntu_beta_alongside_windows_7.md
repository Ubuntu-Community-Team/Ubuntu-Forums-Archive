---
title: "After installing ubuntu beta alongside windows 7"
date: 2012-04-21
forum: Installation &amp; Upgrades
---

### Post by cgaie on 2012-04-21
Hi I have a big problem with my Dell xps8300

I had windows 7 and I decided to install ubuntu beta 12 alongside window without wubby
I boot up into usb stick which had ubuntu beta and went for install
Selected first option install besides window
Installation finished
Start machine and boot up into ubuntu

My windows 7 is gone now but not panic I have Dell back up utility and ease backup +windows 7 installation cd

I tried with easy back to get windows back, restore finished successful
Boot up and I got black screen with some grub text

Tried Dell back up and the same black screen after successful restore

Boot up with windows cd and open cmd to fix mbr bootrec.exe /fixmbr 
Mbr successfully fixed
Start pc and grub is gone

Start pc with window cd to install window

Window 7 start copying files and at the very end screen goes black with a white dash blinking

Start pc with partition manager delete windows partition and linux partition, format, try windows installation again and the very end of copying files, i get the dash blinking again

I tried to merge window and linux partition and I can't

When I deleted partitions before I deleted also swap partition I had for linux 

Now I don't have windows nor ubuntu 

I need some serious help

What can I do to install windows back and merge windows partition which I shrank before to install ubuntu ?

Any help is very much appreciated

Thanks

---

### Post by jadtech on 2012-04-21
you should just be able to put the window 7 cd in and boot do the install after that go in the control panel shrink the partition volum  boot from the USB stick partition the free space leaving room for a 1 or 2 gig swap install ubuntu  always window install first.. 

if you have nothing on that drive you should  able to install windows if not  there could be a HD problem ..

i would make sure there is no partitions left on the drive make sure there is not still a small grub partition...

---

### Post by cgaie on 2012-04-21
Thanks for your reply
The problem is that I can't install windows
I boot up with windows 7 cd and it starts copying windows installation files and at the very end when it is finishing copying windows necessary files the screen goes black and a white dash blinking on the screen. At this point I just need to start pc and start again

I had one swap partition and I deleted it with partition manager 9 
Another thing I tried was extending partition I shrank before I installed ubuntu , just to merge the two partitions to install windows as it was before I installed ubuntu but I don't have any option to do so

Can I do that booting up with ubuntu installation cd?

I'm away today for my birthday I will try something else tomorrow when i get home

I just need some ideas because i ran out of ideas myself

---

### Post by cgaie on 2012-04-22
I sorted my PC.  I just deleted another partition I had with windows 8 and did a backup restore and I'm back in business

I will try again Ubuntu beta booting up alongside windows 7

Thanks:popcorn:

---

