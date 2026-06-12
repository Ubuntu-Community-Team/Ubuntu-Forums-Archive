---
title: "How dist-upgrading hosed my installation"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by minneyar on 2006-06-02
I just thought I'd let everybody know how I managed to mess up my computer... this isn't so much of a "please help me" post, because I know what to do next, but I thought I should warn people so that they don't do the same thing.

I use KDE, and I had my screensaver set up to prompt me for a password in order to unlock the screen.  I started the standard upgrade routine; edited my apt sources, ran apt-get update, then apt-get dist-upgrade, and I let it go.  It said it had to download about 1 GB of packages, so I figured I'd just let it run in the background and check on it later.

A few hours later, I came back, and, naturally, the screen was locked.  I tried to unlock it, and I got an error message saying I would have to manually unlock the session by logging into a text terminal and killing the lock process.  I did so, and then when I tried to switch back to X, my computer locked up.  I couldn't switch terminals, and neither ctrl+alt+backspace nor ctrl+alt+del worked.  After several minutes of inactivity, I rebooted it via the magic SysRq key.

It booted back up, but about half of the services failed to start, including networking.  I told it to do apt-get dist-upgrade again, and it said I needed to run dpkg-configure; I did so, and it failed to configure most of the packages.  I tried a dist-upgrade again, and it said that it was unable to connect to any of its sources.. which would make sense, because networking was broken.

So, here I am, with a half-Breezy/half-Dapper installation that is fairly unusuable.

At the moment, I'm downloading an ISO of the CD release, and I'll see if I can use that to complete the upgrade process... otherwise, I guess I'll be reinstalling from scratch, unless anybody else has a suggestion.  So, the lesson is: just turn your screensaver off while you're upgrading.

---

### Post by ubuntu_demon on 2006-06-02
try my guide :
[http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)

---

### Post by Klaidas on 2006-06-02
Hard lucck :( 
Thanks you for sharing your story

---

### Post by sbooth on 2006-06-03
Hmm... I wish I'd read your post before I started my upgrade last night!  Things were going okay - the downloads all happened (as far as I can tell) and it was whizzing through installing things.  A couple of questions (something about postfix and something else) needed answering when I looked at it this morning and it carried on installing.  I left it when it was doing something to do with loading PCMCIA (I don't have any on that machine)... just went back to look at it and the screen is locked and doesn't seem to recognise input from the keyboard.  Tried to type my password in and no dots appear in the password box.

I've left it sitting there... to come back here to find out how to approach it.  I'm not thrilled having read the problems you've had - I'm not hugely experienced with ubuntu (but am good at following instructions when I've read them!) and hope someone can offer me some advice?

---

### Post by Scarabomb on 2006-06-03
Hehe, I feel your pain.  I first did a dist-upgrade (my dumb *** put upgrade with Dapper Sources THEN Dist-upgrade) and I got Seg faults (Fun!!) I then did again just be interrupted by my supervisor.  I decided the best bet was to get the iso's for the CD for Dapper and sho 'nuff I got some more problems.

Seems the first ISO I picked up was Dapper LTS Server.  Sounded good but doesn't give you GNOME or XSERVER or nothin'.  Next thing I tried was LiveCD install and it hangs at ./etc/boot.... so an and what not.  Also ended up mutilating a few other things that I had.

I wouldn't mind all the time I've spent but the only thing is for internet as good as I'm gonna get (T1?  I dunno but it's slow as hell) I have to pay $5 an hour and I can only give out so much money :(

---

### Post by ubuntu_demon on 2006-06-03
I hope the sticky posts here help :
[http://www.ubuntuforums.org/forumdisplay.php?f=140](http://www.ubuntuforums.org/forumdisplay.php?f=140)

If you have any questions feel free to ask them.

---

### Post by sbooth on 2006-06-03
Thank you... I had read all of the sticky posts but hoped I wouldn't have to do the live CD thing (vain hope that someone knew some magic that would get my machine to boot!).  I now do have to do the live CD thing and am waiting whilst it downloads :-(

Very frustrating... and *disable screen savers/lock before upgrading* should be instructed along with 'close all running programs before upgrading'... for idiots like me who did the latter but not the former!

---

### Post by ubuntu_demon on 2006-06-03
[QUOTE=sbooth]Thank you... I had read all of the sticky posts but hoped I wouldn't have to do the live CD thing (vain hope that someone knew some magic that would get my machine to boot!).  I now do have to do the live CD thing and am waiting whilst it downloads :-(

Very frustrating... and *disable screen savers/lock before upgrading* should be instructed along with 'close all running programs before upgrading'... for idiots like me who did the latter but not the former![/QUOTE]

I have added the tip in "warning / take a look here prior to upgrading" :
[http://www.ubuntuforums.org/showthread.php?t=185467](http://www.ubuntuforums.org/showthread.php?t=185467)

Try this guide and report the errors that you get : 
[http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)

---

### Post by sbooth on 2006-06-03
With nothing to lose, I hit the restart button... and chose both normal and 'recovery' modes at boot time, one after the other.  With either option, the graphical boot gets as far as the third thing to appear (I can't remember which one that is, off the top of my head, sorry) then kicks out to terminal view and has a couple of loading things fail (amongst a lot of 'ok')... then gets to the PCMCIA bit (which I don't need anyway) and hangs solid.  Only way out is another restart.

I'm just burning the kubuntu installation cd thinking I'll just have to start from scratch (a bit of a pain - but I believe I set up /home on a separate partition which, I believe, should help me(?) - I just have to find out how!)

Next time I get a chance (my 5 yr old and 3 yr old are keeping me busy!) I'll go try rebooting and take notes so I can be more accurate about where it falls over.

Incidentally, before it hung on me during the upgrade process the last thing I saw was something to do with PCMCIA.  Jolly annoying since I'm sure I don't need anything to do with PCMCIA!

---

### Post by sbooth on 2006-06-04
Phew.  Finally successfully installed Dapper - having reached the 'unbootable system' stage of upgrading from Breezy!

Huge thanks to ubuntu_demon who saved the day with [http://ubuntuforums.org/showthread.php?t=186672]("http://ubuntuforums.org/showthread.php?t=186672") (his HOWTO fix problems regarding broken dependencies) - which includes the HOWTO fix problems when your system is unbootable about half way through the post.

I did have the convenience of another PC to burn the live CD onto (without which I would have been completely stuck); I booted from the live CD and simply followed the instructions in the HOWTO... TO THE LETTER!  So, I figure it's worth saying that if it rescued my unbootable system it might rescue yours.

(I did have to faff around with nvidia driver installation etc - but at least I've done that before - and there are plenty of guides to that on ubuntuforums).

So, huge thanks to ubuntu_demon :D

---

### Post by ubuntu_demon on 2006-06-04
[QUOTE=sbooth]Phew.  Finally successfully installed Dapper - having reached the 'unbootable system' stage of upgrading from Breezy!

Huge thanks to ubuntu_demon who saved the day with [http://ubuntuforums.org/showthread.php?t=186672]("http://ubuntuforums.org/showthread.php?t=186672") (his HOWTO fix problems regarding broken dependencies) - which includes the HOWTO fix problems when your system is unbootable about half way through the post.

I did have the convenience of another PC to burn the live CD onto (without which I would have been completely stuck); I booted from the live CD and simply followed the instructions in the HOWTO... TO THE LETTER!  So, I figure it's worth saying that if it rescued my unbootable system it might rescue yours.

(I did have to faff around with nvidia driver installation etc - but at least I've done that before - and there are plenty of guides to that on ubuntuforums).

So, huge thanks to ubuntu_demon :D[/QUOTE]


Glad to be of help :)

Here's a thread regarding Xserver problems :
[http://ubuntuforums.org/showthread.php?t=187177](http://ubuntuforums.org/showthread.php?t=187177)

If you have any tips and/or fixes regarding upgrading or installing dapper please post them here :
[http://www.ubuntuforums.org/showthread.php?p=1086319](http://www.ubuntuforums.org/showthread.php?p=1086319)

---

### Post by wog on 2006-06-09
So *how* do you turn off screen savers from the newbie standpoint (for I am a newbie)?

I'd just figured on turning the screensaver timer to maximum and nudging the mouse every so often just to make certain... :)

---

### Post by cillian on 2006-06-09
Hi Wog,
If you're on the standard Ubuntu (Gnome/Brown) you should be able to disable the screensaver from the menu:
System>Preferences>Screensaver

And in the screensaver settings there should be a tab for display modes and in there you should be able to set the mode to "Disable Screen Saver"
I guess under the advanced tab you're going to want to check that power management is also disabled. Since you said you set the screensaver timer to maximum you may have some other set up (KDE/Kubuntu?) but it's bound to be pretty much the same thing.

By the sounds of things sitting there and nudging the mouse for a couple of hours is easier than recovering a half installed system! Yeiks! But surely not as much fun :) 
I'm going to take the plunge myself this weekend. Good luck!

---

### Post by tremlar on 2006-07-16
I didn't shut off screen saver but my problem is the mouse freezes up and keyboard won't work. This is frustrating because I have to shut down and start over everytime.

---

