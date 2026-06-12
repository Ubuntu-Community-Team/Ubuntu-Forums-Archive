---
title: "Strange and unpleasant goings-on with Hardy"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by FokkerCharlie on 2008-05-04
Hi All

I've been having problems with my new Hardy setup- my laptop used to run Gutsy pretty well, until I decided to fit a new HDD.

So, I start with a new installation of Hardy, and all looked good until I enabled the ATi restricted driver.  Then, strange things started to happen- fsck would run on every start, generate a whole load of errors, and fail to get as far as the log-in screen.  Anyway, I have re-installed, tried the restricted driver, but got rid of it when I started getting errors again- eg this one on shutdown:

```
EXT3-FS ERROR (DEVICE SDA1):  EXT3_GET_INODE_LOC: UNABLE TO READ INODE BLOCK
```

I have no idea what that means, apart from being something to do with the hard drive.

On my last attempt at shutting down (after putting the machine into standby), I was presented with messages culminating in:


```
Reading files needed to boot
Preparing restricted drivers
Setting the system clock
Starting basic networking
cp:  cannot stat 'lib/udev/devices/*': no such file or directory
Setting the system clock
Mount point '/dev/shm' does not exist. Skipping mount.
Mount point '/dev/pts' does not exist. Skipping mount.
Loading kernel drivers...
Loading manual drivers...

```

There then followed some messages about critical temp (99) reached, shutting down- at which point I turned off the computer with the power switch.

Any ideas what's going on?

Cheers
Charlie

---

### Post by Pumalite on 2008-05-04
If all started when you installed the driver (not unheard of ATI drivers); remove the driver. You are better off with vesa than an ATI driver.

---

### Post by FokkerCharlie on 2008-05-04
I have already done so!

Does that look like the cause of the problem?

---

### Post by Pumalite on 2008-05-04
How is your computer doing now?

---

### Post by FokkerCharlie on 2008-05-04
It's going ok at the mo.  I should have added above that a precursor to the problems on shutdown (and subsequent start) was odd things going on with the desktop- Firefox would seem to pause for a minute or so, a fair bit of HDD activity would occur, icons would go missing from the panels and menus.

Although I have just heard the ubuntu brand welcome music for some reason...

---

### Post by FokkerCharlie on 2008-05-04
...and now odd things are happening again.

I've been following the instructions for the ATI driver (manual install) here:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

That worked very well in gutsy.  (subbing hardy for gutsy), and in the process, odd things are going on again.  I can't start nautilus:

```

charlie@charlie-laptop:~/Desktop/ati$ sudo nautilus
No protocol specified
cannot open display:
``` 

Or rhythmbox.  I'll restart and see what happens.  Wish me luck!

Charlie

---

### Post by FokkerCharlie on 2008-05-04
Undoing those steps and re-starting seems to have fixed things.

However, I am still stuck with slow graphics!

I need this to work, so I can carry on contributing to FlightGear.  I'll carry on having a fiddle...

Cheers
Charlie

---

### Post by twright on 2008-05-04
have you tried installing the ati driver via hardware drivers

if that fails you could try a fresh install using xfs or reiserfs instead of ext3

---

### Post by FokkerCharlie on 2008-05-04
> have you tried installing the ati driver via hardware drivers

You mean via System>Admin>Hardware drivers?  Yes, I have tried that.  That was what seemed to cause the great big disk problems earlier!

It would be better to try to avoid (yet) another Hardy install, but do you think that a different fs might do the trick?

Thanks for input so far.

EDIT:  Just had to restart again- tried restarting X, which stopped at:

* Running local boot scripts (/etc/rc.local)

Here's the output of dmesg after the restart- I don't know if it helps or not:
[http://www.pastebin.ca/1006947](http://www.pastebin.ca/1006947)

Charlie

---

### Post by wpshooter on 2008-05-04
> **FokkerCharlie said:**
> You mean via System>Admin>Hardware drivers?  Yes, I have tried that.  That was what seemed to cause the great big disk problems earlier!

It would be better to try to avoid (yet) another Hardy install, but do you think that a different fs might do the trick?

Thanks for input so far.

Charlie

No, I think a new O/S would do the trick, anything but Hardy !!!!

I would wait until they finish writing this O/S, which IMHO, they have not done yet.

Good luck.

---

### Post by FokkerCharlie on 2008-05-05
WP Shooter, I am sorry to say that you might be right.  Will persevere for the moment, tho.

Anyway, I just had another error like this:

'Could not start child process gnome-terminal (input/output error)'

When trying to laund the terminal from the menu.  This was again preceded by un-responsiveness from FF3b5 and icons disappearing.  So it seems that the ATi driver might not be the problem, but just may be exacerbating snags in general.

So I'm not using FF for the moment, I've also swapped Wicd in for Network Manager, will see what happens.

I wanted to open the terminal to use dmesg- but couldn't!  So is there another way of getting some useful debugging output?

Cheers
Charlie

---

### Post by Nerevar144 on 2008-05-05
I had strange problems with the restricted driver (white screen on boot) and my ATI Mobility Radeon 9600.  Just use ENVY to install the latest drivers and you won't have any problems except for the normal ATI problems when using Compiz.  To remedy that use the Compiz Fusion Icon to switch between metacity and compiz when your going to be using a 3D app.  Hope this works for you.

---

### Post by FokkerCharlie on 2008-05-05
Thanks Neverar

I'll give that a go.  I'll stick with the no- FF and no ATi drivers for a few days first, tho, to try to isolate what's occurring.

---

### Post by FokkerCharlie on 2008-05-05
Grrrrrrr.......

Just had it again, unresponsiveness from desktop (running Opera only, I think), followed by 'Failed to launch child process xxxxxxx (input/output error)' or something.

Tried to re-start x using ctr+alt+bksp, then this:

* Running local boot scripts (/etc/rc/local)
[ 1409.319657] EXT3-fs error (device sda1): ext3_find_entry: reading directory # 214122 offset 0
(and 4 more of similar messages with different numbers)

So the problem doesn't seem to be:
-  FF3b5
-  ATi proprietary drivers
-  Network manager

Is there any way that I can get some more debugging output to see what is causing all this?  Otherwise, is it worth re-installing with a different format?  And if so, how?!

Cheers
Charlie (from the end of his tether)

---

### Post by Pumalite on 2008-05-05
Download a new iso and burn a new CD at 4x or less after doing md5sum. Install again, but don't expect much of your ATI.

---

### Post by FokkerCharlie on 2008-05-05
OK, I can try that- I did check the ISO for errors, but I will give the re-install a go from the very beginning if you think that will help.

Will have to be in a few days, as I am away from tomorrow, bu will report back!

Cheers
Charlie

---

### Post by Pumalite on 2008-05-05
Good luck.

---

### Post by FokkerCharlie on 2008-05-10
Oh dear.

Tried all of that, and still getting errors.  I began to suspect that I had a hardware problem- so I installed the sensors applet, and sure enough, as my CPU temp rises towards 100 degrees, the problems start.  So that's why it looked initially like a graphics-driver problem.

I also managed to re-create the snags with Gutsy (although it took more effort) I got it to overheat and fail- so looks like a new laptop for me :(

Thanks for all the advice.

Charlie

---

### Post by jimmccool on 2008-05-12
No, don't buy that new laptop yet. I'm having similar problems - started when Firefox crashed and since then I get missing incons all over the show - including the shutdown menu, which is kinda difficult....And there are also missing paths... Looks like a nasty bug.

I don't use the ATI driver on my Acer 5100 laptop - way too flaky. I'm going to try a reboot, stick to Opera for a browswer and see what happens...

---

### Post by FokkerCharlie on 2008-05-13
Well, I have already spent my pennies on a new machine, so jim, you're too late!

I will be very interested to hear what you find with yours, though.  It was useful to me to install sensor-applets from synaptic, and became quite clear that the problems were associated with CPU heat.

Cheerio
Charlie

---

### Post by FokkerCharlie on 2008-05-16
Hey jim, are you still having problems?

Here's something that has turned up- I took the upgraded 160GB HDD out of my old laptop to use as an external drive, and it started playing up- unmounting without any apparent cause in particular.  After playing around for a bit, I re-partitioned the drive into two equal EXT3 bits, and it now works perfectly.

If you have a large HDD, it might be worth having a go at that, too.

Do let us know how you get on.  For what it's worth, I'm loving Hardy on my new 5920!

Cheers
Charlie

---

