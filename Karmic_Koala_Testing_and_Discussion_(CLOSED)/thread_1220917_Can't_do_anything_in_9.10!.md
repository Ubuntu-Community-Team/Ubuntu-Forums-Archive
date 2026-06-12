---
title: "Can't do anything in 9.10!"
date: 2009-07-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tjscool914 on 2009-07-23
Hi All, 

I recently installed 9.10 on my desktop.  Everything was working fine for about 3 days.  Then one day the mouse froze out of nowhere while I was working.  Had to hit the power button to reset my computer.  It booted and was working fine for a few hours when the mouse suddenly froze again.  Had to reset with the power button again. This time, my computer booted, but nothing is working.  It boots into Ubuntu fine and I can login, but I can't do anything from the desktop.  I am able to move the mouse around, but I can't click on any menus(applications.places,system).  Ctrl Alt Delete doesn't do anything.  All I can do is look at my nice desktop and hit the power button to shut the computer off!  Does anyone have any ideas on what might have happened? How to fix it?  Like I said.. it worked fine for a couple days.  :confused:



Thanks for your help!

---

### Post by anagor on 2009-07-23
If you are new to Ubuntu, and/or Linux in general, it will probably be better if you install the 9.04 version, since the 9.10 is still under development and is bound to break (rarely, but still happens).

Also it would be much easier to help you, if you can supply some additional info on your setup.
Is this a 64 or 32 bit version?
Is this Ubuntu or Kubuntu? (gnome or kde or maybe xfce?)
What kind of graphics card you have there and what kind of drivers does it use? (restricted or open)
Do you have compiz (desktop effects) enabled?
Can you work with the keyboard, I mean, can you still press alt-f1 for example to open the menu, and navigate there and inside applications?
Also, since the problem is with your mouse, what kind of mouse is this?

cheers;
Mark.

---

### Post by tjscool914 on 2009-07-23
Hey Mark, 

Thanks for your response.  I am fairly new to Linux.  9.04 was working just fine.  I installed the latest release, even though I new it was still under development!  Here are the answers to your questions:

1.  This is a 32 bit version.
2.  This is Ubuntu and I am using gnome.
3.  I'm not sure what type of graphics card and drive is being used.  I knowits an onboard graphics card.  I believe its a dell gx280.  I will have to check once I get home.  Also have problems with google... looks like someone hacked it.  
4.  I do not have compiz fusion enabled as the graphics card will not support it.
5.  I tried pressing Alt-F1 with no success.
6.  I am using a dell 2 button ps2 mouse.

I will get the graphics card and drive details for you!

---

### Post by anagor on 2009-07-23
Since it's onboard graphics card on dell, it's probably intel's one.
I'm unfortunately don't have such card to test, but I know that the drivers for those cards are going through major overhaul in the upcoming ubuntu (9.10) so there might be a problem with them, also you mentioned that the keyboard doesn't work either, alt-f1/ctr-alt-delete, so it starts to look like the X server is frozen on you.
I would suggest to try and update the system with the latest packages, maybe the problem was fixed already (today karmic alpha3 got out, and one of the fixes was for intel graphic cards, [see here]("http://www.ubuntu.com/testing/karmic/alpha3"))
You can download and install it from this link, or to do an update:
while in the login screen, press ctr-alt-f1, which should bring you to terminal. There, after a login, you can enter the following to update your system:
$ sudo apt-get update
$ sudo apt-get upgrade
(without the dollar sign of course :) )
If after the update and reboot, the system still freezes, boot from a live CD that does work and check the following files for obvious errors or post them here:
/home/{your_user_name}/.xsession-errors (this is a hidden file)
/var/log/Xorg.0.log
/var/log/kern.log

Hope this helps ;)

---

### Post by anagor on 2009-07-23
And about the strangely looking google search, it's not a hack, the Ubuntu devs decided to provide a custom search engine in the firefox a few days ago. There is already a bug for it in launchpad :)
You can disable it in: Firefox -> Tools -> Add-ons
There is one called Multisearch, disable it and all will be back to normal.

---

### Post by RJARRRPCGP on 2009-07-23
> **tjscool914 said:**
>   Everything was working fine for about 3 days.  Then one day the mouse froze out of nowhere while I was working.  Had to hit the power button to reset my computer. 



Thanks for your help!

Sounds like you need to check your power connector and data cable on your HDD.

---

