---
title: "Ubuntu liveCD in frozen and in perpetual loading"
date: 2007-10-14
forum: Installation &amp; Upgrades
---

### Post by JohnESmith on 2007-10-14
Yes, I'm afraid there exist many threads similar to this but I have found no viable solutions for my particular situation:  Installing Ubuntu from the live disk, I came upon the install menu.  Upon selection of the first option (run or install ubuntu), I was greeted with the green text "loading".  This state of "loading" persists for the next hour.

My patience utterly spent, I switched off the computer, stormed off swearing up a hellstorm, and kicked the knickers out of everything plushy that I owned (chair, mattress, etc.) .  In the ensuing weeks, such episodes would repeat itself scores of times.

I have, up to this date, lurked on dozens of forums, downloaded multiple copies of (the same version of) ubuntu, checked the MD5 numerous times, burned 3 separate cds, and have found no solution what so ever.

Help greatly appreciated.  (sorry about the poor writing and lack of cordiality)

(the issue may stim for the burning of the cd.  Each time I burn the iso. the CD is ejected in under 30 seconds.  I'm all for expediency but for a 700mb burn load, that's a little too fast)

---

### Post by Martje_001 on 2007-10-14
Try the alternate cd to install.

---

### Post by Pumalite on 2007-10-14
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Make sure you do md5sum on iso and burn at 4x)

---

### Post by JohnESmith on 2007-10-14
will that help since my computer *does* read live disks (have booted Knoppix)?

---

### Post by JohnESmith on 2007-10-14
I've burned at 1x speed but it was still the same haste with the ejection.

---

### Post by Pumalite on 2007-10-14
If you have less than 512 RAM, an ATI Card or Integrated Video, or other hardware problems[chipsets], then: YES

---

### Post by JohnESmith on 2007-10-14
ok, I have integrated video so I will do that.

---

### Post by ryanVickers on 2007-10-14
that *could  *e a problem - Ubuntu is usually pretty decent with compatibility - my nvidia 7600 GT became supported in 6.06, and everything has worked since!

My point, try (temporarily) disabling your video

---

### Post by JohnESmith on 2007-10-14
I installed with the alternative (text based) disk and the same problem persisted.  It also appears that the computer is *hardly* loading anything as there seems to be a lack of any audiable activity in the CD drive.  I am able to see the menu fine but the system seems to freeze whenever I hit enter.  What I find could be the problem is the fact that the 700 mb cd was burned in less than 30 seconds (and burns as the same rate when I select 1x speed), which by all means, is *uncanny* and furthermore, when looking at the burned disk, the ring indicating the presence of data stretches barely 1/5th the radius of the disk.  Something seems to be at foul (though I've burned 4 disks to the same effect).

---

### Post by Pumalite on 2007-10-14
What about the md5sum on the iso and did you burn it as an 'Image'. And what software are you using to burn the iso?
Download ImgBurn: [http://www.imgburn.com/](http://www.imgburn.com/) Install. Go to Mode>ISO>Burn
Burn at 4x
Have you checked your burner?
Clean the lens. Update the firmware.

---

### Post by JohnESmith on 2007-10-14
I have checked the md5sum and am fairly sure it's burned as an image (or at least a portion of it) since it booted the menu at all.  I actually have ubuntu hoary and am using the right-click > write to CD method.  And on the topic of imageburn, since I'm using an outdated ubuntu, wine no longer supports it.  And lastly, I have not checked my burner or firmware, but it has seemed to work fine for all other software and files I burn.

---

### Post by Pumalite on 2007-10-14
You can use k3b or:

[http://sharkysoft.com/tutorials/linuxtips/cdcommands/](http://sharkysoft.com/tutorials/linuxtips/cdcommands/)

---

### Post by JohnESmith on 2007-10-14
ok, I burned the disk with the aforementioned commands through the terminal.  Somehow nothing happened (well more specifically, a numer of errors happened).  But on a related note, how is kd3 different from just writing the image to the CD?

---

### Post by sidyom on 2007-10-14
i'm having the same problem as you.
in kubuntu and in the new beta, my ISO's were verified, and i get to the install screen, and i hit enter, and nothing happens.
what are your system specs?

---

### Post by Pumalite on 2007-10-14
k3b. Try it. Tools>Burn CD Image

---

### Post by sidyom on 2007-10-14
i'm working with only xp

---

### Post by Pumalite on 2007-10-14
Download and install ImgBurn:[http://www.imgburn.com/](http://www.imgburn.com/)
Go to Mode>ISO>Burn

---

### Post by JohnESmith on 2007-10-14
I've got some old Radeon (700x?  something like that), about 516 ram, Pentium, I forgot the speed, 2g, something like that, forget what the motherboard is (dobt it's important to this situation), and I'm booting ubuntu hoary.

---

### Post by sidyom on 2007-10-15
pumalite, does it really make a difference? i used magicISO.
it wasn't burned improperly, or else it wouldn't have gone to the install screen, right? :confused:

---

### Post by Pumalite on 2007-10-15
If you burn as an 'iso', then is fine. You cannot burn as 'data'.

---

### Post by sidyom on 2007-10-15
okay. i know i burned them as an ISO file. i've tried to boot from cd, and when i do i get a blank screen. i read the help section on the cd, and i changed the boot option so that it is boot: live
this results in a showing of the actions, and it stops at an error saying:
kernel panic! vfs: unable to mount root fs on an unknown block (104,1)

what does that mean?

---

### Post by JohnESmith on 2007-10-16
this thread has been *hijacked*

Well, that's ok, it's good to hit two birds with one rock.  Anyway, I burned the text alternate installation and as of now, it has been displaying the same problem that plagued my other attempts.

---

### Post by Pumalite on 2007-10-16
Try your CD's on another computer and see if they work.

---

### Post by JohnESmith on 2007-10-17
Didn't think of that.  Blasted stupid of me, I'll try it out tommorow, when I can get my hands on another computer.

---

### Post by mikelng555 on 2007-10-18
same problem..
the cd is ok because its booting to my other pc(Intel P4 x86)
but i'm trying to install it to my other pc(amd athlon x64) it's not working
i know you'll say because its x64 thats why, but i tried installing XP and vista x32 and its working..
the problem is the when i enter to install ubuntu, next screen would just go blank.
I adjusted the screen size to 1024x768 through f4 then another screen appeared after I press install..
it shows the ubuntu logo and he progress bar...
but its not moving at all.

---

### Post by JohnESmith on 2007-10-18
alright, tried another computer, disk was broken ( always figured it burned too hasty).  Burning another. Will edit when results return.

---

### Post by Pumalite on 2007-10-18
> **mikelng555 said:**
> same problem..
the cd is ok because its booting to my other pc(Intel P4 x86)
but i'm trying to install it to my other pc(amd athlon x64) it's not working
i know you'll say because its x64 thats why, but i tried installing XP and vista x32 and its working..
the problem is the when i enter to install ubuntu, next screen would just go blank.
I adjusted the screen size to 1024x768 through f4 then another screen appeared after I press install..
it shows the ubuntu logo and he progress bar...
but its not moving at all.

Try 32 bit.

---

### Post by jejones3141 on 2007-10-18
> **JohnESmith said:**
> But on a related note, how is kd3 different from just writing the image to the CD?
k3b gives you the option to ask for verification of the CD after burning, and will also display any error messages from the underlying programs that it uses to burn the CD--that will save you from rebooting until you have a CD that you can be fairly sure is good.

Just out of idle curiosity, go to a shell and type

hdparm /dev/hdx

where you replace x with either a, b, c, or d as appropriate for the CD burner you're trying to use. Unless you have a rather old motherboard or  CD burner, they should be capable of doing DMA, which can make a big difference. hdparm will let you know whether DMA is enabled for it, and will let you turn DMA on if the burner and motherboard are capable of it.

---

### Post by JohnESmith on 2007-10-22
alright, GRUBS actually did *something or another* to my BIOS (or whatever it did) so things wouldn't boot and my cd reader square out wouldn't install anything (frozen every five minutes) translating, therefore, to no live disks.  But I'm sharp now.  Thanks all for replies.

---

