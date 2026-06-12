---
title: "How's Jaunty doing for you?"
date: 2009-02-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Mazza558 on 2009-02-16
Just a quick poll to see how people are coping with Jaunty in the middle of its cycle. Is it going well, or poorly for you?

---

### Post by PRGUY85 on 2009-02-16
I'm dual booting Kubuntu and Ubuntu Jaunty with latest updates.  Gotta say it runs great on a 4 year old laptop with most if not all effects running smoothly.  I'm very impressed with KDE 4.2 and how it's coming along in Kubuntu.  It really is maturing into a great, stable, modern desktop and at times I feel Gnome is falling behind (I am still a Gnome guy). Also, I am still waiting for Ubuntu to display the new notification system (KDE's unified notification system rocks).  

All in all, everything is working great.

---

### Post by jerrylamos on 2009-02-16
Biggest pain is two of my four test machines won't boot unless xorg.conf is set to "NoAccel".  That's a known bug that was posted in the Alpha announcement two months ago.  Yes, they've got Intel graphics controllers.
With "NoAccel" screen response is annoyingly slow especially scroll.

Another gripe is install partitioner which has had various problems.  The resort there is to download the "alternate" which doesn't allow trial before install.  Trial is pretty important at Alpha time because various features could be broken.

And of course sound which works then doesn't or is scratchy or whatever.  At the moment is working I think.

I'm pretty much using jaunty on the test machines O.K.  I like the boot and shutdown speeds.

Jerry

---

### Post by MacUntu on 2009-02-16
Boring. Nothing bad happens. boots quite fast, Gnome loading could be faster, no issues with EXT4. Hardware of my test machine is not up-to-date so there aren't even hardware related problems. Boo!

---

### Post by markbuntu on 2009-02-16
I could only get Jaunty installed by running the live cd and opening a terminal and

ubuquity --no-migration-assistant

I have 6 OSs on multiple hard drives/partitions on this machine some of which are broken/abandoned. Migration assistant just could not deal with that so it crashed ubiquity and left me without grub or initrd etc but the above worked. Now for UbuntuStudio trials.....

---

### Post by Cybie257 on 2009-02-16
Tested out Alpha 4 64 bit on my laptop. Unfortunately, my 4 gigs of ram only show up as 2.9 gigs and the sound is scratchy and the synaptics touch pad isn't working. 

I tested with 64 bit 8.10 and everything works great, except it also shows 2.9 gigs of RAM also. It's a known issue and some have fixed it with something in the BIOS with Memory Hole something. (sorry, can't remember exact terminology. 

I also tried the 32 bit version Jaunty, all my RAM shows up as with any other OS (3.4-3.6 GIGs). But again, the Synaptics touchpad no-workie :( , and the sound was scratchy.

Understanding it's only an Alpha version, I am still anxious to try out future releases and hope all the issues are worked out for the final release. I have faith in the Ubuntu Team to do so as they always come through with a good end product for the major release. 

Overall, I like the speed of Jaunty, just can't use it without my touchpad. Next attempt is on my tower computer. Have to finish my homework assignment first! LOL. 

-Cybie

---

### Post by navsnipe on 2009-02-16
Overall I've had good results.  Seems a bit faster than my Intrepid install that I have been using for 1 1/2 months.

The main issue is the same CD/DVD bugs which has also plagued my Hardy and Intrepid installations  The CD eject bug (the tray comes out and then right back in again) and cannot burn a valid DVD.  My DVD drive is an LG GH22NS30 which works fine in Windows XP.  I hope this is soon fixed as I have converted to Linux/Ubuntu after using MS products for about 18 years and enjoy the change.

---

### Post by Gramps on 2009-02-16
I have it running on an old 1.2 MHz AMD with 768 mb of ram, ext4. I can't see that it boots any faster but I had XP in this machine before so I really don't have anything to compare it to,

mp3 playback sometimes is scratchy and I don't think that it's the mp3's as they are fine on my 8.10 laptop. Also using Banshee when trying to play tunes in the library it will play maybe one or 2 then quit. The most has been 7 then it quit.

Doesn't detect my monitor, I changed for an older crt to a new lcd after install. Resolution is fine so I guess this really isn't a problem. 

This is not my main PC so it doesn't get a normal work out but so far so good. It has survived several updates so far. As time permits I add more stuff to make it more of a clone of my 8.10.

---

### Post by duanedesign on 2009-02-16
> **Cybie257 said:**
> Tested out Alpha 4 64 bit on my laptop. The sound is scratchy and the synaptics touch pad isn't working. 


The touchpad is a known bug, see the link below.
[http://www.ubuntu.com/testing/jaunty/alpha4#Known%20Issues](http://www.ubuntu.com/testing/jaunty/alpha4#Known%20Issues)

CRACKLING SOUND

NOTE: that we have been seeing PCM channels becoming muted during updates without user intervention so it is worth checking your Alsa PCM mixer level if you are suddenly getting crackling sound when sound is supposed to be being produced.

In terminal type the command below and check your PCM mixer level:

alsamixer -Dhw 

Hope these help:)
Dh

---

### Post by autocrosser on 2009-02-16
Running the current Jaunty (Gnome-32bit) with a "almost" new X58 Intel system--just built a Gigabyte GA-EX58-UD4P, 6G of G.Skill DDR3 1600 ram & i7 Core2 920--Everything works as planned (I checked for three months before making this one) & I'm moving to 64bit with the next testing cycle. 

I have to say that the i7 Core2 920 is flat-out a screamer!!! I have it mildly O/C at 3GHZ---I number crunch BOINC units & seeing 8 cores burn thru work units is astounding (The i7 Core2 series runs 4 real plus 4 hyperthreading cores)--Temps at this clock under full load run in the low to mid 50c range--I run my Zalman 9700 from my last bulid--they really fast created a adapter to mount to the 1366 package....All-in-all, a system that will upgrade easy for the next couple of years...

---

### Post by plun on 2009-02-17
Good and Ok for a "geek".;)

On key areas **for newbies** its nothing.

art-work and multimedia is still a complete mess...as with Gutsy, Hardy, and Intrepid. :(

---

### Post by lithorus on 2009-02-17
Where is the "Terrible. Completely stable in its current state." option ?

---

### Post by howlingmadhowie on 2009-02-17
> **Cybie257 said:**
> Tested out Alpha 4 64 bit on my laptop. Unfortunately, my 4 gigs of ram only show up as 2.9 gigs and the sound is scratchy and the synaptics touch pad isn't working. 

I tested with 64 bit 8.10 and everything works great, except it also shows 2.9 gigs of RAM also. It's a known issue and some have fixed it with something in the BIOS with Memory Hole something. (sorry, can't remember exact terminology. 

I also tried the 32 bit version Jaunty, all my RAM shows up as with any other OS (3.4-3.6 GIGs). But again, the Synaptics touchpad no-workie :( , and the sound was scratchy.

Understanding it's only an Alpha version, I am still anxious to try out future releases and hope all the issues are worked out for the final release. I have faith in the Ubuntu Team to do so as they always come through with a good end product for the major release. 

Overall, I like the speed of Jaunty, just can't use it without my touchpad. Next attempt is on my tower computer. Have to finish my homework assignment first! LOL. 

-Cybie

the memory whole is about where input and output mappings are held. usually in a 32bit system this is before 0xFFFFFFFF. when you build a linux kernel you can set the size of the input/output area. i think the ubuntu devs select 1 GB for this. now just to make life easy, the motherboard manufacturers set these addresses as default, so some of your ram is masked even on 64bit systems. you can change this in your bios to have your I/O at a different place in the 64bit address space. however, if you do that i can imagine 32bit operating systems having problems.

---

### Post by ronacc on 2009-02-17
I'm having to try to duplicate other peoples bugs to have any fun :D

---

### Post by W2IBC on 2009-02-17
> **ronacc said:**
> I'm having to try to duplicate other peoples bugs to have any fun :D

lol. 

i did a fresh install on my main box. which is a good sign on how well it is working with the few bugs i have ran across.

---

