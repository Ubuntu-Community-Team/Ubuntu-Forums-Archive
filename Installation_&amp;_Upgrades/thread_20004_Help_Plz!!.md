---
title: "Help Plz!!"
date: 2005-03-14
forum: Installation &amp; Upgrades
---

### Post by musti on 2005-03-14
Hello i don't know if i'm placing this in the right section...

I have 2 questions:
1.

Recently i installed ubuntu linix 

I followed install instructions but i accidently erased my hard drive 
So i said ahn no problem if i can't handle linux i install windows again

Linux installed ... -> I wanted to get on the internet so i made a connection in <Networking> i filled everything in right ... When i try to connect it says that i can't connect ... 

So i put in my modem - install - cd in -> /media/cdrom0/

I try to run Setup.exe -> No result it doesn't work 

So my question is how can i run exe files on linux (I'm sorry but i'm new to linux so please help me ...)

Question 2.

Because i couldn't install my modem and needed to get on the internet to get help i wanted to install windows again ... Cd goes in It boots for a moment -> black screen ... After 2 minutes Grub bootloader says Error 17 so i can't install windows again  :neutral: 

So please  [-o<  help me get my windows back on my pc ... because i need internet for school and i can't use it on linux

Heeeelp

Greetz Kev,

Thx in advance  8)

---

### Post by kassetra on 2005-03-14
[QUOTE=musti]
Linux installed ... -> I wanted to get on the internet so i made a connection in <Networking> i filled everything in right ... When i try to connect it says that i can't connect ... 

So i put in my modem - install - cd in -> /media/cdrom0/

I try to run Setup.exe -> No result it doesn't work 

So my question is how can i run exe files on linux (I'm sorry but i'm new to linux so please help me ...)
[/QUOTE]

Ok, let's deal with these two things first.
EXE files: exe files are of no use to you in Linux.  You can run them, but they do not install anything into Linux - instead with some extra applications installed, an exe file will get installed into a special environment.

Now, let's deal with your networking in Linux:
1. Go to Computer->System Configuration->Networking.
2. Tell me what you see under the Connections tab first of all.
Is there anything there?  There should be a "Type" and a "Device"....

---

### Post by bored2k on 2005-03-14
[QUOTE=kassetra]Ok, let's deal with these two things first.
EXE files: exe files are of no use to you in Linux.[/QUOTE]


I just noticed no newbie guide or FAQ that I have read has this information :-k

---

### Post by az on 2005-03-14
Do you have access to another computer to browse the internet?

Visit [www.linmodems.org](www.linmodems.org) and copy Scanmodem.gz to a floppy

Boot up ubuntu and copy scanmodem to your home directory.

Open up a terminal (console) and do
gunzip ScanModem.gz

then do
sudo ./ScanModem

Look at the information in the files it will create (modemdata)  It will tell you about your modem and what linux driver you need to use.  No, there is usually no linux driver with the cd that came with the modem.  There is no money in it for them to do so.

About the error 17, are you sure that you are booting from the cd?  Grub should not even start if you are booting from the cd.

Just in case, one way to erase grub and make your system completely unusable, is to type

sudo dd if=/dev/zero of=/dev/hda bs=446 count=1

Don't do that.  Really.  You do not want to go there unless you know what you are doing.  You didn't hear it from me.

---

### Post by kassetra on 2005-03-14
[QUOTE=bored2k]I just noticed no newbie guide or FAQ that I have read has this information :-k[/QUOTE]

Hmmm... I guess that would be something people need to know.

---

### Post by Xian on 2005-03-14
[QUOTE=kassetra]Hmmm... I guess that would be something people need to know.[/QUOTE]
The question being what section would you put it under .... "Just Got Here" perhaps?

---

### Post by Buffalo Soldier on 2005-03-15
[QUOTE=bored2k]I just noticed no newbie guide or FAQ that I have read has this information :-k[/QUOTE]
I guess it was so basic and simple to experience computer users that it is taken for granted that new computer users (especially to those who have never used anything else besides Windows XP) will fail to see that different OS uses different type of files and extensions.

I feel this problem is mostly faced by computer users who starts using computer with Windows XP. And are more uncomfortable in Linux than people who have used DOS or Windows 3.11

---

### Post by Cybermagellan on 2005-03-15
[QUOTE=kassetra]Hmmm... I guess that would be something people need to know.[/QUOTE]

I'm semi-new to linux myself (used it multiple times had bad experiences and left) and it's something that I have brought up at where I work where we have someone that is a linux worshiper, but the thing about it is....there is no "You are here->."  Kinda of sites/books/courses that you can look at/read/take that really explain to you what you need to know

*sits on soapbox*
LiveCD's are great. In the case of Knoppix (Holds CD up in hand) it's virtually like Windows so people make the transition to usage to it alot faster. In the case of GNOPPIX (Holds CD in other hand, told you I've tried a few distro's) it's alot like Mac OSX (which I'm typing on) on the layout so some people are familiar with that but Oooo the graphics are great.

I read a post where someone was telling a user here to get lost because they said they were using GNOPPIX and needed help. I think that is sad considering that Ubuntu Linux is plastered as being the platform on the GNOPPIX site. So here is a case of 1. Pretty thing breaks 2. Person WANTS to fix it but there is no documentation 3. Said person gets burned (I've experinced it before) by uber-*nix user 4. Bill Gates/Steve Jobs gets more money by Mr. User because they have an issue....well the numbers are staggering on the websites for help for Win/Mac vs. Linux.

So yeah while people might WANT to use Linux their scared because of it being different. Since Windows was first "combobulated" people are familiar with the BASIC>DOS>Windows>32Bit Windows> and soon 64 Bit Windows platform. Yeah you can laugh at me because I have read the "Linux for Dummies" book (Which isn't too favorable, "if I want a free OS why pay to learn it?") and you can say well you've been "stupified" by the lack of knowing what your using really...but the  thing about it is that's why it is so popular.

Linspire failed because they got dumb. They said well we'll be Lindows and they became the laughing stock of the converters (people really interested in Linux but don't know how to make the transition) because they thought the name would sell the idea....the name just cost them in the courts. I've said it on many occasions and I'll say it again...

You want people to use Linux....you don't need to make it look like Windows...you don't need to make it look like a Mac...just provide common sense documentation for it. That doesn't mean tell people...

*To download the update to your distro of linux open up a terminal and as root type apt-get dist-upgrade.* 

tell people what they care about...

*To download the newest version of whatever version of linux your using open up konsole and the command you want to use is apt-get dist-upgrade. This is like using DOS to download a new version of Operating System* 

Give people an analogy to what they know and they'll take it the rest of the way. I've always told people who were really big linux fans. Make a website. Tell people Step 1,2,3 how to do it and use things that people are used to on a day to day basis and watch them flock. As for myself I am a glutton for punishment I've been dealing with the same problem for the past 3 days and I keep going. I've already determined (because this is my wifes Mac) that once I get linux running straight then no more Windows except the ones in my office building.

*gets off soapbox*
*house orchastra plays "hurry up" music*

So I'd like to thank...

---

### Post by bored2k on 2005-03-15
[QUOTE=Cybermagellan]
I read a post where someone was telling a user here to get lost because they said they were using GNOPPIX and needed help. I think that is sad considering that Ubuntu Linux is plastered as being the platform on the GNOPPIX site. So here is a case of 1. Pretty thing breaks 2. Person WANTS to fix it but there is no documentation 3. 

So yeah while people might WANT to use Linux their scared because of it being different. Since Windows was first "combobulated" people are familiar with the BASIC>DOS>Windows>32Bit Windows> and soon 64 Bit Windows platform. 

*To download the update to your distro of linux open up a terminal and as root type apt-get dist-upgrade.* 

*To download the newest version of whatever version of linux your using open up konsole and the command you want to use is apt-get dist-upgrade. This is like using DOS to download a new version of Operating System* 
[/QUOTE]
Its true some apps have lacking documentation, but that is because, -remember- no one is paying Geek_X, who just made a killer app for free and is sharing it with the world. 

I really dont know what great documentation you are implying other OS's have, because from my lost 10yrs on Windows/Dos I can count with one hand the times the Help page of any application became useful. On the contrary, who doesnt love man pages?

On linux there is just too much to know about to have a throw in your face 3,000 page guide translated in 200languages+Klingon.

Sure I havent seen a no brainer ".exes wont open" , but I cant tell you the number of times server admins have told me "check this script for me", and I have to recur to man pages for help. *breathes*
First off you CAN NOT ask a newbie to use command line, its just not happening most of the times . A persone coming from XP will hate the fact that we try to make them use the commands weve grown to love. Synaptic > Smart upgrade is the way to go ;).


Edit -- > Its also just bad to ask a newbie to go CLI. apt-get upgrade? then getting a fullscreen of weird messages? Why not synaptic easy upgrade? Its easier for anyone coming from Apple/Win. Sure command line is a faster method we have grown to love, but not everyone wants to become a computing *connoisseur* .

---

### Post by Cybermagellan on 2005-03-15
> **bored2k]On linux there is just too much to know about to have a throw in your face 3,000 page guide translated in 200languages+Klingon.[/QUOTE]

I agree completely. And maybe I am jumping in the fire when I say most distro's come with 1000+ apps to use? Then the switches...then...you get the point.

[QUOTE=bored2k]Sure I havent seen a no brainer ".exes wont open"[/QUOTE]

No brainer to who? Remember what windows users have used for years?

[QUOTE=bored2k]First off you CAN NOT ask a newbie to use command line, its just not happening most of the times . A persone coming from XP will hate the fact that we try to make them use the commands weve grown to love. Synaptic > Smart upgrade is the way to go  said:**
> 

True....again I'm not arguing the fact...I'm just saying...Most people who come over to linux from Windows expect it to be just as easy to use sadly without a "Welcome to GNOME" Alot of people have to learn. OMG No Learning! Save my eyes!

[QUOTE=bored2k]Edit -- > Its also just bad to ask a newbie to go CLI. apt-get upgrade? then getting a fullscreen of weird messages? Why not synaptic easy upgrade? Its easier for anyone coming from Apple/Win. Sure command line is a faster method we have grown to love, but not everyone wants to become a computing *connoisseur* .

I've always had the outlook...challenge me to learn the hard stuff...THEN when I've got that mastered...give me the GUI. Does that work for everyone no. But then again offer two options. Option number 1.....APT....Option Number 2 ...Synaptic...people wanna become professionals...they'll learn APT and then backup to synaptic..

---

### Post by musti on 2005-03-15
Hi again 

My problems are fixed i'm installing windows again :P and if its done i'm going to make a multiboot system

Btw thx for the help

---

