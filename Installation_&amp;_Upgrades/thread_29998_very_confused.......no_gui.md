---
title: "very confused.......no gui???"
date: 2005-04-26
forum: Installation &amp; Upgrades
---

### Post by wolfesidhe on 2005-04-26
I'm not even sure if that's what I should call it.          I just installed (or maybe it only installed partially) ubuntu today. It doesn't boot into a gui, I just get the prompt to put in user name and password and then I get prompted for a command?     All this after having to try 6 different cds (shipped not burned) before I got one that wouldn't get stuck at all.      Did I do something wrong?          It's version 4.10           

Any help is greatly appreciated

Thank you

---

### Post by nad on 2005-04-26
I can only suggest that the cd drive may be dirty.

Did you get any live cd's with your order? Do they work in your computer?

Version 4.10, warty, was a fine release. Very stable. You shouldn't be having these problems unless it is hardware related or you found a bad batch of pressed disks.

---

### Post by wolfesidhe on 2005-04-26
[QUOTE=nad]I can only suggest that the cd drive may be dirty.

Did you get any live cd's with your order? Do they work in your computer?

Version 4.10, warty, was a fine release. Very stable. You shouldn't be having these problems unless it is hardware related or you found a bad batch of pressed disks.[/QUOTE]


I got live cd's with the order. There was only one that didnt' work at all, but the others I tried worked.  I take it this means I have to try and reinstall? 

Thank you

---

### Post by nad on 2005-04-26
The graphics system appears to have not set up automatically. Is this a laptop by any chance?

I would try cleaning the inside of the cd drive. Blowing in it with your mouth isn't the best way, but if that is your only choice, go for it. Then try a reinstall. Unless you would like to try some command line diagnostics. Please advise. I am here for the evening.

Please post your machine specifics if you continue to have problems.

---

### Post by az on 2005-04-26
At the prompt, do

sudo apt-get -f install


and if that yields no help, try

sudo apt-get install ubuntu-desktop

and hang on!

you either installed the custom version or it did not finish the installation.

---

### Post by wolfesidhe on 2005-04-26
[QUOTE=nad]The graphics system appears to have not set up automatically. Is this a laptop by any chance?

I would try cleaning the inside of the cd drive. Blowing in it with your mouth isn't the best way, but if that is your only choice, go for it. Then try a reinstall. Unless you would like to try some command line diagnostics. Please advise. I am here for the evening.

Please post your machine specifics if you continue to have problems.[/QUOTE]


Thank you      I will have to try that, although I did also try with 2 seperate cd drives. 

I have canned air, so will use that.

---

### Post by wolfesidhe on 2005-04-26
[QUOTE=azz]At the prompt, do

sudo apt-get -f install


and if that yields no help, try

sudo apt-get install ubuntu-desktop

and hang on!

you either installed the custom version or it did not finish the installation.[/QUOTE]

I like your idea better than having to sit through another install again lol.     I'm going to print that out and try it tonight. If that doesn't work, I'll try the reinstall thing

thank you :)

---

