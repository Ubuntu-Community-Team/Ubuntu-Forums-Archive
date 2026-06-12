---
title: "kubuntu karmic rc unusable"
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by stuart.reinke on 2009-10-24
I have my hard drive partitioned like this

hd0,0 empty
hd0,5 kubuntu jaunty install
hd0,7 swap

I decided to install the kubuntu rc in hd0,0

install went off without a hitch. when I rebooted Grub gave no option for my jaunty install and when Karmic booted it was totally unusable.

I get the wallpaper, and the desktop folderview (empty, no home folder inside). The task bar at the bottom is there but nothing showed up on it.

If I click where the K menu button should be the window menu opens up, but it's filled with criss-cross lines and gobledy gook. No text 

I'm going to use a live cd to reinstall grub to get back my jaunty installation.

how do I go about fixing karmic? I don't even know what kind of bug to file.

I assume this is a graphics problem. I have a ATi Radeon card in an IBM Thinkpad laptop.

Any advice is appreciated.

---

### Post by stuart.reinke on 2009-10-24
bump

---

### Post by PryGuy on 2009-10-25
It's very strange. I had no problems with my Ubuntu, using it since Alpha 5 on my main machine. Installed KDE 4.3 from repo. No problems also...

---

### Post by Asraniel on 2009-10-25
no problems either, best release ever. your cd isn't corrupt by any chance?

---

### Post by stuart.reinke on 2009-10-25
Just the opposite for me. I tried out Ubuntu a couple of times during alpha with no problems. Tried Kubuntu during Beta and RC with the afore mentioned troubles.

I don't think it's the CD. I've tried installing a command line system and kubuntu-desktop from the repos and a full install from both alternate and live CDs. 

The problem even exists while trying to run a live cd. 

I'm pretty sure it's a graphics driver issue. I may install another command line system, change drivers and see if that helps.

---

### Post by edin9 on 2009-10-25
> **stuart.reinke said:**
> Just the opposite for me. I tried out Ubuntu a couple of times during alpha with no problems. Tried Kubuntu during Beta and RC with the afore mentioned troubles.

I don't think it's the CD. I've tried installing a command line system and kubuntu-desktop from the repos and a full install from both alternate and live CDs. 

The problem even exists while trying to run a live cd. 

I'm pretty sure it's a graphics driver issue. I may install another command line system, change drivers and see if that helps.

Kubuntu RC has been a disaster for me too.

---

### Post by Njall on 2009-10-25
Initially I had a problem with Kubuntu Karmic RC; however, the problem was completely related to a KPackageKit bug.  Since recovering from that I've been quite pleased.  Getting past the KPackageKit update issue did require a working knowledge of apt-get; however, it KPackageKit has worked flawlessly for me since the first week after the RC was initially released.

I **ALWAYS** run the "Check CD" function from the live CD before trying to install from it.  Don't think when you can know!  It **HAS SAVED** my bacon at least twice when a CD burn was faulty.

I cannot speak directly to your Grub problem except to say that Karmic is using Grub 2.0 (1.97 beta?) now.  I had a problem with my dual-boot system which was completely my fault.  I rearranged the boot order so that my Windows HD was not the first drive.  Oops.  Once finished banging my head against the wall for that dumb mistake, Grub has worked fine.

Don't beta-test without accepting digital-danger as a close companion.

Regards, 
Nelson

---

### Post by stuart.reinke on 2009-10-25
> **stuart.reinke said:**
> I'm pretty sure it's a graphics driver issue. I may install another command line system, change drivers and see if that helps.

Thought my problem was proprietary drivers that didn't support my older card. Nope, installer uses open source drivers.

Only one thing left to try. Install Jaunty and upgrade. If that doesn't work I guess I'll have to hope and pray the final release works.

---

### Post by vishalrao on 2009-10-25
there was another thread somewhere down this section mentioning problems with the RC then it mentioned that 32 bit worked.

amd64 kubuntu and ubuntu RC fail to install for me too on my desktop, tablet and even virtualbox!

too bad there is just one week between RC and final release i have no time during weekdays to send feedback (missed this weekend too).

---

### Post by mikedep333 on 2009-10-25
Perhaps you could try to use the standard "vesa" driver for X11. That is a safe fallback.

---

### Post by stuart.reinke on 2009-10-26
I hadn't thought of giving the generic driver a try, good idea.

Think I'll try ubuntu first. maybe the problem is with kde. I'll see if gnome works any better.

Might wait for the final release and see if it works then.

---

### Post by solidus0079 on 2009-10-27
> **stuart.reinke said:**
> I have my hard drive partitioned like this

hd0,0 empty
hd0,5 kubuntu jaunty install
hd0,7 swap

I decided to install the kubuntu rc in hd0,0

install went off without a hitch. when I rebooted Grub gave no option for my jaunty install and when Karmic booted it was totally unusable.

I get the wallpaper, and the desktop folderview (empty, no home folder inside). The task bar at the bottom is there but nothing showed up on it.

If I click where the K menu button should be the window menu opens up, but it's filled with criss-cross lines and gobledy gook. No text 

I'm going to use a live cd to reinstall grub to get back my jaunty installation.

how do I go about fixing karmic? I don't even know what kind of bug to file.

I assume this is a graphics problem. I have a ATi Radeon card in an IBM Thinkpad laptop.

Any advice is appreciated.Same is happening to me on a testbed desktop running a Radeon VE.  Ubuntu with Gnome works just fine.  So dissapointing, I really like KDE but every time I go to give a shot at actually using it, it's all glitched out and I end up using Gnome.

Oh and it's *not* a corrupt CD.  I've burned multiple CD's from multiple burners (RC, various dated betas, etc) and even used Unetbootin to make bootable USB sticks.  Always end up with garbaged up desktop with lines, grids, etc on top of a pristine Kubuntu wallpaper.  It's like the window manager itself is crapped up and the rest "works".  (but without a window manager you can't do anything)

Then I tried to make a Kubuntu Netbook remix install USB, I booted to a desktop with a different type of corruption joined with an immediate system freeze.  Oh well, back to Gnome again.

---

### Post by stuart.reinke on 2009-10-27
Solidus, looks like we're in the same boat. I get some minor glitches in gnome but that is usually cleared up by setting desktop effects to none.

---

