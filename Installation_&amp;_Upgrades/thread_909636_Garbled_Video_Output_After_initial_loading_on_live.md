---
title: "Garbled Video Output After initial loading on live CD and completed install."
date: 2008-09-03
forum: Installation &amp; Upgrades
---

### Post by nutbastard on 2008-09-03
System:
Dell Dimension 8300
3.x Ghz
1.5 GB RAM
GeForce FX 5200

Hardy Heron 8.04

Problem:

Garbled Video output during:
    Live CD Boot (After "Ubuntu" status bar loading screen")
    Installation (After "Ubuntu" status bar loading screen")
    Alt CD Installation (After install, on boot, after "Ubuntu" status bar loading screen")

See the pattern here? As soon as whatever is going on during the Loading screen is done (and the video mode switches, im guessing) it all goes to... heck.

I've tried two different monitors to no avail.

Safe Graphics mode on both the regular and alt CDs result in "Video Input Not Supported" (or similar wording) and a Black screen. Regular mode results in strange, multi-colored garbage snow.

I know it's working properly behind all the garbage it's outputting, because turning on the Listening Assistance Option (or whatever it's called) resulted in a voice that would bark out the menu options i was highlighted on, and although it was completely indecipherable, i know it's not frozen, just garbled video output.

I got it to install all the way using the Alt CD, but upon booting it's all colored garbage video output.

Any help would be greatly appreciated. I know enough about working the CLI to perform whatever instructions you may give, (Although GETTING to the CLI from the state im in is a mystery at this point) so have at it.

---

### Post by Pumalite on 2008-09-03
Have you tried Recovery Mode; command: 'xfix'?

---

### Post by nutbastard on 2008-09-04
I have not, as i haven't been able to finalize an installation, it didn't seem worth the effort - but I shall try that later today.

---

### Post by nutbastard on 2008-09-05
OK, here's the solution (as of now)

List of installs that had this problem:
Ubuntu 8.04
Ubuntu Alt 8.04
Dell Ubuntu 7.04

**Kubuntu** installed flawlessly. Since regular old Ubuntu didn't, I'm going to go ahead and assume that the fault lies with Gnome, since that's really the only difference.

This is on my buddys computer so i dont get to have at it daily, and it is not yet hooked up to an internet connection. Once it is i will attempt to install the gnome desktop and will report here as to the results.

Im glad Kubuntu installed, if it hadn't I was going to try Linux Mint (which i still want to try out).

Unfortunately the lesson here is, if installation does not succeed, install something slightly different :\

---

### Post by Pumalite on 2008-09-05
I doubt it. It was probably a bad burn.

---

### Post by nutbastard on 2008-09-08
It looks like i was too quick to praise KDE and bash Gnome: After a single reboot of a completely successful Kubuntu install, it boots to garbled video output.

Can't be a bad burn - I've now got this with Ubuntu, Ubuntu Alt, Ubuntu Dell, Kubuntu, and now Linux Mint. 5 bad burns is just too much for me to inhale, considering some were done from different machines, and at very low speeds with very high quality CDs.

Something is seriously wrong.

xfix did nothing to correct the problem.

in fact, nothing in recovery mode fixed anything.

I'm stumped.

---

### Post by nutbastard on 2008-09-08
Another update - The Kubuntu CD no longer works. It gives the same garbage as the others. I'd accuse the hardware, EXCEPT for the fact that the installer menus and such work fine, and XP is up and running without any similar symptoms.

The intermittancy of the problem worries me, though.

Also, the Linux Mint CD i tried is the one i used to install on my inspiron laptop, from which I am writing this.

Anyone have any idea how i would probe this problem???

---

### Post by Pumalite on 2008-09-08
Clean the lens in your burner. Check CD integrity before install. Do md5sum on the iso. Burn at 4x or less. Do not use CD-RW.

---

### Post by nutbastard on 2008-09-10
Come on man, I've stated that a complete, working install of kubuntu was up and running with no problems, but then reverted to the same issue i've been having after rebooting. I don't see how it's possible that this is a hardware issue, or a problem with the CD.

---

### Post by nutbastard on 2008-09-10
...however i *will* clean the lens and reinstall and see what happens.

---

### Post by sor on 2008-10-09
> **Pumalite said:**
> Clean the lens in your burner. Check CD integrity before install. Do md5sum on the iso. Burn at 4x or less. Do not use CD-RW.Don't mean to criticize, but that's some pretty lame advice. Not only is it a shotgun approach but you won't acknowledge that there might be an issue with the software itself.

Seems like the issue is with an nvidia driver. I have seen the same issue on my system in Suse until I downloaded and installed the driver from the nvidia site. Then I pop in this ubuntu CD today and the install does the same thing. I'll let you know if I figure out a workaround, for any who might see this thread in the future.

---

### Post by sor on 2008-10-09
Ok, so for me, the symptoms were as follows. I had a dual screen setup, screen 0 with VGA and screen 1 with DVI. The garbled video only came up after the ubuntu progress bar completed and loaded the GNOME environment, and it came up on screen 0 while screen 1 was black. Unplugging screen 1 before loading the CD fixed the issue, then I loaded the OS, got the nvidia driver on, and then added the second screen.

So here are my suggestions, based on both the Suse issue I had and this one.

1. if you're using dual screen, use 1 screen at first as I did.
2. use vga rather than dvi if possible, until the third party driver is installed.
3. all else fails, do a text install with the alternate CD ubuntu provides, then in text mode install and set up the nvidia driver:

sudo apt-get install nvidia-glx-new
sudo nvidia-xconfig

---

