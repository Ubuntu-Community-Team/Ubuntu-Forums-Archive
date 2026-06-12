---
title: "Maintaining Ubuntu"
date: 2009-11-30
forum: Installation &amp; Upgrades
---

### Post by dE_logics on 2009-11-30
I've switched to another distribution, but I'll be maintaining Ubuntu on a thumb driver and install it to anyone's computer who asks for Linux.

So I was looking forward towards the dpkg, apt etc... things so as to use them for my purpose (I'm searching for it's man page to be precise, and the various front ends to dpkg confuse me (dpkg itself is a command, then there's apt-get...so what's synaptic?...a front end to apt or dpkg?)).

Also there should be a place where Ubuntu puts the downloaded repository information (the packages available, information about them etc...we call them "snapshots" in Gentoo)...so what is that place?...I plan to update a fresh Ubuntu installation by simply pasting it in the reverent place, then placing the previously downloaded deb packages in /var/cache/apt/archives so Ubuntu does not download but installs from the previously downloaded packages when I apt-get install.

These collected deb packages will be corresponding to the snapshots that I've replaced.

So is there some handbook or something like that?

---

### Post by phillw on 2009-11-30
> **dE_logics said:**
> I've switched to another distribution, but I'll be maintaining Ubuntu on a thumb driver and install it to anyone's computer who asks for Linux.

So I was looking forward towards the dpkg, apt etc... things so as to use them for my purpose (I'm searching for it's man page to be precise, and the various front ends to dpkg confuse me (dpkg itself is a command, then there's apt-get...so what's synaptic?...a front end to apt or dpkg?)).

Also there should be a place where Ubuntu puts the downloaded repository information (the packages available, information about them etc...we call them "snapshots" in Gentoo)...so what is that place?...I plan to update a fresh Ubuntu installation by simply pasting it in the reverent place, then placing the previously downloaded deb packages in /var/cache/apt/archives so Ubuntu does not download but installs from the previously downloaded packages when I apt-get install.

These collected deb packages will be corresponding to the snapshots that I've replaced.

So is there some handbook or something like that?

Hi,

sorry for the dealy - there is another system, that i cannot remember the name of, but aptoncd will do what you want

[http://en.wikipedia.org/wiki/APTonCD](http://en.wikipedia.org/wiki/APTonCD)

And, you can update the apt on cd on a usb drive, whilst retaining the usual install cd type install.

Regards,

Phill.

---

### Post by mac9416 on 2009-11-30
> **dE_logics said:**
> Also there should be a place where Ubuntu puts the downloaded repository information (the packages available, information about them etc...we call them "snapshots" in Gentoo)...so what is that place?...I plan to update a fresh Ubuntu installation by simply pasting it in the reverent place, then placing the previously downloaded deb packages in /var/cache/apt/archives so Ubuntu does not download but installs from the previously downloaded packages when I apt-get install.

Hi there,

phillw suggested APTOnCD, which should work fine for you. But to answer your above question, the "downloaded repository information" (called package index files in Ubuntu) is kept in /var/lib/dpkg/lists. When you copy the packages from /var/cache/apt/archives, you can copy the data from the other directory too. Then run 'sudo apt-cache gencaches'. That will force APT to re-read the index files and know what the latest packages available are.

Hope that helps some!

---

### Post by dE_logics on 2009-11-30
aaaa...apt on CD does not pose that much of an advantage...it's just a front end to copy paste...


Anyway, thanks for giving info about the pacakge index files.


And what about apt commands?...and dpkg front ends preinstalled on Ubuntu?

---

### Post by dE_logics on 2009-12-05
> /var/lib/dpkg/lists

There's no such file caled as lists in /var/lib/dpkg.

I cant copy all the contents of /var/lib/dpkg...I know it contains information about the installed packages.

---

### Post by dE_logics on 2009-12-05
is it /var/lib/apt/lists?

---

### Post by mac9416 on 2009-12-05
My apologies, that's what I should have said. It's easy to get the directories mixed up sometimes. ;)

---

