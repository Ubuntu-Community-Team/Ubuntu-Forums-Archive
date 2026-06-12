---
title: "Ubuntu installation problem ? pls help !"
date: 2006-09-11
forum: Installation &amp; Upgrades
---

### Post by marko2622 on 2006-09-11
**Hello people**.:D 

I also have a major problem with the Linux installation.:confused:  Ubuntu is my first expirience with any kind of linux software. I like the way it looks and i love the entire idea behind it all, and i would like to learn more about it, and start using it instead of windows xp.

I have: 500 mhz (intel)
        192 mb ram (128+64)

My PROBLEM is that when i try to install ubuntu desktop from the cd... everything goes fine... up until the point where it begins the 6 stages.. the first 4 stages are extremely slow, and at first i could not bealive that a stupid window with the time zone selection can take so long to load, then choosing the keyboard layout..:mad:  Sorry for the tone of my comment, but i tried to install 3 days (30 times).. Anyway the farthest i got is the "starting partitioner" where it freezes at 42% (sometimes earlier 28%). The cd-rom stil works.. but it doesent go more that 42% (and let me say that it takes me 30 min's to get to that point). 
Important to say the cd i use is okay. I tried it on my brothers computer (pentium IV + 256 ram) and it works faster and starts the ubuntu partitioner without any trouble.
I have an audio card ess1868 which is not recognized at first but i figured that it can be corrected. But this entire installation turned out to be very difficult. I hesitated to ask for any advice, cause i thougt i could do it on my own by reading some threads, other peoples comments, google search...
And i tried tweaking my bios.. turning off "PNP OS installed", turning of "onboard usb"... and many other things.

What should i do?? Perhaps try ubuntu lite :frown: 

I am clueless](*,) 

*Please help me with this. I know that this is a great product and i would love to try it out.*

---

### Post by rcatman on 2006-09-11
Gnome is very graphical and has a lot of features bundled into it. I'd recommend trying Xubuntu or Kubuntu. I installed Xubuntu on my old Dell Inspiron 3200 (p 233mhz, 164mb ram) and it ran great! I even installed KDE (apt-get xubuntu-desktop) and it ran like a dream! Even with all of KDE's graphical interfaces and features it was flawless. I'd recommend those over installing the ubuntu-desktop. 
What you can do is either download and burn Xubuntu and/or Kubuntu to a cd and install from there or install the ubuntu server version (make sure your internet would be working) and then apt-get xubuntu-desktop and/or kubuntu-desktop.:KS

---

### Post by marko2622 on 2006-09-12
thanx for the advice.:wink: 
To be honest i'm affraid that the same thing will occur with kubuntu and xubuntu.:roll: because i think that the whole thing is a hardware issue.

Luckuly the internet works.. i tried firefox before installing..

Either way i will give it a try.. but if that does not work..:twisted:

---

### Post by marko2622 on 2006-09-12
other advice and solutions are also welcome...

Is this the only way out.? #-o

---

### Post by dkartik on 2006-09-13
> **rcatman said:**
> Gnome is very graphical and has a lot of features bundled into it. I'd recommend trying Xubuntu or Kubuntu. I installed Xubuntu on my old Dell Inspiron 3200 (p 233mhz, 164mb ram) and it ran great! I even installed KDE (apt-get xubuntu-desktop) and it ran like a dream! Even with all of KDE's graphical interfaces and features it was flawless. I'd recommend those over installing the ubuntu-desktop. 
What you can do is either download and burn Xubuntu and/or Kubuntu to a cd and install from there or install the ubuntu server version (make sure your internet would be working) and then apt-get xubuntu-desktop and/or kubuntu-desktop.:KS

I'm also having the same issue with the partition freezing up on me when I'm installing on a computer at home, however, I know that my computer can handle the high graphics of gnome as it is not lacking anywhere in the processor/video card/RAM areas.  This also isn't the first time that I've installed Ubuntu, but it's behaving quite differently than it ever has before, and it's the same cd that I used to install it at work.

First things, when it's loading up from the cd, it goes on for about 5 minutes with these messages:
[some numbers] Buffer I/O error on device sda, logical block 0
[same numbers] sda: assuming drive cache: write through

Now the second line is either shows up twice, or four times, and then the entire message repeats with different numbers.  This goes on for about 5 minutes, then the live ubuntu finally boots up.  When I open up the places menu, I can see all of the hard drives, but every time I run the installer, the partitioner stops working at either 50% or 57%, and I can't quite figure it out.  My computer has 3 IDE hard drives, and two of them will be used for my wife's Windows install, and I was planning on using the third for Ubuntu.  If anyone else has had the same problems and has an answer of how to work around them, that would be great.  

David

---

### Post by dkartik on 2006-09-14
Hey Marko, I did some more poking around, and I got ubuntu working on my computer.  You should download the alternate cd instead of the desktop one, it starts the installation from the cd without having to go into the "live desktop."  With the installation running differently, I was able to get past that part of the install and am able to use Ubuntu now.  Anyways hope that helps, good luck.

---

### Post by marko2622 on 2006-09-14
Thanks a lot mate !!:D 

I will try out your advice as well.
At the moment i have the ubuntu server cd, although i have to admit that the alternate cd version now that you mention it sounds better.:cool: 

When i install the sevrer version... i suppose i dont have the graphic desktop (xwindows).. so i need to type what exactly to install it via internet connection.

apt get.... ??


Once again thank you very much people for all the advice so far !

---

### Post by marko2622 on 2006-09-14
maybe:

apt-get ubuntu-desktop 

?

---

### Post by dkartik on 2006-09-14
Yes there are ways to do that, I'll try to walk you through it, and I hope I'm touching on all the aspects.  First do you have an internet connection running on the computer you put the server on?  If so you can update and get gnome installed, but if it doesn't have access to the internet, then it won't work.  

So first things first, you need to type 
```
sudo vi /etc/apt/sources.list
```
This will bring up your sources list, where you'll need to uncomment out the universe and multiverse repositories.  Just do that by uncommenting them out.  

You will need to press 'i' in order to edit the text in here, and in order to save it when you are done, press the 'esc' key then ':wq' and that will save your changes.

First thing would be to put a # and a space before the one that says the CD at the top, so that it won't require you to put the cd back in to install new packages, then you'll see more below after blocks of comments that look like this:

```
# deb http://someurl/ [text that says universe or multiverse in there]

and 

deb-src http://sameurl/ [same text]
```

There will be a few of those, just remove the # and the space before them so that apt-get knows it can look there for those repositories as well.

After you complete changing your sources.list here are the next series of commands:

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo apt-get install gdm
sudo /etc/init.d/gdm start
sudo dpkg-reconfigure xserver-xorg

```
That should do it, but if you have any problems just post back here and I'll see what I can figure out.  And if anyone else notices that I've missed something, feel free to put in your two cents.  Once again, good luck.

---

### Post by marko2622 on 2006-09-14
wow !!:KS :KS :KS 

Hey thanx once again for such a complete and detailed explanation !=D> 

I will try that out & let you and other people (visiting these posts) know how it all went  !

Thnx for the luck :-\"  I might need some

---

### Post by rcatman on 2006-09-16
dkartik, very good advice. that's exactly what you have to do. 

The alternate cd is what I use. Why wait for live mode to boot up when all you want to do is format and install?

Once you have ubuntu up and running I'd recommend giving Kubuntu and Xubuntu a try. 

Enter either of these two commands from the terminal:
> sudo apt-get install kubuntu-desktop
sudo apt-get install xubuntu-desktop

If you like one, or dont, you can always remove it. 
IE
> sudo apt-get remove kubuntu-desktop

AS far as the hard drive problem, i'm still looking around the forums for people with similar issues. I'm still a bit new aswell.

---

