---
title: "ASUS Eee PC &amp; Ubuntu: HELP!"
date: 2008-04-12
forum: Installation &amp; Upgrades
---

### Post by mrsrandallthomas on 2008-04-12
I have the ASUS Eee PC 4G Surf. I installed 1 GIG of RAM on day one. (So far so good.)

I purchased an external DVD Burner. (Plug and play, all is good.)

LINUX; I'm new to it but learning kinda quick. Yet I still need instructions to be written in crayon. 
(Too many posters on the web assume the reader knows some LINUX basics. Not Good For Me.)

Now.....Having said that. I download Ubuntu made the boot able CD(s) several times. The downloads didn't work on the Eee PC for one reason or another. (64 bit vs. 32 bit and son on.)

However, I found a Ubuntu version that was/is perfect for the Eee Pc. Seems that it was designed specifically for the Eee PC.

PROBLEM: In a word "Partitions".

*I think I understand the concept. Something like Pocket PC, when you check the memory there's a slider that is used to allocate memory. You can allow more to the RAM (if available) on the fly if the machine seems to be running slow from too many applications being open, etc.*

With LINUX and Ubuntu I haven't a clue as how to correctly set this critical feature. I should note that I only want to run Ubuntu and I don't care if it uses all of the memory. How the  partitions are set matters not to me as long as it allows the system to function.

So.......I get Ubuntu up and running. (GREAT!) However, if I shut the machine down it will not reboot. In fact, it doesn't really shut down. The screen goes black and I get an Error 15, which stays there. Can't fully power off. _I'm pretty sure this error is a result of how I set the partitions._ 

{If you don't already know, there two tiny holes on the bottom of the Eee PC. One is a mic, the other is a reset like you'd find on the back of a Palm or Pocket PC.}

I hit the reset, if it won't work I'll also remove the battery for about two minutes. Restart and hit "F2" then reboot the original ASUS Support DVD.

This is a bit long but I want my problem to be stated as clear as possible. 

I'm looking for the easiest answer, which should come in the form of STEP-BY-STEP Instructions. Please don't give me some code and ASSUME that I know where it is to be entered. Please don't give "$" "#" or other symbols and ASSUME that I know that they are not to be entered with the code.

Please feel free to send me a private message if need be. I'm new to the forum and don't know that I will see a post in response to this one.

In any case, I will be forever thankful to whom ever has the knowledge base and the generosity to offer me assistance.

---

### Post by starcannon on 2008-04-13
I have the entire Asus Eee line the 2g, 4g, and 8g.

The 4g is my favorite, that said here are some things I found useful in dealing with the Asus Eee

[LIST=1]
[*]Your going to need to downgrade the Bios if your running the 0801 or newer bios. Flash utility found here [http://pages.videotron.com/jplague/EEEBios.rar]("http://pages.videotron.com/jplague/EEEBios.rar")
[*]Your going to need to download and run this script pack [http://code.google.com/p/ubuntu-eee/downloads/detail?name=ubuntu-eee_v1.0.tar.gz&can=2&q=]("http://code.google.com/p/ubuntu-eee/downloads/detail?name=ubuntu-eee_v1.0.tar.gz&can=2&q=")
[*]As for partitioning schemes, my favorite method for the 4g is 128mb for boot, 1gb for swap (lots don't run swap on an eee you'll have to google and decide for yourself), 128mb for /home, rest for root or /  if you prefer, then i have a 16gb SDHC card that I leave in the machine or my storage needs, 128mb for /home is more than enough to take care of various user config files, a few wallpapers, etc.. etc...
[*]This website [http://www.eeeuser.com/]("http://www.eeeuser.com/") is invaluable to eee users.
[/LIST]

Thats how I setup all of my Eee's (except the 2g its a special case and a pita do not waste money on one), I'm sure you'll have more questions, I come to the forums frequently and  I'll keep an eye on the thread to answer more specific questions as they arise, and as always google is a great tool.

---

### Post by mrsrandallthomas on 2008-04-13
Thank you for the advice.

However, at 5:00am I decided to give it another shot working from information found at [http://hehe2.net/linuxhowto/howto-install-ubuntu-on-your-eee-pc/](http://hehe2.net/linuxhowto/howto-install-ubuntu-on-your-eee-pc/)  
and it worked. 

I don't know if I created issues with how the memory is allocated, but I'll deal with that issue later.

I download Picasa and it was fine. Yet when I tried to download LimeWire it encountered a serious delay installing it so I aborted.

Prior to installing Xubuntu I did not have a problem installing and running those two programs.

---

### Post by starcannon on 2008-04-13
Yeah, I didn't like xubuntu on the Eee, I just used standard 7.10 Gutsy LiveCD and then ran those scripts. That script will also allow you to clock your Eee to 900mhz, Asus underclocks them to 630mhz to maximize battery life, the script lets you clock back and forth using FN-F6.

I run compiz with quite a few effects (including burning down my windows) with no trouble, I am listening to shoutcast radio station using xmms, running compiz on a cube, 5 tabs open in firefox AND editing a picture in the gimp right now on my asus eee no trouble at all.

---

### Post by jmurrayil on 2008-04-13
I tried eeeXubuntu also on the eeePC 4G, but didn't like it either.  Installed Ubuntu 7.10 and all is fine (or close enough for me - Suspend still a problem and shutdown requires the power button 3 s hold to kill all power after Ubuntu shutdown and ends).  I used a USB flashdrives to boot into the LiveCD, easier and faster than a CD.  

Also found a low cost computer case for the eeePC- a leather bible cover with external pockets for the AC adapter, USB mouse, etc.  Works great.

---

### Post by jmurrayil on 2008-04-13
Here is the guide I used to install Ubuntu 7.10 on the eeePC.

[https://help.ubuntu.com/community/EeePC]("https://help.ubuntu.com/community/EeePC")

---

### Post by starcannon on 2008-04-14
use that script pack I linked in that earlier post, it will fix the shutdown issue, suspend will be a pita unless you compile a custom kernel, which would in turn require recompiling the stuff the script installs... I'm waiting until HH releases, it uses the kernel that has the options and that way once I have it all compiled I can just pin it out and be solved.

The Asus Eee with Ubuntu 8.04 is gonna be about as sweet as it gets for UMPC's running linux for awhile i think.

Some other low cost computer cases include the ones for $9.99 u.s. at any wal-mart or its ilk, normally used for portable DVD players.

---

### Post by Promaster91 on 2008-05-16
Does the script run on a 2g EEE Pc? I am trying to overclock it and I am having some problems.

---

