---
title: "[SOLVED] Ubuntu wont run on Dell Vostro 1500"
date: 2007-07-30
forum: Installation &amp; Upgrades
---

### Post by ACGarib on 2007-07-30
Hi, I just got my first laptop! Unfortunately, when I tried to run the Feisty live CD, I get the following error:

/bin/sh: can't access tty; job control turned off (initramfs)


I searched around, but I guess Dell's Vostros are too new to have threads about them.

That error seems pretty vague, so I don't even know where to start to attempt to fix the problem.

Any suggestions?

---

### Post by Pumalite on 2007-07-30
I suspect your machine is old and with little memory. Correct me if I'm wrong, Try Alternate CD. 256 MB RAM or less> Xubuntu Alternate CD:

[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)

---

### Post by ACGarib on 2007-07-30
No, my computer is actually pretty good. It has a T7300 Core 2 duo with 1 GB of ram. (I will upgrade it to 2 GB tomorrow) and a Nvidia 8400 GS graphics card.

The Vostros were just released about a month ago in the small business section of Dell.

---

### Post by Pumalite on 2007-07-30
You have good hardware. You can install with Live CD according to the amount of memory you have, but according to the error you posted you might be better off installing with Alternate CD ( Text Mode). On the other hand, don't forget to do md5sum on iso, burn at 4x, check CD for corruption before install, etc.

---

### Post by yogo on 2007-07-30
> **ACGarib said:**
> No, my computer is actually pretty good. It has a T7300 Core 2 duo with 1 GB of ram. (I will upgrade it to 2 GB tomorrow) and a Nvidia 8400 GS graphics card.

The Vostros were just released about a month ago in the small business section of Dell.

Yeah they are kinda nice, somewhere between a desktop and a Shuttlebox. Was thinking about picking one up for myself.

---

### Post by ACGarib on 2007-07-30
I tried using an older version (6.06), and it didn't get the error, but it ran into another error. It couldn't start X. I looked at the problem, and it said that no screens were found and that no devices were detected. 

When I shut the laptop down, I noticed that ubuntu failed at stopping something about raid monitoring.

Was I not able to start X because 6.06 has dated nvidia drivers that aren't compatible with my 8400 GS? Is there a way to get around that? 

I guess the best thing would to get the Feisty live CD working so I can install it directly instead of dapper upgraded to feisty.

Does anybody have any suggestions?

---

### Post by Pumalite on 2007-07-30
I think you should use the Alternate CD (text mode) to avoid graphical interface problems as the one you mentioned. Then, once IN the system you can get the appropriate driver for your card.

---

### Post by ACGarib on 2007-07-30
Is alternate CD still ubuntu? Is it on the regular Live CD or do I have to dowload a new version? I can get ubuntu to run on the 6.06 disc, but without any GUI.

What is the difference between alternate CD and the regular one (without X working)?

Sorry for all of the questions.

EDIT: Also, can I run this alternate CD as a live session, or do I have to install it?

---

### Post by ev5unleash1 on 2007-07-30
Yea, it's still Ubuntu but it has a more advanced set up and it does not use the X server display. You may need to know all about the hardware like the pasific Graphics card but it is a better way to customize it. So yes it's still ubuntu!

---

### Post by Pumalite on 2007-07-30
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Check the box below the green sign that says: Start Download.

---

### Post by ACGarib on 2007-07-30
But can I run this alternate CD as a live session or is it install only? I am afraid that when I install it, I will go to run it from the HDD and I will get that error that I got with the Feisty Live CD.

---

### Post by ACGarib on 2007-07-31
I don't know if this helps, but I was able to successfully run the dapper live CD in safe graphics mode.

One thing with the alternate CD I am worried about is it is still feisty. I currently can't get feisty to work and I am afraid that installing it in text mode will get around the problem, but on reboot, I will run into the problem and not be able to boot into linux.

---

### Post by ACGarib on 2007-07-31
Well, I finally managed to install ubuntu feisty. Now the problem is getting the Nvidia drivers to work so I can use compiz-fusion. On the live CD I tried using envy, but it said my Nvidia 8400 GS is not supported by any nvidia drivers. Is there a way to get compiz fusion to work with my 8400 GS or is in not compatible with linux? Are there beta drivers I can install?

Also, can I change my LCD monitor to 24 bit? Right now it is in 16 bit and the banding of colors is annoying. I don't have this problem in vista, so I don't think it is my monitor.

---

### Post by ACGarib on 2007-07-31
I finally solved all of my ubuntu problems. (well, sort of)

I had to install the nvidia drivers directly from their website in order for them to work with my graphics card.

I also just changed the default bit depth in my xorg.conf to get rid the the banding issues.

I installed compiz-fusion sucessfully.

But for some reason compiz fusion is very slow compared to compiz fusion on my P4 desktop w/ 1 GB ram and a 9800 pro. I thought I would be getting super high frame rates, but I guess I was wrong. It seems like this is a common problem right now for some computers. One thread said that it may be an issue with dual core processors. I just hope a solution comes around soon.

One other problem I have on both of my computers running compiz fusion is the blur plugin does not work. Neither do a whole bunch of the other plugins. Any help would be nice.

---

### Post by tashmooclam on 2007-08-02
I could not install ubuntu on my vostro 1500, although I installed it a week ago on a 5 year old compaq laptop.
Solution may be:
I am installing it right now in Text Mode.
I tried safe graphics mode and no go.
Why can it be so easy in an old compaq and so difficult in *a brand new Dell?*

---

### Post by hellcat12345 on 2007-08-02
I got it installed using text mode but am now having problems with X getting started.  What did you do to fix that?

---

### Post by ACGarib on 2007-08-02
I followed this guide: [ http://ubuntuforums.org/showthread.php?t=421588]( http://ubuntuforums.org/showthread.php?t=421588) to get ubuntu installed on my Vostro 1500. To get X running, I did ```
 sudo nano /etc/X11/xorg.conf
``` and changed my driver from nv to vesa to get graphics. I then went to [ http://www.nvnews.net/vbulletin/showthread.php?t=94072 ]( http://www.nvnews.net/vbulletin/showthread.php?t=94072 ) and followed the directions to install the newest version of the nvidia drivers that are not in the ubuntu repos yet. I just went to nvidia.com, downloaded the linux driver to my desktop, then followed the directions in the nvnews site.

---

### Post by hellcat12345 on 2007-08-02
Thanks! That worked.

---

### Post by Spam Banjo on 2007-08-09
> **ACGarib said:**
> Hi, I just got my first laptop...

Sorry to hijack your thread... but I really need to ask, what do you think to the Vostro, and how does your Ubuntu install perform now?

I Just ordered one and want some feedback as to how well Ubuntu works on there. Half the reason I bought it was for Ubuntu on the go!!!

I'd especially like to get compiz/beryl running as well, but I got the ATI card in mine and I'm just hoping I don't run into the same compatibility problems as the ATI x1300 in my Demension 9200. I want to avoid the XGL route at all costs.

Compiz-Fusion is a beautiful toy!!! It's one of those things that make windows fan-boys shut-up and listen for a second!!
:lolflag:

---

### Post by cherry316316 on 2007-08-11
> **ACGarib said:**
> I followed this guide: [ http://ubuntuforums.org/showthread.php?t=421588]( http://ubuntuforums.org/showthread.php?t=421588) to get ubuntu installed on my Vostro 1500. To get X running, I did ```
 sudo nano /etc/X11/xorg.conf
``` and changed my driver from nv to vesa to get graphics. I then went to [ http://www.nvnews.net/vbulletin/showthread.php?t=94072 ]( http://www.nvnews.net/vbulletin/showthread.php?t=94072 ) and followed the directions to install the newest version of the nvidia drivers that are not in the ubuntu repos yet. I just went to nvidia.com, downloaded the linux driver to my desktop, then followed the directions in the nvnews site.


i was trying to install the new ubuntu 7 64 bit on my notebook
but , for some reason the setup used to start and then after that
the screen used to go in complete blank and then the cd will stop rotating

i thought , thr is problem in cd , so i again download a new copy of ubuntu and tried on new cd
and same problem, i then tried in safe graphic mode and same problem

then i tried ubuntu 6 , 64 and 32 bit both , and i got the problem of x server
(for more abt the problem pls read
[https://answers.launchpad.net/ubuntu/+question/8351](https://answers.launchpad.net/ubuntu/+question/8351) )

i tried the commands given on those website and still , i am not able to install
after trying those commands and saving the conf file , i restarted the gnome ,
and then i dont know what to do , as thr was nothing written , so i tried
startx command  , i found from some where and then again the screen went into blank and nothing happen

even the cd stopped rotating



but i didnt understand the complete details given on the  website u have mention, also i tried once
break=top and in that also after exit , i got completely blank screen
then i tried the break command in ubuntu 6 and then i got the xserver error
i modified the conf file and then again i got the blank screen.

---

### Post by LudovicusRex on 2007-08-11
Hello, 

 I am **really** new in the field but I still want to install Ubunutu on my new dell vostro laptop. I would like to do a dual boot, but I don't really feal confortable with it. 

 I can copy paste code lines in a terminal although I don't understand everything I type...

 Is there someone outhere who can help me with my installation. I need something very very detailled, step by step for a dual boot installation vista/Ubuntu on my new dell vostro 1500. 

 Thanks in advance

p.s: Does anyone know if the future version of Ubuntu coming in October will be supported by the vostro hadware?

---

### Post by ACGarib on 2007-08-16
Sorry for the very late reply. (I sort of forgot about this thread)

cherry316316: Did you manage to get ubuntu installed?


LudovicusRex: when you pop the Feisty Live CD into to computer and boot to it, does it boot or do you get errors? If so, what errors?

---

### Post by Nightambience on 2007-08-17
This thread's been a big help.  I got Ubuntu to install on Vostro 1400 and got passed the X server via vesa.  I'm now stuck w/ finding my network connection on my wireless... any of you guys having trouble with it too?

---

### Post by jebbiss on 2007-08-17
I Think that if you follow the instructions from this thread almost everything should work.  The Dell Vostro is basiclly the same as the Inspiron except for cosmetics.

[http://ubuntuforums.org/showthread.php?t=501195](http://ubuntuforums.org/showthread.php?t=501195)

I hope it helps

---

### Post by cherry316316 on 2007-08-18
> **ACGarib said:**
> Sorry for the very late reply. (I sort of forgot about this thread)

cherry316316: Did you manage to get ubuntu installed?


LudovicusRex: when you pop the Feisty Live CD into to computer and boot to it, does it boot or do you get errors? If so, what errors?


Hi , I just tried Debian , and then at some point I got the same problem in debian also
then I contacted some of the pro in linux and after some discussion they suggested me to go to windows and download the driver for linux from the Nvidia website
then goto linux and mount that driver and after mounting the driver 
use command 
sh Nvi.....run 
I did that and my comp is working fine

ps; today i install ubuntu 7 32bit on my uncle laptop which is Inspiron 6400
and I got the same problem of Xserver, my uncle has ATI Mobility card ,
so I went to ATI website from windows, downloaded the driver, went to linux
mount that driver , and I run those command, finally the Ubuntu is up and running
so I guess , you also have to follow the same thing. and this is very simple compare to 
using other then those  tricks mentions else where 

anyway , let me know if you get any good luck

cheers

cherry

---

### Post by Spam Banjo on 2007-09-06
> **LudovicusRex said:**
> I am **really** new in the field but I still want to install Ubunutu on my new dell vostro laptop. I would like to do a dual boot, but I don't really feal confortable with it.

I'm still a baby in the Linux world myself, but I successfully have a Triple-Boot on my Vostro 1000 (Vista|Ubuntu|OpenSUSE) and would highly recommend at least a dual boot. It's nice to have Windows as a backup for the programs you can't be without that you can't get working under wine with a little googling. (not that many at all!)

Partition your hard drive before installing and you should be fine. Grub (the Boot list manager that lets you select your OS) sets up for you with a dual-boot. Some tinkering is required for the triple.

---

### Post by Merlin7777 on 2007-10-13
Cherry316316,
I am having the exact same problem. I add the break=top line to the begiining of the boot line and remove the quiet splash line, and I get a black screen after punching in the "modprobe piix" and "exit" lines. 

everything starts to initialize, but I get a black screen and DVD drive stops spinning. Nothing happens. 

Does anyone know why this is happening? And how I can fix it?

---

### Post by cherry316316 on 2007-10-13
> **Merlin7777 said:**
> Cherry316316,
I am having the exact same problem. I add the break=top line to the begiining of the boot line and remove the quiet splash line, and I get a black screen after punching in the "modprobe piix" and "exit" lines. 

everything starts to initialize, but I get a black screen and DVD drive stops spinning. Nothing happens. 

Does anyone know why this is happening? And how I can fix it?

use ubuntu gusty 7.10 [http://www.ubuntu.com/testing/gutsybeta](http://www.ubuntu.com/testing/gutsybeta)
although this is still beta and the final will come in next 5 days , but i am using this from 3 weeks
and this is too good, it configure my wireless and graphic card on its own, less work
and more fun. it has nice 3d effects also, try the normal installation or text installation  , both works fine :)
cheers

---

### Post by Merlin7777 on 2007-10-13
Thanks alot Cherry316316! I will download a copy tonight. I hope it fixes everything.

Thanks again,
Merlin7777

---

### Post by Merlin7777 on 2007-10-14
Yey!! it loads up without any tinkering what so ever!!

Still are a few bugs, but at least it loads!

Thanks Cherry316316!

---

### Post by cherry316316 on 2007-10-15
> **Merlin7777 said:**
> Yey!! it loads up without any tinkering what so ever!!

Still are a few bugs, but at least it loads!

Thanks Cherry316316!

cool, it even configure the webcam and printer on its own :)
do install "cheese" for taking picture
and "checkgmail" for gmail notifier , its much better then windows gnotifier.

---

### Post by aakaasha on 2007-10-15
I have the same problem with the x-server and the graphic card on the old 533MHz pc I am setting up for my girlfriend.
[http://ubuntuforums.org/showthread.php?t=573845]("http://ubuntuforums.org/showthread.php?t=573845")

---

