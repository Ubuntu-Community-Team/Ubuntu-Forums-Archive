---
title: "Toshiba Satellite Pro 4600 won't install Lubuntu"
date: 2014-08-28
forum: Installation &amp; Upgrades
---

### Post by cheapodonuts on 2014-08-28
After formatting the HD and failing to get Lubuntu 14.04 installed, I have proved the machine by installing Win98se from an original disc, but no Linux discs will run properly. The only fault with Win98 is that the screen size won't allow adjustment to fill the screen. But my new Lubuntu 14.04 disc always fails after a while, even though I just checked it and installed a second partition successfully on my PC.
I can't run Lubuntu from the live disc on the laptop, and a normal install ends up looking like this,

[[IMG]http://i81.photobucket.com/albums/j226/chashugh/FailedLubuntuinstall.jpg[/IMG]]("http://s81.photobucket.com/user/chashugh/media/FailedLubuntuinstall.jpg.html")

Checking the disc for faults also shows the same error list.

What is going on?

---

### Post by mörgæs on 2014-08-28
This is not old, but ancient hardware. Nevertheless, if you want to give it a try just for the challenge it's better to begin with the [minimal Lubuntu]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall").

How much memory does it have?

---

### Post by cheapodonuts on 2014-08-29
Hi mörgæs

Using system tools in 98se it appears to be unmodified with 256m RAM (duble the quoted minimum) and a 18gig HD. But hey, if you ask Miley Syrus fans, they'll say that limited resources are beautiful.  ](*,) :rolleyes:

---

### Post by ubfan1 on 2014-08-29
With the Nvidia 6150, you will need the "nomodeset" kernel boot option (F6 at the menu).  Did you hashcheck the downloaded iso?  Did you ever run the media check successfully (maybe on another machine)?  Did you burn the disk as slowly as possible?  I'm running pretty similar HW (Nvidia 6150, 2G ram, AMD Turion, without problems, once I get the Nvidia-current package installed.

---

### Post by mörgæs on 2014-08-30
Ubfan1, thanks for your help but your hardware is much stronger than original poster's. What he states in the signature is not the computer in question.

I never understood why people put hardware specifications into the signature anyway. It only confuses Google (and sometimes people, too).

---

### Post by cheapodonuts on 2014-08-30
Thanx ubufan but that's my PC your talking about not the old Tosh Satellite pro that I'm messing with. My disc is a direct prchase from Linux Shop and works well. The laptop has now gone back to my buddy who owns it with Puppy Linux installed and working (so far).

---

### Post by cheapodonuts on 2014-08-30
Thanx mörgæs, most of my posts are probably on the Absolute Beginner section, as I always forget stuff due to severe tinnitus. But the sys spec in the sig was originally suggested by mods when I first joined the forums.

I have now installed Slako Puppy 5.7.0 in the Tosh so we'll see how my friend gets on with that. He was saying that he nearly threw it out the window before, but he likes dogs, so. . . . ;)

---

### Post by cheapodonuts on 2014-08-30
Marked as solved, although the problem was not addressed, I just went a different route. ;)

---

### Post by mörgæs on 2014-08-30
Posting hardware specifications in original post is a good habit, but I don't see the point in having it in the signature. It surprises me if a mod came up with the idea.

Thanks for the SOLVED flag. I would say that getting any operative system to run on a 4600 is a good solution :-)

---

### Post by cheapodonuts on 2014-08-30
Hah! I have a selection of older PC towers here and will have a go with Puppy in all of them shortly. :p

---

