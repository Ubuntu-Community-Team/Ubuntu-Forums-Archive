---
title: "issue with geforce 8800 gt??"
date: 2008-03-17
forum: Installation &amp; Upgrades
---

### Post by Panther96 on 2008-03-17
Hi, (from windows of course) and i explained a lot of my issues on other posts, but here is for my real tech issue. I put the live cd in, clicked start or install, then it brings a little x and then says its running in low graphics mode, and it couldn't reconize my card and bla bla lba, so i go through a bunch of lists of me picking my driver, my monitor, resolution and etc, after  i click  test or continue (did both) i get a black screen with like words on it then says ok next to them, and i left it like that for 30 mins and still didnt move, maybe asking me to type a command line, but i don't know any command lines, and mandriva didn't as me for any command lines on install, even though i have a graphics issue where i can't get resolution higher then 800x600, but at least it starts, unlike ubuntu, (i just put these disks in yesterday, since im now fed up with microsoft crap) any help guys? I really don't like looking at a command line on starting an os (AND CAN'T EVEN GET THE LIVE CD TO START), or looking at 800x600 resolution on a 22 inch monitor either (mandriva)

Well since my dxdiag excceeds the forum limit...........ill have to type my parts manualy :(

Intel core 2 quad @2.4 ghz (ROCKS)
Geforce 8800 gt (rocks)
2gb of ram(vista sucks it up like a lolipop)
samsung syncmaster 205bw (digital) 22 inch monitor
Realitic sound card 7.1 sourrond sound (no issues, well , at least on mandriva's live cd, *note havn't installed any yet)
Alienware branded motherboard
Bose speakers

Thank you for anyone who helps me with my issue, or at least tries to help, becuase i appreatiate that too.

---

### Post by Ub1476 on 2008-03-17
When you get this window when you can configure driver, screen resolution etc, use "vesa" as the driver and set a resolution of 1024x768. Hopefully it'll work at those settings. If you manage to install Ubuntu, download [Envy]("http://www.albertomilone.com/nvidia_scripts1.html") which will fetch the latest driver from nvidia for you, install it and configure it.

---

### Post by Panther96 on 2008-03-17
well a 1024x768  still will look pretty nasty on a 22 inch monitor also, becuase this is ment to be on 1680x1050 resolution....., ill try that versa driver though, and thank you, but still wondering why i get a command line screen.....

Thank you  for the sudo-rm tip also!

---

### Post by Ub1476 on 2008-03-17
It's just while installing. If some windows are off-screen, you can press <Alt>+Mouse to drag them around in a viewable position.

If you are thrown into the command line screen, type "startx" (which might lead in errors if correct res and driver isn't set).

---

### Post by Panther96 on 2008-03-17
k i was thrown back into a screen again, and i typed startx, nothing happened, am i going to have to wait until  new realeases for this crap or something, becuase i hope maderiva or ubuntu come out with their new ones before the end of this week or eles i lost my chance of my older bro  setting my filesystem type thing (like fat32 and that crap, which i don't know what that means)

Will downloading the beta pre-realease of the new ones might resolve issuses?

---

### Post by Panther96 on 2008-03-21
Ok well i downloaded the beta of 8.04, and it goes on my correct resolution with no errors! Woot i love the demo, and ill fight to install (my brother and my dad don't think its a good idea) when the full version comes out.But so far, as the demo, i love it.

---

### Post by AdamWill on 2008-03-21
the deal (for both MDV and Ubuntu) is simply that your card wasn't released when we both did our last releases (Ubuntu 7.10, Mandriva 2008 ). So they can't detect it, and the drivers they contain don't support it. You could install newer drivers on these releases to get it going, but what you've done is likely more sensible - just use a pre-release of the next distribution release. You can do the same thing for Mandriva - grab 2008 Spring RC2 (came out yesterday), it should detect your card correctly, like Ubuntu 8.04 beta does.

---

### Post by Panther96 on 2008-03-22
Just the only problem with mandriva 2008 spring rc2 is that the file is too big for my cds, my cds can handle 700 mb, which ubuntu is 690mb, so ubuntu is fine, but, mandriva, is 730 mb, and im not sure if you can use 2 cds for an os???

---

### Post by AdamWill on 2008-03-22
they're single CD images. If you're counting bytes...don't. 730,000,000 (or whatever, I forget how many zeros there are) bytes is just about exactly 700MB. The images are built and tested to be burned to 700MB blanks.

---

### Post by Panther96 on 2008-03-22
ok thank you and you were right, got mandriva to fit on that disk.

---

### Post by duhglas on 2008-03-23
Hey, I have a very similar computer to yours same vid card, cpu, ram, and I've been having a ton of trouble installing the 7.1 edition. So I am going to try and install the new beta release and see how that goes. 
Which version did you download though, I wanna use the 64 bit version, but not sure if the    64-bit PC (AMD64) desktop CD, will be best or if I should go with the    PC (Intel x86) desktop CD, download instead.

---

### Post by Panther96 on 2008-03-24
Just download the intel one instead, like i did. I heard that software support for 64-bit linux is iffy, even in firefox plug ins, and its not worth it unless you honestly need 3 seconds shaved off your boot time. Plus, to be on the safer side, its better to just download the intel one, like intel quad isn't fast enough :)

---

