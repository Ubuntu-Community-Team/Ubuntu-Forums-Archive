---
title: "[SOLVED] Xubuntu With Wubi/and the Ubuntu Live CD"
date: 2008-04-02
forum: Installation &amp; Upgrades
---

### Post by theravenproject on 2008-04-02
I have searched the related threads and cannot get the help I need from them so:

I want to install Xubuntu (Because I was told that my cpu "Dell Optiplex Pentium 4 256 mb ram 20 gb HD) wouldn't handle Ubuntu so well-all I have is the Ubuntu live cd with no way to burn any other media...so I heard about WUBI?  I checked that out...I want to know if I can use the Ubuntu Live cd to resize my Win XP partition, Create a Swap partition (**WHAT SIZE SWAP DO I NEED?** and create an EXT3 Partition for Xubuntu...then I want to download Wubi-Download the Xubuntu 7.10 ISO into the Wubi Folder, and then Install Ubuntu...and the use the LPVM application to switch it over to the EXT3 partition thus creating an actual "TRUE" Xubuntu installation?  Can anyone help advise me if this sounds right/possible?  Also-what size swap do I need to create for this setup-I am shrinking my Xp part from 17 gb to 10 gb and then the swap and whatever is left after that I am dedicating to Linux...Also-does anyone know about UNETBOOTIN?  I heard that it can be used to do this whole process more directly but that was with Ubuntu-can it be done wit Xubuntu and if so how?

---

### Post by overdrank on 2008-04-02
> **theravenproject said:**
> I have searched the related threads and cannot get the help I need from them so:

I want to install Xubuntu (Because I was told that my cpu "Dell Optiplex Pentium 4 256 mb ram 20 gb HD) wouldn't handle Ubuntu so well-all I have is the Ubuntu live cd with no way to burn any other media...so I heard about WUBI?  I checked that out...I want to know if I can use the Ubuntu Live cd to resize my Win XP partition, Create a Swap partition (**WHAT SIZE SWAP DO I NEED?** and create an EXT3 Partition for Xubuntu...then I want to download Wubi-Download the Xubuntu 7.10 ISO into the Wubi Folder, and then Install Ubuntu...and the use the LPVM application to switch it over to the EXT3 partition thus creating an actual "TRUE" Xubuntu installation?  Can anyone help advise me if this sounds right/possible?  Also-what size swap do I need to create for this setup-I am shrinking my Xp part from 17 gb to 10 gb and then the swap and whatever is left after that I am dedicating to Linux...Also-does anyone know about UNETBOOTIN?  I heard that it can be used to do this whole process more directly but that was with Ubuntu-can it be done wit Xubuntu and if so how?

Hi and the rule of thumb is swap twice as much as your memory up to one gig. What you are planning sounds like a lot of work. If you are going to create a partition with the live cd the  why not install with the live cd instead of using wubi?

---

### Post by rogerdpenguin on 2008-04-02
I installed wubi, and it works wonderfully.

---

### Post by theravenproject on 2008-04-02
Overdrank...The problem is that my rig will not run Ubuntu very well (Or so I am told) with the memory/HD space that I have so I was recommended to use Xubuntu-well; I don't have a live cd for Xubuntu so I would have to use Wubi to do an install without Bootable media right?  Or now I am checking out this "UNETBOOTIN" prog which it seems bypasses the Wubi process and goes straight to installing your os to a partition without using a cd but I am not yet sure that you can use UNETBOOTIN with Xubuntu?  Does any of this make sense ?  Man, I am beginning to confuse myself-what pain and suffering I am having to go through just to get a dual boot with Xubuntu-Geesh, I sure will appreciate that darned Linux installation once I have it-they'll have to pry it out of my dead hands to get it from me if I can ever pull it off.  My main concern right now is trying to do all of this without crashing/destroying my Xp partition because it is where I have all of my current IDE software and a healthy happy much needed toolbox and stuff I have grown to love....Please Advise...

---

### Post by overdrank on 2008-04-02
> **theravenproject said:**
> Overdrank...The problem is that my rig will not run Ubuntu very well (Or so I am told) with the memory/HD space that I have so I was recommended to use Xubuntu-well; I don't have a live cd for Xubuntu so I would have to use Wubi to do an install without Bootable media right?  Or now I am checking out this "UNETBOOTIN" prog which it seems bypasses the Wubi process and goes straight to installing your os to a partition without using a cd but I am not yet sure that you can use UNETBOOTIN with Xubuntu?  Does any of this make sense ?  Man, I am beginning to confuse myself-what pain and suffering I am having to go through just to get a dual boot with Xubuntu-Geesh, I sure will appreciate that darned Linux installation once I have it-they'll have to pry it out of my dead hands to get it from me if I can ever pull it off.  My main concern right now is trying to do all of this without crashing/destroying my Xp partition because it is where I have all of my current IDE software and a healthy happy much needed toolbox and stuff I have grown to love....Please Advise...

Ok I believe I understand a little :-k It just sounds like alot of work to get xubuntu. If you system will run the live cd of ubuntu that you already have then you can resize you xp partition and then install. This will save you the installation of wubi and converting with LPVM. If you install with the Ubuntu live cd then you can install the xfce desktop environment after with this command ```
sudo apt-get install xubuntu-desktop
``` Hope this helps and do not mean to confuse. :)

---

### Post by theravenproject on 2008-04-02
Okay Overdrank-Now, riddle me this...(LOL!)  If I go and do it the way that you are talking abut- will I not be wasting space installing the gnome desktop environment when I really cannot use it because of my weak memory?  And if so-won't installing the gnome not only be a waste of precious HD space, but will it slow me down more as well?  Space and speed are what I am hoping to save by implementing the xfce desktop env so they are of paramount importance in this install-however I have to do it to save Mem space, maintain speed and save HD space is the way I need to go-now knowing all that; can you direct me a little more specifically?

I THANK YOU GRACIOUSLY FOR YOUR TIME AND PATIENCE WITH ME THUS FAR ALREADY!!!!!!!!!!

---

### Post by overdrank on 2008-04-03
> **theravenproject said:**
> Okay Overdrank-Now, riddle me this...(LOL!)  If I go and do it the way that you are talking abut- will I not be wasting space installing the gnome desktop environment when I really cannot use it because of my weak memory?  And if so-won't installing the gnome not only be a waste of precious HD space, but will it slow me down more as well?  Space and speed are what I am hoping to save by implementing the xfce desktop env so they are of paramount importance in this install-however I have to do it to save Mem space, maintain speed and save HD space is the way I need to go-now knowing all that; can you direct me a little more specifically?

I THANK YOU GRACIOUSLY FOR YOUR TIME AND PATIENCE WITH ME THUS FAR ALREADY!!!!!!!!!!

HI and I can not completely answer that riddle. :) I have in the past install Ubuntu and then switched to Xubuntu and did not see a significant  loss in hardware space but did see a increase in speed after achieving a pure xubuntu. But it was in Feisty and not in Gusty.
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)
If speed and lightweight is what you are seeking then you may look at
[http://fluxbuntu.org/js.html](http://fluxbuntu.org/js.html)
But this is just options and if you are not comfortable with the installation then proceed in the way you have planned with Wubi and so on. Good luck!

---

### Post by theravenproject on 2008-04-03
[FONT="Comic Sans MS"]Overdrank;

      I wish I had friends like you-so easy going, so knowledgeable, instead I have to deal with these babbling idiots!  Anyways, you helped some more but I still have a couple of questions-is that ok?  Id on't want to take up too much of your time!

Okay, I went and checked out the Fluxbuntu site and it looks sweet but at the same time I am not liking what I see._  My main interests as a Linux user are going to be: ** White hat Hacking (The Ethical Hacking Variety)**, programming (C, Perl, Python, C++, and any other languages I come across and can retain!), General Web Browsing (For which I am a devout Firefox user-don't like Konqueror/or any others) and possibly some web design/development-I am really interested in xtml and the new trend in markup languages because I am only twenty six and though just starting as a computer buff-want to be a major part of the next wave of internet development? _ Perhaps I will even develop my own Distro one of these days?  **So I understand that Fluxbuntu is light on the system resources....but what I like about Xubuntu is from what I have been told-it (As well as Ubuntu) can be made readily configured to do these things that I want to do with it and is actually less hardware intensive than Ubuntu...let me get this right now-you tried Xubuntu and the newer distro (7.10) wasn't noticeably faster than your Ubuntu?  Let me know-did I post my system specs?[B]_*BY THE WAY_ PLEASE CAN YOU (OVERDRANK) OR ANYONE ELSE TELL ME ABOUT NETBOOTIN?  I CHECKED IT OUT BUT WANT SOME PERSONAL ADVICE BEFORE I GAMBLE MY LIFE ON IT!!!*_**
**[U]**
Dell Optiplex GX240
Pentium IV
256 mb ram
Rage Ultra....128 video card
Maxtor 20 gb HD[/U][/B]

anyways-this thing is basically a refurbished minimal office work station or possibly something salvaged from a kiosk somewhere...let me know...if I could get away with running Ubuntu on it I would-I did before but eventually it was very slow...I do like gnome though and am not familiar with XFCE at all...[/FONT]

---

### Post by overdrank on 2008-04-03
>   My main interests as a Linux user are going to be: ** White hat Hacking (The Ethical Hacking Variety)**, programming (C, Perl, Python, C++, and any other languages I come across and can retain!),
I can not help there. :(

 > let me get this right now-you tried Xubuntu and the newer distro (7.10) wasn't noticeably faster than your Ubuntu?
Correct it was not noticeably faster in Gusty. Now in Feisty 7.04 yes.

> I do like gnome though and am not familiar with XFCE at all..
XFCE is nice and I still have it on one system and you can run gnome apps on it as well as KDE.

---

