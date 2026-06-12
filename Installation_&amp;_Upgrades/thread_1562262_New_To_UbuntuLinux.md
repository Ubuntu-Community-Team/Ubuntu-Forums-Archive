---
title: "New To Ubuntu/Linux"
date: 2010-08-27
forum: Installation &amp; Upgrades
---

### Post by JakQuik on 2010-08-27
Hi im new to Linux, been using windows and always hated its lack of freedom but never switched because linux sounded intimidating but finally attempted out of pure desire for something new and better, my issue is that ubuntu 10.4.1 freezes on the logo and doesnt go beyond that, i have searched the web and found nothing simple enough for me to understand to fix the problem, my specs can be found here [http://www.newegg.com/Product/Product.aspx?Item=N82E16834280003](http://www.newegg.com/Product/Product.aspx?Item=N82E16834280003) on a 32bit system.
ive been using the wubi installer and nothing else, is it possible my graphics aren't sufficient? and should use the alternate install? or a previous version of ubuntu altogether?

---

### Post by Jim Hill on 2010-08-27
I'm having a similar problem.  I started with 5.10 and went through various upgrades to 9.04 without problems. Notes indicate I continued to 9.10.  Another automatic upgrade downloaded 10.04, which took forever and didn't work.  (The user should be warned when what appears to be a routine upgrade is actually a new version). I tried again at a different time day when there is less internet activity and burnt a CD with 10.04LTS.  I installed it and just get a colored screen - a single color consisting of lines, not a solid color.  It recognized a flash drive containing some documents, but I don't get the regular "desktop", so can't access the internet, see saved files, etc.

I notice there is a 11.x listed, but can't find a convenient download site.  Searching for 11.04 brings up 10.04.  Any suggestions?  I'm running an old Dell OptiPlex with a Pentium 933.

Jim

---

### Post by Sef on 2010-08-27
> Hi im new to Linux, been using windows and always hated its lack of freedom but never switched because linux sounded intimidating but finally attempted out of pure desire for something new and better, my issue is that ubuntu 10.4.1 freezes on the logo and doesnt go beyond that, i have searched the web and found nothing simple enough for me to understand to fix the problem, my specs can be found here [http://www.newegg.com/Product/Produc...82E16834280003](http://www.newegg.com/Product/Produc...82E16834280003) on a 32bit system.
ive been using the wubi installer and nothing else, is it possible my graphics aren't sufficient? and should use the alternate install? or a previous version of ubuntu altogether?

What are your system specs?

---

### Post by JakQuik on 2010-08-27
my specs can be found here [http://www.newegg.com/Product/Produc...82E16834280003](http://www.newegg.com/Product/Produc...82E16834280003)  on a 32bit system

---

### Post by JakQuik on 2010-08-27
whoops nevermind that link is broken sorry about that. heres my specs
[B]
Processor[/B]
Processor class  Intel Core Duo T2080
Processor speed 1730 MHz                                                                                                                                                      
[B]
Graphics[/B]
Video chipset Intel GMA 950                                                                                
                                                                       [B]
Memory[/B]
Installed memory  1 GB
Memory technology DDR2 SDRAM
Memory Speed   533 MHz                                                                               
                                                                       [B]
Storage[/B]
Total HD Size 100 GB                                                                         
                                                                       [B]
Optical Drives[/B]
Optical Drive Type   DVD±R DL/DVD±RW
Optical Drive Speed 4 x

Operating system
Microsoft Windows Vista Home Premium (32  bit)

---

### Post by Ceedub2 on 2010-08-27
Coming from a newb since ver 9.10. Intel graphics pose a problem with Linux or at least Ubuntu. But don't worry I am sure wiser users with Intel chips will help. Cheers

---

### Post by JakQuik on 2010-08-27
also i used the wubi installer

---

### Post by Ceedub2 on 2010-08-27
Can you log in and change a few things before it freezes. Maybe right click on the desktop and choose change desktop appearance then visual effects. Select none. Any better?

Ubuntu net book maybe a good alternative too.

---

### Post by JakQuik on 2010-08-27
no unfortunately i dont even get that far all i have done is install using wubi, reboot then select the OS "ubuntu", it goes to the screen that says ubuntu with the dots, the dots motion for about 13 seconds then stop, and the only way to get out is to power off

---

### Post by bcbc on 2010-08-27
> **JakQuik said:**
> also i used the wubi installer

Try the workaround here for intel graphics...
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

---

### Post by JakQuik on 2010-08-27
i dont get an "install" screen per say its just like a regular windows program, does it mean when i get 5 seconds to press "esc" button for more options before it loads up?

---

### Post by JakQuik on 2010-08-27
you know i dont even think its officilly installed the wubi downloads the ISO but i never get to the installation process it freezes as the GUI installer loads up

---

### Post by bcbc on 2010-08-27
> **JakQuik said:**
> you know i dont even think its officilly installed the wubi downloads the ISO but i never get to the installation process it freezes as the GUI installer loads up

OK that press ESC is to continue the wubi install - it does the actual ubuntu install on the virtual disk you created in Windows. So you could press ESC, hit 'e' on the first option, and you'll see an indecipherable bunch of stuff, somewhere in the middle is 'quiet splash' and you want to add the workaround there. Then press CTRL+X.

I believe if you just left it - it would install (it's an unattended installation) - but you'll have to leave it long enough. If you must see it, do the above. But note you'll have to workaround everytime you boot after that until you fix it.

it's probably better to try a live CD instead, so at least you can figure out whether the workaround works.

---

### Post by JakQuik on 2010-08-27
ok thx for the info, although i left it for about 2 hrs on its own and it was still frozen, but il try for longer just incase and i didnt really wanna do a live cd because i had the wubi but i gess il have to, no big deal though, just gotta get blanks lol

---

### Post by bcbc on 2010-08-27
> **JakQuik said:**
> ok thx, but i left it for about 2 hrs on its own and it was still frozen but il try for longer just incase and i didnt really wanna do a live cd because i had the wubi but i gess il have to no big deal

That seems way too long. I wouldn't leave it that long.

---

### Post by JakQuik on 2010-08-28
another thing is, once before i went to the options and went into some of them-they all stopped at half screen and said "something not something (16) may have trouble" or something like that, srry i dont remember the exact wording (im redownloading ubuntu rite now, thought it might not have downloaded correctly to begin with). hmm i wanna say "hardware not something" but that wasnt the phrase it didnt say hardware

---

### Post by JakQuik on 2010-08-28
heres what it had

init: ureadahead-other main process ( 2708 ) terminated with status 4

mmc0: unknown controller version ( 16 ) you may experience problems

i did the workaround but still nothing maybe i950 instead of i915 ? and do i have to press the tab for completion if it wasnt there at first?

---

### Post by bcbc on 2010-08-28
> **JakQuik said:**
> heres what it had

init: ureadahead-other main process ( 2708 ) terminated with status 4

mmc0: unknown controller version ( 16 ) you may experience problems

i did the workaround but still nothing maybe i950 instead of i915 ? and do i have to press the tab for completion if it wasnt there at first?

I've seen issues with multimedia card readers - but it looks like they cause delays rather than preventing booting.

So, are there any differences now - with and without the workarounds? If you remove the quiet splash, where does the boot process freeze?

---

### Post by JakQuik on 2010-08-30
sory about that delay was moving my brother to college, but the work around takes me to that message  "you may experience problems"

---

### Post by bcbc on 2010-08-30
Do you have any other devices plugged in while installing? e.g. iphone, sd cards etc. if so I'd remove them. 

Maybe try booting a live CD with Ubuntu 9.10 and see if that works? I know 10.04 has some problems with certain graphics card and devices, but haven't seen this problem before.

---

### Post by JakQuik on 2010-08-31
no nothing is plugged in, is there a wubi for 9.10 thing is i got no cds for burning or flash card

---

### Post by bcbc on 2010-08-31
> **JakQuik said:**
> no nothing is plugged in, is there a wubi for 9.10 thing is i got no cds for burning or flash card

I'm not sure, but picking a download server [http://mirror.csclub.uwaterloo.ca/ubuntu-releases/karmic/](http://mirror.csclub.uwaterloo.ca/ubuntu-releases/karmic/) it shows [wubi.exe]("http://mirror.csclub.uwaterloo.ca/ubuntu-releases/karmic/wubi.exe") and [ubuntu-9.10-desktop-i386.iso]("http://mirror.csclub.uwaterloo.ca/ubuntu-releases/karmic/ubuntu-9.10-desktop-i386.iso") (or [ubuntu-9.10-desktop-i386.iso.torrent]("http://mirror.csclub.uwaterloo.ca/ubuntu-releases/karmic/ubuntu-9.10-desktop-i386.iso.torrent")) so you can probably download it from there.

Or any other Ubuntu download server near you.

Place wubi.exe and the .iso in the same folder and run wubi to install.

---

### Post by JakQuik on 2010-09-01
i tried the 9.10 and it still freezes even in safe graphics mode maybe it just aint meant to be:( il try updating my graphics driver perhaps

---

### Post by bcbc on 2010-09-01
what's the exact computer brand and model number?

---

### Post by JakQuik on 2010-09-01
everex stepnote sa2053T

---

### Post by JakQuik on 2010-09-01
i updated the driver and did the work around with no luck this is what ive been getting all this time, in exact words

Setting preliminary Keymap 
mmc0: Unknown controller version (16) you may experience problems

thats when it freezes

---

### Post by bcbc on 2010-09-01
> **JakQuik said:**
> everex stepnote sa2053T

Try adding "sdhci.blacklist=yes sdhci_pci.blacklist=yes" to your boot option overrides.

I found this article [http://www.poplarware.com/articles/everex_stepnote_linux](http://www.poplarware.com/articles/everex_stepnote_linux) and it sounds like Ubuntu will work, but you have to blacklist the sdhci driver modules. 

I'd probably keep i915.modeset override too.

---

### Post by Timothytech on 2010-09-01
Download and install the ISO for ubuntu 10.04 or 9.10... there is an install option for live cd or as an application in windows(wubi).  if i remember correctly, at least there was for 10.04. so go to windows, in control panel and remove program "wubi" then burn the ISO onto a DVD and go that route. its best. if your really gutsy the 10.04 version has the ability to shrink your windows partition so you can install the ubuntu on your HDD. but thats only if your confident or apathetic about your window's well-being.

---

### Post by JakQuik on 2010-09-01
sorry for not knowing how but can u give me a step by step of where to put that sdhci or would i see it by reading the command?

---

### Post by bcbc on 2010-09-01
> **JakQuik said:**
> sorry for not knowing how but can u give me a step by step of where to put that sdhci or would i see it by reading the command?

This [site]("http://www.fitzenreiter.de/averatec/index-e.htm") has a step by step although it looks like a different override "reserve=0xFFB00000,x100000" is used (and it's version 9.04). I appreciate that this is a different instruction from my last post, but it was a comment from that web page by the author that points to this link as being a working solution that should work in future versions of Ubuntu.

So, try first booting an Ubuntu CD. Press a key as it boots (when you see the keyboard and little man at the bottom). Hit F6, then ESC, insert "i915.modeset=1 reserve=0xFFB00000,x100000" (no quotes) just before "quiet splash". Then select "Try without installing".

Give that a go. 

Caveat - please note I cannot give any guarantee as to whether this is going to work or the reliability of the workarounds.

---

### Post by JakQuik on 2010-09-02
!!!!SUCCCEESSS!!!!! i wrote this while in ubuntu, bcbc thanks for your help if i was able to, id send you a batch of special brownies WHOOOOOOOOOOOOOOOOOOOO!!!

---

### Post by bcbc on 2010-09-02
> **JakQuik said:**
> !!!!SUCCCEESSS!!!!! i wrote this while in ubuntu, bcbc thanks for your help if i was able to, id send you a batch of special brownies WHOOOOOOOOOOOOOOOOOOOO!!!

Yum I like brownies :)

Well that's pretty cool - I gotta admit, it seemed a long shot :D

---

