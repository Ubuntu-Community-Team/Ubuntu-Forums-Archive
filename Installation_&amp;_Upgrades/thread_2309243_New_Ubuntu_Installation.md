---
title: "New Ubuntu Installation"
date: 2016-01-08
forum: Installation &amp; Upgrades
---

### Post by stribor2 on 2016-01-08
Downloaded 64!bit iso to my computer. Using pendrive in created bootable USB. 
started my windows 7 and by using F12 chose boot from USB but after i hit enter 
nothing else happens just have blank screen. 

I noticed few times whenni was created bootable USB that had some problems with pendrive had troubles 
writing to it so i had to delete everything and start again. It took me 3 times to complete process of creating bootsble USB. 

Any suggestions?

---

### Post by Bucky Ball on 2016-01-08
Welcome. To create boot drive you must wipe the USB and format it as FAT32 first. Then create the install USB.

Windows 7 installed in UEFI mode? Then Ubuntu must be installed in UEFI mode. However you boot the USB is how Ubuntu will run/install. If Windows is installed in UEFI mode, then:

1/ Boot into Windows and switch off hibernation and faststart;
2/ Boot to the BIOS and switch off secureboot and make sure you are booting the USB in UEFI.

If Win installed in BIOS mode, same as above but in step 2, make sure you are booting the USB in BIOS mode. 

Thing to remember is that you must be able to switch the computer off totally; no suspend or hibernate from Windows. If not, Win will 'lock' the drive as it is hibernating. Ubuntu won't see it, you get problems.

Try the above and see what happens. When you get to the options after booting the USB, choose 'Try Ubuntu' from the install media and see how a desktop runs prior to installing.

How much RAM does this machine have? Is it modern enough to handle a full-blown Ubuntu install? (Which release are you attempting to install?)

---

### Post by stribor2 on 2016-01-09
So i turned off hibernation to zero minutes
could not find settings to disable fast start
i changed the order off boot devices to usb(moved it to first place)
i turned on comp and let it boot without touching any buttons
i can see grup menu ( see attached)
i chose install ubuntu 
comp starts reading usb for second or so and then it stops
screen is blank
after couple minutes i hear ununtu os familiar sound(drums)
screen is still dark. No activity whatsoever

[http://tinypic.com/r/1zzi54m/9](http://tinypic.com/r/1zzi54m/9)

---

### Post by Geoffrey_Arndt on 2016-01-09
Please provide full system specs (make, model, cpu type, ram size, gpu type (nvidia xxxx, amd xxxx, intel xxxx).   If you are getting the GRUB loader screen, this is where you can modify the boot parameter to "nomodeset':

 To enable boot via "nomodeset" grub option" 
   

[LIST]
[*]Boot the machine and at the grub menu highlight the kernel you want to use and click 'e' to edit.
[/LIST]
    

[LIST]
[*]Find the line that ends in 'quiet splash' and after a space, add 'nomodeset'.   The end of the line should look like this:
[/LIST]
    _quiet splash nomodeset_ 
   

[LIST]
[*]Follow the instructions at the bottom of that screen to save changes and continue
[/LIST]

---

### Post by Akhunbala on 2016-01-10
I have a same problem. corb reset time out . After 1 minut come black screen, no signal. What I do it problem?

---

### Post by Bucky Ball on 2016-01-10
> **Akhunbala said:**
> I have a same problem. corb reset time out . After 1 minut come black screen, no signal. What I do it problem?

Welcome. Very unlikely the same problem (they rarely are) and from the information you've given here impossible to know. Please start a new thread regarding your issues with as much detail as you can give about what you've done and what's happening (more detail than what you've given here). 

By all means keep an eye on this and see if you can add some help or use some of the ideas given. Good luck.

---

### Post by stribor2 on 2016-01-10
That worked out well. 
Thank you

---

### Post by Bucky Ball on 2016-01-10
What did? The 'nomodeset' option? If yes and you did that in the grub menu at boot the changes will be lost at reboot. You need to make that permanent by adding to grub.

Open a terminal and:

```
sudo nano /etc/default/grub
```

Look for this line:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

... or something that looks like that with 'quiet spash' at the end. Add 'nomodeset' to the end of that:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```

Control+x then 'y' and 'enter' to save and close, then:

```
sudo update-grub
```

That should make the 'nomodeset' option permanent.

---

### Post by Geoffrey_Arndt on 2016-01-10
As Bucky says above, . . . unless you add the graphical driver that is missing (nvidia or AMD . . . whichever applies).

---

### Post by Bucky Ball on 2016-01-10
> **Geoffrey_Arndt said:**
> As Bucky says above, . . . unless you add the graphical driver that is missing (nvidia or AMD . . . whichever applies).

+1. Yep. You could boot in with the nomodeset option then try a few proprietary drivers and see what you come up with. If nothing, 'nomodeset' it is. Depending on what you're doing, the open-source drivers will work fine.

---

### Post by stribor2 on 2016-01-11
> **Bucky Ball said:**
> What did? The 'nomodeset' option? If yes and you did that in the grub menu at boot the changes will be lost at reboot. You need to make that permanent by adding to grub.

Open a terminal and:

```
sudo nano /etc/default/grub
```

Look for this line:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

... or something that looks like that with 'quiet spash' at the end. Add 'nomodeset' to the end of that:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```

Control+x then 'y' and 'enter' to save and close, then:

```
sudo update-grub
```

That should make the 'nomodeset' option permanent.

Yes I didn't do that and that's probably why it didn't work. So I rebooted again and tried to re-install everything again and now I get this error from my post here

[http://ubuntuforums.org/showthread.php?t=2309435](http://ubuntuforums.org/showthread.php?t=2309435)

Ok i removed Ubuntu and installed it again using bootable USB memory key. 
Right now installation is complete and i have pop up box displayed like this
[http://tinypic.com/r/2vrtxyb/9](http://tinypic.com/r/2vrtxyb/9)
bootable key is still plugged at this point. 
Can you please provide steps to take to complete this installation

thanks

---

### Post by Bucky Ball on 2016-01-11
Pretty clear. The installation is finished, restart the machine. Make sure you enter the BIOS on reboot and set it to boot from the hard drive. Pull the USB to make sure.

---

### Post by stribor2 on 2016-01-11
Yes but before I started installation I have edited "install Ubuntu" and set "nomode set". See Bucky post I posted in #12.  
How do I edit all this from post # 12 at my current point of installation

---

### Post by Bucky Ball on 2016-01-11
You don't. You reboot. You will get to a list of kernels. If you don't, reboot from the login screen, if you get there, and hit the shift key before Ubuntu boots and that will get you there.

When you get to that list, do the 'nomodeset' trick to the end of the first kernel line (highlight it but hit 'e' to edit instead of 'enter' to launch it, add nomodeset at the end of the line that ends in 'quiet splash') and continue. Once at a desktop you can add it permanently in /etc/default/grub, as described in previous instructions.

---

### Post by stribor2 on 2016-01-11
I restarted it and comp keeps going into bios no matter what option I chose comp goes back to bios like endless loop

---

### Post by Bucky Ball on 2016-01-11
To the BIOS??? Are you sure? You would need to hit a key manually to get to the BIOS under normal circumstances (actually, I've never heard of a machine booting directly to BIOS until now).

Have you switched the machine completely off, pulled the USB and restarted? Just let it do it's thing, don't press any key.

---

### Post by stribor2 on 2016-01-11
Yes I did.  Pull out the usb restarted and this is what I see
[http://tinypic.com/view.php?pic=25ovxw1&s=9#.VpR9A6_EirU](http://tinypic.com/view.php?pic=25ovxw1&s=9#.VpR9A6_EirU)

Then when I press enter some error briefly shows on screen something like "Realtek failed......." Then that disappears and goes back to bios

---

### Post by Bucky Ball on 2016-01-11
That's not the BIOS, that is the boot device selection screen. Absolutely no idea why your machine is booting to that. Again, totally new one on me. 

Select the first entry, your hard drive.

* Okay, just read your last post. You need to be specific about that error message the machine is throwing if you can.

PS: I have 'unsolved' this thread as it seems far from solved to me. Also, are you positive you have Ubuntu installed? Could you boot from live media, Try Ubuntu, launch gparted at a desktop and have a look? Do you see any EXT4 partitions?

---

### Post by stribor2 on 2016-01-11
I select first entry which is hard drive
then I see this briefly [http://tinypic.com/r/t8rcwy/9](http://tinypic.com/r/t8rcwy/9)
then I see bios again with those 3 entries and this keeps going into endless loop

---

### Post by Bucky Ball on 2016-01-11
You have a PCIe card in the box. It appears to be a Realtek card or have a Realtek chip on it. What is it? That seems to be where it's halting.

---

### Post by stribor2 on 2016-01-11
Can this be trying to do network boot?

This user had similar error ( my box is Lenovo) but I am lost on how he solved it
[http://ubuntuforums.org/showthread.php?t=2234007](http://ubuntuforums.org/showthread.php?t=2234007)

---

### Post by Bucky Ball on 2016-01-11
Not unless that's what you're choosing. You should be choosing the hard drive, first on the list, with the USB out. 

Please read my last post. Check for new posts before posting because you seem not to be.

---

### Post by stribor2 on 2016-01-11
I am choosing the first option which is hard drive but same thing is happening

---

### Post by Bucky Ball on 2016-01-11
> **Bucky Ball said:**
> You have a PCIe card in the box. It appears to be a Realtek card or have a Realtek chip on it. What is it? That seems to be where it's halting.

Please reply to this, posted a while ago.

Unplug your ethernet cable, if there is one plugged in, and reboot.

(PS: And again, you are booting to the boot device list, NOT the BIOS. No idea why you're ending up there, but you need to manually hit a key at boot to get to the BIOS.)

---

### Post by stribor2 on 2016-01-12
I don't know what kind of card that is.  Ethernet cable is not plugged.  I have wireless enabled on this laptop

---

### Post by Bucky Ball on 2016-01-12
> Realtek PCIe GBE Family Controller Series v2.38 ... Media test failure, check cable.

Whatever that Realtek device is, that's where it's falling down.  From the looks of this thread it is an ethernet card and a problem with your ethernet card. If this is a desktop, try taking that card out and rebooting. Sounds like that card might be dead or have a driver installed for it and there is a problem.

Did you choose to 'Install third-party drivers' and 'install updates' during the install of Ubuntu? Incidentally, looks like you hit F2 at boot to get to BIOS on your machine.

PS: Unsure how you're using wireless on this machine. You have not managed to get to the desktop yet so you don't know if that even works yet. I suggest, and this may sound odd but worth a try, plugging in an ethernet cable and booting. See if that makes it happy.

Other thought: Do you have a USB wireless dongle plugged in when you're booting this? Pull it out if so and reboot the machine.

---

### Post by stribor2 on 2016-01-12
Hi
Thanks for helping me with all this. I did do o 'Install third-party drivers' and 'install updates'  during the install of Ubuntu? 
Regarding "Incidentally, looks like you hit F2 at  boot to get to BIOS on your machine" - because machine keeps going into the loop i just press and hold power button which shuts down computer. Then I press the power again to start it and without pressing any buttons it goes into "list of those 3 boot devices" and since I am forced to chose one I selected first (i also tried other 2 with same results) thern that screen goes away and then I see very briefly that realtek error message and then machine goes back to list of 3 boot devices. 
I chose wireless connection as soon as I started install. It asked me for my language, comp name, user name, wireless network etc...
I don't have anything plugged into computer.

When I get home tonight I will plug Ethernet cable and see if it helps. 
Really appreciate you taking time to respond to my cries for help :)

---

### Post by Bucky Ball on 2016-01-12
When you boot the machine, immediately start hitting F2. Don't wait. Press power, start with F2. Just tap it lightly and repeatedly.

---

### Post by stribor2 on 2016-01-12
will do......isnt that gonna bring BIOS screen? From then I will chose my hard drive but I already did that ):

---

### Post by stribor2 on 2016-01-12
Ok so I plugged Ethernet cable and first what I see is 
this [http://tinypic.com/view.php?pic=30iasmu&s=9#.VpWmeK_EirU](http://tinypic.com/view.php?pic=30iasmu&s=9#.VpWmeK_EirU)
then this runs for bit DHCP and then I see this 
this  [http://tinypic.com/view.php?pic=t8rcwy&s=9#.VpWnFa_EirU](http://tinypic.com/view.php?pic=t8rcwy&s=9#.VpWnFa_EirU)

Then I see boot device list I chose hard drive and we start again from above

:(

---

### Post by stribor2 on 2016-01-12
I think what's happening here is that machine is trying to boot into 
Hard drive and it fails then goes to 
Cd and it fails then goes to 
network boot and that fails as well

i think system cqnt either find hard drive or something else.  I am 90% sure these partitions are messed up somehow.  This is windows 7 machine that I overwrote with Ubuntu.

---

