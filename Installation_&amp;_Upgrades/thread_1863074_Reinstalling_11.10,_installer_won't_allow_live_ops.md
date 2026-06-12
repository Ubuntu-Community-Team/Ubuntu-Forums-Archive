---
title: "Reinstalling 11.10, installer won't allow live ops or install"
date: 2011-10-17
forum: Installation &amp; Upgrades
---

### Post by Fraoch on 2011-10-17
The upgrade from 11.04 to 11.10 did not go well - I had so many issues that I decided to reinstall.  I've upgraded it every time since Dapper, so I figured it was time.

Big mistake.  I just can't get 11.10 installed.

My question is - why won't the installer let me run live or install to a hard drive?  When I select either of these options it just beeps and won't go past the menu.

I am trying to use "rescue a broken system" from Advanced options, but that fails when reinstall is nearly complete, as it's installing software for an Ubuntu Desktop install.  This is after I've reformatted all my drives to make sure there are no existing files interfering.

This is using the alternate install .iso, with the standard .iso I get a corrupted screen.  I don't think it's the media (I'm using a USB flash drive), it installed all the software once but screwed up GRUB.

Oh what a day...](*,)

---

### Post by 23dornot23d on 2011-10-17
If its failing towards the end each time ..... 

I would first look at faulty burn to CD

does the Md5 match with the one on the download page you used .....

The other thing if the screen messes up after , is it a ATI graphics card ... seems
a few problems with these are being reported after the upgrade ....

Check link below to see if there are any similar problems and solutions .......

---

### Post by Fraoch on 2011-10-17
Thanks for your response!

> **23dornot23d said:**
> If its failing towards the end each time ..... 

I would first look at faulty burn to CD

My thought as well, although this is a USB flash drive.  I tried to verify the installation media but the installer wouldn't allow it (saying it was not valid).  Is it expected to work for USB installation media?

I reformatted and rewrote the drive several times.

> does the Md5 match with the one on the download page you used .....

Yes, it does.

> The other thing if the screen messes up after , is it a ATI graphics card ... seems
a few problems with these are being reported after the upgrade ....

nVidia 9400 GT actually.  I remember having problems with this before when I installed Ubuntu into a VM, I'll try playing around with boot arguments but I'm not sure what to use with 11.10.

> Check link below to see if there are any similar problems and solutions .......

Thanks, I am looking into it.

It seems a package does not install properly.  I get to about 17% on the install bar and it fails every time - I'd guess it's the same package but it goes by too fast for me to see.  I tried a little experiment and selected packages manually.  I don't think it worked all that well, aptitude was complaining about unresolved dependencies which I didn't know how to solve.  But installation did complete and GRUB did install properly, it did boot for the first time today...but I got a corrupt display (I'm thinking it did not get the right video driver installed).  I was at least hoping for a shell.

I may be moving on to trying to install 10.04.3 LTS - I'd like to get something, anything, working today.:(

---

### Post by Fraoch on 2011-10-17
I gave up on trying to configure my command-line 11.10 install.  I just couldn't get the "nouveau" driver to work with my 9400 GT and there's not much relevant (or new) information on the Internet.

My last attempt was to install off the minimal CD ( [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) ) and pull everything from the repos but that resulted in an install that wouldn't boot.

So now I'm trying 10.04.3 LTS and if that doesn't work I am just plain giving up.:(  I've tried installing at least 15 times today and I'm not getting anywhere.

---

### Post by Fraoch on 2011-10-17
Holy flying !@$% , I finally installed it!

I'll mark this thread as "solved" but the key was to press Tab to edit the install options and add "nomodeset" (without the quotation marks) at the end of the boot arguments.  I read [here]("http://ubuntuforums.org/showpost.php?p=9782255&postcount=7") that this worked with nVidia 9600 GT boards, so...

That allowed me to boot into the graphical (desktop) installer in low-video mode.  The installation then worked - the link above stated that I'd need to edit GRUB on boot but it booted fine!  The proprietary nVidia driver (version 173) was enabled and working.

Everything seems to be working fine in my new install now - in fact I'm typing this from my Ubuntu box rather than the old Windows XP laptop right now.  Boy, that was scary.

---

### Post by 23dornot23d on 2011-10-17
Good one glad you got it sorted .... ;)

---

