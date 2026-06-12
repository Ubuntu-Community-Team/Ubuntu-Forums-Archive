---
title: "package update error -- &quot;awoken-icon-theme&quot;"
date: 2011-07-19
forum: Installation &amp; Upgrades
---

### Post by SaintDanBert on 2011-07-19
Update manager announced that I had updates waiting.
I tried to spin and install the updates only to get errors.
One package **awoken-icon-theme** keeps showing as ready for update, but when I try the install I get:
```

Preparing to replace awoken-icon-theme 2.0~ppa1~lucid2 (using .../awoken-icon-theme_2.1~ppa1~lucid1_all.deb) ...

Unpacking replacement awoken-icon-theme ...

dpkg: error processing /var/cache/apt/archives/awoken-icon-theme_2.1~ppa1~lucid1_all.deb (--unpack):
 unable to install new version of `/usr/share/icons/AwOken/clear/128x128/places/s11/folder-science.png': No such file or directory

Errors were encountered while processing:
 /var/cache/apt/archives/awoken-icon-theme_2.1~ppa1~lucid1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Yes, I can unmark the package and press forward with whatever else is available. However, when update manager does its dance, this package is right back on the list again.

Yes, I see the string **~ppa1** in the name of the package DEB file.
I'm dashed to discover what might be calling for this specific package from whichever PPA is involved.

Suggestions for resolution?
~~~ 0;-Dan

---

### Post by jayarbie on 2011-07-20
same problem ...

---

### Post by SaintDanBert on 2011-07-20
I found this page: [http://linux.softpedia.com/progDownload/Awoken-icon-theme-Edited-Download-60016.html](http://linux.softpedia.com/progDownload/Awoken-icon-theme-Edited-Download-60016.html) that leads to a tar-ball.

The **tar.gz** download has one of those "wait for NNN seconds ... or sign up" delays. The resulting download does not include a package but instead the raw icon theme files.

This won't fix your update-manager notice troubles, but it does give you the theme if you need it.

Cheers,
~~~ 0;-Dan

---

### Post by SaintDanBert on 2011-07-20
I found this page: [http://cdn.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1707-awoken-icon-set-20-is-available-ppa-ubuntu](http://cdn.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1707-awoken-icon-set-20-is-available-ppa-ubuntu).

This will guide you through adding a PPA and package install. More after I try this.

[color=green]
**Follow-up:**
```

prompt$sudo add-apt-repository ppa:alecive/antigone
[sudo] password for saint: 

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 4FF2E40CEC39A57852C12BAF77589CABF0B5D826

gpg: requesting key F0B5D826 from hkp server keyserver.ubuntu.com
gpg: key F0B5D826: "Launchpad antigone" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

prompt$ sudo apt-get install awoken-icon-theme

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  awoken-icon-theme
1 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
4 not fully installed or removed.
Need to get 0B/35.3MB of archives.

After this operation, 14.7MB of additional disk space will be used.
(Reading database ... 514521 files and directories currently installed.)

Preparing to replace awoken-icon-theme 2.0~ppa1~lucid2 (using .../awoken-icon-theme_2.1~ppa1~lucid1_all.deb) ...
Unpacking replacement awoken-icon-theme ...

dpkg: error processing /var/cache/apt/archives/awoken-icon-theme_2.1~ppa1~lucid1_all.deb (--unpack):
 unable to install new version of `/usr/share/icons/AwOken/clear/128x128/places/s11/folder-science.png': No such file or directory

Errors were encountered while processing:
 /var/cache/apt/archives/awoken-icon-theme_2.1~ppa1~lucid1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
prompt-$  

```

The "unchanged" tells me that I already had this PPA enabled.
After click-grind, the error persists, so there is some problem within the repository for this package.
[/color]

Cheers,
~~~ 0;-Dan

---

### Post by EnGee on 2011-07-22
I also have the same problem!

---

### Post by volneilo on 2011-07-24
Hi folks. Same problem here, hope someone to come up with an answer soon. Googling led me to only this thread, seems like this is a new subject yet.

---

### Post by ParadoxBlue on 2011-07-26
I guess I might as well sign up to this thread. I have the same problem. My error seems to be just the "science" icon. I also notice when I browse through /usr/share/icons/AwOken/clear/128x128/places I find many broken links to icons that don't seem to exist. I've submitted the attached screenshots for everyone's perusal.

---

### Post by marko_4454 on 2011-07-27
I'm also having this problem, hopefully they will fix it soon. My folders are all screwed up :(

---

### Post by dpsk on 2011-07-28
same there :( wanna fix

---

### Post by mcrump001 on 2011-08-02
It seems that doing:

sudo aptitude remove awoken-icon-theme

and then:

sudo aptitude install awoken-icon-theme


fixes the problem.  At least it did for me.

---

### Post by dpsk on 2011-08-02
> **mcrump001 said:**
> It seems that doing:

sudo aptitude remove awoken-icon-theme

and then:

sudo aptitude install awoken-icon-theme


fixes the problem.  At least it did for me.

works fine for me too.

---

### Post by volneilo on 2011-08-03
> **mcrump001 said:**
> It seems that doing:

sudo aptitude remove awoken-icon-theme

and then:

sudo aptitude install awoken-icon-theme


fixes the problem.  At least it did for me.

Many thanks! Worked fine here too!

---

### Post by ParadoxBlue on 2011-08-04
> **mcrump001 said:**
> It seems that doing:

sudo aptitude remove awoken-icon-theme

and then:

sudo aptitude install awoken-icon-theme


fixes the problem.  At least it did for me.
Yup that does seem to have worked. Guess I should have tried that to begin with but didn't want to make things any worse than they already were. Thx.

---

### Post by SaintDanBert on 2011-08-05
> **mcrump001 said:**
> It seems that doing:

sudo aptitude remove awoken-icon-theme

and then:

sudo aptitude install awoken-icon-theme

fixes the problem.  At least it did for me.

Does anyone know which package demands this specific icon theme?

I simply removed the package without a re-install. So far nothing
has complained, but I cannot discover the dependencies with the package
gone from my box.

~~~ 0;-Dan

---

### Post by jayarbie on 2011-08-07
works (thanks) - but what was the reason for the error?

---

### Post by SaintDanBert on 2011-08-07
Just a guess based on limited understanding of how **apt-get** and friends works:
[indent]
Correctly, the update-manager (and synaptic) both identify the package as needing an update. (I base "correct" on results of poking around in *package details* and similar.)

The update runs and tries to fetch the package parts.

During the data fetch, there are errors reported out there in package land resulting in "not found" or similar errors.

The errors cause the update to report a failure.
[/indent]

The errors could be due to a bad dependency or a simple mis-spelled filename or something like that.

Unless or until someone fixes "package land" the error will persist.

Cheers,
~~~ 0;-Dan

---

### Post by cloneroach on 2011-09-03
works fine BRAVO!!!

---

### Post by sub sexy on 2011-09-04
> **mcrump001 said:**
> It seems that doing:

sudo aptitude remove awoken-icon-theme

and then:

sudo aptitude install awoken-icon-theme


fixes the problem.  At least it did for me.


Well that was easy! This fix worked like a charm for me as well. Thanks for posting this. Such a simple fix.

---

### Post by SaintDanBert on 2011-09-04
> **sub sexy said:**
> Well that was easy! This fix worked like a charm for me as well. Thanks for posting this. Such a simple fix.

Finally and at long last, this worked for me as well.
I guess that things got fixed in package land.

It has reached a point where we take for granted that we can use
```

**sudo apt-get install *package***

 or 

**sudo aptitude install *package***

```

This minor problem reminds me that these simple commands have a huge number of moving parts:
[list]
[*]scan of our local installed package inventory
[*]calculation of dependencies
[*]request to locate desired package and all dependencies
[*]interaction with primary repository
[*]interaction with various PPA repositories
[*]request to download desired packages and dependencies
[*]install of each package fetched
[/list]
An occassional hiccough should not be a surprise, but they are rare enough that they continue to surprise us. Thanks, Developers!!

Thanks to all respondents,
~~~ 0;-Dan

---

### Post by awanti on 2011-11-11
yes its worked me too....

1st unistall it then install newer version..

---

