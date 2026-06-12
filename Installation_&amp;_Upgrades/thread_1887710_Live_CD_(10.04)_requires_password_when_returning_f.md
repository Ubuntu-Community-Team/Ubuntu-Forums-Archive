---
title: "Live CD (10.04) requires password when returning from screen-saver"
date: 2011-11-27
forum: Installation &amp; Upgrades
---

### Post by jharris1993 on 2011-11-27
(Note:  I posed an abbreviated version of this as a reply within the "General Help" forum.  I am re-posting here so that I can make it easier to find within a search, and to expand on the issue.)

I suspect rather strongly that this is - or should be - a bug.

**_Issue_:**
Started a HP laptop (though I suspect any computer would do  this) into the Live CD to do a disk image of a multi-boot Windows/'nix  box to an external USB drive (using ddrescue)

While the image was being spooled off to a USB drive, I began working on  another system.  Eventually I went back to the Ubuntu Live system and  it had gone into "screen-saver" mode.  Upon returning from screensaver  it wanted a password - and nothing worked!

I tried all the obvious choices:

[LIST]
[*][blank]
[*]"password"
[*]"Password"
[*]"ubuntu"
[*]"Ubuntu"
[*]"Ubuntu 10.04"
[*]. . . and a few others that I don't remember right now.
[/LIST]
 
This particular CD image was downloaded from one of the "Genuine Ubuntu" :) mirrors, and it has passed CD Verify repeatedly.

**_Question_:**
If the live CD is supposed to boot and start w/o a password, why  does it request a password on return from screen-saver?  :confused:

IMHO, this represents a HORRID user experience, especially if the user is not exactly a bleed-edge Ubuntu/'nix sysadmin.

**_Workaround_:**
CTL-ALT-F1 brought me to a shell where I could create a password for "ubuntu", I just ran "passwd" and supplied a  new password.  Returning to the graphical screen then allowed me to  login.

What say ye?

Jim ()JR)

---

### Post by ajgreeny on 2011-11-27
The password for the live CD is completely blank, so if you had just hit "Enter" when the request appeared, without typing anything, you would normally have been logged in again as the live session user, ubuntu.  However, I have never seen a live CD with a screensaver that needs a password so I wonder if your CD was corrupt in some way.

Apart from this problem, does everything else seem to work OK, or do you have other glitches that appear from time to time.  It is probably worth checking the CD next time you boot.

---

### Post by jharris1993 on 2011-11-27
> **ajgreeny said:**
> The password for the live CD is completely blank, so if you had just hit "Enter" when the request appeared, without typing anything, you would normally have been logged in again as the live session user, ubuntu.  However, I have never seen a live CD with a screensaver that needs a password so I wonder if your CD was corrupt in some way.

Apart from this problem, does everything else seem to work OK, or do you have other glitches that appear from time to time.  It is probably worth checking the CD next time you boot.

Re:  Hit "Enter"
That was the FIRST thing I tried.

I wonder _why_ they have a screen-saver enabled (and have the power options set to "_**suspend on lid close**_"?!!! :rolleyes: )  I totally clobbered a 500 gig spool right smack dab in the middle of it - simply because I _**closed the *&^%$#!!! lid**_ on my laptop! ](*,) (emoticon:  smoke out of both ears)

Re:  Re-re-re-checking the CD.
I guess I could do that, but I have done this at least a zillion times and it's always totally OK.  However, since CD's DO go bad, I will try that again.

Re:  Everything else.
Everything else works right-as-rain.

Except for some of the, (IMHO), asinine choices :) made by the people who spin this beast, everything works wonderfully.   In fact, I have an assortment of Ubuntu live CD's that will run on just about everything aside from a flat tire or a undercooked pancake.

I don't mean to grump or flame - it's just that watching a half-day's work go down the toilet tends to make me just a tad unhappy.

Thanks for the answer!

Jim (JR)

---

