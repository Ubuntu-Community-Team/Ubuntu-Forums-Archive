---
title: "ACPI=off problems"
date: 2007-09-17
forum: Installation &amp; Upgrades
---

### Post by chrini on 2007-09-17
Hello,

So I want to install ubuntu on an old K6-3 system and I've been getting an ACPI error, so I set acpi=off in the boot terminal and it actually made more progress than before, except now a "frequency out of range" message scrolls across my screen (it seems to be a message from my monitor, not ubuntu). I was wondering if anyone has any ideas as to how to fix this problem?

---

### Post by Pumalite on 2007-09-17
Tell us the specs of an 'old K6-3 system'

---

### Post by Pumalite on 2007-09-17
If you have finished installing your system, you might need to configure your xserver.

---

### Post by chrini on 2007-09-17
The K6-3 is 450 MHz, what else do you need to know (I'm at work and don't have the specs in front of me so I'll have to post any extra specs later tonight). 

Also, I have not yet gotten Ubuntu to install... I am not even getting to the installation process. I can make it to the boot options and then after that I type in the acpi=off command to get by the acpi error and then after that my screen flashes black and then I get the frequency out of range message.... let me know if you need any other info and I'll try to let you know as much as possible. I'll be able to give you the mobo name once I get back as well, if that will help...

Oh, and the system has 256 MB of Ram and a cheap, used vid card that I got for a temporary fix at a local computer shop... let me know what else you need.

---

### Post by Pumalite on 2007-09-17
256 MB RAM>Xubuntu Alternate CD: [http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)

---

### Post by chrini on 2007-09-17
Ok.... I think I have that at my house, I had to use it to put ubuntu on another old system.... I guess I thought that it might be a bigger issue and didn't think about using the alternate installer.... If I'm still having problems I'll be sure to let you know what's going on tonight. Thanks for the tips.

---

### Post by Pumalite on 2007-09-17
You are welcome. Good luck.

---

### Post by fwojciec on 2007-09-17
> **chrini said:**
> Hello,

So I want to install ubuntu on an old K6-3 system and I've been getting an ACPI error, so I set acpi=off in the boot terminal and it actually made more progress than before, except now a "frequency out of range" message scrolls across my screen (it seems to be a message from my monitor, not ubuntu). I was wondering if anyone has any ideas as to how to fix this problem?

This has nothing to do with acpi or your computer not being powerful enough to run ubuntu - this means that your xorg.conf is misconfigured (the computer, or the video card more specifically, is trying to display something that the monitor is not physically able to display).

Try running something like "sudo dpkg-reconfigure xserver-xorg" - search the forums for more info about this.

---

### Post by Pumalite on 2007-09-17
Anything heavier than Xubuntu will run too slow in your system.

---

### Post by chrini on 2007-09-17
Thanks for your replies... I tired the Alternate CD and same message... It makes since that it would be the video card since it is a message from the monitor (I can tell by the dialogue box). So I'll try to run that command.. do I need to run that in a plain text command line or in the boot up option? And what exactly does that specific command do? So that I know for future reference. Thanks again...

---

### Post by Pumalite on 2007-09-17
If you end up with blank screen: Ctrl+Alt+F1 to get command line.
At the command line:
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
Choose most defaults, choose 'vesa' as the driver, then: startx
If need be: sudo /etc/init.d/gdm start

---

### Post by chrini on 2007-09-18
Thanks... I'll give that a try, however, I'm not sure if I can even do that unless I can get to the command line before starting the install (like at the install options interface). If I can do that, then it won't be a probelm, but if I have to actually select install, then I think I lose all video. Because the screen is not only black, but it is acting as though it isn't getting any video from the video card.... I'll try what you told me to do first (when I get back from work) and then let you know how it goes.... I also have another cheap video card that I cah try out and see if that fixes the problem.... you never know.

p.s. I forgot to mention (if it is of any help) that I am using an AGP video card (I got it used at a local computer shop).

---

### Post by Pumalite on 2007-09-18
It's supposed to do that. Just install and then apply my commands.

---

### Post by chrini on 2007-09-18
Oh, while I am on here I have an unrealted Ubuntu question for anyone who knows something about Hard Drives (if you don't then just ignore this question). I have an 80 gig Seagate HDD (I'll give some of the specs below) that I can't get my computer to recognize. I've read a ton of threads and forums to search for an answer but  I have not found any that are either cost effective or reasonable. I can hear the drive spin up and maybe (maybe) hear a clanking noise as it trys to load (but only once, and it seems that I have heard it in working drives before). Other than that, it just won't be recognized by any of my computers (even my external HDD enclosure). Anyone know of a simple way to try to fix it? I have no important data on it, I would like to use it though if I can get it to work.

Specs:

Seagate U6 ST380020A
Frimware 3.9

Let me know if you need anything else.

---

### Post by chrini on 2007-09-18
What do you mean "It is suppose to do that".... how can I install it if I can't see the installer?

---

### Post by Pumalite on 2007-09-18
If you cannot see the installer you have major problems and they are not related to your xserver.

Are you using the Alternate CD?

---

### Post by chrini on 2007-09-18
Yea, I used the alternate CD (I think it says text mode installer on the menu? I can't remember). But yea, it boots up fine to the installer menu, I press F6 to add acpi=off in the boot option (because if I don't then I get an acpi error) it loads the kernel, says that something (I can't remember the name, some kind of linux word) has logged in and what not, then the screen kind of flashes black (as much as it can flash from black screen, to another black screen). And then I get the message from the monitor that the frequency is out of range. I know it is from the monitor because it has the blue dialog box floating around like other message I've gotten from this Gateway monitor.

I think it sounds like a video card issue, but I just don't understand why it would show anything from the installer if it was the video card.

---

### Post by Pumalite on 2007-09-18
In that case, see if you can get a command line with Ctrl+Alt+F1

---

### Post by chrini on 2007-09-18
Ok, I'll give it a try this evening... thanks, and I'll let you know how it goes.

---

### Post by Pumalite on 2007-09-18
You are welcome. I'll be here.

---

### Post by chrini on 2007-09-18
Ok, I cannot open a command line at the installer menu.... so I'm not sure what to do.. I tried putting the other (pci, instead of AGP) vid card in to see if that worked, but I couldn't even get it to work at all. I might just be SOL in this case. I am going to try to install windows, just to see if that one does the same thing. If you have any other ideas as to how to fix this then please let me know. Thanks.

---

### Post by Pumalite on 2007-09-18
Try installing something else. See if your hardware works.

---

### Post by chrini on 2007-09-18
Alright, now we're getting somewhere... I got that pci video card to work so now I can test it with that.. I'll let you know how it works...

---

### Post by chrini on 2007-09-18
Finally, the installer!!!!!

Ok, I think it is working now... obviously the video card. So do you think that the video card is bad? Or is it worth keeping around? I might install Ubuntu with the working pci card, and then see how it reacts with agp card.

Thanks for your help... I really appreciate it!

---

### Post by Pumalite on 2007-09-18
Glad it finally worked! Stick to the card that works for the time being. When you get more used to Ubuntu you can start trying other things.

---

### Post by chrini on 2007-09-18
Yea, I'll use the current one, and I'll take note of what you initially told me to pass in the command line. I've been using ubuntu at work for the past 3 or 4 moths, so I am somewhat used to it. But no where near an expert. Thanks again.

---

### Post by Pumalite on 2007-09-18
We all start as newbies. I consider myself one. (that way I can keep on learning).

---

### Post by chrini on 2007-09-19
Not sure if anyone is still looking at this post, but I resolved the video issue and now I have another. The alternate installer freezes up at about 25% of the base installation process. And the regular installer freezes up in the loading process of the installer. Any ideas? 

I think it is an HDD issue, because I discovered that I can't even get my motherboard/bios to recognize my HDD, which would explain why it would freeze up in the base installation, because it has nowhere to put anything. Anyways, that is my thoughts. Any other suggestions?

Specs:
Motherboard: S7-MVP3 (VIA Chipset)
CPU: AMD K6-iii, 450 MHz
RAM: 196MB PC133 SDRAM
Video: Used 3dfx(?) [I got it at a computer shop used with no info]
HDD1: WD400 [model: WD400BB-00JHA0]
HDD2: Maxtor [sorry, forgot to write it down...let's just look at one for now]

---

