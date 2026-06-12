---
title: "VERY dark screen Ubuntu 11.10"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by M. Amin on 2011-10-14
Hi,
When I try Ubuntu 11.10 on a USB I get a very dark or dimmed screen, so dark that I thought it's turned off. After looking carefully at the screen I found that it's displaying this picture
[IMG]http://www.ubuntu.com/sites/www.ubuntu.com/files/active/try-intsall.jpg[/IMG]
but as I said.. VERY dark.. and I dunno what to do with it.

---

### Post by MAFoElffen on 2011-10-14
> **M. Amin said:**
> Hi,
When I try Ubuntu 11.10 on a USB I get a very dark or dimmed screen, so dark that I thought it's turned off. After looking carefully at the screen I found that it's displaying this picture
[IMG]http://www.ubuntu.com/sites/www.ubuntu.com/files/active/try-intsall.jpg[/IMG]
but as I said.. VERY dark.. and I dunno what to do with it.
Is it a laptop? What make and model?  I'm wondering if it just is not turning on the back-light... There is a bootup option for that if it is:
[]("http://ubuntuforums.org/showpost.php?p=10757555&postcount=10")[http://ubuntuforums.org/showpost.php?p=10757555&postcount=10](http://ubuntuforums.org/showpost.php?p=10757555&postcount=10)

---

### Post by M. Amin on 2011-10-15
Laptop HP G62. And I can't even open the terminal to do what's in the link you put there. I can't do anything with it it's completely dark.. I could hardly see what was there.

---

### Post by MAFoElffen on 2011-10-15
> **M. Amin said:**
> Laptop HP G62. And I can't even open the terminal to do what's in the link you put there. I can't do anything with it it's completely dark.. I could hardly see what was there.
Boot the LiveCD. The first screen will be black with a keyboard/person icon (input). Press esc. A screen asking for keyboard type will appear. Press escape or enter (each both end up as US.) You will be at the "Advance Installation" screen.  Press <F6>, a dropdown boot options menu will appear. Arrow down to "nomodeset". Press the shiftbar to select. Pre Escape to close that menu, retaining the selected options. Select "Try".

See if that works...  The option I gave you was a workaround that works "after" the system is installed.  You are still trying... and having that problem on the LiveCD.  :embarrassed:

---

### Post by bslayers on 2011-10-15
After updating to 11.10 my laptop screen will darken, I can still barely see the screen but have to restart the laptop. I did not have this problem prior to the update. I also do not have a left hand side bar. All I have across the top of the left screen is "File Edit View Go Bookmarks Help" nothing else.

---

### Post by M. Amin on 2011-10-15
Thanks a lot for your help. But as you said, this can be done "after" it's installed already.. so.. is there any other way?

---

### Post by MAFoElffen on 2011-10-15
> **M. Amin said:**
> Thanks a lot for your help. But as you said, this can be done "after" it's installed already.. so.. is there any other way?
Post #2 is after the install. Post #4 is with the LiveCD before/during the install.  One more option would be to install from the Alternate Install CD. It is all text based, so it might act differently (backlight-wise) being its in a different graphics mode.

---

### Post by M. Amin on 2011-10-15
Finally! Thank you!
I didn't install it yet I'm just trying it from the USB. Can I ask you what did that change exactly? And will I be able to install 11.10 and work on it normally like any other? Or that "nomodeset' thing was a compromise?

---

### Post by MAFoElffen on 2011-10-16
> **M. Amin said:**
> Finally! Thank you!
I didn't install it yet I'm just trying it from the USB. Can I ask you what did that change exactly? And will I be able to install 11.10 and work on it normally like any other? Or that "nomodeset' thing was a compromise?
"nomodeset" is usually a kernel mode switch to tell nvidia chipsets to use a VESA mode... On bugs at launchpad it was found that in some laptops having problems with the backlight not working propery using the LiveCD, that casper/isolinux was misidentifying the video hardware as nvidia when they weren't... and the "nomodeset" kernel boot option was correcting that.

---

### Post by M. Amin on 2011-10-16
Wow! :D I'm really thankful for your help but I didn't get much of that.. sorry :D
So will I be able to just use it fine?

---

### Post by MAFoElffen on 2011-10-16
> **M. Amin said:**
> Wow! :D I'm really thankful for your help but I didn't get much of that.. sorry :D
So will I be able to just use it fine?
Please try it and see if it works out for you.

---

### Post by M. Amin on 2011-10-16
Thanks a lot. I really appreciate it.

---

### Post by M. Amin on 2011-10-17
Ok I installed 11.10.. but I still get the dark screen! but when I choose the recovery mode it works.
Is there a way to fix that?

---

### Post by YrrchSebor on 2011-10-17
hi, this is my first post in Ubuntu Forums :). i am having the dark screen problem with 11.10 on my Acer Aspire 5336, but the nomodeset fix works great. my question is, is it safe and ok to set the computer to permanently run like this? when i go to 'additional drivers', nothing shows up as available, and i read somewhere to try installing nvidia drivers, but that didn't help. i have searched so many things with no real luck, trying to find a different solution. can i just edit GRUB to keep the nomodeset setting? thanks in advance for any help.

---

### Post by M. Amin on 2011-10-18
bump

---

### Post by MAFoElffen on 2011-10-18
> **M. Amin said:**
> Ok I installed 11.10.. but I still get the dark screen! but when I choose the recovery mode it works.
Is there a way to fix that?
Steps:
1) edit rc.local
     ```

gksudo gedit /etc/rc.local

```2) Add the command before EXIT 0
```

setpci -s 00:02.0 F4.B=00

```Save and exit

3) Restart.

---

### Post by M. Amin on 2011-10-19
Still the same problem

---

### Post by M. Amin on 2011-10-19
Bump

---

### Post by M. Amin on 2011-10-20
Bump again..

---

### Post by MAFoElffen on 2011-10-20
> **M. Amin said:**
> Bump again..
Did you add the line I gave you back from Post 16 into /etc/rc.local?  I gave you instructions for that as you said you installed, still had problem, but could get in through recovery mode.

That is the "only" consistent working work-around that I know of for that...

---

### Post by M. Amin on 2011-10-21
Yea I did exactly what you said in post #16.. Thanks for your help anyway

---

### Post by MAFoElffen on 2011-10-21
There are a few more to try... Did you try "nomodeset" as a kernel boot option?  Did you try "i915.modeset=0"?  Did you try "acpi_osi=linux"?

---

### Post by M. Amin on 2011-10-21
Well I dunno how to do any of this..

---

### Post by M. Amin on 2011-10-21
Bump

---

### Post by MAFoElffen on 2011-10-21
> **M. Amin said:**
> Well I dunno how to do any of this..
Just got back home.

First- Do you have function key hot keys on your keyboard that dim and brighten your screen?  I had a user last night that told me his that those hot-keys for his laptop's keyboard somehow was "reversed"... not just that, but the whole function of his dim/bright was backward.  Seems its supposed to start in the brightest mode (his started in the dimmest mode).  To toggle brighter, his hot-key used to be <fn><left arrow>, now its <fn><right arrow>.  To toggle brighter, his hot-key was <fn><right arrow>, now its <fn><left arrow>.  Make sense?  (mine has these keys, but has never worked with any version of Linux nor Unix... But worth a try.

On temporarily adding modesets during boot time:

Note: You may need a flashlight or attached monitor to see this if the above didn't relate to you...

Boot. At end of BIOS Messages, hold down shift key. > Grub Menu should display > Press "e" to get into an edit mode. > Arrow down to the line that begins with "linux" > Arrow right to the section of that line between where it says "quiet splash" and before "vt.handoff=7" > Insert "i915.modeset=0 acpi_osi=linux". Try both first, then try 1 at a time later on a later attempt to narrow it down.> Press <cntrl><x> to boot.

Tell me how it goes.  I should be on tonight for about 3 or 4 hours more.

---

### Post by M. Amin on 2011-10-23
Sorry for being late. I don't have hot keys for screen brightness. In  fact, I can't even find a way to do it with 11.10 running already. 
I tried the other method, adding that line in the Grub menu. It worked  but it's not saved, I have to do it every time I use my laptop. And in  all cases, I can't adjust the resolution of the screen, nor its  brightness.

---

### Post by M. Amin on 2011-10-24
Oh and guess what.. 11.10 can't see my other monitor when I attached it to my laptop.
So, I can't adjust the resolution, I can't adjust the brightness of the screen and my external monitor does not work on 11.10!
Clearly there's something wrong with 11.10 and my graphics.

---

### Post by MAFoElffen on 2011-10-24
> **M. Amin said:**
> Sorry for being late. I don't have hot keys for screen brightness. In  fact, I can't even find a way to do it with 11.10 running already. 
I tried the other method, adding that line in the Grub menu. It worked  but it's not saved, I have to do it every time I use my laptop. And in  all cases, I can't adjust the resolution of the screen, nor its  brightness.
Look at Post 1 of my sticky:
**[B]Sticky:**[/B] 			                         [COLOR=#008C00]**[all variants]**[/COLOR] 			 			[Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535")

Look under the title "**Now that I found something that works, how do I make it permanent?**"

---

### Post by kimutsuchi on 2012-02-10
Is this problem solved yet?
Hi, I'm new here, and I experienced what the topic starter has gone through. I have an Acer Aspire 4736Z laptop. I searched everywhere for a solution but I got nothing. I tried everything that is suggested here but it seems the real problem is with my laptop. Recently, I noticed that when I set my laptop's brightness to its highest before rebooting, when booting in Ubuntu 11.10 from a flash drive, the screen goes very dark. But when I set it to lowest (or any other than the brightest), booting is fine.

I just wanna share what I found out, because it might be the same for you. :) Hope I helped somehow.

---

### Post by Doug11 on 2012-03-30
> **MAFoElffen said:**
> Boot the LiveCD. The first screen will be black with a keyboard/person icon (input). Press esc. A screen asking for keyboard type will appear. Press escape or enter (each both end up as US.) You will be at the "Advance Installation" screen.  Press <F6>, a dropdown boot options menu will appear. Arrow down to "nomodeset". Press the shiftbar to select. Pre Escape to close that menu, retaining the selected options. Select "Try".

See if that works...  The option I gave you was a workaround that works "after" the system is installed.  You are still trying... and having that problem on the LiveCD.  :embarrassed:

This worked for me for the install. Now just to get it permanent. Thanks

---

