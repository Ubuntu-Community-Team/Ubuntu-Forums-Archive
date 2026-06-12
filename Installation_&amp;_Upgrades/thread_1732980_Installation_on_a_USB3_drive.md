---
title: "Installation on a USB3 drive"
date: 2011-04-18
forum: Installation &amp; Upgrades
---

### Post by loseby on 2011-04-18
Have a Samsung Story Station USB 3 drive and want to install Ubuntu on that. 

My Setup at the moment is
Motherboard ...Gigabyte X58A-UD7
Windows 7 64 bit   ... C: SSD 150GB
                   ....E: Raptor 300GB 
                   ....F: Harddrive 250GB

I use ACHI and system works ok. Now I want to install Ubuntu on the the Samsung drive ( S: ) and want to know the best way to go about this . Does Ubuntu support USB3 drives ?  I notice in Win7 it has a USB3.0 Host Control Utility /Driver from NEC installed and I assume thats to enable USB3. So what about Ubuntu ?  Does it need drivers or does it have them ?

Would it be best to wait for the next version of Ubuntu ( 11 ? ) as it may have the drivers for USB 3 etc ?

btw: when it comes to linux I am pretty much of a novice. I have it installed on a dual boot system on another PC but keep having problems with that and as this is the main PC  ... I would rather have it installed in this room  :-)

---

### Post by Hedgehog1 on 2011-04-19
At this time, Ubuntu cannot boot from a USB 3.0 port.

You can install and boot it from a USB 2.0 port for now, and then move to the faster USB 3.0 port when when it is supported.

So you can still use Ubuntu on the drive, just gotta run slower for a while (or use an eSATA drive - that works fine).

***The Hedge***

:KS

p.s. Data drives (ones you don't boot from) can be attached on the USB 3.0 ports and Ubuntu will read/write to them fine. The Kernel just doesn't carry the different USB 3.0 code to boot from them yet.

---

### Post by loseby on 2011-04-19
thanks for the reply hedge, saved me a lot of mucking around

maybe I should have asked the question before buying the USB3 external hard drive  :P


the hard drive is USB2/3 so it should still work for installation of Ubuntu ?

will 11 ( whatever its called ) support USB3 ?

---

### Post by oldfred on 2011-04-19
Do not know if it is a grub2, Ubuntu or both issue with USB3.

More info on installing:
Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by Hedgehog1 on 2011-04-19
> **losbey said:**
> thanks for the reply hedge, saved me a lot of mucking around

maybe I should have asked the question before buying the USB3 external hard drive  :P


the hard drive is USB2/3 so it should still work for installation of Ubuntu ?

will 11 ( whatever its called ) support USB3 ?

As long as you use a USB 2.0 port on you computer, you will be opertional on the USB 3.0 drive in that port.

**oldfred** (who knows a lot!) mentioned: *'Do not know if it is a grub2, Ubuntu or both issue with USB3'* Meaning: *'Hedge - check your facts - it may be Grub that chokes on USB 3.0 and not the Kernel'*

Once it is released, load Natty using a USB 2.0 port, and then after you have booted from it a few times and you know it works, move it to a USB 3.0 port and see if it boots. If it does, then Natty (11.04) supports USB 3.0 booting.

**_Oh_** - and be sure to tell the rest of us.  You have just been voted: **"USB 3.0 boot Guinea Pig"**.  *Congratulations!*


***The Hedge***

:KS

---

### Post by loseby on 2011-04-21
I will try installing 10 this weekend using a USB2 port. After installation I will try swapping to USB3 and see what happens.

Now I want GRUB to stay clear of my Window drives so maybe I will disconnect my internal hard drives before mucking around with it. Will check out oldfreds link first and will let you know how it goes

---

### Post by loseby on 2011-04-23
well having no luck  ....  I thought it could be an issue with my graphics card as it starts purple then the screen goes blank and that is it


ended up removing all my hard drives ( ahci mode ) , changed the CD Rom to one of the Gigabyte ide ports ( strange that windows cannot see it if I boot to windows ) and the result was the same .... tried putting it on a USB stick and just the usb drive and selected run from usb and it worked....selected the install 10.10 from the desktop and it then went around installing it on the udb drive. Sad thing was when I went to reboot ... it fails, cant find the usb drive

Well I dont know how 10,10 goes with sata drives using achi mode but all up .... a failure which may have a lot to do with my BIOS and achi mode as the cdrom is not recognised in windows .... I could swap hard drive ports but its a real pain in the butt as my monster graphics card all but covers a couple and I dont want to play around with moving the beast.....

what I may do to play around with making a ubuntu installation on a usb drive is put it an another external usb drive on this PC and see what happens

I wish I still drank alcohol , then I may be able to understand this post  :)

---

### Post by loseby on 2011-04-23
update:

tried it on a different USB drive ( USB2 ) and it was very similar to the USB3 drive but after continued rebooting from a blank screen it finally worked  ....  I am positive its something to do with the video drivers , well not positive, justguessing.......

anyway after updating I had the same problem and had to reboot a number of times before it worked again  ..... this time I managed to install the amd drivers and on reboot it worked, next thing is to attach all my window hard drives and boot ( F12 )to whatever I want

hopefully when 11 comes out in a few days it will work a lot better

---

### Post by Hedgehog1 on 2011-04-23
> **losbey said:**
> update:

tried it on a different USB drive ( USB2 ) and it was very similar to the USB3 drive but after continued rebooting from a blank screen it finally worked  ....  I am positive its something to do with the video drivers , well not positive, justguessing.......

anyway after updating I had the same problem and had to reboot a number of times before it worked again  ..... this time I managed to install the amd drivers and on reboot it worked, next thing is to attach all my window hard drives and boot ( F12 )to whatever I want

hopefully when 11 comes out in a few days it will work a lot better

Thanks for the update (and I think you are correct about the video drivers causing the temporary issues).

So do you feel confident that the 10.10 kernel/10.10 grub does not boot from USB 3.0?

I am looking forward to your results with Natty 11.04.  As a side note, the 11.04 builds have been very stable (few if any changes) on Natty these last few days. It is installable now if you want to try it this weekend and not wait till next weekend.

Your call - and thanks for your efforts and sharing the knowledge!

***The Hedge***

:KS

---

### Post by loseby on 2011-04-23
not sure about USB3 but will try it on Natty 11.04 when it comes out , do you know if Natty supports USB3 ?

actually its really not that important as this installation on a USB2 drive is now pretty stable, well after installing the restricted drivers for my video card

its strange but I dont get to see GRUB when I boot, maybe something to do with installing it with all my other drives disconnected ( well at the hard drive end I pulled at the sata leads )

---

### Post by oldfred on 2011-04-23
If the os-prober only found one system, you do not normally get the grub menu. You have to hold down the shift key from BIOS until menu appears to get it.

---

### Post by loseby on 2011-04-25
thanks young fellow

Well dont need GRUB as I the USB as an on/off switch and/or use f12 key at boot to select which hard drive to boot from and as I mostly use Windows I use the sleep function so no real hassles


anyway, any news on USB3 with 11.04 ?

---

### Post by loseby on 2011-04-28
major update

Just installed Ubuntu 11.04 on the USB3 drive connected to a USB3 port and it looked promising....the drive led flashed blue ( blue is usb3 and green is usb2 ) but it failed to work when rebooting...nothing, couldnt locate the drive

well, I think put the USB2 drive on and installed 11.04 on and here I am typing from this

edit: translation...installed on another USB HDD which is USB2 and it worked perectly and still is

---

### Post by loseby on 2011-04-28
some interesting things happen with this USB3 drive, when I boot and hit the F12 key it gives me the quick option of what I want to boot from and with hard drives you press the + to expand it and it shows at the moment the Samsung 500GB USB2 drive on top, then my SSD drive (win7 boot) then my Raptor 300GB and another 250GB drive that I keep some data on. But the Samsung Story 1TB hard drive is not listed but the LED is flashing blue .

When I go into the Samsung 500GB USB2 hard drive that has 11.04 on it it shows a 987GB file system on the desktop. This is the Samsung Story USB3 drive and I can access all the files on it, well the ones that were installed from the setup.

So why wont the Samsung Story drive show up in the Gigabyte quick boot menu ?

---

### Post by Hedgehog1 on 2011-04-28
> **losbey said:**
> major update

Just installed Ubuntu 11.04 on the USB3 drive connected to a USB3 port and it looked promising....the drive led flashed blue ( blue is usb3 and green is usb2 ) but it failed to work when rebooting...nothing, couldnt locate the drive

well, I think put the USB2 drive on and installed 11.04 on and here I am typing from this

edit: translation...installed on another USB HDD which is USB2 and it worked perectly and still is

Well, thanks for testing this for us all.  Now we know that Natty also does not boot from the USB 3.0 port.

Appreciate your efforts on this!


***The Hedge***

:KS

---

### Post by loseby on 2011-04-29
> **Hedgehog1 said:**
> Well, thanks for testing this for us all.  Now we know that Natty also does not boot from the USB 3.0 port.



***The Hedge***

:KS

I am not sure about this. Am curious as to why Gigabyte selection tool ( f12 key ) does not see the USB3 drive ?

---

### Post by loseby on 2011-04-29
btw: from another forum 

> I think this post is in the wrong place and has nothing to do with linux.
Best as I can tell, when you hit F12, you are still in the early BIOS boot process - therefore no operating system is booted, Linux or otherwise. If drives aren't appearing there, it's because the motherboard/bios is lacking support. 

so maybe it has nothing at all to do with Linux

---

### Post by loseby on 2011-04-29
FINAL ATTEMPT :

1/ I ended up flashing the motherboard BIOS to latest version and when I pushed the F12 key this time the Story Drive was sitting there

Installed 11.04 on it and it seemed to ok but on rebooting just a pinkish screen so I did a reboot and this time I managed to the GRUB screen but after selecting 11.04 it failed and after a while dropped to a shell which is pretty useless to me  :-)

Tried again and this time selected safe mode and finally after a lot of data I finished up with this message :


ALERT! /dev/disk/by-uuid/d6f80de3-2f83-414b-b994-ccf451143616 does not exist
Dropping to SHELL


So the inital problems were caused by incompatible BIOS/hardware but a problem still exists somewhere with USB3 and Linux 11.04

---

