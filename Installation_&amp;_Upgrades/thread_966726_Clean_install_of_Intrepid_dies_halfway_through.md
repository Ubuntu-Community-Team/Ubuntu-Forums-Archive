---
title: "Clean install of Intrepid dies halfway through"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by ftmichael on 2008-11-01
I had a look through the forums and couldn't find anyone who had the same problem I'm currently having.  I downloaded the 8.10 .iso and burned it to an install CD, then put it in my new (secondhand) desktop, which had Windows XP on it.  I booted from the disc and got through the first few steps of the installation with no problem - setting the language, time zone, and keyboard layout; telling it I wanted to use the entire hard disk for Ubuntu, overwriting everything currently there; and setting my name, password, and the computer's name.  It gave me the little confirmation screen and I clicked Install.

From there, the screen went garbled briefly, then black.  After a few minutes, it brought up the Intrepid login screen.  Entering my name and password gave me an error, no matter how many times I tried.  I left it alone so it would log in as 'ubuntu' automatically after a few seconds.  When it did this, it gave me a blank orangey-tan (Intrepid default colour, but without the wallpaper) screen, which stays put for as long as I leave it.  After a few minutes like that, the install disc stops spinning and the hard drive doesn't seem to be doing anything either.  Moving the mouse will move the cursor on the screen, but clicking (left or right) does nothing.

The first time I ran the installer, it said that the hard disk was in two partitions of about 50% each, which I told it to overwrite.  The second and third times I ran the installer, it said that one partition was 98% and the other was 1% - again, I told it to overwrite.  And booting without the disc in place gives me an error, saying that it has nothing to boot from and I should insert the boot device and press F1 to continue.  Inserting the Intrepid install disc and pressing F1 takes me back to the screen with the options - try Ubuntu, install Ubuntu, check disc for errors, etc.  So clearly it started to overwrite, got rid of 98% of the data on the (60GB) hard disk, then crapped out somehow.

I tested the CD for errors and it said there weren't any.  I ran memtest off the Intrepid disc - it ran for 15 minutes or so and found no errors.

I ran it as a live CD, selecting 'try Ubuntu with no changes to my hard drive' or whatever it says on the initial menu, and had the same issue - it took me to a login screen, where I left it alone for ten seconds so it would login as 'ubuntu', and I got the same blank default-colour screen - except when left for a few minutes, the screen turns black, still with the cursor visible.  Moving the mouse (and therefore the cursor) makes the disc start spinning again, but the disc doesn't seem to actively do anything, and there's no change on the screen.

I'm at a loss at this point.  Thoughts?

---

### Post by zaine_ridling on 2008-11-01
Similar experience. Want to start over with a new install (was running 8.04); boot CD to blue screen of choices, select install, HD whirs for a minute, then dies to a black screen. I can CTRL+C to a prompt is all, other than hard reboot.

I would guess it's not picking up my ATI 4850 card, but as a n00b, I don't know how to install them prior to installing the OS! Ouch. Now I'm longing for the old days of 8.04.

---

