---
title: "Ubuntu 10.10 will not install"
date: 2010-12-10
forum: Installation &amp; Upgrades
---

### Post by greybeard62 on 2010-12-10
I have 10.10 running on this machine, Lenovo X61 and an older Toshiba laptop.  Last night I tried to install Ubuntu 10.10 on a new Lenovo U160 with i5-470um processor.  I am not trying anything special, no dual boot, I want to blast Win 7 away like always and run only Ubuntu 10.10.  This is the same CD which loaded and installed on the other laptops.  It blinks the CD light, gets to the "little guy" screen, then hammers the CD for a very long time, then goes away into a black screen.  I really depressed everything I could (all keys).  I noticed that the space bar or enter cause the CD drive to blink again but nothing visible on display.  OK.  Then I tried to install 10.4 from a good CD and the exact same thing happens.  This CD was used to install at least 5 laptops.  I have downloaded 10.10 64 bit .iso and will try that soon as I burn it.  Is there a known problem with the i5-470um or is this a graphics/display issue?  I can't think of anything really unique about the new Lenovo, the i5-470um is the newly released 18 watt stamp proc, just out around November I think.  Other things on the new U160 are pretty generic, webcam, HDMI, usb, 4GB mem, 500GB drive, 11.6" screen.

---

### Post by sikander3786 on 2010-12-10
I would suggest to try 'nomodeset' parameter from F6 menu at boot.

[https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options](https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options)

---

### Post by greybeard62 on 2010-12-10
Thank you!  The install is almost finished now, everything looks great so far.  "nomodeset" selected and everything else is going normal.  I've been using Ubuntu now since 06, seldom have asked for help because stuff just works, answers easy to find.  Yeah, someday is today for me, still disagree with paying the W tax but everyone else has to as well.  On the shiny bright new U160 I booted Win 7 one time, to make recovery dvds and back it up - just in case.

---

### Post by sikander3786 on 2010-12-10
Glad to know it worked for you :-)

If satisfied, you can mark this thread Solved using **[COLOR="Red"]Thread Tools[/COLOR]** near the top of this page.

Happy Ubuntu-ing!

---

### Post by Quackers on 2010-12-10
After installation is finished it will ask for a reboot. The same thing may happen again as this is a graphics problem.
If it won't reboot properly, reboot again and hold down the shift key. The grub menu should appear with the top item (ubuntu) highlighted. Press the "e" key and a new screen will appear. If you navigate to the end of the line which says "quiet splash" and remove it then type in "nomodeset" - without the quotes, and press ctrl + x to reboot it should go to the desktop. 
Once there, if you run Additional Drivers from the System > Admin menu the drivers for your graphics card will be installed (hopefully). After this it should boot normally.

---

### Post by greybeard62 on 2010-12-10
Quackers, thank you.  Now, I booted into a blank screen, then followed your instructions.  Rebooted into command line interface, logged in...so what is the sudo or command to get the graphics drivers?  I have no menu, just command line now.

---

### Post by Quackers on 2010-12-10
You need to reboot again and during bootup hold down the shift key. This will bring up the grub menu. When it appears press the "e" key and a new screen will appear.
Navigate (with the down arrow and right arrow) to the end of the line that says "quiet splash". Remove those 2 words and in their place type "nomodeset" but without the quotes.
Press ctrl + x to reboot.
Desktop should now appear.
Run Additional drivers from the System > Admin menu.
Install any drivers it finds.
Reboot.
Should be tickety-boo :-)

---

### Post by greybeard62 on 2010-12-10
Exactly what I did, rebooted, changed "quiet splash" to "nomodeset", ctrl-x to reboot.  Booted into command line, tty1, logged in.  Now, my question is how to get the graphics menu or what is command line to download graphics drivers?

---

### Post by sikander3786 on 2010-12-10
Thanks to Quackers. I knew it was going to happen but :facepalm: too lazy to mention it here. Forgive me and kudos to Quackers.

---

### Post by Quackers on 2010-12-10
After logging in type startx and hit enter. See if the desktop arrives.

---

### Post by greybeard62 on 2010-12-10
In other words following your instructions I do not reboot into the desktop (graphical interface) but into command line mode, tty1.  I can log in here, did, I just don't have a clue what commands to issue to download additional drivers.

thanks.

---

### Post by Quackers on 2010-12-10
Try post #10 or press ctrl+Alt+F7

---

### Post by greybeard62 on 2010-12-10
Thank you, I do use the terminal and command line occasionally but not a command line guy.  I appreciate your patience.  The message after login and entering "startx" is "Fatal server error: no screens found"  

"ctrl ALT F7" hangs at "* Checking battery state..." no further output.

---

### Post by sikander3786 on 2010-12-10
Which graphics card is there? nomodeset might need to be changed to something else if it isn't Nvidia.

Post the output of this command.

```
lspci | grep VGA
```

---

### Post by Quackers on 2010-12-10
It's not my patience that's the problem :-) It's how much I know (or don't know) about graphics problems!
Hopefully somebody with more knowledge on this subject will come along.
For the moment, am I correct in thinking that if you do a normal reboot the grub menu does not appear and it boots to a black screen with a login prompt in white?
And if you do a reboot while holding the shift key down, the grub menu does show up and after pressing the "e" key and then removing quiet splash and replacing it with nomodeset, you still boot to the same black screen with the white log in prompt?

---

### Post by greybeard62 on 2010-12-10
This is not nvidia controller, integrated graphics.

"VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)"

---

### Post by Quackers on 2010-12-10
Aha! Sikander I was going to pm you for assistance :-)
Excellent timing :-)

---

### Post by sikander3786 on 2010-12-10
Thanks Quackers. I was keeping an eye ;-)

Based on your graphics card, you might need to put one of these in place of 'nomodeset'.

1. i915.modeset=1
2. i915.modeset=0
3. xforcevesa

Lets hope any one of them works :-)

---

### Post by greybeard62 on 2010-12-10
Results of trying the three options editing grub, ctrl-x reboot

i915.modeset=1  boots into black screen

i915.modeset=0  boots into tty command line, "startx" gives Fatal server error: no screens found.

xforcevesa    boots into black screen

---

### Post by sikander3786 on 2010-12-10
Just to make sure, you are editing the **first** entry in Grub menu?

You are not deleting the whole line but just deleting the words quiet & splash and typing nomodeset or whatever parameter in their place.

---

### Post by greybeard62 on 2010-12-10
That is correct, I am editing the first line which is highlighted, press the "e" key, then replacing only those two words, "quiet splash" with the parameters suggested.  Then "ctrl-x".

---

### Post by sikander3786 on 2010-12-10
**Added:** What are your graphics specs? First let us know about that. Specially RAM.

```
free -m
```

[/Added]

That is weird. It shouldn't be happening like that...

Lets try reconfiguring your graphics from the same command line.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf
```

Note, it is a capital 'X' in X11 and lower-case 'X' in xorg.conf.

If it says, file not found, ignore and proceed to the next command.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Reboot:

```
sudo shutdown -r now
```

Lets see what it does now. I am feeling sorry for your bad experience with Ubuntu. It shouldn't be doing that.

---

### Post by greybeard62 on 2010-12-10
free -m (can't cut and paste so just entering for you)
total 3699, used 231, free 3467, shared 0, buffers 17, cached 55

Swap: total 10832, used 0, free 10832

Will need to look at Lenovo spec but i5-470um with Intel integrated graphics

---

### Post by greybeard62 on 2010-12-10
graphics adapter is 

Mobile Intel HM55 Express

---

### Post by sikander3786 on 2010-12-10
You said it is an older laptop? With nearly 4 GB of RAM, it isn't that much old.

You can try reconfiguring your graphics as mentioned in post # 22. If that doesn't solve the problem, hang in there. I am going to do a search on your problem and in the meanwhile, some other member might jump in with some better suggestions.

Edit: Actually you didn't say it is an older machine. You said it is a newer machine and I mis-understood as I always do ;-)

---

### Post by greybeard62 on 2010-12-10
I appreciate your help.  Sorry for confusion, this is absolutely new laptop, just got it last night, processor shipped dates in November this year.  I run Ubuntu 10.10 on a 3 yr old Lenovo X61 and a 6 yr old Toshiba, 10.4 on an 8 yr old Toshiba p4.

---

### Post by Quackers on 2010-12-10
I wonder if the graphics chipset is so new that no driver exists yet?

---

### Post by greybeard62 on 2010-12-10
ran code from post #22, re-boots into dark screen.

---

### Post by sikander3786 on 2010-12-10
I found something for you. As Quackers said, it is a very new graphics chip and therefore not yet supported in Linux (??). They said that Kernel version 2.6.33 would support it but don't know if it does or not.

[https://bugs.launchpad.net/ubuntu/+bug/518938](https://bugs.launchpad.net/ubuntu/+bug/518938)

This might be the fix.

[https://bugs.launchpad.net/ubuntu/+bug/518938/comments/4](https://bugs.launchpad.net/ubuntu/+bug/518938/comments/4)

---

### Post by greybeard62 on 2010-12-10
OK, whew! Tried all that stuff, reloaded kernel, updates etc.  Apparently this is going to be an issue for a lot of people since most of the ultra-portables are shipping with this new chipset now.  For the time being there is apparently no answer or fix which works, at least on my U160 Lenovo.  From searching the forums this is an issue with Acer, Asus etc as well on the new laptops with this chipset.  Some fixes worked for some others, none for me at this time.  Glad I made the backup and rescue and recovery sets.  Glad I tested them too.  Nothing worse than a shiny new paperweight!  Thanks again for your efforts and time.  Guess I can keep checking the forum for fixes.

---

### Post by zobayer1 on 2010-12-10
umm.... hello, I am new here.
I have also been using ubuntu for years in my old pc (really old)
It has:
AMD Athlon X-64 3400+
nVidia Fx5500
512 MB of ram
200GB Sata

Is this very poor for ubuntu 10.10 to be installed? I used upto 10.04 on it, but when I try to install it, it hangs at the step where it says "configuring hardware... ". Just to mention, it I could test it without installing. But it is creating problem when I try to install.

So, if this is a performance issue, my bad, I need to buy a new pc now.

---

### Post by greybeard62 on 2010-12-10
Uh, I don't recommend buying a new PC to run Ubuntu ---read the thread, new PC won't run Ubuntu, period.  There is no fix apparently for the new graphics chipset, Intel HM55, integrated.  This is the most common chipset sold right now in probably all the ultraportables or those machines with i core processors which do not have discrete graphics adapters.  So, be sure you check it out before buying a new machine for Ubuntu/any distro Linux.  A question to the manufacturer usually results in "our laptops are certified to run Windows 7", no discussion.  That said, hopefully a fix will be forthcoming soon, always has.  Been hanging around since 2006 running Ubuntu and this is the first bomb, also the first very new laptop I put Ubuntu on.  The processor was released in Nov 2010 so no kernel support for the chipset at this time.  You can also buy a laptop with a non-Intel discrete graphics adapter.  Now, thank the sky I backed up with Clonezilla because Rescue and Recovery won't work with an ext4 partition, gotta re-format the thing.

---

### Post by Quackers on 2010-12-10
> **greybeard62 said:**
> Uh, I don't recommend buying a new PC to run Ubuntu ---read the thread, new PC won't run Ubuntu, period.  There is no fix apparently for the new graphics chipset, Intel HM55, integrated.  This is the most common chipset sold right now in probably all the ultraportables or those machines with i core processors which do not have discrete graphics adapters.  So, be sure you check it out before buying a new machine for Ubuntu/any distro Linux.  A question to the manufacturer usually results in "our laptops are certified to run Windows 7", no discussion.  That said, hopefully a fix will be forthcoming soon, always has.  Been hanging around since 2006 running Ubuntu and this is the first bomb, also the first very new laptop I put Ubuntu on.  The processor was released in Nov 2010 so no kernel support for the chipset at this time.  You can also buy a laptop with a non-Intel discrete graphics adapter.  Now, thank the sky I backed up with Clonezilla because Rescue and Recovery won't work with an ext4 partition, gotta re-format the thing.

In all honesty, it is the graphics chipset that seems to be the problem.
Again, in all honesty, I think it's asking a bit too much of the developers to have a "fix" for a processor that's only been out for a month. I'm sure they are busy enough :-)
Integrated graphics were never the best at any time.

With regard to recovery it is always good policy to make the recovery dvd's, as problems can happen with recovery partitions. With recovery dvd's it wouldn't be a problem partitioning the drive.
Did you make the Windows repair cd? You may need that to repair Windows mbr after using the Clonezilla image.

It is also good practise to find these things out before making irrecoverable changes to any system.

---

### Post by greybeard62 on 2010-12-10
I agree with you on every point, hardly fair to expect the developers to be on top of this.  My response was for the poster to check what he is buying...his question was regarding buying a new PC for Ubuntu.  My response is still the same, the new graphics chipset is not supported.  My further response is, I did all the backups, R&R, Windows and did a Clonezilla which is always the best option because we need to change partition back.  MBR must be restored as well.

I fully expect the Intel HM55 to be supported because so many units are shipping with it now.  Integrated graphics works fine for probably 99% of the users out there today who are not gamers, not doing graphics design; we just don't need the extra horsepower so why spend the extra $$$$.  I can do everything I do normally, including GIMP, play movies, watch TV etc on my 8 yr old Toshiba, not discrete.  Like everyone I just wanted a new toy.  Not too much to expect Ubuntu to work on it and it is not a "non-standard" device by any means when surveying the market today.  So, we should not expect every laptop to have a discrete graphics adapter of a particular brand to function, nor should we denigrate the purchase of an integrated adapter which suits the functionality/purpose of the buyer.

The question and answer for those Ubuntu/Linux supporters is; don't be defensive, Windows 7 came with it, worked and had the drivers.  If Intel has provided the driver info then Ubuntu/Linux will provide them as well but that is the catch and the Windows market glory, they get it first, they sell it on every laptop made except Apple, then we throw it away when Ubuntu works.

The reason we don't have Apple is proprietary hardware and money.  They have OK stuff.  We want Ubuntu because of reliability, platform independence and readily available open source software.

And, BTW, the Rescue and Recovery DVDs do not work, boot into Windows, then stall, no options.  They did work before.  The screen is supported, drivers there.  I would never bet my lunch on R&R, use Clonezilla. image disk, lets you restore MBR.

---

### Post by Quackers on 2010-12-10
I take your points, on the whole.
However, remember Vista? What a shambles.

I am somewhat dismayed at your recovery dvd's not working. I have heard of it before, but I have had no such problems with mine.
I can literally do anything to my partitions and my recovery dvd's will always re-install Win 7 - using the whole disc, or even to just part of it.
Maybe I have just been lucky in that respect :-) It's always better to be lucky :-)

---

### Post by greybeard62 on 2010-12-10
Ha!  We digress from original issue but yes, Vista was the motivator for my conversion to Ubuntu.  I tried a lot of distros and found Ubuntu well supported, great forums and what a relief from Vista.  I'll never forget the Vista mess.  Thanks again for your help, I'll sit on this a while and keep checking back.

---

### Post by Quackers on 2010-12-10
You're welcome :-)
I hope you can run Ubuntu on your machine soon!

---

### Post by zobayer1 on 2010-12-10
So, for now, I would rather keep using 10.04 (this one also makes some trouble in display -- low refresh rate, painful for eyes, could not find a suitable driver for nVidia 5500 / 6200.
But it runs....

---

### Post by greybeard62 on 2010-12-11
Just a question please.  This is not a new problem, very common, you can see Bug #518938 as Sikander noted.  Now, to be helpful I don't know how to bump this since the bug page says only 10 users are impacted.  I'd guess more like 100,000 at least.  The issue is the Intel HM55 chipset which has been in production and shipping since late 2009 on almost every mfg laptop without discrete graphics, particularly the i-core processors.  I happen to have a new CPU, i5-470um which started hitting market in Nov 2010, but the issue is the Mobile Intel HM55 chipset which has graphics and all ports etc supported in one chipset.  Can some kind person refer all these graphics adapter issues including me to proper place to get the list updated so the developers aren't really thinking only 10 people are impacted?  There is another mirror bug on the HM 55 but the number above was posted Feb 2010, so this is not new problem.  I followed the fix instructions, even xorg-edgers, took a while.  Problem there, no xorg.conf file now, must create one, inept here on that process.  So, I don't know if I really got the newest driver up or not, tried the force at boot with no different results after all that work.  It appears the fix did work for some but not most.

Thanks

---

