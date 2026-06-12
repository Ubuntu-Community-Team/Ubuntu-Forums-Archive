---
title: "Installing VNC into Ubuntu Server Raspberry Pi breaks ssh pipe and prevents reboot. W"
date: 2023-09-12
forum: Installation &amp; Upgrades
---

### Post by kierumcak on 2023-09-12
First time setting up a Pi. Only have basic familiarity with linux and operating systems. Right now I am doing the setup entirely with an ssd card and SSH. So if something prevents me from SSHing into the device I consider it "bricked" and start over.What I am doing right now I thought is quite simple. I am trying to use Ubuntu Server with my Raspberry Pi 4 because I thought that would lead to wider compatibility with libraries/programs that exist in the linux community. I figured since I am familiar with bash it would be fine.I realize the Raspberry Pi OS already has VNC built in but I really want to learn what is going on with Linux so I am purposefully making my life a bit difficult. Please when you answer feel free to explain in as much detail what I might want to know, would love to know more than just how to fix this.So what I do is the following	1	Install Ubuntu Server 64 bit onto my micro SD card configured with SSH via the Raspberry Pi Imager	2	Run the command I got from here sudo apt install xfce4 xfce4-goodies in hopes of installing VNC.	3	This command runs for a long time (hour or two) but eventually finishes.	4	If I am connected over SSH and leave the computer alone the ssh pipe will break. I can't ssh back in even after power cycling.	5	If I keep with the computer SSH does something I have never seen before and somehow gives a full screen GUI warning me about Needsrestart.And that's about where I'm at. A few observations I guess:	1	If I connect the sd to my computer and try to open etc/bin/bash in a text editor it is un-intelligable. Same with zsh. Many tutorials mention I might be able to edit these files to boot into safe mode, get out diagnostic info etc.	2	I have never before seen a full screen GUI pop up in vnc (except for like text editors and gdb). It's a purple screen with like an alert. And it will list like 2 things and say ok. I think it's something about Needsrestart or Daemons using outdated libraries. This pops up after the installation. I believe it just asks me to restart certain things.	3	Is there no way I can get to the logs/ssh history for the device from looking at the micro SD card on Ubuntu? See what went wrong? Is this only a RaspberryPI OS thing?	4	Part of me is wondering if it's an issue with the cheap but recommended AEGO Micro SD Card 32GB Mini sd Card UHS-1 Class 10 microsd 32gb I am using. I know SD cards aren't reliable. The first time this happened I had issues mounting it onto my Mac to wipe it. Couldn't first aid or anything. Had to use a different reader. However successive attempts have had the sd mount just fine. I don't really know how to tell if the SD failed.	5	Is there any way to convince my Mac to keep the SSH pipe open so I don't have to baby sit it and can step away while it does this long install and still observe the state after? (ssh breaks after the install)	6	This install seemed to create wider system issues. I remember ignoring the popup or just saying ok then having issues with other system things like when I tried to mess with ufw I got ERROR: '/etc/ufw/user.rules' is not writable could be unrelated. I may have messed up my users. I also couldn't install the script for my fan due to this error 'sudo apt-get install' is showing "Not using locking for read only file /var/lib/dpkg/lock" warning on Ubuntu Touch	7	Is it possible that VNC is fundamentally incompatible with Ubuntu Server? I am using that because the Raspberry Pi Imager only allows me to set up the SSH login+wifi if I install server. I don't have a keyboard/monitor for using Desktop to connect it to wifi+setup log in and can't find instructions how to modify its boot to do that. I always figured I could "install" a GUI into ubuntu server. But perhaps it is just fundamentally incompatible to tAny thoughts or tips would be greatly appreciated.Edit: I was able to reproduce this issue on a DigitalOcean Ubuntu server. Or at least the purple screen. It looked just like this It looked just like this. A giant purple screen with Daemons Using Outdated Librarysmultipathd.servicepackagekit.serviceunattended-upgrades.serviceOk | Cancel

---

### Post by kierumcak on 2023-09-12
I am sorry but the line breaks didnt make it in this post. Is there anywhere on this site that gives a guide on post formatting? I would look around but page loads on this site take 20+ seconds for me so its not very easy to find.

---

### Post by coffeecat on 2023-09-12
> **kierumcak said:**
> I am sorry but the line breaks didnt make it in this post. Is there anywhere on this site that gives a guide on post formatting? 

Identify and disable whichever browser add-on/extension you are using which is breaking forum functionality. A good start in finding the culprit is anything that interferes with javascript. The noscript extension is a notorious repeat offender in this regard.

The forum lagging you are experiencing is being experienced by everyone. Probably yet another ddos attack. We shall see.

---

### Post by MAFoElffen on 2023-09-12
My Raspberry Pi 4 (8GB) runs full blown Ubuntu Desktop very well. I installed it originally as Ubuntu Server Edition 20.04 LTS on MicroSD, installed what I wanted onto it, then converted it to boot from USB attached NVMe...

Since you are ssh'ing and VNC'ing into your's, I am assuming that you do not have it connected to a display(?) And probably through either WiFi or the Ethernet port?

Yes. Please reformat that frist posts so that it is easier to read. It's very hard for me to pick out any details from it.

---

### Post by TheFu on 2023-09-13
> **MAFoElffen said:**
>  Yes. Please reformat that frist posts so that it is easier to read. It's very hard for me to pick out any details from it.

Yep.  Walls of text don't get much help. Too hard to read.

BTW, I use noscript, but enable JS just for ubuntuforums.org and enough works for me.  The Advanced editor seems to work fine too, BTW.  Don't screw with fonts or colors. Stick with defaults.

These forums use BB-code, but very few posts need more than bold, code, quote and perhaps list tags. The Adv editor has buttons for those.

---

