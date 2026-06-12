---
title: "[SOLVED] Installation Help"
date: 2008-07-03
forum: Installation &amp; Upgrades
---

### Post by KILLER_K on 2008-07-03
First off let me thank you for joining the forums to ask my questions.

I just downloaded the Ubuntu 8.04 amd64 iso and burnt it to a cd. And rebooted and tried to install this os and i failed. So forgive me as this is my first ever attempt to use linux.

Here is my pc specs:
Q6600 @ Stock
Peltier cooling
G.Skill 4 gig pc6400
Raptor 10k sata hard drive {spare}
Nvidia 8600gt

I'm probably just overlooking something simple. Will a sata hard drive be fine? As this is a spare and my thoughts was to unplug my other hard drives run the linux on it and have it where i can hit a key to choose what hard drive to boot from.

Next i see some talk in here about a "standard" and a "advanced" cd? Did i perhaps get the wrong cd download? Sorry for all the questions but this is rather new to me at this time.

Almost forgot i do get to the part where the big "Ubuntu" screen comes up and the orange bar goes across but it locks at the beginning and does nothing else after that.

Good Day

---

### Post by Pumalite on 2008-07-03
At what stage did you fail and what error message did you get?

---

### Post by KILLER_K on 2008-07-03
That is just it no error the bar stops scrolling across and it just sits there. It is the screen right after you choose install and some text shows up at the bottom and the the big "Ubuntu" logo appears and it is trying to install.

I can take a few pics when i reboot it and show you if you need it.

Good Day

---

### Post by oldos2er on 2008-07-03
When the menu of the Livecd first comes up, run "Check cd for defects.'

---

### Post by Pumalite on 2008-07-03
Burn a new CD at 4x or less after doing md5sum on the iso. Clean the lens in your burner for good measure.

---

### Post by KILLER_K on 2008-07-03
Did that and the disc check out 100% fine. So i'm not sure what the issue is. How do i format this hard drive first then try to install the os? As i haven't seen a menu to do this with yet.

But i'm downloading both this time the "alternative" and the "desktop" one. So we will wait and see what happen now.

Good Day

---

### Post by KILLER_K on 2008-07-03
Same thing as before stops about 6 seconds after the "Ubuntu" logo comes on and the progress bar scans across about 3 times it stops on the 3rd ornage block.

Any other suggestions to try at this point?

Good Day

---

### Post by dodle on 2008-07-03
There is another iso you can download that has a text based installation.  Your computer is plenty fast enough to handle a graphical installation but maybe the other will work better for you.

---

### Post by Pumalite on 2008-07-03
Does the menu offer 'Safe Graphics Mode'?

---

### Post by KILLER_K on 2008-07-03
Yes, it does offer the "safe graphics mode" but all yeild same thing. Freezes after it starts installing.

Do i need to format it from ntfs to something else? As i see no options for this yet on the disc. Kind confussed why it isn't going all the way through. Perhaps a command line or something i need to use at the "f6" option.

Downloading the "standard text version" and will see what happens i feel lost at this point.


Good Day

---

### Post by Partyboi2 on 2008-07-04
To see at where it could be hanging at remove the splash screen.
When you are at the main menu screen press F6 and change the word ```
splash
``` to ```
nosplash 
``` then press enter.  Let us know where it stops at.

---

### Post by KILLER_K on 2008-07-04
Okay finally got it installed. From what i gathered the "live" isn't a install disc biut more less a try and mess nothing up deal. but i could be wrong.

Downloaded the "standard" all went in fine. Now where do i view my drivers , etc that i need for the os? Because i didn't see anything like device manager like windows has. Sorry to mention the windows but that is all i know.

Good Day

---

### Post by Sef on 2008-07-05
> Okay finally got it installed. From what i gathered the "live" isn't a install disc biut more less a try and mess nothing up deal. but i could be wrong.

It is an install disk too.  Sometimes the alternate cd will install where the Live CD fails to.

---

