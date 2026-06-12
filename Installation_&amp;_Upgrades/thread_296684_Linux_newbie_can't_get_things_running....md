---
title: "Linux newbie can't get things running..."
date: 2006-11-09
forum: Installation &amp; Upgrades
---

### Post by thelostsoul on 2006-11-09
Okay, guess I should start with some system specs, just remember that my system is an el cheapo compcrap (compaq), so I don't know every piece of hardware on it, but I probably know more than I'll remember to include here:
Processor: Intel Pentium 4 (single) 2.53ghz
Graphics Card: NVidia Geforce FX 5500 (PCI)
RAM: 512mb
(secondary graphics card: Geforece4 MX420 [AGP][currently removed])

Now my story:  (note: I am referring ONLY to Live boots in all my stories, I have not yet prepared my HDD for an install as I am just testing distros to make a decision)
I started with Freespire and both gfx cards inserted.  However, the second one is terrible and was causing issues when I tried to boot into Windows (plus it was only increasing my systems watt usage to be that much more than the power supply can handle).  Well, Freespire ran only when I booted using the xdriver=vesa option.  I then decided I didn't like Freespire, so I downloaded and burned ubunto to a disc.  Ubunto would load up, but would only use the second (agp) graphics card after it got passed the boot screen.  So in my first attempt to get things running in my PCI card, I removed the AGP one.  Ubunto now will not boot.  It either hangs at about 1/4 of the way back on the first progress bar, or gives the attached message after the progress bars.  I have tried including options like "agp=off", "agplock=0", "xdriver=vesa" but to no avail.  I am at a total loss now and have no idea what to do.  This is pretty much my first attempt to seriously use linux, but I need a little help here...

Thanks!

[IMG]http://img.photobucket.com/albums/v247/sk8rdc/DSC02664.jpg[/IMG]

---

### Post by twsnnva on 2006-11-10
Try adding "noapic" to your boot options.

---

### Post by Neobuntu on 2006-11-10
I don't know but offer the following observations.

It looks like you have good NVidia cards but one is a "leagacy" card and would use those "restricted modules." I would just leave in the 5500.

A shot at defining the problem might be the graphics card (5500) memory amount is not recognised or configured correctly.

Paste in a ```
sudo dpkg-reconfigure xserver-xorg
```
and hold down the [Enter] key for quickly selecting all the defaults. Then reboot and if it works, see the forums for easy set up of the NVidia DRI (Direct 3D) module.

What Kernel are you using? Try the Generic one if you are using Edgy. If Dapper, then stay there; for now.

Yes those P4's run hot. Better an "M" (or better mobile P4) or AMD 64 bit.

But hey, I think your system rocks!

---

### Post by confused57 on 2006-11-10
I don't know if these threads will help or not:

[http://www.ubuntuforums.org/showthread.php?t=164935&highlight=graphics](http://www.ubuntuforums.org/showthread.php?t=164935&highlight=graphics)
[http://www.ubuntuforums.org/showthread.php?t=33142&highlight=5500](http://www.ubuntuforums.org/showthread.php?t=33142&highlight=5500)

---

### Post by thelostsoul on 2006-11-10
Thanks for all your help!

I'm not at my computer right now, so I can't try anything yet, but @neobuntu, where do I put that line you gave me?
Is it when I boot with the CD and press F6 before or after what is already in that box, or before the dashes?

Also, I'm using the 6.10, "Newest Release" one.  I believe it's the 2.6 kernel.

Thanks!

---

### Post by confused57 on 2006-11-10
> **thelostsoul said:**
> Thanks for all your help!

I'm not at my computer right now, so I can't try anything yet, but @neobuntu, where do I put that line you gave me?
Is it when I boot with the CD and press F6 before or after what is already in that box, or before the dashes?

Also, I'm using the 6.10, "Newest Release" one.  I believe it's the 2.6 kernel.

Thanks!
Here's a guide for reconfiguring the xserver:
[http://www.ubuntuforums.org/showthread.php?t=187177](http://www.ubuntuforums.org/showthread.php?t=187177)

or

[http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)

---

### Post by thelostsoul on 2006-11-10
Hmm...I think you've misunderstood me here.  I am unable to boot into the CD.  Linux is NOT installed.  I can't enter any of these commands, and when I press esc on boot to get to the boot: prompt, it tells me "Could not find kernal image: sudo" or whatever I type in there.

---

### Post by Neobuntu on 2006-11-14
Yes perhaps a xserver instructional page would be better than my (once miss spelled) command above but you enter it into the console; so that means you may need to be up on stopping and starting X.

As above; to quickly setup X (and then hold down the [ENTER] key to select all defaults):

```
sudo dpkg-reconfigure xserver-xorg
```

So you'll need to restart X; you could just reboot but here's what I then do:

Kubuntu
```
sudo /etc/init.d/kdm restart
```
OR
Ubuntu
```
sudo /etc/init.d/gdm restart
```

Tripple click these for easy highlighting and quick "cut and paste" to a console terminal.

It's all about speed, baby!

This is what I would try, as a first step; after installing a new video card.

---

### Post by thelostsoul on 2006-11-25
Sorry for not posting my status, but here's what I did:

Popped in my GeForce4 MX, booted into the live CD and installed Ubuntu using that card.  Then I modified my xorg.conf file manually for my Greaphics card and its PCI slot.

When I got in I used ctrl alt f1 and shutdown gdm, then installed the official nvidia drivers from nvidia.com.

The nvidia-glx installed another kernel on me for some reason.

Thanks for everyone's help though...

---

