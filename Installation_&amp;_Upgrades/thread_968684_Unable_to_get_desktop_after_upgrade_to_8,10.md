---
title: "Unable to get desktop after upgrade to 8,10"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by GoManVanGogh on 2008-11-02
Hello Fellow Partisans- I've been using 8.04 on a Dell Optiplex GX 60 (Celeron, 1 meg ram) for some time. Initially I went through some configuration agony, with a Viewsonic hi-res monitor and getting a wireless connection (via USB and an old Netgear 811.b stick) but it was reliable for at least 4 months. Wireless USB was a problem on 8.04, and when I installed the first time, I had to do it without the USB stick, then insert. Later that did not matter. Using NDIS wrapper and a Windows driver on it. 

I'm explaining the above because I now have a somewhat similar problem after doing a Network upgrade. But this does not seem to be related to any USB card- I've tried booting with and without.

I get to the point where I log in with user name and password (I use the Gnome desktop), and get that screen just fine. Res looks right, the options work, and I have the nice drumbeat. But when I log in, I never get to the desktop.

I see the busy round dot for a bit, and the pointer. Eventually I hear the desktop-is-appearing-now Ubuntu theme music, but I never get the desktop showing at all. 

I'm in a real quandry here. It seems there is no way to get into a safe video mode and try that. I tried using an older kernal, but there is no difference. 

I'm not any sort of a UNIX expert, though I have been around the block enough to try everything obvious. This is a dual-boot machine used for testing. I have no valuable docs on it, and I'm thinking of replacing the hard drive sometime and just running Ubuntu.

I'm open to suggestions and solutions - Am on the Intel motherboard video, and could go for an ATI card if you all think that is worth a try. Not a NEW ATI, probably, but an older one.

Thanks, in advance, for your help. 
:guitar: - GoManVanGogh

---

### Post by GoManVanGogh on 2008-11-03
27 views so far and no comments? Anybody know if this is an X problem? or a Gnome problem, or a video issue? Should I wait for a full distro DVD and just install new? How can I diagnose?

---

### Post by zaine_ridling on 2008-11-03
Seems like 8.10 is a graphics disaster. In 8.04 I was able to load the catalyst drivers for my ATI 4850 radeon card, but nothing works in 8.10; in fact, it won't even get past the installation screen. Fedora 9, however, loads like a champ, recognizes everything. (But I prefer kubuntu!)

I understand the usual -- and often easily fixable -- problems surrounding desktop Linux. But when users can't install from popular cards, it's a real downer.

---

### Post by GoManVanGogh on 2008-11-04
I've tried using the motherboard graphics from the Dell, which are intel-based AND with my Nvidia card. The Nvidia card gives me an Ubuntu logo when it start to load before stopping completely about 20% in. This is the same problem I had with 8.04 when I first started with it.

I'd been using the intel board chipset. On this, it loads to the login screen, but then fails.

I'm not sure of what to do. I can't get a console. I could get to files to edit by booting of an 8.04 DVD but I'm getting frustrated.

Thinking of switching to Debian, or maybe Solaris, now that it's freeware, if not open source.
:guitar:

---

### Post by dstin1 on 2008-11-04
Try this it worked for me

> **Drate said:**
> If you find you can get to the GDM but it won't finish logging you in (black screen, mouse moves), then goto a failsafe terminal session and do this:

sudo apt-get remove compiz compiz-core

That should fix ya (well, allow you to login to Gnome anyway).

There is a launchpad bug: 277373

---

### Post by Tantor on 2008-11-05
I have upgraded from hardy to intrepid by pressing the "upgrade now" button in the updates manager. After rebotting, I couldn't get to gnome any more. I got my wallpaper and a mouse cursor that I was able to move but everything else was froze, no CTRL+ALT+DEL or CTRL+ALT+F1 would work. I have automatic login so I am not completely sure at what stage the problem appears but since my custom wallpaper was loaded I would say I could get to GDM just fine and that the problem shows during the login.

After some googling, I booted into recovery mode and from a root terminal removed compiz and compiz-core. Now I am able to boot normaly (of course the desktop effects are gone.) My real problem is that everything is working very slowly; windows take some time to get drawn. Does this makes sense at all? Is it possible that removing compiz has slowered my system? Or is it an unrelated problem? I thought that removing compiz would made my system faster. Some advice?

My graphic card is (as shown by "lspci | grep VGA"),

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

I've seen bug reports concerning this issue at

[https://bugs.launchpad.net/ubuntu/intrepid/+source/compiz/+bug/277373](https://bugs.launchpad.net/ubuntu/intrepid/+source/compiz/+bug/277373)

and

[https://bugs.launchpad.net/ubuntu/intrepid/+source/compiz/+bug/259385](https://bugs.launchpad.net/ubuntu/intrepid/+source/compiz/+bug/259385)

I am a bit concerned because the bug reports on those links go back to the alpha and beta versions of Ubuntu 8.10 and somewhere there was some debate over whether this was an important issue or not, since they weren't getting many reports over this. I will try to file a bug report and please do so if you have the same problem.

Do you think that this problem would eventualy be fixed? Or should I try to go back to hardy? Can someone think of a way to downgrade just the component that is causing the problem? Everything was just fine in hardy.

Thanks in advance!

---

### Post by GoManVanGogh on 2008-11-07
Hi-

I get an orange screen, mouse moves, no desktop or wallpaper. How do I get to the failsafe terminal session? 

Thanks!

---

### Post by GoManVanGogh on 2008-11-07
Thanks! This worked. I searched forums (fora?) to find how to get the failsafe terminal (Ctrl-Alt-F1 combo) and although the graphics were funky, managed to blind-type in the magic commands. 

After a logoff, I was able to do a "normal" login, and am now back on the new desktop. 

-GoManVanGogh

---

### Post by SpectralDesign on 2008-11-08
I don't even get to GDM login...  I get the text login only...

I thought there was a program called xconfig or something to reconfigure the x setup but I can't find it... help?

---

### Post by alg on 2008-11-19
Good day!
I'm new to Ubuntu (and Linux as well), but been around with other operating systems for quite some time.

I too am having this problem, but the mentioned "Ctrl-Alt-F1" does not work.

This is a new install, done twice now.

Again, like the others, 1)system boots, 2)I am able to login with username and password (the options menu is also available) and then a full colored screen (sometimes orange or brown, and sometimes black) with nothing on it except the mouse cursor.  The cursor does move, but there are NO functions such as right click.

Any help would be really appreciated.  This is tainting my view of Linux in general and Ubuntu in particular.  After making the decision to at least try it, I hope I'm not wrong.

---

### Post by alg on 2008-11-19
Just wanted to update my initial post.

I have been successful in removing version 8.10 and installing version 8.04.

---

### Post by motin on 2008-11-19
Bug report: [https://bugs.launchpad.net/ubuntu/+bug/300028](https://bugs.launchpad.net/ubuntu/+bug/300028)

---

### Post by GoManVanGogh on 2008-11-19
> **alg said:**
> Just wanted to update my initial post.

I have been successful in removing version 8.10 and installing version 8.04.

Most of the problems I've seen - and finally resolved seem to center more around GNOME than Ubuntu. You might try Kubuntu and work with KDE for a while. Many of my friends who run Linux use the KDE desktop. None are on Ubuntu, some run Open Suse or another distro. One friend doesn't care about open source and likes the free Solaris, but he was a SUN user for years.

---

