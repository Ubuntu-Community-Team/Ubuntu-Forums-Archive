---
title: "Can't upgrade to Hardy Heron."
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by John Jones on 2008-04-29
Ever since I installed Gutsy, I've been getting an error message whenever I check for updates. This wasn't a problem, because it didn't prevent me from updating.

However, now that I want to upgrade to Hardy Heron, I'm getting the same error message, and the upgrade process stops.

The error message is:-

Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/Release](http://archive.canonical.com/ubuntu/dists/hardy/Release) Unable to find expected entry  commercial/binary-i386/Packages in Meta-index file (malformed Release file?)

Does anybody know how I can deal with this, please?

Thanks in advance,

John

---

### Post by GlennW on 2008-04-29
I think that I've got the same problem. Whenever I use the Update Manager or open the automatic update on the panel, I end up with the same thing. 

(Check the attached screenshot of the actual error message.)

Prior to this error message, a different box popped up saying that Third Party Repositories would be disabled.

What do I need to do to rectify this problem?

---

### Post by GlennW on 2008-05-03
Can anyone help us out?

---

### Post by tetsuc on 2008-05-03
same issue for me. I am upgrading to 8.04 from 7.10 via the alternate CD. Following the popup that tells me that third party repositories have been disabled I get:

Could not download the upgrades

The upgrade aborts now. Please check your internet connection or installation media and try again. 

Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/w/wxwidgets2.6/libwxgtk2.6-0_2.6.3.2.2-2ubuntu4_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/w/wxwidgets2.6/libwxgtk2.6-0_2.6.3.2.2-2ubuntu4_i386.deb) 404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/w/wine/wine_0.9.59-0ubuntu4_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/w/wine/wine_0.9.59-0ubuntu4_i386.deb) 404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/v/vcdimager/libvcdinfo0_0.7.23-4ubuntu1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/v/vcdimager/libvcdinfo0_0.7.23-4ubuntu1_i386.deb) 404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/w/wxwidgets2.6/libwxbase2.6-0_2.6.3.2.2-2ubuntu4_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/w/wxwidgets2.6/libwxbase2.6-0_2.6.3.2.2-2ubuntu4_i386.deb) 404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/x/xosd/libxosd2_2.2.14-1.4_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/x/xosd/libxosd2_2.2.14-1.4_i386.deb) 404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/w/wxwidgets2.8/libwxbase2.8-0_2.8.7.1-0ubuntu3_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/w/wxwidgets2.8/libwxbase2.8-0_2.8.7.1-0ubuntu3_i386.deb) 404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/w/wxwidgets2.8/libwxgtk2.8-0_2.8.7.1-0ubuntu3_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/w/wxwidgets2.8/libwxgtk2.8-0_2.8.7.1-0ubuntu3_i386.deb) 404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/u/ufraw/ufraw_0.13-1build1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/u/ufraw/ufraw_0.13-1build1_i386.deb) ...etc...

---

### Post by Kizlum on 2008-05-03
I got similar errors. I've commented (add # at the line's start) all bad lines in my sources.list. Then, apt-get update and the update-manager worked.

---

### Post by tetsuc on 2008-05-04
Okdoke, for lack of anything else to do I commented out a couple of lines in my sources.list (all third party stuff) and, in addition, tried this too. 36 minutes and I will know... NOTE that the third party sources had already been removed.

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free

thanks for the help! hope it works...

if this doesn't I will switch back to doing a clean install with the live cd - and hope that this time it recognises that it can import my settings from 7.10.

---

### Post by Pumalite on 2008-05-04
You can also try changing Servers if you are sure of your connection.

---

### Post by tetsuc on 2008-05-04
that worked for me :-). But I decided to add a new user (to start with the  8.04 default settings) and then copy all of my files over and made a small mistake with a chown statement by applying it recursively to the / ... nothing works now so I am trying to repartition and install that way.

:-(

---

### Post by Pumalite on 2008-05-04
Good luck.

---

### Post by GlennW on 2008-05-05
Hey guys, I think I may have found the answer, at least it worked for me. I was reading elsewhere and came across this:

[INDENT]At a guess, /etc/apt/sources.list is still full of gutsy repositories rather than hardy. What you want is something like:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse[/INDENT]

So, using gedit, I opened the sources.list file, commented out all the files that had "gutsy" in them and copied the entire block (see above) to the bottom. After that the install proceeded with no major issues!! The only thing I needed to do after that was to activate the proprietary nvidia driver. I have to say, hardy rocks! Good luck!!

---

