---
title: "trying to get from 8.04 to 10.04 beta"
date: 2010-04-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by levlhed on 2010-04-01
I get as far as the beginning of installing the packages and receive the following error:

[B][I]Could not install the upgrades

Error during commit
'E:Couldn't configure pre-depend openoffice.org-core for openoffice.org-evolution, probably a dependency cycle.'
Restoring original system state[/I][/B]

Any idea what I can do to get past this?

---

### Post by conradin on 2010-04-02
unselected those updates for office, and try it again.

---

### Post by Sef on 2010-04-02
Moved to Lucid.

---

### Post by ranch hand on 2010-04-02
I have updated 3 8.04.4 installs to 10.4.  I have failed in doing so another 3 times.

I would recommend going with the old debian method using apt and manually editing your /etc/apt/sources file (change every instance of hardy to lucid).

Make real sure that your 8.04 system is up to date minutes before trying to upgrade.

Comment out any ppas that you are using and any other repo than the ubuntu ones including medibuntu.

I would also remove the flash plugins for FF.

Doing this may bring you on upgrade.  You will have to run dpkg --configure -a several times until there is no more improvement and then boot to recovery and use the dpkg option there.  These steps will do what the "cleanup" in UM is supposed to do.

The three I upgraded were all done that way.  One was a clean install with nothing added.  One was a clean install with all the stuff I normally add to it, including all the restricted stuff.  The third was a copy of my Hardy install from 9-08.  The last was done done with the medibuntu repo enabled.

My three failures were all clean installs that I tried to upgrade through UM.  They did not get "returned to former state".  They just got fried.

I am going to be trying it again after B2 is out.

When the time comes, I will not be doing this to my Hardy installation.  I have tried the conversion to ext4.  Not a real good deal compared to a clean install with files transfered.  I also do not want grub-legacy.

Playing with the upgrade is fun but, in this case particularly, a clean install is going to give you a better out come.  Ext4 will be full force, no left over remnants of grub-legacy and a faster boot time than you are going to get with an upgrade.

I would also

---

### Post by levlhed on 2010-04-02
Thank you for the advice, however it came too late for me :(
After posting this I'd gone back and (in a stroke of genious) used synaptic to just uninstall all of Open Office and proceeded with the upgrade.
 
The upgrade got to about 75% and came up with an error.  I can't actually recall what it was now, something about the network manager not being able to grab something?  Anyway, the computer was frozen and I was unable to select OK or whatever to try and get past it.  The only option to me was to reboot and now I get a whole screen of errors at boot and never get anywhere.  The errors are during the initial stages of booting and I don't ever get into the OS or anything.
 
I'm pretty sure my options are limited at this point.  I'll probably just go out and buy a new hard drive and do a clean install, then see if I can't still access the old drives to get what I need off of them.  I suppose it'd be a good time for me to do the thing where your home dir is on a different partition/etc; when I first installed Ubuntu I didn't have the benefit of experience (I guess it was some version 6 or 7?).  I typically do this with the My Documents folder in Winblows installs anyway.
 
 
P.S. I meant to post this in Installs/Upgrades forum!
 
Thanks again.

---

### Post by Kilz on 2010-04-02
> **levlhed said:**
> I suppose it'd be a good time for me to do the thing where your home dir is on a different partition/etc; when I first installed Ubuntu I didn't have the benefit of experience (I guess it was some version 6 or 7?).  I typically do this with the My Documents folder in Winblows installs anyway.


An alternate to that method is creating a couple partitions. A layout I found a few years ago seems to work for me in this age of terabyte drives. I have 2 partitions for installs about 45 gigs each and the rest is a media/files partition. In the files one I have a Documents, Video, Music, ect folders. I have the current version of Ubuntu and the beta/another distro/development installed on the 45 gig ones. I mount the files/media to /mnt/files and symlink in the folders in the media/files to the home directory.  This way my files are there no matter what I boot into. The home directory is also easily copied from one 45 to another. An advantage is that when something goes wrong in whatever Im testing, I still have the current stable version to fall back to.

---

### Post by ranch hand on 2010-04-02
A separate partition is good.  I came in on Hardy and it is still on one partition.  I have separated a copy of it into two partitions and that does work but it is a lot easier to just do it when you install.

You may be able to chroot in and continue trying to upgrade with apt and have a working install.

If there is anything on there you want backing it all up on another drive seems smart to me.  You should be able to get into it.

---

### Post by gordong11 on 2010-04-02
Trust me when I say, back-up your data and install via a LiveCD. When I did the upgrade, I had so many bugs and weird thing happen. I couldn't take it anymore so I tried a clean install. It was so worth it, what a difference!!! this is the best beta I ever tested from Ubuntu. Everything works but a few minor glitches here and there. I can even game, every software title I have installed works perfect. I have installed over 80 apps so far, all via software center, all work perfect.


Went back to Wine 1.1.31, wine-doors, and google earth are the only titles not through software center. Wine 1.1.31 I find is the best wine for gaming titles that I play. not 1 crash or error.

---

### Post by levlhed on 2010-04-02
I just booted to a live CD to see what there is to see, but my mouse and keyboard don't seem to work? They are both PS/2 and switcing to USB isn't really an option as I use a PS/2-based KVM.
 
Are there known issues with using PS/2 mouse/keyboard?

---

### Post by gordong11 on 2010-04-02
I am using both a ps2 mouse and keyboard. I had no issues with the live CD, can you try and re-start the live CD? or even the install process without them?

I'm sure it's a live CD issue.

---

### Post by cariboo on 2010-04-02
> **levlhed said:**
> I just booted to a live CD to see what there is to see, but my mouse and keyboard don't seem to work? They are both PS/2 and switcing to USB isn't really an option as I use a PS/2-based KVM.
 
Are there known issues with using PS/2 mouse/keyboard?

I have a 4-port D-Link KVM that is PS/2 only, I have zero problems running the Live CD. I have also found that Lucid finally detects my old KDS crt monitor correctly, whereas with older versions I always had to set horizontal and vertical refresh rates before being able to get the correct resolution.

---

