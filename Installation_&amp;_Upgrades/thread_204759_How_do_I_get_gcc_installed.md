---
title: "How do I get gcc installed?"
date: 2006-06-27
forum: Installation &amp; Upgrades
---

### Post by mwob on 2006-06-27
Hi,

I'm very new to Linux...I'm trying to give it a fair trial to see how it works for me...  Anyway, I'm having some trouble..

I have a speetouch USB modem, and I want to get it to work using this cool script: [http://steve-parker.org/speedtouchconf/](http://steve-parker.org/speedtouchconf/)

The problem is that a pre-req to that script is that you have "gcc", "make", "unzip", and "libc6-dev" installed.... How do I do this? I can verify that its not there - when I type "gcc" in a terminal it says command not found.

I tried "sudo apt-get install gcc", but I get an error complaining about "E:Pacakge not found". I get the same error when I try "make" or any of the others. Soooo, I tried opening the "Add/Remove programs", and switching to advanced. In there I could only find a reference to "gcc-4.0 -base", which it said was installed anyway (although it reported some "conflicts"). 

I also tried "sudo apt-get install build-essentials" as suggested elsewhere, but that gives the same "package not found error (is it trying to connect to the internet?)

This is driving me crazy!!! 

Many thanks

Matt.

---

### Post by Dr. Nick on 2006-06-27
**build-essential **is what you want, It will most likely be connecting to the internet. I assume you have no internet since your trying to get your modem going right?

It may be on the cd aswell I am not sure, Have you tried build-essential without the "s" on then end, or was that a typo?

---

### Post by FredB on 2006-06-27
And try to get - if you hardware can support it - an ethernet based modem. I suffered a lot of years because of USB ADSL modem :(

And for me speedtouch == nigthmare.

---

### Post by mwob on 2006-06-27
Thanks for the replies!

Dr Nick - I tried both "essential" and "essentials" and neither work for me (prob. becuase its trying to connect as you say and then that fails).

Soooo, when you say try the CD, I'm afraid my linux knowledge dries up ;) What do I need to do, search the CD for a file to run? Will it be an RPM?

Thanks for the info!

---

### Post by Dr. Nick on 2006-06-27
If it is on the cd then it should have picked it up for you when you tried to apt-get it, The cd is usually one source and then the other sources to get software are online. 

Not sure what you could do short of downloading all the packages needed from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and putting them on a removeable storage, or a shared portion of hard drive.

---

### Post by CaptSammy on 2006-06-27
I am having a devil of a time also with gcc. Attempting to apt-get build-essential I get broken package errors:
The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: gcc (>= 4:4.0) but it is not going to be installed
                   Depends: g++ (>= 4:4.0) but it is not going to be installed
E: Broken packages

Tried searching everywhere and nothing seems to display a fix for this.

---

### Post by Dr. Nick on 2006-06-27
[quote=CaptSammy]I am having a devil of a time also with gcc. Attempting to apt-get build-essential I get broken package errors:
The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: gcc (>= 4:4.0) but it is not going to be installed
                   Depends: g++ (>= 4:4.0) but it is not going to be installed
E: Broken packages

Tried searching everywhere and nothing seems to display a fix for this.[/quote]

Hmm, not sure what exactly that would be caused by.

A few things to try

Have you ran 

**sudo apt-get update**

then try to install build-essential?

Also what is the state of your system? Fresh install or a update from breezy?

---

### Post by CaptSammy on 2006-06-28
Fresh install of Dapper Ubuntu server, this ubuntu has been nothing but a hassle. I dont understand why this is so difficult. Fresh install on a plain ol Celeron D with Soundblaster Live card and a couple plain hard drives. Most every attempt to install just about anything pops with a broken package errors. Same with a Destop Dapper install. So can I assume that all the ubuntu packages arent actually all broken? 

edit: May have figured the issue, I placed a sources.list provided by myth directions, and it is pointing to breezy sources I think. Going to revert to original and give it a go...

---

### Post by aysiu on 2006-06-28
[quote=CaptSammy]Fresh install of Dapper Ubuntu server, this ubuntu has been nothing but a hassle. I dont understand why this is so difficult. Fresh install on a plain ol Celeron D with Soundblaster Live card and a couple plain hard drives. Most every attempt to install just about anything pops with a broken package errors. Same with a Destop Dapper install. So can I assume that all the ubuntu packages arent actually all broken? I thought Ubuntu was more mature than this....[/quote] Dependency errors almost always stem from conflicting repositories. Once you have a good sources.list, you shouldn't run into any dependency errors or broken packages.

Here are the exact steps you should take.

Put your CD in the drive--either the Desktop CD or Alternate CD.

Copy and paste (Shift-Insert) these commands: ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.old
sudo nano /etc/apt/sources.list
``` Delete (Control-K) everything in there. Then save (Control-X), confirm (Y), and exit (Enter). ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by CaptSammy on 2006-06-28
Thanks for the replies. I got it straight, reverted to my original list file. Although now I wonder if I should re-install from scratch, not sure if my previous installed items may have put me in a bad way. Anyone have a good sources list for building mythtv? Or should I stick with my original and add as I ferret out needed repositories?
Thanks again, that was frustrating.

---

### Post by aysiu on 2006-06-28
Try this: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by mwob on 2006-06-28
Glad you got it sorted CaptSammy,

I'm going to try enabling my cd as a repositry ([http://monkeyblog.org/ubuntu/installing/)](http://monkeyblog.org/ubuntu/installing/)). Hopefully that will do some magic and enable me to get gcc working. What peeves me off is that at no point during my install of Ubuntu did I ever get asked what pacakges I want to install..... I just booted teh CD and then commited it to HD...maybe thats the wrong way to go about it?

---

### Post by aysiu on 2006-06-28
The Alternate Install CD is more flexible and allows you to do a server install, a server then custom install, a regular install, an OEM install, etc.

The Desktop CD is intended for new users who might get confused by too many options. It just copies the Ubuntu installation to your hard disk and automatically installs Grub to the MBR.

---

### Post by mwob on 2006-06-28
Thanks for the info aysiu,

If I reach a dead end, can I download the alternate install and install it "over" the current linux install....Would I need to boot the CD or load it from my current Linux setup and go from there?

Geez, I hate asking such newbie questions (feel free to ask me anything about XP ;) )


Thanks!

---

### Post by aysiu on 2006-06-28
Yes, you can always install over an old installation, and you would need to boot from the CD.

---

