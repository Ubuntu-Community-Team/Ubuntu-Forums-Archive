---
title: "Which distro for HD Movies?"
date: 2012-10-09
forum: Installation &amp; Upgrades
---

### Post by SlugSlug on 2012-10-09
Hi

Pre 10.04 My old PC would play 720 Movies But due to kernel updates / Dropped support for old ATI Cards the pc is now useless as it's used for a TV .

The GFX card is a X800Pro

Am wondering is anyone knows a distro that could help bring the PC back to life and play 720's ?

Tried xubuntu and same issue so I think I need the old kernel / ATI drivers

---

### Post by GeForce 9500GT on 2012-10-09
I have an old pc (P4 3.0 GHz / 2 gig memory / Intel onboard GPU) and this "oldie" is connected to my flatscreen tv in order to play movies. I installed [Lubuntu 12.04]("http://lubuntu.net/") which has the lightweight desktop environment [LXDE]("http://lxde.org/"). And i don't have any issues with playing video's at this moment. I'm using Vlc as videoplayer.

---

### Post by SlugSlug on 2012-10-09
I think I need kernel 2.6.31 or earlier

Debian 5 has this ~ is this still usable ?

---

### Post by GeForce 9500GT on 2012-10-09
> **SlugSlug said:**
> I think I need kernel 2.6.31 or earlier

Why do you think you need an earlier kernel? There's not much reason to go for an older kernel. Besides that, you'lll gonna miss a lot of kernel updates

---

### Post by SlugSlug on 2012-10-09
Need old kernel for ATI driver support

---

### Post by GeForce 9500GT on 2012-10-09
Support for your videocard is not only depending on the kernel, ATI and Nvidia need a so called proprietary driver. 

Here are some links for your videocard:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
[http://askubuntu.com/questions/133398/amd-ati-drivers-from-website-vs-proprietary-drivers-in-ubuntu-12-04-repos](http://askubuntu.com/questions/133398/amd-ati-drivers-from-website-vs-proprietary-drivers-in-ubuntu-12-04-repos)

You can install the latest lightweight ditro such as Xubuntu or Lubuntu and install the correct driver to get your card working.

---

### Post by SlugSlug on 2012-10-09
Unfortunately the ATI  is not installable later kernels ~ Thats why I need to older ones :)

---

### Post by doorknob60 on 2012-10-09
Try Debian stable, or oldstable if you need to go back that far. If you do have to use Debian 5 (oldstable), you should still be able to, but "2012-02-06 : End of security updates / End of life", so be aware of that. If you're just using it as a media center that shouldn't be much of an issue, if you're content with using old versions of things like VLC or whatever else you use.

---

### Post by SlugSlug on 2012-10-10
Thanks I'll give debian 5 a shot

---

### Post by SlugSlug on 2012-10-15
For the record,

I installed Debian 5 (oldstable) hit dependency hell compiling apps (VLC was a pain). did a dist-upgrade to Debian 6 (squeeze / stable) and it's running HD movies now pretty sweet. 

I've disabled the entries in sources.list to stop any updates breaking it 


Thanks

---

