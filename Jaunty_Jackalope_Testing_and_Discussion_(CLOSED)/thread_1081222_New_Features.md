---
title: "New Features?"
date: 2009-02-26
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by GuitarRocker2562 on 2009-02-26
I just installed JJ a4, and I must say, there are no big new changes, is it just me? Am I missing something?

---

### Post by taavikko on 2009-02-26
[https://wiki.ubuntu.com/JauntyJackalope/TechnicalOverview](https://wiki.ubuntu.com/JauntyJackalope/TechnicalOverview)

---

### Post by GuitarRocker2562 on 2009-02-26
So notifications and ext4? That's it?

---

### Post by perlluver on 2009-02-26
Also a new GDM login page, a new volume control.  The network manager has more features, faster boot time.  Open Office 3.0.  I can't think of any others right now, but I am sure there are some other new features.

---

### Post by olskar on 2009-02-26
> **perlluver said:**
> Also a new GDM login page, a new volume control.  The network manager has more features, faster boot time.  Open Office 3.0.  I can't think of any others right now, but I am sure there are some other new features.

The new volumecontrol was removed?

---

### Post by perlluver on 2009-02-26
> **olskar said:**
> The new volumecontrol was removed?

No, I meant that was a new feature.  The sideways volume control.

---

### Post by philinux on 2009-02-26
Better xorg and nvidia driver. Compiz is really smooth now here.

---

### Post by DeeZiD on 2009-02-26
> **philinux said:**
> Better xorg and nvidia driver. Compiz is really smooth now here.

Well, at least kwin4 with compositing is much faster with older xorg and nvidia 180.29.


Dennis

---

### Post by Simian Man on 2009-02-26
Ubuntu never really adds many features.  It is about refining the user experience and incorporating newer upstream Debian packages.  If you want a distro that adds a bunch of new stuff, check out [Fedora]("http://fedoraproject.org/wiki/Releases/11/FeatureList") :).

---

### Post by Sand &amp; Mercury on 2009-02-26
> **DeeZiD said:**
> Well, at least kwin4 with compositing is much faster with older xorg and nvidia 180.29.


Dennis
Much better for me too, that is pretty much the clincher for me. Now I can enjoy Kubuntu as intended.

---

### Post by rockin_goliath on 2009-02-26
Is the new pulseaudio mixer from Gnome, as stated in the Gnome Roadmap, going to make it in?

---

### Post by Nullack on 2009-02-26
You get kernel 2.6.28, gnome 2.26, xorg 1.6 and many other new packages. Its not a huge release but a nice evolution.

---

### Post by olskar on 2009-02-26
> **rockin_goliath said:**
> Is the new pulseaudio mixer from Gnome, as stated in the Gnome Roadmap, going to make it in?

It got in, and was taken out again, it will propably not get in again.

---

### Post by Halow on 2009-02-26
I liked that volume control. It makes dealing with multiple cards easier. Instead I had to go back to pavucontrol, which is supposedly obsolete. =(

---

### Post by kyleabaker on 2009-02-26
What time do they usually update the release pages for the alphas? Alpha 5 still isn't published (at the time of posting this):

[http://www.ubuntu.com/testing/jaunty/alpha5](http://www.ubuntu.com/testing/jaunty/alpha5)

@olskar
Have any idea why the new pulseaudio mixer from Gnome was pulled? link maybe? Just curious.

---

### Post by PRGUY85 on 2009-02-26
> **kyleabaker said:**
> What time do they usually update the release pages for the alphas? Alpha 5 still isn't published (at the time of posting this):

[http://www.ubuntu.com/testing/jaunty/alpha5](http://www.ubuntu.com/testing/jaunty/alpha5)

@olskar
Have any idea why the new pulseaudio mixer from Gnome was pulled? link maybe? Just curious.

I am waiting patiently for it too.  Any news?

---

### Post by olskar on 2009-02-26
> **kyleabaker said:**
> What time do they usually update the release pages for the alphas? Alpha 5 still isn't published (at the time of posting this):

[http://www.ubuntu.com/testing/jaunty/alpha5](http://www.ubuntu.com/testing/jaunty/alpha5)

@olskar
Have any idea why the new pulseaudio mixer from Gnome was pulled? link maybe? Just curious.


Think this was it:
> gnome-media (2.25.5-0ubuntu2) jaunty; urgency=low

  * debian/control.in,
    debian/gnome-media-common.install,
    debian/rules:
    - enable the intrepid version of the mixer capplet rather than the new one
      (lp: #324807)

 -- Sebastien Bacher <seb128@ubuntu.com>   Thu, 05 Feb 2009 16:13:35 +0100

Read the discussion on [https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/324807](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/324807)

Apparently it was buggy, can't help to think it is better to fix those bugs than to revert to another volume control

---

### Post by kyleabaker on 2009-02-26
I still haven't made up my mind on the new volume control, but I definitely like the fact that I no longer have to toggle it off manually to get it to disappear. The previous applet would not disappear until you manually clicked the icon again (at least for me it wouldn't).

---

