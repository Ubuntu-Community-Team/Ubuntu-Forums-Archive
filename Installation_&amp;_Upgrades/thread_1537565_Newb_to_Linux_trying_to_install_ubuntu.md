---
title: "Newb to Linux trying to install ubuntu"
date: 2010-07-23
forum: Installation &amp; Upgrades
---

### Post by Sidewind75 on 2010-07-23
Hello all.

I have been interested in running Linux for quite some time. I am trying to Install Ubuntu 10.04 64 but when the splash screen goes away the monitor goes to sleep and i cant do anything. I have searched google and found some other problems like this but hitting esc and doing some of the options posted in those searches did nothing. 

I have also tried Wubi and same thing however when i go to safe graphics i get further but it says to root file system and thats as far as i can go

PC specs are

Intell I7 2.8
8 gigs ram
2 WD veliociraptors in raid on an Intel chip
and a ATI 5870


Any help would be apreciated

---

### Post by Rubi1200 on 2010-07-24
Have a look here and see if it helps:

[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

---

### Post by Sidewind75 on 2010-07-24
No that did not work i dont see any of the options they talk about all i have is f6 then i have nomodeset
acpi=off

i dont know how to do nomodeset=1 or nomodeset=0 or to choose the different video cards

---

### Post by Sef on 2010-07-24
How does the Live CD run?

---

### Post by tommcd on 2010-07-24
> **Sidewind75 said:**
> No that did not work i dont see any of the options they talk about all i have is f6 then i have nomodeset
acpi=off
i dont know how to do nomodeset=1 or nomodeset=0 or to choose the different video cards
What video card do you have? 
When you hit F6, a popup window will come up with some options. If you hit the Esc key (I think it is Esc). The popup will disappear and you will have a cursor at the boot line that will allow you to add any options you want. 
**EDIT**: I just saw that you have ati. Try:
nomodeset
xforcevesa
Try them one at a time. The last one should work if the other nomodeset fails.
Also, when you boot the Ubuntu CD, first choose the option "check disc for defects". And let that run. If it reports errors, then the CD is bad.
Be sure to always burn a linux install CD at the slowest possible speed.

---

### Post by Sidewind75 on 2010-07-24
I would like to Thank you for the help guys i got it installed and its running ok. I did notice however that my HDMI audio out is only doing sterio  how do i get it so that my reciever can use the outputs as doblby or DTS or whatever the signal is. and i KNow my card can do this because it does it in windows 7

Also i am trying to install Mplayer and got it thru the Ubuntu sofware center it installs but i cannot find it anywhere


Thx again

---

### Post by tommcd on 2010-07-25
> **Sidewind75 said:**
> I would like to Thank you for the help guys i got it installed and its running ok.
Excellent!
You see, the linux kernel developers have been using *kernel mode setting* to load the open source graphics drivers in the most recent kernels. Unfortunately, this has resulted in in some problems for certain graphics cards during this transition. These bugs will likely be worked out in time.... Many of them have already.
Phoronix has been following the evolution of this closely if you would like to read up on it:
[http://www.phoronix.com/scan.php?page=article&item=kernel_modesetting&num=1](http://www.phoronix.com/scan.php?page=article&item=kernel_modesetting&num=1)
[http://www.phoronix.com/scan.php?page=article&item=linuxtag_2010_kms&num=1](http://www.phoronix.com/scan.php?page=article&item=linuxtag_2010_kms&num=1)
[http://www.phoronix.com/scan.php?page=search&q=kernel+mode-setting](http://www.phoronix.com/scan.php?page=search&q=kernel+mode-setting)
> **Sidewind75 said:**
> 
 I did notice however that my HDMI audio out is only doing sterio  how do i get it so that my reciever can use the outputs as doblby or DTS or whatever the signal is. I'm not knowledgeable on this so I don't know. Perhaps a separate thread is in order for this issue.
> **Sidewind75 said:**
> 
Also i am trying to install Mplayer and got it thru the Ubuntu sofware center it installs but i cannot find it anywhere

A wise choice. MPlayer is still the best linux multimedia player imo. I can't live without it!
Simply open a terminal and run:
```

sudo apt-get update
sudo apt-get install mplayer

```
If you get errors, post them here.
You may need to log out and log back in for MPlayer to show up in the: applications > sound & video menu. I don't recall ever having to do this for MPlayer though.
After you install MPlayer, try to run MPlayer from the terminal. Just run:
```
gmplayer /path/to/your/video_file
```
... where /path/to/your/video_file is the path to a video file on your hard drive.
So if you have a video in your home directory for example, open a terminal, then make sure you are in your home directory:
```
cd ~
```
Then run:
```
gmplayer my_video
``` 
The MPlayer GUI should open and the video should play.
You can even run MPLayer straight from the terminal. Just leave off the "g" from the "gmplayer" command.
If you get any errors, post them here.
Also, make sure you have the restricted codecs for multimedia:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

