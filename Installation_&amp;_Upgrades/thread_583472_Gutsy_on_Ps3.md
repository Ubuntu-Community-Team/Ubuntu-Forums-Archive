---
title: "Gutsy on Ps3"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by Onay on 2007-10-20
I want to put Gutsy Gibbon on my Ps3, but I am a bit apprehensive. I just need a few things clarified.

- When I use the backup utility, will it save my demos, save game data, and online profile?
- Once installed, will wi-fi work out of the box for Ps3?
- Are there any unrecoverable dangers that could be done to the main Ps3 XMB (i.e. can it be bricked?)
- Will only 256 MB of RAM become an issue?

I also have other questions (about compiz, sound, blu-ray, etc), but I'd be very excited to have linux running on an 8 core system with the new "cell" kernel. Thanks guys.

---

### Post by Onay on 2007-10-20
Bump... Do I keep posting questions in the wrong sections, cause no one seems to want to help me :(

---

### Post by Onay on 2007-10-20
Bump...

---

### Post by IMOC on 2007-10-20
> **Onay said:**
> I want to put Gutsy Gibbon on my Ps3, but I am a bit apprehensive. I just need a few things clarified.

- When I use the backup utility, will it save my demos, save game data, and online profile?
- Once installed, will wi-fi work out of the box for Ps3?
- Are there any unrecoverable dangers that could be done to the main Ps3 XMB (i.e. can it be bricked?)
- Will only 256 MB of RAM become an issue?

I also have other questions (about compiz, sound, blu-ray, etc), but I'd be very excited to have linux running on an 8 core system with the new "cell" kernel. Thanks guys.

You bumped this!  How quick do you expect a response?

Gutsy Gibbon will not work on the PS3, or it didn't work for me anyway.  See [http://ubuntuforums.org/showthread.php?t=582848]("http://ubuntuforums.org/showthread.php?t=582848").
I had Feisty Fox working just fine before that though.

For some of your other questions:
The backup utility saves all that you want.
WiFi does not work, I could not get it to work.
The main PS3 XMB cannot be bricked.
256MB of RAM was fine for me - it depends what you intend to do.
Also the disc drive didn't work for me and I don't think the full 8 core system is used.

---

### Post by Onay on 2007-10-20
Did you try to upgrade to Gutsy from Feisty, or did you do a clean Gutsy install? Word on the street is that upgrading doesn't work at all, but I would expect that a clean install would.

What Ps3 SKU did you try? Like 20, 40, 60, or 80gb model?

---

### Post by IMOC on 2007-10-20
> **Onay said:**
> Did you try to upgrade to Gutsy from Feisty, or did you do a clean Gutsy install? Word on the street is that upgrading doesn't work at all, but I would expect that a clean install would.

What Ps3 SKU did you try? Like 20, 40, 60, or 80gb model?

If you know of a link to a Gusty disc for the PS3 then I will give it a try.  I have not been able to find one, though I am not sure where to look.

I have the 60GB model, 10GB used for XMB.

---

### Post by thecheatah on 2007-10-20
[http://www.ubuntu.com/getubuntu/releasenotes/710](http://www.ubuntu.com/getubuntu/releasenotes/710)

PlayStation 3 changes

    *

      The kernel flavor for PlayStation 3 systems has changed from powerpc64-smp to cell. Users upgrading their PlayStation 3 from Ubuntu 7.04 to 7.10 should run this before or after the upgrade:

      $ sudo apt-get remove linux-image-powerpc64-smp linux-powerpc64-smp linux-restricted-modules-powerpc64-smp
      $ sudo apt-get install linux-cell

    *

      In addition, the block device names have changed from the normal /dev/sdX naming to /dev/ps3dX (e.g. /dev/sda1 will now be known as /dev/ps3da1). Standard installs should not be affected by this, since they use UUID naming. However, if you changed /etc/fstab to refer to hardcoded device names, you will need to adjust these for the new kernel.

I havnt tried this, but I remembered reading that in the notes.

---

### Post by Onay on 2007-10-20
> **IMOC said:**
> If you know of a link to a Gusty disc for the PS3 then I will give it a try.  I have not been able to find one, though I am not sure where to look.

I have the 60GB model, 10GB used for XMB.

[http://cdimage.ubuntu.com/ports/releases/gutsy/release/](http://cdimage.ubuntu.com/ports/releases/gutsy/release/)

That's the final release, you need to download the PowerPC/Ps3 image. By the way I'm also using a 60gb model, so this would apply to me. If you want to try it out, that would be great, since I kinda have a bunch of demos and videos stored on my Ps3 that I need backup, so hopefully that doesn't take too long.

EDIT: I'm going to look around and see if the alternate install CD would be better, since I hear it takes a long time to boot up with the live CD and there used to be bugs in Feisty with it.

---

### Post by IMOC on 2007-10-20
> **Onay said:**
> [http://cdimage.ubuntu.com/ports/releases/gutsy/release/](http://cdimage.ubuntu.com/ports/releases/gutsy/release/)

That's the final release, you need to download the PowerPC/Ps3 image. By the way I'm also using a 60gb model, so this would apply to me. If you want to try it out, that would be great, since I kinda have a bunch of demos and videos stored on my Ps3 that I need backup, so hopefully that doesn't take too long.

EDIT: I'm going to look around and see if the alternate install CD would be better, since I hear it takes a long time to boot up with the live CD and there used to be bugs in Feisty with it.

Thanks for the link, I shall download it whilst I am watching the rugby.

---

### Post by oddroot on 2007-10-20
> **Onay said:**
> I want to put Gutsy Gibbon on my Ps3, but I am a bit apprehensive. I just need a few things clarified.

- When I use the backup utility, will it save my demos, save game data, and online profile?
- Once installed, will wi-fi work out of the box for Ps3?
- Are there any unrecoverable dangers that could be done to the main Ps3 XMB (i.e. can it be bricked?)
- Will only 256 MB of RAM become an issue?

I also have other questions (about compiz, sound, blu-ray, etc), but I'd be very excited to have linux running on an 8 core system with the new "cell" kernel. Thanks guys.

I did this last weekend or maybe the one before that. Backing up your PS3 to a usb disk will save all the demos, wallpaper, savegame data and stuff... (installed 7.04)

As far as I know there is no way to brick the PS3... I have to imagine that the XMB resides in flash or somewhere other than the harddrive, cause you can take the drive out, put a new one in and XMB still exists.

The 256M ram will be an issue, i don't really care what anyone says. X, even stripped down is a pig and has been for many years.. Adding gnome/kde on top... At either rate though, it does run pretty well, or atleast 7.04 did, I haven't gotten gutsy's X to run yet on the ps3.

I did the upgrade to gutsy today... while the system boots, X does not.. you can escape over to the command line by hitting alt+ctrl+f1 and log in there... of course if you aren't familiar with linux it isn't going to help you much :)

---

### Post by Onay on 2007-10-20
> **oddroot said:**
> I did this last weekend or maybe the one before that. Backing up your PS3 to a usb disk will save all the demos, wallpaper, savegame data and stuff... 

As far as I know there is no way to brick the PS3... I have to imagine that the XMB resides in flash or somewhere other than the harddrive, cause you can take the drive out, put a new one in and XMB still exists.

The 256M ram will be an issue, i don't really care what anyone says. X, even stripped down is a pig and has been for many years.. Adding gnome/kde on top... At either rate though, it does run pretty well, or atleast 7.04 did, I haven't gotten gutsy's X to run yet on the ps3.

Will the new kernel take advantage of the cell processor? It is aptly named "cell" now, but I doubt it will be able to harness it's power. I've read that it still uses only the PowerPC architecture, and that would do us a disservice. If Gutsy utilizes the cell processor, then technically it should be performing at Folding@Home speed, which if I'm not mistaken is much faster than most PC's.

I just don't want to go through the trouble of installing this on my PS3 just to find out that I can't even run any decent programs and/or use any OpenGL window compositing (like compiz).

---

### Post by Onay on 2007-10-20
From what I can see, even using the Xfce window manager would not make the ps3 a "usable" desktop for any kind of productivity or fun purposes. If this is simply a showcase that I cannot fully use, then I might hold off until we can take full advantage of the Ps3 architecture as well as added support, since upgrading old distros seem to ruin the install completely.

---

### Post by sanosuke001 on 2007-10-26
Honestly, I hope they don't try to leverage the SPE's for the OS. I installed Ubuntu on my PS3 for the explicit purpose of programming with the SPEs myself. If the OS locked a few up for its own purpose, then most applications written using the SPEs would be affected. Since the majority of people doing development on the PS3 are doing it for the sole purpose of parallelism I don't see it happening for the reasons above.


And I don't think the problems with usability are because they're only using the PPC core, I think it's more of a RAM issue.

---

### Post by marlowe650 on 2007-10-27
Xubuntu on the ps3 is certainly no replacement for a solid desktop pc, but i've turned it into a great media center.  And as a general desktop experience, it's far from "unusable," -- At this moment, I'm on my ps3 running firefox to reply to this message between rounds of Marvel vs Capcom on xmame, whilst waiting for a torrent to download.  The official gutsy build for the ps3 installs great, and besides having to edit a couple conf files to get the video settings I needed, I'm absolutely amazed at how much of it works essentially out of the box.  Totally worth it, imo, and if you don't like it, just format and get rid of it.  Best of luck.

---

