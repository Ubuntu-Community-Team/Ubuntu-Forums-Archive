---
title: "Karmic sound problem?"
date: 2009-08-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by XKCD64 on 2009-08-03
I'm using Alpha 3.  I got sound perfectly fine a few days ago.  Now nothing.  My sound is up all the way and nothing....

---

### Post by phenest on 2009-08-03
We're gonna need to know a bit more about the hardware your using. Is it a desktop? Laptop? Make? Model? What sound card?

---

### Post by MTGap on 2009-08-03
Have you rebooted your computer recently? Sometimes I've had it just stop working out of the blue for no reason. Just restart your session it should hopefully be working again.

---

### Post by Rainstride on 2009-08-03
> **XKCD64 said:**
> I'm using Alpha 3.  I got sound perfectly fine a few days ago.  Now nothing.  My sound is up all the way and nothing....

i have the same problem.

go to the sound manager, click the hardware tab, select your hardware, make sure it has both input and output selected in the drop down menu.

if you don't see output as an option, open the system monitor and kill pulse. it should show you what you need it the drop down list now.

---

### Post by JohnJackson on 2009-08-03
Also make sure the volume is up for the particular application in the applications tab in sound preferences.

---

### Post by amano on 2009-08-03
Didn't Ubuntu return to testing the glitch free playback model? Reverting this to non-glitch free playback would be worth a try.

---

### Post by XKCD64 on 2009-08-03
My thanks to [Rainstride]("http://ubuntuforums.org/member.php?u=554611"), and [JohnJackson.]("http://ubuntuforums.org/member.php?u=529568")

It works now.  :)


And just an FYI, I didn't post my hardware information because I knew it was an ubuntu problem, because it works perfectly in my Windows 7 partion.

---

### Post by Regenweald on 2009-08-03
> **XKCD64 said:**
> 

And just an FYI, I didn't post my hardware information because I knew it was an ubuntu problem, because it works perfectly in my Windows 7 partion.

Knowing that it works in windows is of no consequence here. Other members ask about your hardware because each piece of hardware has issues specific to itself.

You could just have easily said my video doesn't work. Both Nvidia and ati have VERY separate issues in Linux. How could someone guide you if they don't know where to start?

FYI.

---

