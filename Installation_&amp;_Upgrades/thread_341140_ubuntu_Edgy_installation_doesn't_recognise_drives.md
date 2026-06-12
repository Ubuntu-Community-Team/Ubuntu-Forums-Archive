---
title: "ubuntu Edgy installation doesn't recognise drives"
date: 2007-01-18
forum: Installation &amp; Upgrades
---

### Post by X-2 on 2007-01-18
Hi,

I am new to Linux and having problems installing ubuntu 6.10 Edgy. I have tried to install the alternate on my PC that has windows XP already installed.

The installation always halts at finding drives on the PC, it just can't recognise any of the drives. I have checked that iso burnt was ok, I checked the MD5 sum as well. Also downloaded the iso several times and burnt using 4X speed etc.

The PC has 2 drives both ide and 1 dvd rw drive. Tried using a command line (can't remember properly) on booting but I think that was used to detect SATA drives.  

Any kind of help will be appreciated!

Thanks.

Note: Tried to install using desktop Live but I can't change the resolution and that affects the installation, cos I can't even press ok or next which is hidden at the bottom of the screen, resizing window doesn't help either :(. In any case I'd like to install using alternate.

---

### Post by j19sch on 2007-01-18
If you post some more hardware details, people who know more than I do, might be able to help you. What motherboard? What devices?

Only thing I can think of is a RAID-problem or a master/slave problem.
Do you have two IDE-drives connected to one IDE-slot? And is the jumper of one drive set to master and the other to slave? Don't know if that could be the problem, but it gives you something to do, 'till you get some other replies...:twisted: 

Joep

---

### Post by X-2 on 2007-01-18
Thanks for your thoughts.

The PC I'm trying to install in has an old mb Gigabyte GA-6WMMC7 but it runs with XP home with no probs. Got 256mb ram and the two hd are on ide cable to one ide slot and yes I have checked and made sure 1st hd is primary master and the other primary slave (jumpers).

Other devices are only pci slots used for usb 2 and soundcard creative soundblaster.

I have no problem with that configuration running XP and I added the 2nd hd to install ubuntu on it. Not to sure if the pci slots might be causing the problem but the problem just lies within detecting my hd's.

---

### Post by j19sch on 2007-01-18
Two more questions:
1. Does the live CD detect the hard drives?
2. Have you considered temporarily disconnecting the Windows HD and then try to install Ubuntu? Not that it would solve much, but it might help pinpoint the problem.

---

### Post by X-2 on 2007-01-18
I tried using the Live CD again it detects my floppy drive and dvd drive but doesn't detect the hard drives properly.

And yeah also tried to install to just the empty hd with no luck :(. I'll try that method again tonight if I have time. Please give any random thoughts about solving this problem and I might get lucky with the installation.

---

### Post by Malevolution on 2007-02-02
I'm seeing precisely the same problem, which I posted last night [here](=http://www.ubuntuforums.org/showthread.php?t=252023).  I'll copy and paste what I put there.

I'm seeing exactly the same problem with edgy eft. I'm trying to install on an Inspiron 1501 with the stock HDD setup -- 60 gig, 5400 rpm "sata" at least as they put it.

No matter what I do, Ubuntu does not see *any* partition on it. I have 30 gigs of it etched out for Windows XP (a dreadful necessity), and with the remaining space I've tried a couple of things to try to get ubuntu to recognize the HDD.

Sabayon sees the entire HDD just fine, including Windows' NTFS partition. With GParted on Sabayon I've tried the following with the non-Windows 30 gig portion:

Two 15 gig partitions on reiserfs -- nothing found by ubuntu
One 15 gig partition on ext2, the remaining 15 gigs raw / unformatted -- nothing found by ubuntu

As I'm new to linux (since a passing familiarity with freebsd some 12 years ago), I wanted to try Ubuntu because it's hailed as the best for newbies -- Sabayon, the first I've tried, is a friend's favorite that I just don't have the knowledge to play with now. It sees the partitions, though :/

---

### Post by X-2 on 2007-02-02
Hi Malevolution,

I kind of fixed the problem of installing ubuntu with two solutions, but I'm not sure if you can use them because you are using a laptop.

1. First of all I tried installing on a completely different PC with the same kind of configuration as in 2 HD, except better memory and Graphics Card and without a TFT monitor. And the install was a breeze, what I'm trying to figure is transferring the ubuntu HD onto my comp :( .

2. I tried installing with only 1 clean HD so without my Primary XP HD. It was installing fine as well but right at the end of install there's always a problem as in it can't find a specific file etc. 

All I can say is for some reason ubuntu doesn't recognise certain HD's at all. Thats all from my experience.

---

### Post by Malevolution on 2007-02-02
Thanks for the reply, X-2.

> **X-2 said:**
> All I can say is for some reason ubuntu doesn't recognise certain HD's at all. Thats all from my experience.

Seems that way.  And part of the reason I came to Ubuntu was that I was having problems in Sabayon, like a complete inability to access the user accounts configuration, which is simply, apparently a [known issue](http://www.sabayonlinux.org/forum/viewtopic.php?t=3140&highlight=user+accounts) for which, well, there's no working workaround.

So my first two user experiences with linux have both been bombs.  I'm beginning to see why folks stick with Windows. :(

---

### Post by X-2 on 2007-02-02
> **Malevolution said:**
> 
So my first two user experiences with linux have both been bombs.  I'm beginning to see why folks stick with Windows. :(

I know what you mean, I tried several times even before I got ubuntu running on a separate PC. My advice is just take a break from linux installations for couple of days or a week and try it again.

I am not giving up yet cos I really wanna use a linux on my PC :D .

---

### Post by Malevolution on 2007-02-02
> **X-2 said:**
> I know what you mean, I tried several times even before I got ubuntu running on a separate PC. My advice is just take a break from linux installations for couple of days or a week and try it again.

Oh, I'll give it a rest once I get *truly* frustrated.  I'm not there yet -- at least this is an insurmountable roadblock for the time being.  There's still the desktop PC to try out.

> I am not giving up yet cos I really wanna use a linux on my PC :D .

Neither am I...  Might go back to Sabayon; my linux addict friend showed me what it can do and, well, Wow.  Pretty; pretty.

if I can keep from using Windows except where *absolutely* necessary (e.g. for work), that's what I'd like.  The way I see it, linux should be able to do about 3 of 4 things I do on a computer (hey, I'm a PC gamer; there is a reason to keep Windows!), and look better doing it.

Bugger Vista.

---

### Post by Sebs0r on 2007-02-05
The thing i don't like about linux (since im a newb) all the command line stuff... how am i supposed to know what that stuff means. Anyway, to get the CD to recognise your HDD i found pressing F6 at the installation menu (leading you to other boot parameters) just add the word "irqpoll" between the second and third section and everything should be fine.... give that a try and se what happens.

---

### Post by Sebs0r on 2007-02-06
Quick update: irqpoll solves nothing - it just ignores the problem. To fix the issue, i found the "pci=nomsi" command worked well.

Give that a shot

---

