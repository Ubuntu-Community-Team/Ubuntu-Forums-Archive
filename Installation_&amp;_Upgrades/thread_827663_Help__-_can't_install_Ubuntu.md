---
title: "Help  - can't install Ubuntu"
date: 2008-06-13
forum: Installation &amp; Upgrades
---

### Post by ranchero on 2008-06-13
I'm new to Ubuntu. Trying to install it on my new system - it shows the installation bar and then hangs at approximately 75-80% :(

AMD 6000+, Crosshair, 2GB RAM, 80GB SATA HDD, ATI All-in-Wonder. No Raid or any other special stuff.


 Ubuntu downloaded CD, 7.10, CD check shows no errors.


Update:
Once I've just got error message along with other stuff on the screen:

"error receiving uevent message: no buffer space avalable."

---

### Post by Avenger1432 on 2008-06-13
try to start live cd in recovery mode..i dont remember in 7.10 but should be a verbose option or recovery or diagnostic mode.  should give you some messages as to the reason it may be freezing.

---

### Post by ranchero on 2008-06-13
It only shows option "start in safe graphics mode" I'll try it right now.
...exact same thig :( - bar stops under letter N in "UBUNTU".

Worst of all, I've installed XP day before without any problems in 10 mins :(
(Now there's another HDD, it's empty)

---

### Post by Avenger1432 on 2008-06-13
no there should be another option like when you are about press start or install ubuntu.. should be something on the  bottom of the screen with boot options..

---

### Post by Avenger1432 on 2008-06-13
when you do find that...  if you have a digital camera try uploading a picture of that to this thread.

or maybe someone else has a better idea, idk.  its not like you can go fetch a log you havent even installed the system.. there is no way to get the logs.  so try to write down what you see on the screen when the diagnostics show...  and write them down here...  or use a dig. camera

---

### Post by ranchero on 2008-06-13
The other thing I have F6, when I press it some kind of command line appears:

"Boot options t=casper initrd=casper/initrd.gz quiet splash--|"

---

### Post by Avenger1432 on 2008-06-13
or try this... when you have   "start or install ubuntu" selected  if you see a bunch of stuff written on the bottom of the screen  edit that after you see  "Quiet Splash"  add  "-v" after it.  I am not sure if that is it but try anyways.

---

### Post by Avenger1432 on 2008-06-13
> **ranchero said:**
> The other thing I have F6, when I press it some kind of command line appears:

"Boot options t=casper initrd=casper/initrd.gz quiet splash--|"
  

yes try to add    -v after that command. if that doesnt work... delete   quiet splash--| all together and replace it with "-v"  not sure this will work however  im not an expert on this..   just trying to help best i can... hopefully someone who really knows their stuff will help.

---

### Post by ranchero on 2008-06-13
I pressed F6 and removed "quiet splash" and I've got this

---

### Post by Avenger1432 on 2008-06-13
ya unknown boot option...  did you try the "-v"?  other than that I don't know.


Sorry,  I hope someone else comes along to help...  but i gotta go,  gl

---

### Post by ranchero on 2008-06-13
Thanks anyway.

Here's result with  "-v" (it showed many errors when was running as far as I could see :), here's final screen when it stopped)

---

### Post by Avenger1432 on 2008-06-13
aha better results it looks like... well thats all i know i just wanted you to post something that some expert on ubuntu can look at and analyze and hopefully come up with a conclusion... 


anyways, peace out  I hope you get it working..

---

### Post by ranchero on 2008-06-13
Anyone? Should I go back to Windows?
BTW, I've downloaded CD one more time - file "ubuntu-7.10-alternate-amd64.iso", burned it, same thing, hangs.

---

### Post by Avenger1432 on 2008-06-13
try the 32 bit.. not 64 bit...  you dont have over 3 gigs of ram... you dont need the 64 bit.


But other than that, where the heck is the ubuntu support community!!!  Same thing is happening with my thread in general help.


Where is the support community?!



P.S.  also try the normal not Alternate CD...

---

### Post by avtolle on 2008-06-13
Since you are using 7.10, press F6, and at the end of that boot line add the parameter all-generic-ide then continue.

---

### Post by ranchero on 2008-06-13
It started wit "all-generic-ide", but there's no applications, nothing, just wallpaper, and when I was trying to change wallpaper, system hang... Second time it didn't start at all, just hang angain...

---

### Post by ktechman on 2008-06-13
Try reburning the cd in 1x mode it worked for me.

Cheers

---

### Post by ranchero on 2008-06-13
Here's last time I tryed it yesterday and just now, with "all-generic-ide"

---

### Post by avtolle on 2008-06-13
I am aware that 7.10 had a problem with correct handling of ide drives (I know you are not using ppc, but we had to do something similar on that platform to get things to boot). Are you using the Live CD or the alternate one?

---

### Post by avtolle on 2008-06-13
8.04 took care of the ide problem, BTW. Is there a good reason that you are trying 7.10 instead?

---

### Post by ranchero on 2008-06-13
Well, people say 8.04 has too many glitches yet, but it looks like 7.10 not any better...Very sad, I was so hoping to ged rid of POS XP, but looks like I'll have to stay with it...

I'm using alternate CD right now, yesterday it was live CD, I think (I downloaded it few months ago).

---

### Post by avtolle on 2008-06-13
Understand what you are saying. If you can get 7.10 installed, there are many updates and fixes around. For me, 8.04 has proven to be much more trouble free than 7.10 was.

---

### Post by ranchero on 2008-06-13
So, no any other suggestions?..

---

### Post by avtolle on 2008-06-13
Glancing at your system specs, something which is likely causing some problems on 7.10 install and may cause a problem on an 8.04 install is the SATA drive set up. That's why (among other things, including the IDE detection problem) I suggested the boot parameter. From reading one of your earlier posts, as I understand it, when you tried that again on a restart, it didn't work.  I will suggest that after restarting the computer, that you do try rebooting with the "all-generic-ide" boot parameter one more time to see whether it gets you into the installation routine. I'll ponder a bit, and post with any other thoughts that may occur.

EDIT: If you get it up to the desktop again, don't try to change the wallpaper, etc., until you download and install all upgrades into your system. That may clear some things up.

---

### Post by ranchero on 2008-06-13
I've disconnedted HDD and trying to run it with "all-generic-ide" but still no success...

---

### Post by Pumalite on 2008-06-13
Tyr any of these alone or in different combinations:
noapic nolapic acpi=off pci=noacpi irqpoll pnpbios=off vga=0x317

---

### Post by ranchero on 2008-06-13
Wow! I've downloaded 8.04, and it run right away!
I've even burned iso on DVD-RW, not on CD.
Anyway, even wireless was recognized instantly and connected.
But all I have - blank desktop, what should I do next? How I download updates and install programs?

Should I install Ubuntu first? (Right now it's running as liveCD)

---

### Post by ranchero on 2008-06-13
Update - I've pushed "Help" and it hang again :( What the f.

Could that be because system was a little overclocked (5%, it was flawless in XP)?
I've run it second time not overclocked - now Help opens, but I don't know, what glitch to expect next ...

---

### Post by ranchero on 2008-06-13
Well, it was nice try, but I think this thig's just useless for average user right now...After an hour of trying to do SOMETHING I figured that part of the desktop with buttons wasn't even on the screen with default resolution! Somehow I managed to download and install video drivers and to change resolution to 1152x864, than system became slow as Pentium 2! And after restart it changes settings so desktop is not aligned on the screen again... I guess the whole thing just too good to be true.

---

### Post by Avenger1432 on 2008-06-15
Good to see it worked...  kind of...

---

### Post by Pumalite on 2008-06-15
Yeah...I was sure the OP was ranchero.

---

