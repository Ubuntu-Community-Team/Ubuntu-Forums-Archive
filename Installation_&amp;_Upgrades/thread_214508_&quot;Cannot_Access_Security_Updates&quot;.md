---
title: "&quot;Cannot Access Security Updates&quot;"
date: 2006-07-12
forum: Installation &amp; Upgrades
---

### Post by Optiker on 2006-07-12
After weeks of trying to resolve problems with accessing repositories in my Kubuntu Dapper 6.06 installation at work, with no working solutions here or from my inhouse IT guy, I decided to do a clean reinstall today. Things went relatively well until an error message went by that said... "Cannot Access Security Updates." But, it continued on and presumably installed. I booted and all seemed OK. I went in and uncommented the UNIVERSE repositories in sources.list, but noticed the lines regarding security were as shown below.

[B][COLOR="Purple"]# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe[/COLOR][/B]

I uncommented the last two, but not the first two since the notations regarding failure to verify were relative to the first two.

Then I attempted to install GIMP using Adept. As reported in my posts after the previous clean install, when I tried to install GIMP using Adept, it refused with an error message to the effect that it couldn't access the packages because something wasn't right and could "break" my system.

This is essentially back to where I started weeks ago. As I tried various suggestions, the consistent mesage came back that when trying to access the repositories, an incorrect header was returned.

Is the failure to access security updates critical here so possibly the problem? If not, any suggestions before I give it up and wipe it off?

Thanks!

Very frustrated...](*,) 
Optiker

---

