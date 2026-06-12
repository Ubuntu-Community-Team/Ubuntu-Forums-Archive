---
title: "Poor colours in boot screen"
date: 2009-10-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mgol on 2009-10-14
I just can't look at the new pre-login and login screen in my 64-bit Karmic. It seems to be pretty, but colours are terrible. I feel like in back good days when I discovered I have only 16 bit colour depth set in Windows and I could see it when colours where meant to change smoothly. I just see "jumps" instead of smooth change.

This made me think that maybe I have only 16-bit depth? How can I check (any command?) what is my current colour depth? Don't say about xorg.conf - for me this file doesn't even exist.

Or maybe I have 24-bit depth after I log in but not before? Or maybe just the picture is made in 16-bit mode?

I'd appreciate any help; the current screen seems really unprofessional.

---

### Post by Longinus00 on 2009-10-14
Can you check your version of xsplash by running the following?

```
$ apt-cache policy xsplash
```

---

### Post by mgol on 2009-10-14
Here You are:

$ apt-cache policy xsplash
xsplash:
  Installed: 0.8.3-0ubuntu1
  Candidate: 0.8.3-0ubuntu1
  Version table:
 *** 0.8.3-0ubuntu1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages
        100 /var/lib/dpkg/status

---

### Post by Longinus00 on 2009-10-14
Well, if it looks ugly on both the login screen and the splash screen then there's not much that can be done. You can try to play around with the color/brightness/contrast settings in your monitor and see if that helps any.

Personally, I've noticed that the amount of banding in the splash image is highly dependent on the monitor you see it on, so there may not be much of anything you can do about it besides using a different monitor. If you want to change the background to a different image that is also doable.

[http://ubuntuforums.org/showpost.php?p=8018470&postcount=2](http://ubuntuforums.org/showpost.php?p=8018470&postcount=2)

GDM now uses the largest xsplash image for its background so changing the xsplash backgrounds now also changes GDM. Every time an update to xplash-artwork comes around you'll have to rechange the images. This should happen less and less the closer we get to release.

---

### Post by mgol on 2009-10-14
Why would it depend on my screen? I see the right of those three images:
[http://en.wikipedia.org/wiki/File:Colour_banding_example01.png](http://en.wikipedia.org/wiki/File:Colour_banding_example01.png)
correctly, withound any visible banding. However, I can see it clearly in this image:
[http://lh6.ggpht.com/_FJH0hYZmVtc/SpXDJ9J1GdI/AAAAAAAACVk/-YYv-fzTlh4/s1600-h/gdm-list-3%5B3%5D.png](http://lh6.ggpht.com/_FJH0hYZmVtc/SpXDJ9J1GdI/AAAAAAAACVk/-YYv-fzTlh4/s1600-h/gdm-list-3%5B3%5D.png)
Isn't it just poorly made splash graphic file?

**EDIT:** BTW, I don't have any screen settings available. I use a notebook (this from my signature) and laptops usually don't have screen OSD menu.

---

### Post by NRDNick on 2009-10-14
I've been waiting for them to resolve this issue for a while now. I'm using a 22" Samsung LCD and I'm in the same boat as you, heavy color banding as if the image is 8 bit. It's almost like it's not using the correct background image for my resolution. Any ideas guys? I just hope it gets fixed by the time it hits the release version.

---

### Post by mgol on 2009-10-15
I reported it here:
[https://bugs.launchpad.net/ubuntu/+source/xsplash/+bug/451880](https://bugs.launchpad.net/ubuntu/+source/xsplash/+bug/451880)
If You have a launchpad account, please subscribe and mark "it affects me".

---

### Post by Longinus00 on 2009-10-15
> **mgol said:**
> Why would it depend on my screen? I see the right of those three images:
[http://en.wikipedia.org/wiki/File:Colour_banding_example01.png](http://en.wikipedia.org/wiki/File:Colour_banding_example01.png)
correctly, withound any visible banding. However, I can see it clearly in this image:
[http://lh6.ggpht.com/_FJH0hYZmVtc/SpXDJ9J1GdI/AAAAAAAACVk/-YYv-fzTlh4/s1600-h/gdm-list-3%5B3%5D.png](http://lh6.ggpht.com/_FJH0hYZmVtc/SpXDJ9J1GdI/AAAAAAAACVk/-YYv-fzTlh4/s1600-h/gdm-list-3%5B3%5D.png)
Isn't it just poorly made splash graphic file?

**EDIT:** BTW, I don't have any screen settings available. I use a notebook (this from my signature) and laptops usually don't have screen OSD menu.

It depends on your screen because not all screens are created equally. For instance, I see no banding on the monitors connected to my main computer when viewing the 2nd image you posted (viewsonic & samsung). I do, however, see banding on a hanspree lcd. You might also have some other problem if you can see banding in that 2nd picture, I had to turn the contrast *way* up in gimp before I could see any.

In the meantime, you can try changing to background to a different picture which has less banding.

---

### Post by kestal on 2009-10-15
I also see, what appears to be a bad quality background on both. Using a calibrated monitor for photography.. So this is a bit of a set back in my eyes. The screen is 24" and Ubuntu xsplash/gdm backgrounds look horrible while Windows 7 looks proper (in terms of background quality itself).

---

### Post by mgol on 2009-10-15
> **Longinus00 said:**
> I see no banding on the monitors connected to my main computer when viewing the 2nd image you posted
You might not see it as it's not very visible even for me (and I have good eyes). It is however visible very much on the boot screen (I'd attach an actual-sized image but I don't know how to find it). If You had a link to a bigger one, You'd be welcome.

**EDIT:** Here is a bigger one (still smaller than 1440x900 that I have, but larger than the previous one):
[https://wiki.ubuntu.com/Artwork/Incoming/Karmic/Boot/Demo?action=AttachFile&do=get&target=xsplash-3.png](https://wiki.ubuntu.com/Artwork/Incoming/Karmic/Boot/Demo?action=AttachFile&do=get&target=xsplash-3.png)

---

### Post by Longinus00 on 2009-10-15
> **mgol said:**
> You might not see it as it's not very visible even for me (and I have good eyes). It is however visible very much on the boot screen (I'd attach an actual-sized image but I don't know how to find it). If You had a link to a bigger one, You'd be welcome.

**EDIT:** Here is a bigger one (still smaller than 1440x900 that I have, but larger than the previous one):
[https://wiki.ubuntu.com/Artwork/Incoming/Karmic/Boot/Demo?action=AttachFile&do=get&target=xsplash-3.png](https://wiki.ubuntu.com/Artwork/Incoming/Karmic/Boot/Demo?action=AttachFile&do=get&target=xsplash-3.png)

Trust me when I say I can see no banding when using my current monitor but that I do see banding when using a hanspree one. All the splash images are in /usr/share/images/xsplash/ but there's no need to attach them as we all see them on bootup.


> **kestal said:**
> I also see, what appears to be a bad quality background on both. Using a calibrated monitor for photography.. So this is a bit of a set back in my eyes. The screen is 24" and Ubuntu xsplash/gdm backgrounds look horrible while Windows 7 looks proper (in terms of background quality itself).

The problem with the background is that slow/subtle gradients are highly affected by a monitors color gamut. It doesn't help that the jpg compression is stripping out lots of color data from the soft gradient. One of the proposed plans is to use either png or svg instead of jpg, but I'm not sure if that's been decided upon yet.

---

### Post by mgol on 2009-10-15
> **Longinus00 said:**
> Trust me when I say I can see no banding when using my current monitor but that I do see banding when using a hanspree one.
OK, sorry for my doubts. I hope You don't feel offended by this.

> **Longinus00 said:**
> One of the proposed plans is to use either png or svg instead of jpg, but I'm not sure if that's been decided upon yet.
Are there any png samples of the current splash image so that I could check if it looks noticeably better?

---

### Post by Longinus00 on 2009-10-15
> **mgol said:**
> OK, sorry for my doubts. I hope You don't feel offended by this.


Are there any png samples of the current splash image so that I could check if it looks noticeably better?

[http://bazaar.launchpad.net/~bratsche/xsplash/debug-time/annotate/88/images/bg_1280x1024.png](http://bazaar.launchpad.net/~bratsche/xsplash/debug-time/annotate/88/images/bg_1280x1024.png)

---

### Post by mgol on 2009-10-15
> **Longinus00 said:**
> [http://bazaar.launchpad.net/~bratsche/xsplash/debug-time/annotate/88/images/bg_1280x1024.png](http://bazaar.launchpad.net/~bratsche/xsplash/debug-time/annotate/88/images/bg_1280x1024.png)
I see no real improvement here. ;/

---

### Post by NRDNick on 2009-10-15
Thanks for starting the bug report, I added myself to the list.

---

