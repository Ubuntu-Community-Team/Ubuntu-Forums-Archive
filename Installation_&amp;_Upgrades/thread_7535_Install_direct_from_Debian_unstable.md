---
title: "Install direct from Debian unstable"
date: 2004-12-08
forum: Installation &amp; Upgrades
---

### Post by turnip_flan on 2004-12-08
Hello,

I am enjoying the install method in Ubuntu coming from an rpm based distro.

Has anyone had experience installing direct from the debian unstable repositries? and what are the package repositries you have to add to synaptic?

I know you can turn on universe and multverse etc but I am specifically after monodevelop which is only in debian unstable now. I have tried the ones on [http://www.ubuntulinux.org/wiki/BreakMyUbuntu](http://www.ubuntulinux.org/wiki/BreakMyUbuntu) but tsengs site seems to be down and I am thinking I could get them direct from the debian sites.

---

### Post by az on 2004-12-08
Try a debian repository.  They are all listed on debian.org

add them to your sources.list

deb [http://http.us.debian.org/debian](http://http.us.debian.org/debian) unstable main contrib non-free

You can also find repositories on apt-get.org.

These are made for debian and so they will (may) break you system.

You can also try to apt-get source packages from debian unstable so that they are compiled with an ubuntu base.  A sure-fire way to know that it would break your system is to try installing it that way and if it cannot compile - you know!  And you do not end up with a broken system.  Add deb-src entries into your sources.list file.

Good luck!

---

### Post by Coburn on 2006-05-30
Okay, azz.

Be specific.

You are way over my head.

How do you tell apt-get to fetch the source from debian unstable?  What is the syntax for adding deb-src entries to /sources.list, or is it just (##)?

I know how to add a source to Synaptic, although I needed that line with the URI.  I was entering it wrong.  [http://ftp](http://ftp)...

I'll go look in the doc pages, but thanks for your help anyway.  I might need it, and so might someone else.

By the way, this is so I can instal **[COLOR="Red"]moto4lin[/COLOR]**, which the developer has inexplicably made dependent on unstable libs and packages.  Back to the future, I guess.  My safest course seems to be using Synaptic, or, better yet, apt-get.

Thanks.

Update:  I was able to install moto4lin, with dependencies, using Synaptic.  I also manually installed p2kmoto, which I didn't remember if Synaptic got for me, because it seems to be a key dependency.  The only trouble I had was that within the program Preferences dialog it shows ID's for Vendor and Device.  You configure it as an AT device for things like using it as a wireless link for your laptop, and as a p2k device for file access.  For some reason I had the AT and p2k Device ID's switched around--maybe it was the startup defaults that were backwards.  I think p2k is 4801 and AT is 4802.

---

