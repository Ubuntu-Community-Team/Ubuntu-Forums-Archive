---
title: "Mysteries of kubuntu installation (reloaded)"
date: 2006-04-15
forum: Installation &amp; Upgrades
---

### Post by dglp on 2006-04-15
I have managed to get Kubuntu 5.10 *[COLOR="Magenta"]almost[/COLOR] *successfully installed. But there are several mystery elements that crop up at one time or another. I will share them with you, in reverse chronology. 

1. [IMG]http://nunovo.zoto.com/img/45/a50dc89221a806e9a6ae2f250088223b-.jpg[/IMG]

The text alternates between 'Configuring the basic system...' and 'Info: switching console charset mapping to C'. It's been doing this for over an hour now. 

2. [IMG]http://nunovo.zoto.com/img/45/76bdf989facadd7578255c0665863b2d-.jpg[/IMG]

This one is very interesting, but I haven't a clue as to what it's about. I thought I was supposed to be seeing a GUI after I installed Kubuntu, not a command line. I haven't bothered to look for a glossary of commands, but suppose that there's one out there somewhere.

3. [IMG]http://nunovo.zoto.com/img/45/c94acbfdb538f0bff3475dd4a059aea9-.jpg[/IMG]

This one was stuck in a loop until I forced the installation to finish. It asked for account name, username and password repeatedly. Wouldn't stop asking. Did I mention that it kept repeating the request for account name, username, and password? Repeatedly?

4. [IMG]http://nunovo.zoto.com/img/45/6a6eb5e6e84f684e117b1d25b18f8ce6-.jpg[/IMG]

Lest you think it was all a mess, here's evidence that some things worked as expected.

5. [IMG]http://nunovo.zoto.com/img/45/092bc865ecd1b46e95df4348bb48ec93-.jpg[/IMG]

This one was from the 'live' CD, which I ran before trying to do the full installation. The thing works, fundamentally. From CD, that is.

6. [IMG]http://nunovo.zoto.com/img/45/0e289df7f113935efcf265e0ef200490-.jpg[/IMG]

Here's another interesting one. Don't know that it has any bearing on the other stuff, but it doesn't come up every time I run the installation. My recollection is that it only came up once. But I've done so many iterations now that I cannot recall exactly what came up when. 

There are one or two other examples of mysterious failures, but they're similar to ones I've shown above. Out of all this, all I know is that the installations are very nearly successful. But not quite. 

There are more snaps here, if you're interested in following the sequence of events: [http://nunovo.zoto.com/user/lightbox/CAT.222/average_rating-desc/0-30](http://nunovo.zoto.com/user/lightbox/CAT.222/average_rating-desc/0-30)

---

### Post by Kapre on 2006-04-16
dglp - you are correct that the install did not go through (not all files were copied). Can you try using a LiveCd and check on the settings that its using. Post again.

K

---

### Post by dglp on 2006-04-16
Hi Kapre, thanks for the response. Are there any particular settings that you want me to look at, and/or compare? 

The Live CD has worked every time I've tried it. The installation fails every time - and that's probably around twelve times since yesterday.

David

PS: Most recent effort made it all the way through the CD-based installation, but failed on the subsequent restart.

[IMG]http://nunovo.zoto.com/img/45/5ae40b47f0f22032e51cf44aa609356f-.jpg[/IMG]

No copying errors, no repetitions of prompts, everything ran to spec.

[IMG]http://nunovo.zoto.com/img/45/6242fbce58e418a1cc85c2c61559fe21-.jpg[/IMG]

Until the machine restarted. 
This is the first time I've seen this error. Having scouted around the web for reports, it looks ike it's either corruption in the disc or a bug in GRUB. I may reformat that partition to see if it makes any difference.

---

### Post by dglp on 2006-04-17
CASE CLOSED

[IMG]http://nunovo.zoto.com/img/45/2b1065b31376d3bcf470214c797de8f1-.jpg[/IMG]

Hard drive corruption? 
Reformatted the existing partition and reinstalled a couple of times, but after doing the final reinstall I was rewarded with this screen.

Would now be good to run some kind of disc checker/repair utility, presuming there is one available.

---

