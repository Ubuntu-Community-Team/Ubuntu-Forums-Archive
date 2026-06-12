---
title: "Problems with Beta-1 (kinda long)"
date: 2010-04-04
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by xeddog on 2010-04-04
I just did an involuntary fresh install of Lucid beta-1 64-bit on my machine.  It was involuntary because I downloaded the beta-1 liveCD iso, burned it to a cd, and then rebooted my machine.  I was expecting the Language screen to come up followed by the options screen that would let me verify the integrity of the disk.  Well,  after a couple of minutes I arrived at the conclusion that the disk was bad because it never came up.  I got the purple screen with the dots under the Ubuntu name but nothing else.  It was then that I noticed that I was having a lot of hard disk activity.

So I turned the machine off and restarted it.  When I selected Jaunty from the grub menu, my Jaunty installation on sda was gone.  Got a message about having to load the kernel first.  When I pressed a key I was presented with the grub menu again.  Fortunately I had a second disk (sdb) with a Karmic install that still worked so I was able to get a system booted, but my Jaunty was gone.  That would not have been a big deal if not for one thing.  I had not backed up my mail for a few months, so I lost it all.  I also had some video files for my grand daughter that got wiped out too, but they are easily replaceable.

Next thing I did was to try to download the LiveCD again from a backup machine, and reburn it.  Brought the cd to this machine, and the same thing happened.  No opportunity to verify the disk, it just started doing something to my disk.  Since my Jaunty was already gone I let it run for about 15 minutes and nothing seemed to happen.  Finally, it just stopped doing anything at all.

Then I booted my Karmic again and downloaded the Alternate cd.  After burning this one I was able to verify it, and then ran an install that seemed to run to a normal completion.  The last thing it told me to do was to remove the CD from the drive and reboot.  When I did that, I got the purple screen again and nothing more.  I have to add that I have a dual monitor setup with a widescreen 1080P LCD as primary, and a 4:3 CRT as secondary.  The purple screen was on the lcd, and I noticed that the crt was black except for a few white dots along the top that looked like they may have been part of a message.  

I tried rebooting a couple of times and got the same thing every time.  So on a whim I decided to see if I could force the message (if that is what it was) to my lcd.  I turned the crt off and on the next boot the machine came up.  I did notice that there were a few messages that strobed onto the screen, but they were gone so fast that I could not read them.  It didn't matter any more because I had a system now.  The first thing I did was apply all 483 updates, and then rebooted. 

When I turned on my crt again and then powered off/on and rebooted, the machine still came up, but the crt never came out of powersave.  I tried running nvidia-settings but it would not let me activate the other monitor.  The Hardware Drivers gave me two options:  version 173, and version current.  Didn't there used to be version 185???   Anyway, I went to the nVidia website, downloaded the latest driver (195.36.15), and installed it using the recovery mode.  When I rebooted back to normal mode I was able to get both of my monitors working as they were before.  Whew!  What a hassle.  But now on to fixing everything else that needed fixing.

Now I wanted that to mean just installing apps, and doing the customization that I wanted.  Seeing as this is a 64-bit install there are a couple of things that I cannot get working at this time.  Like Adobe Reader and that flash crap, but hey.

So after all this, there are still three things that I need some help with (for now).  

1.  I have a Microsoft Intellimouse (PS/2 with wheel), and the wheel doesn't work.  Never had a problem with this mouse on any of the other OS's I have used it with.  I can't find any settings to turn it on, and I am at a loss on this one.  I have searched the Ubuntu forums and cannot find anything either.  It did work for a while, but has since stopped completely.  

2.  I am running the conkyforecast module in conky to put desktop weather on my crt display (which is to the left of the lcd).  That works great, but what is wrong is that conky seems to be hiding the other icons I have on my desktop (both monitors).  If I put my mouse cursor over one of them, it will display for about a second and then disappear again.  If I close conky, the icons will stay visible when I hover the cursor over them.  I went to the developers thread on conkyforecast, but he is running Arch and is not having any problems like this.  He suggested it might be an Ubuntu thing.  

3.  Last thing for the time being.  I took a couple of screenshots, but I cannot find the images ANYWHERE!!  Where in the *^%$##@*&()(&^%^ does the app put them???

If you have read all of this, thanks.  If you have read all this and have an answer for me, THANKS!

xeddog

Machine is GigaByte EX58-UD3R motherboard with Intel I7-920 processor.  6GB ram.  nVidia Geforce 9500 GT graphics card with LCD and CRT displays.  Disk sda is a Sata 1TB and sbd is a 300GB IDE.

---

### Post by VMC on 2010-04-04
I read most of it. beta1 should not have done anything on its own. When you boot the livecd you should see at the bottom of the screen a "keyboard" and a "human", apparently meaning for you to push a key to get to the old style boot menu. I usually push space bar and am presented with the try befre and install and test memory options. But even if you leave it alone and push nothing you should finally end up with a menu that has two choices, in a graphical display. One to Try ubuntu before install and the other one to install. There it should wait indefinitely for you selection using the mouse.

Edit: Usually the screenshots end up in your home directory. They were from your installed OS and not the Livecd one, correct?

---

### Post by thatguruguy on 2010-04-04
> **xeddog said:**
> 
3.  Last thing for the time being.  I took a couple of screenshots, but I cannot find the images ANYWHERE!!  Where in the *^%$##@*&()(&^%^ does the app put them???


Wherever you tell it to.

---

### Post by darrenn on 2010-04-04
Strange so far as I know it won't install without telling you. If it did that would be one major bug.

---

### Post by xeddog on 2010-04-05
VMC & thatguruguy - Correct, from the installed OS.  However the screenshot app never did ask me where to save them.  I think I have figured it out though, and it is user error.  I was selecting the "Grab the current window" option, but I did not specify a delay so it used the default of 0.  I just tried it again and if I specify a delay and then select the window I want, it works. 

darrenn - Up until today, the problem was reproducible.  I just tried booting the same cd again and it seems to be ok now.  I was able to verify it for the first time.  In addition to that, apparently this is NOT a LiveCD because there is no option in the list to run Ubuntu without changing your computer.  Only to install it.  I guess if you press any key it will start the install, but I am certain I did not do that.  To tell the truth, The first time I booted the cd I put the disk in the drive, did a restart from the upper panel in my Karmic installation, and went to the kitchen to get a cup of coffee and was gone for 4-5 minutes.  I was expecting to see the option to select language when I got back, or at worst, the Ubuntu Live desktop, but certainly not whatever happened.

So.  No takers on the mouse problem?  Oh well, thanks for the replies anyway.

xeddog

---

### Post by cariboo on 2010-04-05
The only problem I've had with Microsoft mice, is that the wheel switch seems to wear out fairly quickly on the cheaper models. I've gone through 2 in the last year, I really liked the [Arc]("http://www.microsoft.com/hardware/mouseandkeyboard/ProductDetails.aspx?pid=112"), but it only lasted about 9 months and [this]("http://www.microsoft.com/hardware/mouseandkeyboard/ProductDetails.aspx?pid=108") one lasted even less time. 

Microsoft used to make good quality mice and keyboards, but as with every thing else hardware related the quality seems to be getting worse.

---

### Post by rtalcott on 2010-04-05
I have an Asus p4s800d-x....runs 9.10 & OpenSolaris 2009.06 with no problem...I tried installing 10.04 from numerous daily builds and the beta and I get a mouse freeze as soon as the desktop comes up...I am using a Logictech usb mouse...works fine on THIS machine with 9.10 and OpenSolaris.....mouse freeze comes when I use the usb connectors on the motherboard...I also have 3 extra usb ports on the front connected to the motherboard usb header in to a Rosewill unit that has ports for various memory formats + 3 usb ports....if I connect the mouse to one of these usb ports it works...

rt

---

### Post by xeddog on 2010-04-05
cariboo907 - My mouse must be one of the older good quality meeses because it is fine.  I can boot Karmic and it works flawlessly, wheel and all.  It's just that the wheel doesn't work in Lucid.

rtalcott - I just added a USB mouse and it works flawlessly in Lucid too, wheel and all.  I can't use regularly though because it is from a laptop and the cord is just waaay too short (maybe 2 feet), and it is way too small for me. 

xeddog

---

