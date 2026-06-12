---
title: "Adding sources to sources.list?"
date: 2005-07-07
forum: Installation &amp; Upgrades
---

### Post by GnomicGhost on 2005-07-07
Hi all.
Firstly, I have searched for the answer here & elsewhere and I have googled it but nothing came of that so...
Now I realise this is probably a really newbie request, however I'm having absolutely no luck whatsoever trying to add sources to my sources.list.

I want to add: [http://mirror.mcs.anl.gov/pub/ubuntu/pool/main/libs/libsndfile/](http://mirror.mcs.anl.gov/pub/ubuntu/pool/main/libs/libsndfile/) to get the  libsndfile1_1.0.10-1_i386.deb that I can't get off the the ubuntu server due to the MD5SUM problems at the moment.

Can someone please walk me through adding this (and others) to the sources.list so I stop getting the errors I have been getting.
I have tried 'copying' the format/syntax of the other repos's substituting the address I want, but it won't accept it.

I'm wanting to install the codecs as at [www.ubuntuguide.org/#codecs](www.ubuntuguide.org/#codecs) but I can't get the first one 'gstreamer0.8-plugins'.

Any help would be greatly appreciated.
Thanks.
GG

---

### Post by frodon on 2005-07-07
Can you post your source.list file with the syntax you use to add the line, it will be useful to help you.

---

### Post by GnomicGhost on 2005-07-07
I'm trying things like:
deb [http://mirror.mcs.anl.gov/pub](http://mirror.mcs.anl.gov/pub) ubuntu dists hoary 
deb-src [http://mirror.mcs.anl.gov/pub](http://mirror.mcs.anl.gov/pub) ubuntu dists hoary

Also with and without slashes '/' between each of the dir's, going right back to:
deb [http://mirror.mcs.anl.gov/](http://mirror.mcs.anl.gov/)

I've forgotten exactly what I wrote once before and am not getting the same errors, but it was something like 'error on line 33' of sources.list and wouldn't go any further.
However now it tells me (since using the top lines)
----------------------
W: Couldn't stat source package list [http://mirror.mcs.anl.gov](http://mirror.mcs.anl.gov) ubuntu/dists Packages (/var/lib/apt/lists/mirror.mcs.anl.gov_pub_dists_ubuntu_dists_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://mirror.mcs.anl.gov](http://mirror.mcs.anl.gov) ubuntu/hoary Packages (/var/lib/apt/lists/mirror.mcs.anl.gov_pub_dists_ubuntu_hoary_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
----------------------

Thanks.

---

### Post by ImaMadGoat on 2005-07-07
I'm having a similar problem running apt-get update.

this is my sources.list file

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://mirror.mcs.anl.gov/pub/ubuntu](http://mirror.mcs.anl.gov/pub/ubuntu) hoary-updates main restricted
deb-src [http://mirror.mcs.anl.gov/pub/ubuntu](http://mirror.mcs.anl.gov/pub/ubuntu) hoary-updates main restricted

deb [http://mirror.mcs.anl.gov/pub/ubuntu](http://mirror.mcs.anl.gov/pub/ubuntu) hoary-security main restricted
deb-src [http://mirror.mcs.anl.gov/pub/ubuntu](http://mirror.mcs.anl.gov/pub/ubuntu) hoary-security main restricted

# deb [http://mirror.mcs.anl.gov/pub/ubuntu](http://mirror.mcs.anl.gov/pub/ubuntu) hoary-security universe
# deb-src [http://mirror.mcs.anl.gov/pub/ubuntu](http://mirror.mcs.anl.gov/pub/ubuntu) hoary-security universe

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

#Primary Mirror (5/17/2005) overloaded :)
#deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted
#deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted

#backup Mirror - FAST
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted


when I run apt-get update, it 'get's up to 18 and after a few 'hit's I see this.

Failed to fetch [ftp://ftp.nerim.net/debian-marillat/dists/stable/main/binary-i386/Packages.gz](ftp://ftp.nerim.net/debian-marillat/dists/stable/main/binary-i386/Packages.gz)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hoary/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/hoary/multiverse/source/Sources.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.


Any help on this would be appreciated. I'm brand new to Linux and I love it, I'd just llike to get this part working. 

Thanks in advance

The Goat

---

### Post by mingus on 2005-07-07
[QUOTE=ImaMadGoat]
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

#Primary Mirror (5/17/2005) overloaded :)
#deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted
#deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted[/QUOTE]

Pull out these lines . . . debian-marillat is gonna cause you a lotta problems.  The backports repository you've got is for dev; use a mirror instead.

---

### Post by mingus on 2005-07-07
[QUOTE=GnomicGhost]I'm trying things like:
deb [http://mirror.mcs.anl.gov/pub](http://mirror.mcs.anl.gov/pub) ubuntu dists hoary 
deb-src [http://mirror.mcs.anl.gov/pub](http://mirror.mcs.anl.gov/pub) ubuntu dists hoary
[/QUOTE]

Note the syntax in ImaMagGoat's post below . . . you are missing /ubuntu in the directory name, "dists" is wrong, "hoary" needs to be followed by whichever repositories you want, e.g., "main", "restricted", "universe", "multiverse".

---

### Post by ImaMadGoat on 2005-07-07
Dude.....you are my hero.

I can't believe I spent that much time on a problem only to have it be fixed so easily.

UBUNTU IS MY NEW HOME! \\:D/

---

### Post by GnomicGhost on 2005-07-08
Thanks for you help mingus.
I still don't really understand how if the path is */dists/hoary, you can just put */hoary excluding the dists.  But anyhow I've finally got the packages I wanted from another source.
I'll have a play with them and see how I go.
Thanks again mingus.
 \\:D/  \\:D/  \\:D/

---

### Post by mingus on 2005-07-08
[QUOTE=GnomicGhost]Thanks for you help mingus.
I still don't really understand how if the path is */dists/hoary, you can just put */hoary excluding the dists.  But anyhow I've finally got the packages I wanted from another source.
I'll have a play with them and see how I go.
Thanks again mingus.
 \\:D/  \\:D/  \\:D/[/QUOTE]

The package manager looks for an index; it doesn't read the raw directory itself.
If you check the other repositories, you will see how the pathing works.  Just look at the Starter Guide and elsewhere for the correct syntax; it is consistent.

---

### Post by GnomicGhost on 2005-07-08
Will do and again cheers.

---

