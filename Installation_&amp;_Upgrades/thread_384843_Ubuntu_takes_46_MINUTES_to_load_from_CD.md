---
title: "Ubuntu takes **46 MINUTES** to load from CD"
date: 2007-03-14
forum: Installation &amp; Upgrades
---

### Post by pdxuser on 2007-03-14
Version: Ubuntu 6.10
Hardware: Dell Dimension L600cx, purchased in 2000, with 256MB RAM, clean formatted HDD, used to run Windows XP.

I downloaded the Ubuntu Desktop ISO and burned it to a CD.  The CD works great on my current computer.  It boots off it fine, I can run Firefox, Writer, whatever.  But the computer I want to install to is the older one with the specs I mentioned above.  Here's what happens when I boot from the CD on that machine:

Boot menu loads immediately
I select the start/install option, and I immediately see "Loading Linux kernel"
9s later, I see the Ubuntu progress bar screen.
4m:06s later (4:15 total), after some wild flickering, static, and jumping around of the progress bar screen, I see an "x".
10s later (4:25), I see the brown desktop without wallpaper.
2m:24s later (6:49), I see a gray box on the screen
13s later (7:02), I see the Ubuntu bar with items loading
12s later (7:14), the gray box turns out to be an error message: "There was an error starting the GNOME Settings Daemon" [...] "The last error message was: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."  I'm betting the reply timeout expired, given how slowly things are going.
4m:32s later (11:46), the Ubuntu loading bar disappears.
40s later (12:26), I see the two toolbars, only they're just empty gray bars.
14m:22s later (26:48), both empty gray bars have disappeared.
5m:02s later (31:50), the File Browser begins to load.
3m:08s later (34:58), the default wallpaper appears.
11m:48s later (43:46), the File Browser finishes loading.
1m:22s later(45:08), the "Example" and "Install" icons appear on the desktop.
1m:04s later (46:12), the CD drive stops accessing the CD.

After that 46-minute load time, I go to close the File Browser.  11 minutes and 54 seconds later, it's closed and the CD drive has stopped accessing the CD.

Clearly I don't want to bother playing around with this thing, so I go straight for the install button.
3m:10s later, the "Opening Install" dialog box appears.
39s later (3:49), the "Opening Install" dialog box disappears.
56 minutes later (60m), the CD drive stops accessing the CD, the cursor has disappeared, and I'm kicking myself.
10 minutes later (66m), the CD drive is accessing the CD again!  Cool!
10 minutes later (76m), it stopped again.
70 minutes later (146m), it's still stopped.  No cursor, and nothing has happened since the "Opening Install" dialog disappeared.

First, does anyone know what the problem is?  I'm thinking maybe there's a problem with my memory.  When I ran Windows, there was a day when suddenly it was always a lot slower, but it wasn't anywhere near this absurd.  I'm thinking my virtual memory (swap file) may have just taken over for my (theoretically) faulty RAM.  But now, with my cleanly formatted hard drive, there's no swap to fall back on.  This is just a theory.  Let me know if it sounds valid or if you have a better idea.

Next, I'm wondering if anyone thinks Xubuntu would work any better?

Remember, the CD works just fine on my current computer, so I don't think it's a bad ISO or a bad burn.

Thanks!

---

### Post by rsambuca on 2007-03-14
256 MB should be enough, albeit very tight for the live CD.  You would be much better off installing xubuntu from the alternate CD.  The alternate CD is text based, but still very straight forward.  The big difference, is that it doesn't have to load the OS into RAM, so it is lighter on system resources, which it looks like you need.

Good luck!

---

### Post by pdxuser on 2007-03-15
Thanks!  I didn't know what the alternate CD was.  Do you think the Ubuntu alternate CD should also be fine, then, since Ubuntu should be OK once it's running off the hard drive?  Or is 256k still going to be too slow?

---

### Post by MihaiM on 2007-03-15
Try use the alternate cd with the text installation or an older version of Ubuntu prior to the introduction of X installation.

I had real problems with laptops with 256MB RAM and the new Ubuntu installer. I had to install an older version and update after.

---

### Post by Aliarse on 2007-03-15
Whats the speed of your CD drive? On my pc when trying out the live cd, things were slow, but not 48 minutes slow. 5/10 mins max on a 52x read cd drive..

(edit)

if you still cant get it working after trying a load of options, theres always the [windows based installer]("http://www.ubuntuforums.org/showthread.php?t=338279&page=137"), which im currently using, and would reccomend to any new linux user/ex to be windows user.

---

### Post by pdxuser on 2007-03-15
I don't know the speed -- it doesn't say on the front or any visible part inside the case.  I also can't check in Windows Device Manager because the hard drive is freshly formatted, meaning the Windows installer isn't of much use, either.  The drive is CD-ROM only, so it's certainly behind the times, but I didn't have any trouble with it before, though I rarely used it and certainly never ran major applications (or games) live off of it.

---

### Post by pdxuser on 2007-03-15
Again, I wonder if anyone thinks the Ubuntu alternate CD, rather than the Xubuntu alternate CD, might be a good choice for me, or whether Ubuntu would probably run too slowly for me even off the hard drive?

---

### Post by rsambuca on 2007-03-15
Look - they will both run on your machine, it is just that the gnome desktop will take more system resources, so it will run slower than xubuntu for you.  Try one, if you don't like it, try the other.

---

### Post by pdxuser on 2007-03-15
If I installed Xubuntu, could I then just install the GNOME packages and have Ubuntu?  Would there then be any difference?  Alternately, if I had Ubuntu and it went too slowly, could I just remove the GNOME packages?

---

### Post by rsambuca on 2007-03-15
Yes, you can install xubuntu and then load the ubuntu desktop.  It will be a little different than the regular ubuntu because you will have some of the Xfce Packages from Xubuntu.  You can also delete the packages you don't want later.

You should probably check out this [[COLOR="Red"]website[/COLOR]]("http://www.psychocats.net/ubuntu/purexfce") as it answers a lot of your questions.

You realize by now you could have downloaded ubuntu, kubuntu, xubuntu, and edubuntu, installed them, tried them all out, and picked the one that works best for you!;)   Just teasing, but sometimes you just have to make a decision!

---

### Post by PryGuy on 2007-03-17
> **pdxuser said:**
> Version: Ubuntu 6.10
Hardware: Dell Dimension L600cx, purchased in 2000, with 256MB RAM, clean formatted HDD, used to run Windows XP. I have the same problem here with my Acer TravelMate 292ELC (Celeron 1.3GHz, i852 chipset, 30Gb HDD, 256Mb RAM). The thing is that I think that I used to install Edgy from *the same CD* a few months ago ang everything was fine. I didn't make any hardware changes or something...

Thanks to all the people suggesting to use the alternate install CDs, but the LiveCD install is a default way to install Ubuntu and it should work flawlessly!

Dear Ubuntu developers! I love Ubuntu and all and think it's the best distribution so far, BUT it's a damn bug, and it has to be fixed in Feisty! You've heared me! :mad:

EDIT: Yet, when I use the text mode installer everything installs fine and it detects my wireless card but when I boot into my Edgy the wireless PCIMCIA adapter disappears! WTF?!

---

### Post by new-bee on 2007-03-24
> **pdxuser said:**
> Version: Ubuntu 6.10
Hardware: Dell Dimension L600cx, purchased in 2000, with 256MB RAM, clean formatted HDD, used to run Windows XP.

I am trying to load Ubuntu 6.10 onto a Compaq Deskpro PIII with 20GB HDD and 256MB of RAM and am having _exactly_ the same issue as you.  However, I have one slight variation, in that if I do not move the mouse every five minutes, the screen goes blank, but the CD-ROM keeps working away!

Have you had any luck getting Ubuntu to load?  Cheers.

---

### Post by mramsey on 2007-03-24
Try This[http://ubuntuforums.org/showthread.php?t=392241]("http://ubuntuforums.org/showthread.php?t=392241") it worked for me!

---

### Post by new-bee on 2007-03-25
> **mramsey said:**
> Try This[http://ubuntuforums.org/showthread.php?t=392241]("http://ubuntuforums.org/showthread.php?t=392241") it worked for me!

Thanks mramsey.  I tried putting the command at the beginning of the string as well as at the end, but I still received the "settings daemon" error message and lots of cd-rom activity, but no installation.

I've now downloaded version 6.06.1 LTS and that has at least partitioned the HDD and loaded some files, but it has been sitting on 40% of "Configuring apt - Scanning the mirror ..." for some time now.  I'm not sure what to do now!  Cheers.

---

### Post by new-bee on 2007-03-25
After sitting on 40% of "Configuring apt - Scanning the mirror ..." for about 40 minutes, things started to progress.  About an hour or so later version 6.06.1 was installed.

I clicked on the get updates and now have 112 updates to download and install.  I'm definitely going to search for some disk imaging software, as I am not going through this again!

---

### Post by Joh_ on 2007-03-25
I absolutely hate the live CD.. It took me 45 mins just to get to the point of the installation where it starts copying files. And of course, that's also where the CD stopped and nothing happened... They also seem to have made the graphical installation even worse in Feisty Fawn. It took the installation a whooping 10 minutes just to find out I didn't have any other operative systems to copy users and settings from as the hard drive was clean.

From now on, alternative CD is the way I'm going until the installation speeds up. It's even faster fully installing windows or OSX than simply getting the damn thing to start copying files.

---

