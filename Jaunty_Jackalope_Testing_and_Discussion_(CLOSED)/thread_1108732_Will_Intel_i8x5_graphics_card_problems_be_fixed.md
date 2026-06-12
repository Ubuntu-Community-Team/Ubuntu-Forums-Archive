---
title: "Will Intel i8x5 graphics card problems be fixed?"
date: 2009-03-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by trot2millah on 2009-03-28
Since the first Alpha of Jaunty there have been major incompatibility problems with Intel i845, i865 etc. graphics cards that render Ubuntu unable to work normally.  I'm running the Jaunty beta on my laptop, and have Intrepid on my archaic desktop which has an i845 graphics card.  Will this bug get fixed in time?

---

### Post by chuckyp on 2009-03-28
I'm trying to install jaunty on a system where I disable the 845 onboard and put in an old ati rage xl. I'm getting kernel panics all over the place etc... The performance is just horrible on the 845 in jaunty. I was able to get it workign with some of the bug fixes but I couldn't handle the GL performance. I wish someone could fix the i8x5 cards in ubuntu would be nice.

---

### Post by trot2millah on 2009-03-28
> **chuckyp said:**
> I'm trying to install jaunty on a system where I disable the 845 onboard and put in an old ati rage xl. I'm getting kernel panics all over the place etc... The performance is just horrible on the 845 in jaunty. I was able to get it workign with some of the bug fixes but I couldn't handle the GL performance. I wish someone could fix the i8x5 cards in ubuntu would be nice.

Ya there are workarounds out there, unfortunately they are either too complicated for the average user (me), or the performance is so sluggish that it's not worth it in the first place.  I really hope this will get resolved, I love Jaunty and hope I can put it on my old machine which could use some faster boot times.

---

### Post by tjeremiah on 2009-03-28
Im wishing the same. With 8.10 there were minor problems but with 9.04, its just all over worst. Major screen tearing (for me) and jitters here and there. Im waiting for the final release of 9.04 to do anything. (downgrade?)

---

### Post by exXP on 2009-03-28
> **chuckyp said:**
> I'm trying to install jaunty on a system where I disable the 845 onboard and put in an old ati rage xl. I'm getting kernel panics all over the place etc... The performance is just horrible on the 845 in jaunty. I was able to get it workign with some of the bug fixes but I couldn't handle the GL performance. I wish someone could fix the i8x5 cards in ubuntu would be nice.

I also have an Intel 845 motherboard but have had no problems with Jaunty Beta.  In the past, I've had to get into menu.lst and change a few things but not this time. After having considerable trouble with 845 graphics with Fedora 10 and PCLinusOS2009 and getting nowhere, this comes as a welcome relief.
exXP (and not going back)

---

### Post by trot2millah on 2009-03-28
> **exXP said:**
> I also have an Intel 845 motherboard but have had no problems with Jaunty Beta.  In the past, I've had to get into menu.lst and change a few things but not this time. After having considerable trouble with 845 graphics with Fedora 10 and PCLinusOS2009 and getting nowhere, this comes as a welcome relief.
exXP (and not going back)

Interesting....so the Jaunty Beta just worked for you?  Did you have previous versions of Jaunty before you got the beta?  If I hear that this is a non-issue anymore than I will upgrade the computer, but I was highly worried about all the X failures and such that I was hearing.

---

### Post by amac777 on 2009-03-29
I've got the i845, I just installed the beta and updated all the new components and I'm still not able to startx without doing one of the bug fixes in xorg.conf (Option "DRI" "False"), which gives me the screen at full resolution 1400x1050 but doesn't allow me to watch videos..... :(

---

### Post by amac777 on 2009-03-29
> **amac777 said:**
> I've got the i845, I just installed the beta and updated all the new components and I'm still not able to startx without doing one of the bug fixes in xorg.conf (Option "DRI" "False"), which gives me the screen at full resolution 1400x1050 but doesn't allow me to watch videos..... :(

Ok, after a little more reading the bug reports and trying out the various fixes, I found the best work-around is this in xorg.conf:

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"Intel"
	Option		"Legacy3D"	"false"
EndSection
```

With this, I get 2D at full resolution and video all working acceptably. 3D / compiz still doesn't work but I can live without that for now.

for the record, lspci shows:
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)

---

### Post by exploder on 2009-03-29
Here is my Intel integrated graphics.

00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)

I filed the bug report. The first fix gets youtube to work in full screen but Hulu is choppy in full screen and nearly cripples Firefox. DVD playback is a real struggle too. I hope the Developer's come up with a fix for this.

---

### Post by exXP on 2009-03-29
> **trot2millah said:**
> Interesting....so the Jaunty Beta just worked for you?  Did you have previous versions of Jaunty before you got the beta?  If I hear that this is a non-issue anymore than I will upgrade the computer, but I was highly worried about all the X failures and such that I was hearing.

I downloaded the LiveCD to check that it would work. As I mentioned I did the same thing with Fedora10 and PCLinuxOX2009 but could not get past the log-in stage on either one. I'm not about to install a distro if I can't get the LiveCD to work.  On 8.10 I had some trouble with Compiz being set to ON on the LiveCD but somebody in this forum published a work-around. 
Jaunty Beta came up straight away in the right screen resolution and, while there are minor problems, things are mostly working well.
I have the 845GL chipset with a 1.6GHz Pentium 4, 1.5GB of RAM.

exXP (and not going back)

---

### Post by Kareeser on 2009-03-29
Full screen youtube problems aren't always due to the open source intel driver

See here: [http://blogs.adobe.com/penguin.swf/2008/08/secrets_of_the_mmscfg_file_1.html](http://blogs.adobe.com/penguin.swf/2008/08/secrets_of_the_mmscfg_file_1.html)

---

### Post by tjeremiah on 2009-03-29
I tried all of that and none work. Maybe if I was in 8.10 things will be better.But it has something to do with this beta thats making things worst. How do I report a bug about my specfic intel card?

---

### Post by killerguy on 2009-04-10
****This will never be fix it started in 8.10 they doing this to get high end computers to work right with ubuntu and low ends are left out it be best to get a new distro that works or stick with 8.04 until they stop supporting it

---

### Post by castrojo on 2009-04-10
> **tjeremiah said:**
> I tried all of that and none work. Maybe if I was in 8.10 things will be better.But it has something to do with this beta thats making things worst. How do I report a bug about my specfic intel card?

[https://wiki.ubuntu.com/X/Reporting](https://wiki.ubuntu.com/X/Reporting)

---

### Post by tjeremiah on 2009-04-10
> **whiprush said:**
> [https://wiki.ubuntu.com/X/Reporting](https://wiki.ubuntu.com/X/Reporting)
thanks.

---

### Post by Kareeser on 2009-04-10
My Intel 8x5 card has been working great since the second week of the Beta. Give it a try.

---

### Post by volneilo on 2009-04-15
**Kareeser** and **exXP**, did you get Compiz to work in your i845 cards? This is the only thing that prevents me to upgrade to Jaunty yet. My Jaunty Beta LiveUsb boots ok, but Compiz refuses to work (as it was in Intrepid)...

---

