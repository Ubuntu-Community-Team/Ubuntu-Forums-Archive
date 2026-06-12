---
title: "Looking to upgrade to 12.04.1 LTS, but should I?"
date: 2012-09-25
forum: Installation &amp; Upgrades
---

### Post by Crazy K on 2012-09-25
So I finally checked to see if I could upgrade to 12.04.1 through the update manager and it's there saying I can upgrade. I already upgraded from 8.04 to 10.04 so I'm thinking about going to 12.04. This is, my PC is pretty old. It has about 600MB or RAM so would that be enough? 

I had a PC that had about 2GB of RAM, but it died. Funny how newer PC's seem to crap out more than the old ones. 

Anyways I was wondering if I should upgrade or not? 

I heard someone on here say it's best to go with Xubuntu for computers with ram less than 1gb. How would I upgrade from Ubuntu 10.04 to that though, if it's even possible?

---

### Post by Crazy K on 2012-09-25
Also I noticed with Ubuntu 12.04.1 it has a dock on the left side, is there a possible chance I can get rid of that to free up some RAM?

---

### Post by Crazy K on 2012-09-25
Also if this helps, here's some info on my PC

623.2MB of RAM

Processor 0: Pentium III (Coppermine)
Processor 1: Pentium III (Coppermine)

Available disc space: 7GB (I can easily clear some stuff out if I have to)

---

### Post by jrog on 2012-09-25
> **Crazy K said:**
> Also if this helps, here's some info on my PC

623.2MB of RAM

Processor 0: Pentium III (Coppermine)
Processor 1: Pentium III (Coppermine)

Available disc space: 7GB (I can easily clear some stuff out if I have to)
I wouldn't want to run Ubuntu with that amount of RAM -- Unity would likely not be a pleasant experience (though I can't be sure, I suppose). Xubuntu is a much better option; if you want to go even more minimal, Lubuntu is also excellent. 

There are lots of different ways you could go about getting there. You could simply upgrade to Ubuntu 12.04, then install xubuntu-desktop (or lubuntu-desktop) after upgrading. (After a while, if everything is okay with Xubuntu/Lubuntu, you could then remove the non-Xubuntu/Lubuntu packages on your system, but that's another topic.) Or you could install xubuntu-desktop or lubuntu-desktop on your current system, then upgrade, then remove unnecessary packages (this would take longer than the first option, since you'd be installing new packages, and thus upgrading more packages than in the first case). Or (what I would recommend), you could backup necessary files, download the Xubuntu or Lubuntu 12.04 ISO, and reinstall from the disc.

---

### Post by jrog on 2012-09-25
By the way, if you decide to just install xubuntu-desktop or lubuntu-desktop (and then upgrade either before or after that, as discussed above), you can find out how to remove unnecessary packages by going to the following page and checking out the links (on the left-hand side) for "Pure Xubuntu" and/or "Pure Lubuntu:" [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by mikewhatever on 2012-09-26
Honestly, I think a clean install is needed here, and Xubuntu is the obvious candidate. I can't recommend Lubuntu because of some major issues, but if you want to try, by all means, it's rather lightweight.
Ubuntu 12.04 will not run well on your machine.

---

### Post by black veils on 2012-09-26
clean install lubuntu. i doubt xubuntu will run well enough on that ram, so why bother when you can have lubuntu!

---

### Post by Paddy Landau on 2012-09-26
> **mikewhatever said:**
> Honestly, I think a clean install is needed here…
Fully in agreement. Please back up all your data first.

> **mikewhatever said:**
> I can't recommend Lubuntu because of some major issues…
I have been using Lubuntu for some years on older machines, and I strongly recommend it.  My experience with Lubuntu 12.04 has been nothing but perfect. In other words, YMMV.

If you want something even lighter than [Lubuntu]("http://lubuntu.net/"), take a look at [Bodhi]("http://bodhilinux.com/"); it is Ubuntu-derived, although not part of the official Ubuntu family.

---

### Post by jrog on 2012-09-26
> **Paddy Landau said:**
> I have been using Lubuntu for some years on older machines, and I strongly recommend it.  My experience with Lubuntu 12.04 has been nothing but perfect. In other words, YMMV.
That's been my experience, as well, and I have seen rave reviews of Lubuntu all over the place (particularly for 12.04) -- I don't believe I've seen a negative one yet. mikewhatever, what are the "major issues" you're thinking of?

---

### Post by Crazy K on 2012-09-26
Which one would be better to use than? Lubuntu or Xubuntu? 

Will all programs in Ubuntu work in Lubuntu and Xubuntu? Like maybe the mtp-lastfm program that I use to scrobble music to last fm?

---

### Post by PaulW2U on 2012-09-26
> **mikewhatever said:**
> I can't recommend Lubuntu because of some major issues, but if you want to try, by all means, it's rather lightweight.

And these major issues are? No problems here.

---

### Post by PaulW2U on 2012-09-26
> **Crazy K said:**
> Which one would be better to use than? Lubuntu or Xubuntu? 

It's really a personal choice against what works on your hardware and what you like.

My advice would be for you to try Xubuntu first and then Lubuntu if you feel that your PC is not running as fast as it should be.

> **Crazy K said:**
> Will all programs in Ubuntu work in Lubuntu and Xubuntu? Like maybe the mtp-lastfm program that I use to scrobble music to last fm?

You can install any program you like under any flavour of Ubuntu. Missing dependencies will be installed automatically to allow the program to run.

---

### Post by Paddy Landau on 2012-09-26
> **Crazy K said:**
> Which one would be better to use than? Lubuntu or Xubuntu?
On your machine, I would recommend Lubuntu — it's the lightest. Or you could try Bodhi for an even lighter touch, but Bodhi is not an official part of the Ubuntu family.

> **Crazy K said:**
>  Will all programs in Ubuntu work in Lubuntu and Xubuntu? Like maybe the mtp-lastfm program that I use to scrobble music to last fm?
All applications that work on one will work on the other. That's the good thing about belonging to the Ubuntu family. You may find that your favourite application is not installed (e.g. Firefox or Libre Office), but that's not a problem — just install it from the Lubuntu Software Centre!

---

### Post by Crazy K on 2012-09-26
I think I might try Xubuntu first, just because it looks better. I have a 500GB External HD so I can put all my files to that before the install.

---

### Post by mikewhatever on 2012-09-26
> **jrog said:**
> That's been my experience, as well, and I have seen rave reviews of Lubuntu all over the place (particularly for 12.04) -- I don't believe I've seen a negative one yet. mikewhatever, what are the "major issues" you're thinking of?

Well, that's just my personal opinion, so feel free to disagree.
I've done a little [review of Lubuntu 12.04]("http://ubuntuforums.org/showthread.php?t=1987163") a while back, and, IFAIK, some of the issues haven't been resolved to this day. I am rather sceptical of "rave reviews", they are usually dunb and worthless. :P

As this thread is not about the merits of Lubuntu, let's not discuss it here. Feel free to PM me if you have comments.

---

### Post by jrog on 2012-09-26
> **mikewhatever said:**
> Well, that's just my personal opinion, so feel free to disagree.
I've done a little [review of Lubuntu 12.04]("http://ubuntuforums.org/showthread.php?t=1987163") a while back, and, IFAIK, some of the issues haven't been resolved to this day. I am rather sceptical of "rave reviews", they are usually dunb and worthless. :P

As this thread is not about the merits of Lubuntu, let's not discuss it here. Feel free to PM me if you have comments.
Thanks, that review is helpful. I haven't experienced the stability/crashing issues you mention in the review, but my experience with Lubuntu has been pretty limited.

---

### Post by Crazy K on 2012-09-26
I'm in the process of putting everything important to my EX HDD. When I'm done with that I'll put the ISO image on a disc and be ready to install probably tomorrow sometime.

---

### Post by jrog on 2012-09-26
> **Crazy K said:**
> I'm in the process of putting everything important to my EX HDD. When I'm done with that I'll put the ISO image on a disc and be ready to install probably tomorrow sometime.
Let us know how it goes!

---

### Post by Crazy K on 2012-09-27
Having a bit of a problem right now. I changed the boot options to CDROM first and then HDD and at boot it says there's no disc or nothing to boot from that. 

Anyways did I burn the iso. image correctly? Because when I have the disc in it shows this: [http://i.imgur.com/s4B2B.jpg](http://i.imgur.com/s4B2B.jpg)

I thought it was just supposed to be the ISO image on the disc.

---

### Post by Crazy K on 2012-09-27
I think I might know what the problem is, I'm pretty sure I was having problems because of this when I first installed 8.04 back in the day. Anyways at startup, it lists how much RAM I have, and it lists it as 256MB. Which is wrong of course because I have 600MB of RAM or so. 

Anyways could this be a problem when trying to install? 

Also with the disc in the drive it brings up this prompt: 

```
A volume with software packages has been detected.
Would you like to open it with the package manager?

```

The options are Cancel or Start Package Manager. Should I go to Package Manager and see if it's possible to install from there?

Also there's another option at boot "click esc to go to menu or setup or something. I can get into CMOS right at the beginning by pressing Delete when it says to. After that page loads it loads the next where the option to click "esc" to go to menu or something along those lines. I have a very limited time to click it, because it's only 2 seconds.

---

### Post by Crazy K on 2012-09-27
I tried Lubuntu and I'm having the same problem. It doesn't boot the live cd, just boots up to Ubuntu. 

Now could I install Lubuntu or Xubuntu 10.04 and then upgrade from there?

---

### Post by Crazy K on 2012-09-27
I think I might just go along with the Ubuntu upgrade rather than do this. I was easily able to upgrade to 10.04 from 8.04, so I might just jump to it. I'll just have to get rid of the dock and whatever else would be a memory hog. I know I'll get rid of most of the stuff on the menu bars as those I would imagine be memory hogs as well.

---

### Post by Crazy K on 2012-09-27
So it was weird, during the upgrade to Ubuntu 12.04.1 it asked me to insert Xubuntu 12.04.1 into the disk drive. What could that mean? 

Anyways I halted the upgrade and I'll do the rest of it tomorrow.

---

### Post by Paddy Landau on 2012-09-28
Crazy K, you need to boot from the CD that you burned; it's no good just putting the disk in while Ubuntu is running. Your computer manual will tell you how to achieve that.

Your CD looks as though it has been correctly burned.

[LIST=1]
[*]Did you [check the MD5 Sum]("https://help.ubuntu.com/community/HowToMD5SUM") of the downloaded ISO before burning it? (If not, do so now.)
[*]Did you follow the method on the [Ubuntu download page]("http://www.ubuntu.com/download/desktop") to burn the CD (see the links on the right side of that page)?
[/LIST]

I would not try to upgrade Ubuntu to 12.04 on your machine. You may find that it runs ridiculously slowly — or not at all. Rather back up and then install Xubuntu or Lubuntu.

You'll need to figure out how to get your CD working first, or you can try booting from a USB instead (instructions also on the Ubuntu download page).

---

### Post by jrog on 2012-09-28
What Paddy says above seems correct to me, too. Are you actually booting from the CD that you burned, or are you just inserting it while Ubuntu is already running? From everything you've described, the latter seems to be what's happening.

---

### Post by Crazy K on 2012-09-28
I booted it everytime with the disk in the drive. I just left it in when it got to the desktop.

The first time I used Brasero I did two copies of Xubuntu, both didn't work. So I decided to try Lubuntu but with K3b and that did the md5 sum for me automatically. That too didn't boot up either. 

What I'm saying, is that it wont boot the live CD at startup.

And like I said above, I was able to get into CMOS and change the boot options, but I don't even know if that's the right area.

---

### Post by Crazy K on 2012-09-28
> **jmore9 said:**
> I just finsihed doing a dist upgrade to 12.10 from 12.04 and all went reasonably well.  Only problem is Medibuntu repos are not avaiable for 12.10 yet as far as i can figure out.

And only have 1 problem with Nvidia driver as i cannot change the display to 1024 x 768 i get some kind of sual monitor error when i only have one.

But all in all went very well.

I'm just trying to install Xubuntu, but I can't even get the CD to load up at the boot process. This doesn't really help me. :(

---

### Post by jrog on 2012-09-28
> **Crazy K said:**
> I booted it everytime with the disk in the drive. I just left it in when it got to the desktop.

The first time I used Brasero I did two copies of Xubuntu, both didn't work. So I decided to try Lubuntu but with K3b and that did the md5 sum for me automatically. That too didn't boot up either. 

What I'm saying, is that it wont boot the live CD at startup.

And like I said above, I was able to get into CMOS and change the boot options, but I don't even know if that's the right area.
When you burned the CD using Brasero, did you select the "Burn Image" option to burn the CD?

---

### Post by Crazy K on 2012-09-28
> **jrog said:**
> When you burned the CD using Brasero, did you select the "Burn Image" option to burn the CD?

The first time I did not, I believe I went with Data CD, the second time I did burn image.

---

### Post by Paddy Landau on 2012-09-29
> **Crazy K said:**
> I booted it everytime with the disk in the drive. I just left it in when it got to the desktop.
> **Crazy K said:**
> The first time I did not, I believe I went with Data CD, the second time I did burn image.
The data CD won't work. The second time should have worked.

In [post=12265050]post #19[/post], you said:
> **Crazy K said:**
> I changed  the boot options to CDROM first and then HDD and at boot it says there's  no disc or nothing to boot from that.
I rather suspect that your computer is not even looking at the CD when booting.

[LIST]
[*]Double-check that your changes to the BIOS were saved.
[*]Can you try your CD in someone else's computer (don't install; just try booting from the CD)?
[*]When you boot your computer, you may find that you can press F2, F10, F12, Del or some other key to get to a boot menu &#8212; your computer's manual should tell you if that is possible.
[/LIST]
 > **Crazy K said:**
> &#8230; with K3b and that did the md5 sum  for me automatically.
K3B only checks that the CD-writing was correct. It does not check that the downloaded ISO is correct. You need to follow the instructions to [check the MD5 sum]("https://help.ubuntu.com/community/HowToMD5SUM") of the downloaded ISO; you can find the [MD5 sums (Ubuntu Hashes)]("https://help.ubuntu.com/community/UbuntuHashes") from that page. Please do it now before you do anything else, as an incorrect download will sabotage everything else (it has happened to me before).

---

### Post by Crazy K on 2012-09-30
> **Paddy Landau said:**
> The data CD won't work. The second time should have worked.

In [post=12265050]post #19[/post], you said:

I rather suspect that your computer is not even looking at the CD when booting.

[LIST]
[*]Double-check that your changes to the BIOS were saved.
[*]Can you try your CD in someone else's computer (don't install; just try booting from the CD)?
[*]When you boot your computer, you may find that you can press F2, F10, F12, Del or some other key to get to a boot menu — your computer's manual should tell you if that is possible.
[/LIST]
 
K3B only checks that the CD-writing was correct. It does not check that the downloaded ISO is correct. You need to follow the instructions to [check the MD5 sum]("https://help.ubuntu.com/community/HowToMD5SUM") of the downloaded ISO; you can find the [MD5 sums (Ubuntu Hashes)]("https://help.ubuntu.com/community/UbuntuHashes") from that page. Please do it now before you do anything else, as an incorrect download will sabotage everything else (it has happened to me before).

I restarted it a couple times and checked to see that it was what I had put it on. 

I don't have a computer manual for this as I got it from a friend for $50 many years ago. It says to hit del to go into a menu right at startup, and that brought me to what I previously mentioned. Then after that, it says something along the lines of to go to menu hit F2 I believe. And it has a 2 second countdown and no matter what I do it doesn't bring me into this other menu or setup or whatever. 

I'll see if the discs work in my sister's PC tomorrow, and I'll update you. 

Now how would I check to see the MD5sum for the disc when it's already made?

---

### Post by Crazy K on 2012-09-30
I think it was the md5sum causing the problems. I checked and for the Xubuntu download I just did it came up with this: 

```
acb6bd5412fcefc5082cb98cb039de10
```

When it's supposed to be this: 
```
52fddd81e75bb421a5435a42ca9ec6df
```

Now what do I do now?

---

### Post by jrog on 2012-09-30
> **Crazy K said:**
> I think it was the md5sum causing the problems. I checked and for the Xubuntu download I just did it came up with this: 

```
acb6bd5412fcefc5082cb98cb039de10
```When it's supposed to be this: 
```
52fddd81e75bb421a5435a42ca9ec6df
```Now what do I do now?
Your first hash is the right one, according to the site here, at least if you downloaded 12.04**.1**: [http://cdimage.ubuntu.com/xubuntu/releases/12.04/release/MD5SUMS](http://cdimage.ubuntu.com/xubuntu/releases/12.04/release/MD5SUMS)

The hash you're saying it's supposed to be is for 12.04 (not 12.04.1). Which one did you download?

---

### Post by Crazy K on 2012-09-30
I wish I knew that beforehand. I went with the site that was showed to me. I thought it would of been just 12.04. Oh well, I re-downloaded the ISO, so I hope it's the same again. 

Yup, it's right. Going to make yet another DVD with this and see what happens.

---

### Post by Paddy Landau on 2012-10-01
> **Crazy K said:**
> Yup, it's right. Going to make yet another DVD with this and see what happens.
If yours is a very old computer, perhaps it is unable to boot from a DVD? Try burning to a CD instead.

---

### Post by Crazy K on 2012-10-01
Yeah I'll see if I can get some CDs soon. I know I used CDs for the installs before. I'd like to get Xubuntu on here though, just so I can have a faster PC. I doubt it'll be too much faster, but whatever frees up some RAM usage, I'm all for.

---

### Post by Paddy Landau on 2012-10-01
> **Crazy K said:**
> I'd like to get Xubuntu on here though, just so I can have a faster PC. I doubt it'll be too much faster, but whatever frees up some RAM usage, I'm all for.
You'll find Xubuntu quite a bit faster than Ubuntu (12.04 needs at least 1Gb RAM), and Lubuntu faster still. I use Lubuntu on old computers to great effect. If that is still too slow, try Bodhi, which should blaze on your computer.

---

### Post by Crazy K on 2012-10-02
I tried a CD instead, same problem. It doesn't boot up the live CD. Any idea on how I could do this? I burned it correctly, but yet nothing. I got 4 more CDs so I'll see what I can do. I might check out Bodhi, but will I be able to install Ubuntu programs or no? 

Oh and the GRUB menu at loadup is the thing I can't get into. I have to press ESC to get to it, but only a 2 second window, and even if I click it, nothing happens.

---

### Post by Crazy K on 2012-10-02
Yes I got it. I tested Xubuntu, Lubuntu and now I'm posting this message from Bodhi. I'm really digging Bodhi right now because it's so fast. I might end up installing it. But I need to know if I can download Ubuntu programs on here. I know on their site they mention Ubuntu. 

But yeah, if I can get rythmbox, MTP-lastfm, and some other programs, than I'm good. :)

---

### Post by Crazy K on 2012-10-02
I think I might go with Lubuntu, just because I know that everything that works with Ubuntu will work with this, plus it just looks much better than Xubuntu. Bodhi is quite nice too, and fast, and I might just go with that yet, we'll see. I just want to make sure everything I want to use works on each OS.

Oh and by the way, I was able to boot the live CD by holding ESC right near the part where you click Delete to get into BIOS, which brought me through some prompt thing, I then let it go from there. That's how it works for me at least.

---

### Post by Paddy Landau on 2012-10-03
> **Crazy K said:**
> Yes I got it … I was able to boot the live CD by holding ESC right near the part where you click Delete to get into BIOS…
Whew! Well done for managing to figure it out. You'll need to write it down somewhere in case you have to do it again in the future and have forgotten!

> **Crazy K said:**
> I'm really digging Bodhi right now because it's so fast. … But I need to know if I can download Ubuntu programs on here.
I've loaded Bodhi in a VM, and yes, you do have access to the Ubuntu applications. Start Synaptic Package Manager (from Applications > Preferences) to find Rhythmbox and other applications.

> **Crazy K said:**
> … Lubuntu, … just looks much better than Xubuntu.
That's funny, because most Xubuntu users prefer its looks to Lubuntu! But you must go with your preferences.

> **Crazy K said:**
> Bodhi is quite nice too
You may not be aware that Bodhi has several appearances from which to choose. I have not used Bodhi except experimentally, so I cannot comment on them.

BTW, if we have answered your question, please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") to help others.

---

### Post by Crazy K on 2012-10-03
I did notice you can choose themes right at startup, so that was nice. I might end up going with lubuntu. I might play around with Lubuntu and Bodhi and see which one I should go with.

---

