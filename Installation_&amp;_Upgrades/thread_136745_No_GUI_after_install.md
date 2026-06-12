---
title: "No GUI after install"
date: 2006-02-26
forum: Installation &amp; Upgrades
---

### Post by Germ on 2006-02-26
Hi there!
   I´m new to this world of Linux and was trying to install Ubuntu in my laptop, but every time I do. I get an error message saying something like "Xserver not able to to start"
  I get a command line screen but no GUI. I guess this has something to do with my graphic card (ATI Radeon Xpress 200M) but being new to Linux I have no idea what to do.
   I installed Suse 10 on my daughter´s  pc with no problems, but I have been recommended Ubuntu as a beguinner distro. I still haven´t been able to use Linux for web browsing (again drivers isues) but haven´t really worked too hard on it as I want to get the Ubuntu problem out of the way first.
   I would apprecciate any help on this subject as I want to get Linux working and my knowledge on it working soon as a new musical application is to be released  (Energy XT2) for Linux.\\:D/ 
   Thanks to anyone willing to help me with this issue.
          Germ :twisted:

---

### Post by BeatBoxRocker on 2006-02-26
Exec this at the command line to reconfigure X: sudo dpkg-reconfigure xserver-xorg

Check the options and see if there's something wrong.

Saludos!

---

### Post by Germ on 2006-02-27
Thanks I will try that and see what the results are!:) 
  I find it kind of funny that it didn´t seem to recognize my video card :rolleyes: 
    Anyway. I might go the Kubuntu way as I seem to like KDE better than Gnome. I just find my way around a bit easier with it even though I like the G look better.
   Thanks again. I will post any results I get as soon as possible.
           Germ.:twisted:

---

### Post by Germ on 2006-02-27
Ok tried that line you recomended and I got a " No Xserver-Xorg" installed message :-k 
  Kindda weird. Anyway. Now I installed Suse 10 instead and even thought it is working like a breze in my laptop (no problems whatsoever with video card even thought I don´t have hardware rendering) but I can´t connect to the internet. I guess I´ll have to work out a bit more than I expected on this OS :confused:  But I have taken it as a personal challenge :twisted: 
   Thanks for the help.
       Germ:twisted:

---

### Post by opensourcerocks on 2006-02-27
Hey Dude, 
Having the same problem as you are.
[http://ubuntuforums.org/showthread.php?t=136299](http://ubuntuforums.org/showthread.php?t=136299)
I wonder if it is the 64 bit causing the problem.
Are you using 64 bit?

---

### Post by opensourcerocks on 2006-02-27
Have you tried the live cd?
I have very limited bandwidth which only allows for a bout on 700 mg file a month.

---

### Post by k5knt on 2006-02-27
[QUOTE=Germ]Ok tried that line you recomended and I got a " No Xserver-Xorg" installed message :-k 
  Kindda weird. Anyway. Now I installed Suse 10 instead and even thought it is working like a breze in my laptop (no problems whatsoever with video card even thought I don´t have hardware rendering) but I can´t connect to the internet. I guess I´ll have to work out a bit more than I expected on this OS :confused:  But I have taken it as a personal challenge :twisted: 
   Thanks for the help.
       Germ:twisted:[/QUOTE]

I have the same video card as you, on a Toshiba Satellite A105 notebook. I also tried SUSE with the same results.  Check the thread I started [here]("http://ubuntuforums.org/showthread.php?t=137343"). 

Try reinstalling Ubuntu. The next time X fails reboot and select "Recovery Mode". This will allow you to edit the */etc/X11/xorg.conf* file.

At the command prompt type:
```
cd /etc/X11
cp xorg.conf xorg.conf.org
```
This takes you to the X11 directory and then makes a copy of the file. Now type: 
```
 nano xorg.conf
```
or 
```
 vim xorg.conf
```

And add the following line to the end of the "Device" section:

```
option        "noaccel"
``` 

Note many here use the nano editor. I prefer vim. I think nano might be easier to use, I just learned on vim. ;) 

Here is the relevent section of my xorg.conf file.
```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Xpress 200M (RC410)"
	Driver		"ati"
	BusID		"PCI:1:5:0"
	# This option MUST be added for X to start
	option		"noaccel"
EndSection
```

After saving the file reboot and you should get your desktop but without hardware acceleration (I believe).  

I'm still working on getting other drivers sucessfully installed.

Hope this helps.

Kent

---

### Post by opensourcerocks on 2006-02-27
Well this work for my Shappier Ati X700 card as well.
Also os hardware acceleration something that I should be concearned about losing.

Thanks also for the help

---

### Post by k5knt on 2006-02-28
Losing acceleration and whether or not it is important is kind of a personal thing. If you do gaming or use other applications that are graphic intensive it might be a problem. 

I installed planet penguin racer and the graphics were so slow and choppy, that I couldn't get past the initial menu screen. I haven't tried playing DVDs at this point so I'm not sure if that is affected or not.

Kent

---

### Post by opensourcerocks on 2006-02-28
Thanks for the reply:) 
I will be watching dvds so, I think :-k 
I will have to wait for a version that works.:-? 
Thanks again

(Although kind of dissapointed):cry: 
I like UBUNTU:p

---

