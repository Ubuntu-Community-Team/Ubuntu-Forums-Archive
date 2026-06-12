---
title: "My impressions of Ubuntu 10.04"
date: 2010-03-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by punkrockguy318 on 2010-03-07
Hello ubuntuforums!:) I'm a long-time Ubuntu user (since warty) and have been enjoying Ubuntu on my desktop and laptop ever since then.  Ubuntu 9.10 has basically suited all my needs, although I have had a couple serious annoyances with it.  But anyway, I upgraded my 9.10 partition to 10.04 alpha3 today so I could test it out and make sure my application that I develop, fceuX, will work properly on it when Ubuntu 10.04 is released.

* The upgrade process went smoothly, as usual.  I had added a lot of ppas and unsupported repos on my 9.10 install, but the upgrade process still went smoothly.  There were problems with this a few releases back but it's good to see that the upgrade routine is fairly versatile.

* On my first boot of Ubuntu 10.04; i literally gasped when I saw my gdm login screen.  I couldn't believe that the boot time was so quick.  On just a guestimate, I'd say it's almost half the time of the bootup speed of 9.10 (i have no benchmarks to support this, but I am very impressed).  The new boot splash screens are beautiful as well.

* It's nice to see that my terminals default to using framebuffer now.  On my 32 inch TV, my VTs had huge fonts due to the lack of frame buffer.  I now have nice high res fonts and a nice VT to work with.

* Gnome and GTK dialogs seem to be significantly faster.  I noticed this on the live CD as well (once things had been loaded into RAM).  My application fceuX opens without any delay whatsoever on my machine now.

* My <b>FAVORITE</b> improvement of Ubuntu 10.04 is the sound system.  There were a ton of issues in 9.10 with the sound system.. Bugs in many different codebases (some sound drivers, pulseaudio, SDL, ALSA).. My application fceuX uses SDL and I have floods of bug reports coming in about sound.  There are some workarounds, but nothing too clean.  I compiled fceuX in 10.04 and sound worked absolutely perfectly.  A huge sigh of relief from me!  Other SDL applications (openarena, skulltag, snes9x) has issues with sound as well, but work fine in 10.04.  Kudos to everyone that's helped fixed sound in Ubuntu.

* I'm a big fan of the split plane in Nautilus; I had been hoping for that feature for a while.

* The open source radeon driver suprised me.  I wasn't expecting to be able to run any 3d games at all, but there is decent 3d support.  I can run warsow, skulltag, openarena, and a copule other 3d games with perfectly fine framerates on my radeon 4750 without fglrx.  I will however upgrade to fglrx whenever its available for Xorg 1.7

* MPlayer is a huge improvement.  I'm not sure about anyone else, but gmplayer was completely broken for me in 9.10.  Mplayer works better than totem or vlc IMHO (as a matter of preference)

* The work done to integrate social networking is interesting.  It's clean and unintrusive.  I use facebook, but not very often.  It's nice to have an application/applet to check up on that sort of thing.  However, I don't see myself getting extensive use out of this.

* I haven't noticed ANY regressions so far (other than ati dropping the ball on being late on drivers).  It's a very solid improvement over 9.10, especially with the sound system.  

NOTE: this is still alpha obviously so I don't recommend others to upgrade now.  i'm a programmer and don't mind patching/working around if things break.  i also have other partitions

Can't wait for 10.04 for be released!  Looks like the best Ubuntu release in a while!

-Luke

---

### Post by kaldor on 2010-03-08
Awesome. I'm hoping it'll be great. Under-the-hood fixes like sound, drivers etc is what I am looking forward to.

I just hate the default wallpaper. Everyone that I have shown it to thinks it looks tacky and low-quality. Looks like a 20 minute GIMP job.

Easy fix, but first impressions last!

But all in all, it's an LTS release; these gotta be good!

---

