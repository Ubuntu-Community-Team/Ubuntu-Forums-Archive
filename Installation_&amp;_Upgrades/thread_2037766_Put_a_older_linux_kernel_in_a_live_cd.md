---
title: "Put a older linux kernel in a live cd?"
date: 2012-08-05
forum: Installation &amp; Upgrades
---

### Post by TheGuyWithTheFace on 2012-08-05
So, I'm trying to put Lubuntu on a old computer with a AMD K6-2 processor. Unfortunately, the AMD K6-2 hasn't been supported since l0.04 lucid lynx. I'd prefer to install a OS that has official support from canonical, so I was wondering how I could put the kernel from lucid on the live cd with 12.04 precise. Any suggestions?


P.S.

Just for laughs, here are the specs of this computer:

1998 IBM Aptiva

os: windows 98 (first edition)
motherboard: I couldn't find Identification, but I'm almost dead certain It's the original board.
cpu: AMD K6-2 @ 350 MHz
Ram: Originally 64 Mb, but I "upgraded" it to 192 to accommodate Lubuntu's needs
Hard Disk: 8gb
Video Memory: 4mb

---

### Post by Cheesemill on 2012-08-05
Deleted

---

### Post by cwsnyder on 2012-08-05
A couple alternatives:  Lubuntu 10.04 will be supported until April 2013.

Debian 6 will probably be supported into 2017 with security updates and could be installed with LXDE as the desktop and setup with similar applications.

Otherwise, you are probably looking at using DamnSmallLinux, Puppy Linux, or one of the other specialty distributions which support older computers.

---

### Post by Cheesemill on 2012-08-05
> **cwsnyder said:**
> Lubuntu 10.04 will be supported until April 2013.

Nope.

Lubuntu 10.04 wasn't an LTS release, support ran out last year.

---

### Post by TheGuyWithTheFace on 2012-08-05
> **cwsnyder said:**
> A couple alternatives:  Lubuntu 10.04 will be supported until April 2013.

Debian 6 will probably be supported into 2017 with security updates and could be installed with LXDE as the desktop and setup with similar applications.

Otherwise, you are probably looking at using DamnSmallLinux, Puppy Linux, or one of the other specialty distributions which support older computers.

As Cheesemill said, Lubuntu 10.04 no longer has support because it's not a LTS. I was considering using one of the other linux oses, but I was really hoping to use something with the same core as Ubuntu so I can have access to more programs. If I have to choose between Lubuntu 10.04 and Debian, DSL, or Puppy linux, I'd choose Lubuntu.

---

### Post by TheGuyWithTheFace on 2012-08-05
That being said, I still haven't given up on putting an older kernel on lubuntu 12.04's live cd...

---

### Post by mastablasta on 2012-08-06
> **TheGuyWithTheFace said:**
> I was considering using one of the other linux oses, but I was really hoping to use something with the same core as Ubuntu so I can have access to more programs..
 
other linuxes have programmes acess as well only they sometimes need to be compiled form source as they are not in their repositories.
 
Debian probably has same programmes available as Ubuntu. but you need ot add repositories.
 
then there is red hat (or the free CentOS or Scientific Linux) with loooooong support.
 
for light use you can also try Slitaz. has a nice colleciton of programmes.
 
note that after you make it work don't expect all porgrammes to run on that CPU since they have their own requirements as well. depends really what you plan to use the computer for.
 
Old version of (ubutnu based) Bodhi linux could also be an option.

---

### Post by TheGuyWithTheFace on 2012-08-06
ok, I think I'll try Bhodi. If anyone still has any ideas about Lubuntu, though, please tell me.

---

### Post by Simian Man on 2012-08-06
1) It doesn't really matter that Lubuntu 10.04 wasn't LTS, because the only difference between that and the Ubuntu 10.04 LTS is the desktop.  So all the important bits will still receive security updates.

2) Unless you're using this machine as a public-facing server, it doesn't *really* matter if you are getting updates or not.

---

### Post by TheGuyWithTheFace on 2012-08-06
True, but I prefer to stay somewhat up-to-date.

---

### Post by TheGuyWithTheFace on 2012-08-06
Well, Bhodi isn't for me. Even though my computer has enough ram to run it once installed, there seems to be no way to install it without a live session, which I don't have enough memory for. So, mastablasta mentioned something about being able to compile things from scource to make them work in different distros. Does this mean that by compiling from scource I'll have access to the same programs I have in Ubuntu?

---

### Post by Simian Man on 2012-08-06
> **TheGuyWithTheFace said:**
> 
1998 IBM Aptiva

os: windows 98 (first edition)
motherboard: I couldn't find Identification, but I'm almost dead certain It's the original board.
cpu: AMD K6-2 @ 350 MHz
Ram: Originally 64 Mb, but I "upgraded" it to 192 to accommodate Lubuntu's needs
Hard Disk: 8gb
Video Memory: 4mb

> **TheGuyWithTheFace said:**
> True, but I prefer to stay somewhat up-to-date.
Do you now?

---

### Post by TheGuyWithTheFace on 2012-08-06
Ha! You got me there... 

This computer is really just a pet project for bragging rights. I'm simply playing around with it. I'm trying to get a semi-current os because I've found with windows 98, no programs seem to still work on it, understandably so. Going from a out-of date unsupported os to a less out of date but still not supported os really doesn't do me any good. 

Wait! Are you implying that this computer isn't top-notch?

:lolflag:

---

### Post by Cheesemill on 2012-08-06
If I were you I would go for Debian stable.

Ubuntu is based on Debian so it won't be the same learning curve that you would get switching to another distro. You still use the same apt-get commands to install software and update the system and you will find that you can get all the same software for Debian that you can for Ubuntu (including LXDE). The only main difference is that Debian prioritizes stability over having the latest versions of software so you will just find that your software will be a few versions behind (but you will still be running a fully supported OS).

Going this route will be far easier than trying to use an old kernel with the latest Ubuntu or compiling anything from source.

Downloads for the i386 version of Debian stable can be found here:
[http://cdimage.debian.org/debian-cd/6.0.5/i386/iso-cd/](http://cdimage.debian.org/debian-cd/6.0.5/i386/iso-cd/)

You can use the netinst or businesscard ISO's to install if your machine has an internet connection, if not you just need CD-1.

---

### Post by TheGuyWithTheFace on 2012-08-06
I thought about Debian, but the minimum processor speed is 1 Ghz, which this computer is pretty far behind.

---

### Post by Cheesemill on 2012-08-06
> **TheGuyWithTheFace said:**
> I thought about Debian, but the minimum processor speed is 1 Ghz, which this computer is pretty far behind.

1GHz is the minimum *recommended* speed, you will still be able to install it on a much lower spec processor.

The system requirements for Debian are never going to be higher than the system requirements for Ubuntu, so if you were thinking of trying to install Ubuntu with an earlier kernel you then you have nothing to lose by trying Debian first.

I just say give it a go and see if the performance is acceptable.


Another option to look at would be #! (CrunchBang Linux).
This is based on Debian but uses the OpenBox window manager instead of LXDE to provide an even lighter system. #! is my distro of choice for low spec machines.
[http://crunchbanglinux.org/wiki/about](http://crunchbanglinux.org/wiki/about)

As you can see from the attached screenshot a fresh install of #! only uses around 75MB of RAM when fully booted into the GUI. The included applications are chosen to use minimal resources. You also don't need to run a Live CD to install so you should be able to get it running on your hardware.

---

### Post by TheGuyWithTheFace on 2012-08-06
ok, I'll give it a go!

---

### Post by 1clue on 2012-08-06
Somehow I seem to be unable to find where you say ***why*** you want to do this.

If it's just on a lark, then go right ahead.  I've done it too, several times.

If on the other hand you expect to do something practical with this machine then I suggest you look at current memory and CPU requirements for the software you intend to use.

If it's an isolated box then your best bet is to go find a CD from the timeframe when this box was new.  If you intend to run a web browser on it, that might be problematic since things like flash won't likely work with an old browser.

Finally, I might point out that a new computer can go for usd $300 or even lower.  If you have a job, then I recommend you figure out how many hours of work that translates to.  Last one I bought was a 64-bit windows 7 laptop with webcam for $250.

Just food for thought.

---

### Post by TheGuyWithTheFace on 2012-08-06
> **1clue said:**
> Somehow I seem to be unable to find where you say ***why*** you want to do this.


This is just a project I'm playing with in my spare time. Right now I'm on my toshiba satellite with an intel i7 CPU and 6 gigs of ram. The "dinosaur" I'm working on is, as you said, on a lark. If it's unusable, no big deal, I didn't pay anything for it. If I can get a usable computer, I get bragging rights.

---

### Post by 1clue on 2012-08-06
> **TheGuyWithTheFace said:**
> This is just a project I'm playing with in my spare time. Right now I'm on my toshiba satellite with an intel i7 CPU and 6 gigs of ram. The "dinosaur" I'm working on is, as you said, on a lark. If it's unusable, no big deal, I didn't pay anything for it. If I can get a usable computer, I get bragging rights.

OK then you have my full support.  You've given me one of two possible "correct" answers IMO.  The other one being similar to that you live in a third-world country and are living on a dollar a day, and you need a computer for some reason.

---

### Post by mastablasta on 2012-08-07
if debian doesn't work then DSL (uses old kernel and is ment for old computers, i think based on debian, and can install on 16 MB ram). i am not sure how well the kernel is patched. applicaitons might be a bit dated.
Another and better option is Slitaz. with an updated/patched kernel and nice selection of applicaitons which can even be downloaded.i think you can squeeze it on that ram amount and CPU
 
and yes you can get same applciations as in ubuntu if you compile them from source.

---

### Post by 1clue on 2012-08-07
Ya, [http://distrowatch.com/search.php](http://distrowatch.com/search.php) might be a really good site to hit.

Put in "old computer" or similar, get as specific as you want and see what comes up.

I think you'll have a really tough time getting a modern mainstream distro to work on it.  Most of them focus on computers that are being bought today, so they're concentrating on multiple 64-bit cores, large memory and that sort of thing.  You don't have any of that.

Another option might be Gentoo, but you'll need to cross compile for it which would be much more entertaining.  Scratch that one.  :)

---

### Post by TheGuyWithTheFace on 2012-08-07
Well, I installed crunchbang, and the install went well, but the system keeps hanging during startup on "loading initial ramdisk". If I can't get that worked out, debian's next on the list.

---

### Post by TheGuyWithTheFace on 2012-08-07
I just realized how off-topic we've gotten. That's fine with me, I'm having fun learning about all these distros, but a name change may be in order, and I don't think I have privileges to do that.

Forums Moderator, if you're reading this, feel free to change the name to something more like "Old OS for 14 year old computer?" or something like that.

---

### Post by Cheesemill on 2012-08-07
Another option would be to forego the GUI completely and just install a CLI system (either Ubuntu or Debian based).

You can get CLI web browsers, mail clients, text editors and media players.

---

### Post by TheGuyWithTheFace on 2012-08-07
A CLI web browser? how would I view the content?

---

### Post by Simian Man on 2012-08-07
> **TheGuyWithTheFace said:**
> A CLI web browser? how would I view the content?

With your imagination!

No, really you would only see text and alt-tags for images.  It works well for things like Wikipedia, forums, etc. but not for things like Youtube :).

---

### Post by TheGuyWithTheFace on 2012-08-07
oh.

---

### Post by Cheesemill on 2012-08-07
> **TheGuyWithTheFace said:**
> A CLI web browser? how would I view the content?

Through the terminal :)

I've attached a screenshot of the [links]("http://www.jikos.cz/%7Emikulas/links/") web browser (obviously the background comes from me using a transparent terminal).
[More links screenshots.]("http://www.jikos.cz/%7Emikulas/links/screenshots/png.html")

You can also get CLI image viewers and video players that use the framebuffer, meaning they run without having to install X.
For example you can play videos in CLI mode using mplayer by utilizing the framebuffer:
```
mplayer -vo fbdev video.avi
```(although I doubt that your hardware would be able to decode the files quickly enough).

I actually ran a little experiment on myself a few years ago to see how long I could last without using the GUI and was a lot more successful than I thought, by using the virtual terminals (CTRL+ALT+F1 - CTRL+ALT-F7) to multitask and the various CLI applications I made it for a good few days.

---

### Post by TheGuyWithTheFace on 2012-08-07
that actually doesn't look too bad! Still, I'm gonna aim for a graphical environment, and fall back on A text-based os if necessary.

---

### Post by 1clue on 2012-08-07
As late as early 2000, I used a non-graphical Linux distro as my only workstation at work.  You can do a lot with lynx, links (both web browsers but different) and screen.  It just so happened that the main things I needed for my job were terminal emulators (VT220, 5250 and 3270) and a compiler.  My favorite editor is still vim, so I was covered there.  My mail reader was pine.

You can adjust the size of the characters on your terminal, you don't just have to live with that they give you.

This sort of setup is perfectly fine for any non-workstation.  Ubuntu Server is a terminal-only setup, although you can install X if you want.  Ubuntu Server is a pretty good starting point for a mainstream server IMO.  But it's still going to be oriented toward modern hardware, which you probably won't have much luck with.

Using a CLI box as a workstation gives you a slightly slanted and frustrating view of the world, but it worked for me for quite awhile.

Awhile back, Linux geeks started saying that Linux was the fastest operating system you would ever put on your computer.  That was based on the fact that you can have a multi-user operating system without the overhead of graphics.  At the time, accelerated graphics cards were not the norm.  Even so, I think today you would get a noticeable speed boost.

Anymore, people still say that but they're wrong.  Get a fully loaded GUI with all the bells and whistles turned on and you're significantly slower than Windows or Mac.  Use Blackbox or FVWM and you might still get the advantage.

But all that said, if you do want X then go for a stripped down X with a very lightweight window manager.  Blackbox is just a super simple WM you might want to try first.

---

### Post by mastablasta on 2012-08-08
> **TheGuyWithTheFace said:**
> Well, I installed crunchbang, and the install went well, but the system keeps hanging during startup on "loading initial ramdisk". If I can't get that worked out, debian's next on the list.
 
chrunchbang is debian (easier to install and some added backports for better hw support). suggest you troubleshoot the install rather than go pure debain first.

---

### Post by TheGuyWithTheFace on 2012-08-08
Well, I couldn't find anything from googling it, do you have any ideas?

---

### Post by Cheesemill on 2012-08-08
Try asking on the CrunchBang forums, they're a friendly lot over there.

[http://crunchbanglinux.org/forums/](http://crunchbanglinux.org/forums/)

---

### Post by mastablasta on 2012-08-08
yeah best to just ask on their forums. otherwise:
[http://ubuntuforums.org/showthread.php?t=1756703](http://ubuntuforums.org/showthread.php?t=1756703)

It's probably something else form what i can tell:
[https://www.google.com/search?q=loading+initial+ramdisk&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:sl:official&client=firefox-a](https://www.google.com/search?q=loading+initial+ramdisk&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:sl:official&client=firefox-a)

it's best to run botoinfoscript and then post on their forums. 

another option is AntiX. It has IceWM or Openbox. and i think it is based on debian and mepis (mixes packages form debian stable and Ubuntu). well at least older versions were on mepis.
I think latest version of antix uses debian testing.
> It should run on most computers, ranging from 64MB old PII 266 systems with pre-configured 128MB swap to  the latest powerful boxes. 128MB RAM is recommended minimum for antiX.  The installer needs minimum 2.2GB hard disk size. antiX can also be used as a fast-booting rescue cd. 

---

### Post by TheGuyWithTheFace on 2012-08-08
ok, I'll try antiX next if debian doesn't work. I couldn't find anything in the forums about crunchbang, but I was able to install debian with the exception of grub or lilo. So, right now, I'm trying to find a way to install a bootloader, but if I do that, I *should* have a functional system waiting for me...

---

### Post by TheGuyWithTheFace on 2012-09-08
Well, after much trial and error, (mostly errors), I put tinycore on it with an LXDE desktop environment, and it works like a charm!

---

### Post by TygerTung on 2012-09-08
Is it rather fast?

---

### Post by TheGuyWithTheFace on 2012-09-08
Actually, yes! It's hardly a supercomputer, but it's plenty fast enough so long as I have less than 3 tabs open, but given that it has only 192 megs of ram, that's pretty decent. Beats windows 98, which it originally had, and it can run modern programs, so I'm pretty happy!

---

