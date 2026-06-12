---
title: "LIve DVD Login &amp; Password????  (SOLVED)"
date: 2019-07-21
forum: Installation &amp; Upgrades
---

### Post by ken0069 on 2019-07-21
I've been trying for two days now to install Ubuntu Mate 18.4.2 x32 bit in a Dell 4300 x32bit desktop that was previously running Linux Mint 17.3 x32, but I'm having major problems getting past the login screen because I don't know the username and password and haven't been able to find it on internet search?? BTW, this is the first time I've encountered this?  FYI I did an install of Ubuntu Mate 18.4.2 x64 on two other systems here that were running Mint 17.3 and didn't see the login screen on either of those?

So, I was thinking there was something wrong with that ISO image I burned to that DVD so I went and downloaded Ubuntu Mate 18.4.2 AGAIN (on my metered service Sprint hot spot) only to find out that it's doing the exact same thing as the original one did, ie, boots to the login screen that I can't get past???? 

So could someone please explain to me WHY all of a sudden the Live DVD username and login has appeared and does anyone know what the username and login is suppose to be for that system??

Thanks,

Ken

---

### Post by PaulW2U on 2019-07-21
I think you must have logged out which is why you're being asked for a password to log back in.

As far as I know the user-name is **ubuntu-mate**. There is no password.

Hope that helps.

---

### Post by deadflowr on 2019-07-21
Try ubuntu-mate for username and leave the password blank.
This should still hold:
[https://ubuntu-mate.community/t/live-session-password/7219/2]("https://ubuntu-mate.community/t/live-session-password/7219/2")

edit: That^^^
ninja'd

---

### Post by ken0069 on 2019-07-21
Nope!  Ubuntu Mate doesn't work and neither does ubuntu-mate or ubuntumate with and without caps on the first letter of those words.  I've done a bunch of searching and used everything I could find but still can't login.  

And this one doesn't work either.  [https://ubuntu-mate.community/t/live-session-password/7219/2](https://ubuntu-mate.community/t/live-session-password/7219/2)

Oh, and FYI this login screen shows up as the desktop when LIVE DVD FINISHES BOOTING so there is no way I could log out when I never logged in.

---

### Post by PaulW2U on 2019-07-21
> **ken0069 said:**
> Oh, and FYI this login screen shows up as the desktop when LIVE DVD FINISHES BOOTING
I've no idea why that is happening. It's not something that I've ever seen.

I've just booted into an Ubuntu MATE live session and checked both the GUI log-in and tty log-in. The user-name is definitely **ubuntu-mate**, i.e. all in lower-case. No password required.

---

### Post by CatKiller on 2019-07-21
> **ken0069 said:**
> So could someone please explain to me WHY all of a sudden the Live DVD username and login has appeared
An X crash will do that: automatically logs in, X crashes, back to the login screen as the first thing that gets shown when X restarts.

---

### Post by ken0069 on 2019-07-21
So what would cause an "X" crash then, whatever that is?  :confused:  

Like I said, that Dell has been running Linux Mint 17.3 for a while now but it's at end of life is the reason I was going to Ubuntu Mate 18.4.2, which I like because of the minimal install it will do without all the useless junk of a full install.  

The "**ubuntu-mate" **username login does not work.  One thing I haven't done is try to boot from that DVD in something else to see if the same junk shows up.  I'll try that later on this evening and let you know how that works out.

Thanks for the input guys!!

---

### Post by CatKiller on 2019-07-21
> **ken0069 said:**
> So what would cause an "X" crash then, whatever that is?  :confused:  

[https://en.wikipedia.org/wiki/X_Window_System](https://en.wikipedia.org/wiki/X_Window_System)

Pretty much anything. It's crufty and creaky and fragile and 35 years old, and no display device manufacturer is especially inclined to be forthcoming with details of their implementation nor to strictly follow the best practices of software used by a tiny proportion of their customers.

> The "**ubuntu-mate" **username login does not work.

By "does not work" I take it that you mean "goes back to the login screen," rather than saying, "incorrect user name or password," since you haven't said.

---

### Post by TheFu on 2019-07-21
I would suspect that the source of the ISO isn't reputable or has corrupted the installer.  I've never seen a live boot Ubuntu-Mate require a login.  It should boot to a desktop.  To get back to it, just reboot, don't try to logout and login.

Check the sha256 sums for the ISO file used with the official Ubuntu-Mate ISO sha256 sums.

---

### Post by ken0069 on 2019-07-21
FYI, ISO image came from an FTP server called heanet.ie.....twice, downloaded using Filezilla?  Don't think there's any more reputable than that one.  

Ennywho, that DVD DID boot normally on another system so I'm assuming it's not the disk/ISO Image.  

Tomorrow I'm going to experiment with some different hardware (DVD drive and Video card) to see if that has any effect on it.  I've also got an ISOs of Linux Mint-mate 18.3 and Mint-Mate 19.1 that I'll try as well.  

Again...........Thanks for taking the time to help with this guys!!!

---

### Post by pascua28 on 2019-07-22
It's odd. Never experienced such. Maybe try to leave both blank?

---

### Post by TheFu on 2019-07-22
> **ken0069 said:**
> FYI, ISO image came from an FTP server called heanet.ie.....twice, downloaded using Filezilla?  Don't think there's any more reputable than that one.  

Ennywho, that DVD DID boot normally on another system so I'm assuming it's not the disk/ISO Image.  

Don't assume anything.
What about the sha256 sums?
What's wrong with [https://ubuntu-mate.org/download/](https://ubuntu-mate.org/download/) ???  You know, the official source?

Mint is a different distro and has nothing to do with Ubuntu's packaging.

---

### Post by ken0069 on 2019-07-22
FOUND IT!  Seems Ubuntu Mate 18.4.2 x32 does NOT like anything legacy Nvidia!  I tried 4 different Nvidia AGP cards I have in it and all did not work, but some with different symptoms, ie, one wouldn't show video at all!  Heck I even tried a couple of PCI cards and they didn't work either.  Oh well.  

So, I had an ATI Radeon 9500 Pro AGP card in another system and tried that and BINGO!  Worked and installed with it.  Only problem being that video card is for another system I use as a Quake II LAN game server so I don't want to leave it in the Dell.   

Ennywho, I just decided to put the original Nvidia card back in it and install Linux Mint 18.3 and be done with it, in fact, that install just completed a few minutes ago so now I can start removing all the crapware that I don't want on it.  

Again THANKS GUYS for the input and I'll just mark this one "SOLVED" and be done with it.  

Have a wonderful day!!

---

