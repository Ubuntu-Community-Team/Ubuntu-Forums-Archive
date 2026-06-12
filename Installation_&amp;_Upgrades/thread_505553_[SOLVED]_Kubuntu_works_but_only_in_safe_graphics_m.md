---
title: "[SOLVED] Kubuntu works but only in safe graphics mode."
date: 2007-07-20
forum: Installation &amp; Upgrades
---

### Post by NeillHog on 2007-07-20
I am attempting to install Kubuntu to my Windows PC.
The install was OK and starting normally from the CD works. As long as I only move the mouse then everything is OK. Some programmes will start bút as soon as I get started on (for example) Konqueror then everything locks up except the mouse which will still move but no longer click. The only way out is to restart the PC.

If however I start in Safe Graphics Mode then everything runs normally and I can do everything.

I have installed to the PC and here the symptons are the same except that there is no safe graphics mode available so the installed version always freezes on me shortly after trying to do something.

Many people have written about graphics problems during installation but I can not find anyone who has got this far before the problem appears.

The problem exists with 7.04 and 6.06 although I have only installed 7.04 - 6.06 I have only tried from CD

I should mention that the graphic card has two outputs but the problem appears on both.
I should also mention that I am very very new to this so I may not immediately understand your answer but thank you anyway.

I am going to make this work some how!

Have fun

Neill

---

### Post by myoungf1 on 2007-07-20
what are your system specs ie graphics card specs etc

---

### Post by NeillHog on 2007-07-20
Sorry! I knew there was something I had forgotten.

The processor is a Celeron running at 2.7GHz.
I have 512MB of Ram and GBs of hard disc.

The graphics card is a NVIDIA GeForce Ti4200 on PCI-Bus 1.

It has two outputs. One VGA and one DVI. Each one currently has a monitor connected although I have tried with only one connected.
In Windows I run extended desk top with both monitors set to 1280x1024.

Thanks for asking.

Neill

---

### Post by NeillHog on 2007-07-20
Sorry to have bothered you all.
I just found a thread about a bug that describes my problem perfectly.
I still don't know how to solve it but I know that I am not alone :-)

---

### Post by NeillHog on 2007-08-12
Excerpts from my Linux Diary on this subject

So now how to get the screen looking good. Once again back to Google and the Ubuntu Forums. I discovered that my graphic card was not supported by the driver in Kubuntu but that there was another one which I could download from NVIDIA. It took me some time to work out which but eventually I downloaded it to the PC and then after logging in in console mode and finding it (more Unix commands) I ran the self extracting file.

Of course I received an error message saying that the system was missing something. This time it was software that the system needs to compile drivers and so on. More research produced a command sudo apt-get install build/essential which you give in from the Konsole terminal programme. Once that was done I started the driver packet again and everything seemed to work.

Restarted the PC and one screen now worked perfectly and didn't freeze. But I have two screens so I went to the &#8220;system administration&#8221; and then &#8220;monitors and display&#8221; and tried to switch on the second monitor (as in Windows). This crashed my system three or four times so I went back to NVIDIA.com and looked some more. Eventually I found a readme file that said that what I needed to do was activate twinview in the configuration file. Obviously! At least I now know where the configuration file is and how to edit it so this time things were relatively easy.

Started everything again and &#8211; the two screens are running perfectly side by side.

Thanks all of you!

---

