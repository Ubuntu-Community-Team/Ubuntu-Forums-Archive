---
title: "What is the difference between Ubuntu, Kubuntu and Xubuntu?"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by charliep8 on 2007-04-25
Okay, I did search this forum for this question and found nothing. I searched Google and found too much. Please don't flame me for asking a simple questions. I KNOW that Ubuntu uses GNOME, KUbuntu employs KDE and XUbuntu runs with XFCE. I also know that benchmarks for the three flavors is about the same:

[http://www.phoronix.com/scan.php?page=article&item=650&num=2](http://www.phoronix.com/scan.php?page=article&item=650&num=2)

And I know that you can install KDE on Ubuntu or Gnome on Kubuntu or KDE on Xubuntu or ... etc. So my questions are:

1. When you install Gnome on Kubuntu do you basically have the identical files as you would if you installed KDE on Ubuntu?

2. How much hard drive space does each additional desktop require?

3. Is there an Ubuntu distribution that includes all three desktops?

4. Does Xubuntu include Gnome? Because I thought I saw an option to boot using basic Gnome. But then Kubuntu does NOT include Gnome, so I am kind of confused. Is (or is not) Xubuntu basically the same as Ubuntu + XFCE?

5. Which desktop is the best from a software compatibility standpoint? E.g. if I install Xubuntu will I run into a bunch of software that just doesn't run?

6. Is there a Windows-like Theme for XFCE or KDE? I know about XPDE but I here it is kind of lame. But I like to customize things so I don't think I will be happy with Gnome.

Thanks for the answers!

---

### Post by raja on 2007-04-25
1. Should be true mostly.
2. I have Ubuntu Feisty running and typing ```
sudo aptitude install kubuntu-desktop
``` lists a lot of packages and ends with ```
Need to get 257MB of archives. After unpacking 726MB will be used.

``` So there eyou go.
3. No. But then all you have to do is install Ubuntu and then ```
sudo aptitude install kubuntu-desktop
sudo aptitude install xubuntu-desktop
```
4. No
5. Software compatibility is not the issue here. If you want something with a very small memory usage, either because you are a stickler for speed or have a low memory system, go for XFCE. Otherwise try both Gnome and KDE. Find which is to your liking.
6. I dont know what exactly you want. But anyway I find gnome very customizable too. And atleast to me, more pleasant to use than KDE. Have a look at gnomelooks.org for themes.

---

### Post by charliep8 on 2007-04-25
2. So, KDE would require 726 MB to add to Ubuntu. 

I did similar checks for XFSE:

Need to get 64.3MB of archives. After unpacking 252MB will be used.

XFSE requires only 252MB to install.

Can anybody with Kubuntu or XFSE run the command:

sudo aptitude install ubuntu-desktop

to see how much disk space is required by Gnome?

6. I know that Smooth XP for Gnome is available here:

[http://www.gnome-look.org/content/show.php?content=16732](http://www.gnome-look.org/content/show.php?content=16732)

My question was, is there a similar XP-like theme for KDE?

---

### Post by konungursvia on 2007-04-25
Ubuntu uses "GNOME" as its front-end graphics and desktop, Kubuntu uses "KDE" for the same, while "Xubuntu" uses Fluxbox I believe. Deep underneath, they have the same core Ubuntu linux, just different "faces".

---

### Post by jerrylamos on 2007-04-25
I've run all three.

Ubuntu is the core Ubuntu which is reputed to have some of the Gnome experts behind it.  As far as applications and services I seem to be able to do most anything with less keystrokes than some of the others.

Xubuntu has a lightweight XFCE window manager which takes less space and runs faster.  It's got a glaring omission for me in not being able to browse the local LAN workgroup computers to share files.  Printer sharing works fine.  Some of the other services are not obvious how to do to me.

Kubuntu uses KDE window manager (as in Kool Desktop Environment) has lots of eye candy and lots of support for fancy graphics and games.  If you're interested in Linux for itself and all kinds of flossy support go to it.  It has a glaring omission for me in that its internet browser Konqueror does not do AOL mail.  Sure, I can install  Firefox too, but Ubuntu & Kubuntu come with Firefox to start with.  Kubuntu is a bit slower example in safe graphics mode with VESA driver.

So if you have older slower hardware or are shorter on memory try Xubuntu.  I find 1 gHz Celeron with 512 mb PC133 memory runs all three of them just fine.  I'm mostly interested in applications like internet & internet mail & internet video & word processing & digital photos & file sharing so I do fine on Ubuntu.  

Cheers, Jerry

---

### Post by charliep8 on 2007-04-26
So, I had a Xubuntu disk handy and went to see how much disk space Gnome requires:

> Need to get 282MB/283MB of archives. After unpacking 962MB will be used.

So the disk space required for the three different desktops is:

Gnome:   962MB 
KDE:        726MB
XFSE:       252MB

Looks like Gnome is fat, but 1GB of disk space is not going to matter to me, so I am going to install all three and play around with them using the commands:

> sudo aptitude install kubuntu-desktop
sudo aptitude install xubuntu-desktop

---

### Post by bro on 2007-04-27
I installed Kubuntu instead of Ubuntu because I think I like it better after working with Gnome for a while. 
There must be some differences however. I don't see de restricted-manager anywhere for example. Is this normally there in Ubuntu Feisty? I head to apt-get install it. Same for the ntfs-3g ntfs-config. Are they supposed to be in any control panel? At least not in Kubuntu Feisty by default. 
It's hard to say for me which desktop I like better. I love beryl which won't work as I don't seem able to install it properly in kubuntu (didn't try ubuntu feisty, but worked fine in edgy). 

Same time Katapult is addictive, like gdeskbar where's kdeskbar? 
I love Kde's configurability, But then again I can do whatever I want on Gnome.. I wish ubuntu had a monopoly and forced everybody to use Gnome through vendor lock ins so I didn't need to choose :biggrin: 

Is there much overhead using KDE apps on Gnome (like say yakuake? Amarok or Quanta+)? Given that I don't care too much about a little overhead.

---

### Post by janetk on 2008-01-06
I have been using kubuntu on one machine (PC1) for several months, with qcad as an important part of my work. It printed to a samsung ml3051 printer by magic. (the machine was networked to my other machine,(PC2 running SuSE) which had the printer installed on it). Because of some small glitches which had accumulated that I couldn't solve, I copied qcad and its drawings and moved them to PC2 via a dvd, then did a clean install of kubuntu 7.10 on PC1. I brought back the package,and when everything seemed to work, I installed the same Kubuntu on PC2, thus eliminating the SuSE . Catastrophe! No way could I get either machine to print to the samsung. I also found that connecting the 2 machines by zero config was beyond my talents. In desperation I replaced the kubuntu with ubuntu, and all by itself, it prints to the samsung.
>So there is one important difference between the two buntus!!<
But now, with no previous experience with gnome, I am encountering (teething?) problems. One, although I'd had no problems getting the qcad into the kde envronment from the dvd, I can't get it into my ubuntu/gnome environment. This is most strange, because the ubuntu comes with a scaled-down qcad, that installs automatically. (Unfortunately, I need the full scale version).
For clarity: The qcad was originally installed in the home directory of the SuSE, that folder then copied to the first Kubuntu set-up, again to the home directory.All this worked fine. This was the folder that was copied to the dvd, and went into the home directory of PC2,now also kubuntu. Again it worked fine. But now, when I move the same folder to the home directory of the ubuntu (PC1), it won't install. 
Can anyone understand all this giberish, and can anyone Help? Please?  
P.S. I don't know how to do the smileys, or they would be all over this note.

---

