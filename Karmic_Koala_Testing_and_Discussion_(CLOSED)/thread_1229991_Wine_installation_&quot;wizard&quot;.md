---
title: "Wine installation &quot;wizard&quot;"
date: 2009-08-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tuxpenguin on 2009-08-02
I've seen the idea of bundling Wine with Ubuntu mentioned many times. Personally, I'd love to see this done, even if just to impress some Windows fanatics with Ubuntu. It would be great to be able to pop in a Photoshop CD [or something along those lines] and have Wine seamlessly run the installer.

However, I understand why this hasn't been done yet. It would add weight to the .iso file size, and I'm sure Wine is a pain to configure for packaging before the actual OS install. However, it would be very convenient and new-user-friendly to have *something* that helps to use Wine. Let's say a new user has just finished installing and updating a new Ubuntu install, and not knowing any better, tries to open a .exe file to install a piece of Windows software. He is prompted with a dialog box [or other notification] that briefly explains that this file is not natively compatible with Ubuntu, but also offers to install Wine from the repos and try running it that way. Maybe even explain the limitations of Wine, or give a list of programs that are currently known to work.

Like I said, I don't claim to know better than the devs, but I just thought I give you my opinion. Little touches like this go a long way to impress new users. Anyone else have any ideas like this?

---

### Post by running_rabbit07 on 2009-08-02
On the reverse side I'd love to see Microsoft start making their programs so that they run on Linux. Though they have very few programs I enjoy. Photoshop would be a nice addition to Linux.

---

### Post by zekopeko on 2009-08-02
This is being considered as part of Appcenter.

[https://wiki.ubuntu.com/AppCenter#Unresolved issues](https://wiki.ubuntu.com/AppCenter#Unresolved issues)

---

### Post by psyke83 on 2009-08-02
Bundling WINE is not a good idea. Having it installed by default will lead users into believing that Ubuntu is fully compatible with their Windows programs. 

Really, it will. We could have a huge neon light on the homepage saying "Not 100% Windows compatible", and cognitive dissonance would transform that warning into "100% Windows compatible!".

This will also open another attack vector to Ubuntu - users installing random .exe files from the internet. Whilst I'm not too confident that WINE has such perfect support for Windows malware (fortunately), I'm sure there are cases where rogue software can damage files in user directories.

---

### Post by buzzmandt on 2009-08-02
I agree with psyke, then people will be wanting to use internet explorer for wine and malware becomes a real risk.  It has to be understood that windows progs and exe's do not run natively and I think the whole one extra step it takes to install wine serves that purpose.

---

### Post by Reiger on 2009-08-02
There is PlayOnLinux though. You may want to take a look at that.

---

### Post by phenest on 2009-08-03
If you want to impress users, then show them what Linux can do *without* Windows. Otherwise, they won't see the need to switch to Linux, because Linux will look like it's semi dependant on Windows.

---

### Post by inportb on 2009-08-03
> **running_rabbit07 said:**
> On the reverse side I'd love to see Microsoft start making their programs so that they run on Linux. Though they have very few programs I enjoy. Photoshop would be a nice addition to Linux.

Well, Microsoft is making Linux run on Windows :x
And like, Photoshop is an Adobe product and you know how Adobe is with these things...

---

### Post by thezood on 2009-08-03
> **tuxpenguin said:**
> I've seen the idea of bundling Wine with Ubuntu mentioned many times. Personally, I'd love to see this done, even if just to impress some Windows fanatics with Ubuntu. It would be great to be able to pop in a Photoshop CD [or something along those lines] and have Wine seamlessly run the installer.

However, I understand why this hasn't been done yet. It would add weight to the .iso file size, and I'm sure Wine is a pain to configure for packaging before the actual OS install. However, it would be very convenient and new-user-friendly to have *something* that helps to use Wine. Let's say a new user has just finished installing and updating a new Ubuntu install, and not knowing any better, tries to open a .exe file to install a piece of Windows software. He is prompted with a dialog box [or other notification] that briefly explains that this file is not natively compatible with Ubuntu, but also offers to install Wine from the repos and try running it that way. Maybe even explain the limitations of Wine, or give a list of programs that are currently known to work.

Like I said, I don't claim to know better than the devs, but I just thought I give you my opinion. Little touches like this go a long way to impress new users. Anyone else have any ideas like this?

Why not show the user what a terrific program GIMP has become lately? Although perhaps not all of Photoshop's functionality but pretty close.

---

### Post by tuxpenguin on 2009-08-15
Just to be clear, I'm not trying to imply that open-source software is inferior to Windows software, quite the opposite, in fact. The whole idea of having documentation related to Wine included in Ubuntu is to show that Ubuntu can be easier to pick up and start using than Windows.

Anyway, the idea was just to see what people thought about it. :) Maybe a better option is detect what software the user is trying to install, explain how Windows software vs. Linux software works, and offer an free or open-source alternative? Of course, it's impossible for Ubuntu to recognize every piece of existing Windows software, but it probably wouldn't be difficult to offer GIMP as an alternative to Photoshop, etc.

---

### Post by psyke83 on 2009-08-15
> **running_rabbit07 said:**
> On the reverse side I'd love to see Microsoft start making their programs so that they run on Linux. Though they have very few programs I enjoy. Photoshop would be a nice addition to Linux.

Wow, I didn't realize that Adobe Photoshop was written by Microsoft. You learn something new every day... ;)

---

### Post by psyke83 on 2009-08-15
> **tuxpenguin said:**
> Just to be clear, I'm not trying to imply that open-source software is inferior to Windows software, quite the opposite, in fact. The whole idea of having documentation related to Wine included in Ubuntu is to show that Ubuntu can be easier to pick up and start using than Windows.

Anyway, the idea was just to see what people thought about it. :) Maybe a better option is detect what software the user is trying to install, explain how Windows software vs. Linux software works, and offer an free or open-source alternative? Of course, it's impossible for Ubuntu to recognize every piece of existing Windows software, but it probably wouldn't be difficult to offer GIMP as an alternative to Photoshop, etc.

You mean something like [this]("http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software")?

---

### Post by autocrosser on 2009-08-15
> **tuxpenguin said:**
> Just to be clear, I'm not trying to imply that open-source software is inferior to Windows software, quite the opposite, in fact. The whole idea of having documentation related to Wine included in Ubuntu is to show that Ubuntu can be easier to pick up and start using than Windows.

Anyway, the idea was just to see what people thought about it. :) Maybe a better option is detect what software the user is trying to install, explain how Windows software vs. Linux software works, and offer an free or open-source alternative? Of course, it's impossible for Ubuntu to recognize every piece of existing Windows software, but it probably wouldn't be difficult to offer GIMP as an alternative to Photoshop, etc.

That to me is a better option---I for one DO NOT want Wine as a pre-install on my system--I find it far less than optimal that I would find Windows-style files/folders on my system....I have tried Wine once or twice in the past & came away with a bad taste in my mouth each time--vowing that I would not do that again & having to clean up the cruft that Wine leaves behind. To this day I have always found analogs "close" enough to what I want to not resort to Wine to "fill" in the "gap".

---

### Post by Seventh Reign on 2009-08-15
> **buzzmandt said:**
> I agree with psyke, then people will be wanting to use internet explorer for wine and malware becomes a real risk.  It has to be understood that windows progs and exe's do not run natively and I think the whole one extra step it takes to install wine serves that purpose.

There are people that WANT to use Internet Explorer????

They shouldn't be allowed to touch a keyboard!

---

### Post by shafin on 2009-08-15
> **Seventh Reign said:**
> There are people that WANT to use Internet Explorer????

They shouldn't be allowed to touch a keyboard!
I'm one of them. :(
Actually it's more like sites that force me to use IE. Some sites in my native language are not unicode compliant and wont load properly in FF or Chrome. Right now, virtualbox is a better solution for me than wine, though.

---

