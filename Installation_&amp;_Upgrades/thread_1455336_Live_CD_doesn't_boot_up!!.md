---
title: "Live CD doesn't boot up!!"
date: 2010-04-15
forum: Installation &amp; Upgrades
---

### Post by TheNerdAL on 2010-04-15
When I boot my computer, It boots up but stays on the Compaq logo for a few seconds and then goes into my HDD drive boot and not my liveCD, I have my CD Group first in BIOS, help!

---

### Post by earthpigg on 2010-04-15
lots of possibilities. 

will that LiveCD boot with other computers?

will different LiveCDs boot on that computer?

---

### Post by Xeneth on 2010-04-16
I know My computer requires a button to be pressed to boot from CD.  Maybe like that?

---

### Post by la3875 on 2010-04-16
Need a little more info. I found the Lucid beta will burn the image to a CD but will not run. When I burn the same image on a DVD, the live disk works...

---

### Post by TheNerdAL on 2010-04-16
> **Xeneth said:**
> I know My computer requires a button to be pressed to boot from CD.  Maybe like that?

I pressed ESC and I put my CD Drive to boot up first and still nothing. :(

---

### Post by TheNerdAL on 2010-04-16
I think it's my Optical drive, but I don't know!

---

### Post by TheNerdAL on 2010-04-16
Anyone?

---

### Post by TheNerdAL on 2010-04-16
Okay so I got to the part where I can check for defects. The Ubuntu Logo comes up but nothing happens. I press ESC and I get this:
```
stdin: error 0
stdin: I/O error
```

---

### Post by TheNerdAL on 2010-04-17
*bump*

---

### Post by earthpigg on 2010-04-17
> **earthpigg said:**
> lots of possibilities. 

will that LiveCD boot with other computers?

will different LiveCDs boot on that computer?

?

---

### Post by la3875 on 2010-04-17
*[I]> **la3875 said:**
> Need a little more info. I found the Lucid beta will burn the image to a CD but will not run. When I burn the same image on a DVD, the live disk works...*[/I]

Are you burning the image to CD or DVD. Might also be the burn quality? Try burning at a lower speed than max.

---

### Post by TheNerdAL on 2010-04-17
> **earthpigg said:**
> lots of possibilities. 

will that LiveCD boot with other computers?

will different LiveCDs boot on that computer?

The Live cd booted with my sister's laptop but rebooted when I left the room which was wierd. O.o And for different CD's I only burned a 9.10 one and a 10.04 beta 2 one and both didn't boot that well. 

They booted but when I check for defects it doesn't work.

---

### Post by TheNerdAL on 2010-04-17
> **la3875 said:**
> *[I]*[/I]

Are you burning the image to CD or DVD. Might also be the burn quality? Try burning at a lower speed than max.

CD and I burned it at 8X using K3B

---

### Post by TheNerdAL on 2010-04-17
Should I attempt another burn but with a lower speed? K3B's lowest speed possible is 8X though.

---

### Post by TheNerdAL on 2010-04-17
What is the lowest speed I can go and what is a good program that I can use with that speed? Thanks!

---

### Post by TheNerdAL on 2010-04-17
Well, I tried 4x and it booted up okay and had no errors but it said that file system could not be mounted or something like that, help!

EDIT: MD5SUM is good.

---

### Post by wilee-nilee on 2010-04-17
> **TheNerdAL said:**
> 
.

Noticing your signature, watch Song of the South again and recognize that the Brier stories are twice removed stories from the plantation, and guess who the bad guys were in the real version. Then try and figure out if it is a pre or post 1865 representation.

---

### Post by TheNerdAL on 2010-04-17
> **wilee-nilee said:**
> Noticing your signature, watch Song of the South again and recognize that the Brier stories are twice removed stories from the plantation, and guess who the bad guys were in the real version. Then try and figure out if it is a pre or post 1865 representation.

?

---

### Post by TheNerdAL on 2010-04-17
I burned a new cd at 1x and checked everything, which was good. But when I click install, it just freezes and has a black screen with a white underscore! Help!

---

### Post by oldos2er on 2010-04-17
What are your system specs?

---

### Post by TheNerdAL on 2010-04-17
> **oldos2er said:**
> What are your system specs?

I used a LiveCD that I got from Shipit and it was Kubuntu 10.04 and it installed okay. I am on Kubuntu right now. So Could it be just the CD?

---

### Post by cK` on 2010-04-17
I have a similar problem, my cd will begin to boot up but right before the installion screen comes up i get a "unrecoverable error" and it restarts my computer. Tried reburing it and using the 64bit version but same problem.

I guess i have to upgrade from 9.10 to get it to work.

---

### Post by TheNerdAL on 2010-04-17
I have an update, I can run Ubuntu off the cd perfectly! I might be able to install it by clicking the Icon on the desktop hopefully, I will update if it works.

---

### Post by TheNerdAL on 2010-04-17
It doesn't work. :(

---

### Post by eltonw on 2010-04-17
> **TheNerdAL said:**
> When I boot my computer, It boots up but stays on the Compaq logo for a few seconds and then goes into my HDD drive boot and not my liveCD, I have my CD Group first in BIOS, help!

It's possible that you may have burned the ISO to the CD or DVD as a single data file. Load the disk and have a look:confused: at the contents. It should show a few text files and several directories, If not, you did not use the right option when burning the ISO to the laser disk. 

*[COLOR="Sienna"]You should **NOT** see a single file ***.iso on the CD / DVD disk.[/COLOR]* .. and YES, if the iso image was properly extracted, you should be able to boot [FONT="Comic Sans MS"]... CD or DVD doesn't matter ... as long as the disk _has sufficient capacit_y[/FONT]. You can even use RE-writable media, if you only want to try out the distro,

HTH...

---

### Post by eltonw on 2010-04-17
> **cK` said:**
> I have a similar problem, my cd will begin to boot up but right before the installion screen comes up i get a "unrecoverable error" and it restarts my computer. Tried reburing it and using the 64bit version but same problem.

I guess i have to upgrade from 9.10 to get it to work.
...sounds like a dirty or scratched disk. You can try carefully cleaning the disk, with a soft cloth, OR do a new burn with a different disk.

HTH,

---

### Post by TheNerdAL on 2010-04-17
I'm doing a new burn on a different computer. <.< Hopefully it works.

---

### Post by TheNerdAL on 2010-04-17
Even the cd I burned on the laptop doesn't work! :( WHAT IS THE PROBLEM?!
 
EDIT: It works but let's just see if it works through everything.

---

### Post by oldos2er on 2010-04-17
> **TheNerdAL said:**
> I used a LiveCD that I got from Shipit and it was Kubuntu 10.04 and it installed okay. I am on Kubuntu right now. So Could it be just the CD?

Um, no I'm asking about your computer's specs, i.e. CPU, RAM, video card, motherboard, etc.

---

### Post by TheNerdAL on 2010-04-18
> **oldos2er said:**
> Um, no I'm asking about your computer's specs, i.e. CPU, RAM, video card, motherboard, etc.

I have no idea, I'm getting mad!

---

### Post by TheNerdAL on 2010-04-18
I think it's my optical drive that is the problem but it worked one time perfectly!! :(

---

### Post by TheNerdAL on 2010-04-18
Now I'm getting the logo only and caps lock and scroll lock lights are blinking.

---

