---
title: "Problems with new 9.10 installation"
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by HoodedOne on 2009-10-10
OK, first a little background so you all know where I'm coming from... I'm a techie who has worked in IT (networking/server/DB programming).  I'm a longtime MSDN subscriber, currently running Windows 7 on both of my home computers, having beta tested Win7 since the first unstable release.  I was also an official Vista beta tester before that.  I have been something of a M$ loyalist, more out of familiarity and personal ease of use than out of any feeling of deep abiding superiority.

I've installed and tried (dual booted) various unix packages through the years, and I think that Ubuntu is the closest to the kind of mature, user-friendly, practical end-user OS that I've seen.  I've tried a couple of different versions of Ubuntu over the past few years, but I've never stuck with it that long.  From what I've been reading, and from what my Ubuntu-loyalist friends have been telling me, the latest builds are approaching the level of usability you find the more "mature" Windows operating systems, and I'm anxious to give it another go.  I like the idea of going completely open source and completely eliminating my reliance on Windows and Microsoft; what do you think -- are we there yet?  

I've been experimenting the past few days with dual booting into Ubuntu.  I first tried installing the latest stable build, 9.04, but when I ran the installed, the GRUB bootloader did not install correctly, and so when my computer tried to boot into the new OS for the first time, it just froze my computer at that point, with some kind of GRUB error displayed.  I ended up running a repair using my Win7 DVD, which fixed the bootloader so I could boot back into Windows.

I then downloaded the 9.10 beta CD, and tried installing it.  This worked without a hitch, and I am currently able to boot into either Win7 and Ubuntu.  I spent many hours playing with the Ubuntu installation, and especially as far as the GUI goes, found it to be much more friendly and usable than any previous Ubuntu build I'd tried.  

Inexplicably, after installing several software packages and spending a lot of time customizing/configuring this installation, the last time that I booted into Ubuntu, the OS could no longer find my network adapter (onboard Ethernet), and so I cannot get online.  It displays the message "no network devices available" and the network icon on the panel in the upper right corner of the screen shows a big red X on it.

I'm kind of at a standstill as to what I can do with this installation as long as I can't get online, and I have no idea what might be broken.

My other question is this -- one of the primary functions for which I use my home desktop computer is as something of a multimedia center.  It is very important for me to be able to use this computer to play high-resolution video files smoothly.  So far, I have not had a lot of luck with this.

I have an NVIDIA dual head video card (8600GT) with 2 monitors attached.  I did install the latest driver for my card from NVIDIA itself, and it did install properly and I can use the NVIDIA control panel to adjust OpenGL settings, etc., for the card.  

From what I've read, running an NVIDIA card with Ubuntu is not the ideal situation.  I've tried playing video files of various resolutions, using mplayer, the Gnome-specific mplayer, and VLC, all with substandard results.  Especially when viewing videos full-screen, they tend to be quite choppy, with a lot of dropped frames and sometimes this strange "flashing" affect where the entire screen seems to turn white for a frame or two occasionally.

I've tried all combinations of settings in mplayer and VLC with no real improvement from one output setting to the next.  

So my question is twofold -- (a) any ideas on how to get my install to recognize my ethernet card again, so I don't have to blank the partition and start anew with a completely new install and (b) is it worth it to keep working on this -- will I ever be able to get the kind of crystal-clear, smooth, high-res HD video that I am easily getting under Windows?

Oh, I didn't mention -- I am running the AMD64 version of Ubuntu 9.10.

Thanks in advance to anyone who can provide some help,
Aaron L.

---

### Post by HoodedOne on 2009-10-10
An update --

I'm not sure why, but when I booted back into my Ubuntu installation, it recognized the Ethernet adapter right away again, and I'm back online.  So my remaining question is about the NVidia adapter in Ubuntu and whether it's practical.  I'll keep researching it on my own, but I'll also watch this space for your suggestions.

Thanks!

---

### Post by Daniel1994 on 2009-10-10
I've used ubuntu(9.04) for about 8 months now, on an acer with nvidia graphics. And my experience is that ubuntu and nvidia goes hand in hand. Perhaps it's because you're running a beta version? Did you install the drivers like: system>admin>hardware drivers?

---

### Post by sandyd on 2009-10-10
did you try installing the drivers?

by running
```

jockey-gtk

```

---

### Post by bapoumba on 2009-10-10
Moved to Karmic.

---

### Post by ConXtionS on 2009-10-10
Hello Fellow Windows Dude....
 
I too have been told that ubuntu is ready for prime time.  While I do not have all the background in windows that you have, I am fairly skilled at it.
 
My Experience is mostly with networking, as I owned a small ISP.
 
Soo.........
 
I would consider 9.04 to be an unpolished alpha compared to what you and I are used too.  I dont mean that to sound derogitory at all.  It is simply that ubuntu is NOT windows.  There appears to be some PRIDE FACTOR in being a "LINUX DUDE or DUDETTE" so many things that windows does for you, Linux makes you figure out yourself.   I am not sure if that is good or bad yet.
 
Because the software is open source many of the programs are not well polished.   For instance, a couple weeks ago I decided that I was going learn LINUX finally.   There is a program for recording and viewing TV called MYTHBUNTU here.     As you know with media center and even a small understanding of what you want to do setup for MCE is a hour at most.   Well for linux the curve has been more harse.   This far in to the project I can tell you that today I finally figured out how to get my screen resolution correct.  LOL
 
It was 5 days of  little sleep and I did finally get the mythbox to record tv.  Its not perfect, and in a few months I think I can make it do what I WANT it to do.  I have ready many posts about mythtv here and over the net, and it seems that most people just give up.
 
So, those are the cons.... Its just not "Windows EASY"....
 
The plus's are the people.   I have went to every LINUX distro I know of, and the ubuntu people are BY FAR the kindest and most eager to help get your system running.  I am not saying that the really brilliant guys sit in the noobs forum waiting to answer yet another "ubuntu broke my puter" post. But it does seem if you a considerate, patient and are willing to help yourself that it seems anything CAN be done here.
 
Before I get hammered here I would like to say I realize that many of you work very hard making UBUNTU better.... I also understand that some of the best minds in the industry get paid by microsoft so I am not cutting what you have done down at all... But it is kind of a get what you pay for issue.
 
If you want it to just WORK out of the box, Windows still has a wide lead in my opinion.
If you want the best Media Center, again its Windows hands down...
 
If you want to help build a better OS, and you have the time to learn then I hope you will continue your journey in UBUNTU.....
 
Fair well and I hope I didnt anger anyone....
 
just my two cents
 
Jim

---

### Post by emarkay on 2009-10-11
Not to start a fray, but I have been with "PC's" since before PC's (Apple II) and for the past few of years have migrated to Ubuntu.  The only time I ever even use Windows is on my game PC that has one program - MS Flight Simulator 2004 (X-plane is a better sim, but I like the force feedback capability and views in FS).  Other than that I have not used Windows XP for easily 2 years, and have interfaced with numerous Win users and applications seamlessly - aside from a few restrictive websites that DEMAND IE, (bizarrely, including a few US Government sites!) and thus, I therefore ignore them.

I have yet to find a legit argument for Windows, aside from the following: You CAN sue  someone over it (you can't with Open Source) if it causes "lost wages", you are forced because some paranoid, milquetoast  IT person says so where you work, or you heard last century that Linux is hard and free software is bad.   :)

Also, remember Karmic is still BETA, not even RC yet, so there is much remaining to do.

---

### Post by VMC on 2009-10-11
HoodedOne , you might want to try the search function at the beginning of karmic section and search for nvidia. You will get a lot of hits, so just be patient and browse through the material. nvidia + ubuntu at google will also find some good choices. I don't have nVidia video so I can't be much assistance. I do know that many here do use nVidia with great success. 

Both you and ConXtionS need to understand that if you start off comparing Windows with Linux you will be disappointed at best.
Just for now have a dual boot and in time I think we and Ubuntu will grow on you. Eventually, when you get proficient with Linux.  You may even find yourself using Windows less and less. I know I have. Right now I only use Windows for Skype. To my surprise, I have used very little of Windows. Open Office has grown by leaps and bounds.

With using karmic, for me anyway, it now is acting like a real beta status. Very rock solid. Everything now works. I had issues with my video card, but now it's fixed. The "devs" are hard at work fixing broken programs (packages). Now I realize there are some things that Linux offers that Windows doesn't - more debug info. A much better log system, different ways to accomplish the same task. Windows now to me anyway seems boring.

It really comes down to your wants and needs. I feel I'm not giving up anything using Linux over Windows.

I heartily wish you the best on your new adventure of exploring the world of Linux and the way of the penguin.

---

### Post by lancest on 2009-10-11
> **ConXtionS said:**
> 
If you want it to just WORK out of the box, Windows still has a wide lead in my opinion.
Jim
Ok so you are Linux noob and have a right to your opinion. 
I used to work with Windows up to XP and can tell you in my experience Ubuntu is far easier to get going OFTB than at least XP. Ubuntu is significantly easier in my book any way you look at it.
[LIST]
[*]Canon (& obscure)cameras- no drivers needed
[*]3G Huawei modem- no drivers needed
[*]Many printers & HP 1020- drivers there or instant download. 
[*]Logitech USB headset- no drivers needed
[*]Many webcams -no drivers needed
[*]Apple and Logitech wireless keyboards- no drivers needed for special functions
  [/LIST]

This and more.I've seen alot of hardware on desktops and notbooks work instantly on Ubuntu that surely would have required alot more driver hunting on the internet than just installing Ubuntu.

Does Windows come with OFTB Office support including PDF creation? I've either got to waste money or go steal it with Windows. 

(Haven't heard good things about OFTB Vista drivers too and don't use it)
Windows may have a bit more polish in some areas but I hate to thing about it's many security by obscurity holes. I hope you aren't including Vista in this either because it's truly hated by many.

---

### Post by GeorgeVita on 2009-10-11
> **HoodedOne said:**
> ...I then downloaded the **9.10 beta** CD, and tried installing it. This worked without a hitch, and I am currently able to boot into either Win7 and Ubuntu. I spent many hours playing with the Ubuntu installation, and especially as far as the GUI goes, found it to be much more friendly and usable than any previous Ubuntu build I'd tried.

Inexplicably, **after installing several software packages** and spending a lot of time customizing/configuring this installation, **the last time that I booted into Ubuntu, the OS could no longer find my network adapter** (onboard Ethernet), and so I cannot get online. It displays the message "no network devices available" and the network icon on the panel in the upper right corner of the screen shows a big red X on it.

I'm kind of at a standstill as to what I can do with this installation as long as **I can't get online**, and I have no idea what might be broken.
> Ubuntu Karmic Koala is in development, use only for testing purposes!!!

Ubuntu 9.10 is still in development!
Last couple of days many bugs are on their 'way out' causing many new malfunctions (you can see a lot of kernel updates within updates)...

Regards,
George

---

