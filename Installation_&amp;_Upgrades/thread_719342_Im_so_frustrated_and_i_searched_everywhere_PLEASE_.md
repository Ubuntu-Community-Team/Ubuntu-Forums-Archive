---
title: "Im so frustrated and i searched everywhere PLEASE HELP"
date: 2008-03-09
forum: Installation &amp; Upgrades
---

### Post by kpariaug on 2008-03-09
hi, i've been lookin around a bit now for some help with my ubuntu install problems.

my problem is: when i boot the ubuntu cd, i get the menu, and i can select the options. 

no matter which option i choose, i get through the loading bar and then all the white lines of text status checks.

after the checks it goes white and looks like dead pixels everythere.(the screen it white with lines of random black, and every possible color of dot just splattered on the screen.) then, after that, it slowly fades to black, and i mean SLOWLY and UNEVENLY. it actually looks like the signal cable to the screen got cut. i have no problem just rebooting with the power button and loading vista though when it "fails".

MY COMPUTER:
[LIST]
[*]compaq f572us laptop
[*]80 gb sata
[*]2.5 gb ram
[*]amd athlon 64 x2 1.7ghz processor
[*]nvidia geforce go 6100 graphics
[*]and nvidia...um...some ****, chipset
[/LIST]

yep thats pretty much my story. i've looked around but noone has really described my problem i've just seen other nvidia related problems with the "white screen of death". i would appreciate any help. and BTW im running (or trying to run) the most recent version of the 64bit one.

---

### Post by Arthur Archnix on 2008-03-09
Hopefully by latest you mean Gutsy, and not the recent Alpha of Hardy.

That being said you have two options, that i see:

First is try to find an option or switch that you can add to the boot-up parameters. For example, noapic is a popular one, though unrelated to your problem. But something similar perhaps. So search for something like NoDRI or NoNvidia, if such a thing exists.

Second, which is what I'd do, is download the alternate cd. It uses a text based installer. Once you get it installed, fixing the video becomes much easier.

Maybe scan through the forums though, search for your video card, and see whether people are having the same problem.

---

### Post by kpariaug on 2008-03-09
thanks for the quick reply.
will do asap. (just need some sleep first)

PLEASE keep the tips coming.

---

### Post by keratos on 2008-03-09
go back to ubuntu downloads and download the alternate CD image

---

### Post by Sef on 2008-03-09
> Second, which is what I'd do, is download the alternate cd. It uses a text based installer. Once you get it installed, fixing the video becomes much easier.

To download the alternate cd, there is a box that you check at the bottom of the download page before you start the download.

---

### Post by mimada on 2008-03-09
You might want to check your Ubuntu CD for corruption as well.

---

### Post by Pumalite on 2008-03-09
Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do md5sum on your iso, burn at 4x or less in good quality CD-R media, check for CD integrity after burn and before install.

---

