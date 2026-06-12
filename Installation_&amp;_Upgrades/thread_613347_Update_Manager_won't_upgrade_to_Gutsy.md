---
title: "Update Manager won't upgrade to Gutsy"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by Baasha on 2007-11-14
I have been trying to upgrade for several days using Upgrade Manager.  Each time the process stalls at Modifying Software Channels, at the bottom of the window it says fetching fille 55 of 61.  What's wrong?

---

### Post by larry wales on 2007-11-17
Hi,

I'm having a similar problem:

Trying to upgrade through the Update Manager, and it always chokes with the following error:

> 
A problem occurred during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg) Could not resolve ‘wine.lowvoice.nl’
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_GB.bz2](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_GB.bz2) Could not resolve ‘wine.lowvoice.nl’
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz) Could not resolve ‘wine.lowvoice.nl’


Now, I uninstalled wine from my computer long ago.  Why is the system still trying to fetch these files?  And - ultimately - how can I perform the update??

thank you,
larry

---

### Post by ramkumail on 2007-11-17
Hi,
 A quick solution will be to remove all third party sources from settings > repositories in synaptic and then try the upgrade.(can also do that by editing /etc/apt/sources.list file). All i mean is that keep only ubuntu repos and disable all the others. Let me know if this works.

---

### Post by larry wales on 2007-11-17
Coolio!! That worked!!  


Muchas gracias amigo \\:D/

---

### Post by ramkumail on 2007-11-18
I am glad that it worked. If this is the problem then one can overcome it by removing only wine repository(the repository that is failing to be fetched) rather than all third party repos which you might need in the future.

---

### Post by ozfinngeek on 2007-12-05
I am also have a similar problem and am not sure how to fix it, seems to be having trouble with the repo's below.

Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/dists/gutsy/Release.gpg 
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/dists/gutsy/main/i18n/Translation-en_AU.bz2 
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/dists/gutsy/restricted/i18n/Translation-en_AU.bz2 
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg) 
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_AU.bz2) 
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_AU.bz2) 
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_AU.bz2) 
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_AU.bz2) 
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg) 
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_AU.bz2) 
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_AU.bz2) 
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_AU.bz2) 
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_AU.bz2) 
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg) 
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_AU.bz2) 
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_AU.bz2) 
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_AU.bz2) 
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_AU.bz2) 
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_AU.bz2) 
Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy/Release.gpg](http://archive.canonical.com/ubuntu/dists/gutsy/Release.gpg) 
Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy/partner/i18n/Translation-en_AU.bz2](http://archive.canonical.com/ubuntu/dists/gutsy/partner/i18n/Translation-en_AU.bz2) 

any help would be appreciated.

Thanks

---

### Post by PmDematagoda on 2007-12-05
Post the result of:-

```
cat /etc/apt/sources.list
```

---

### Post by ozfinngeek on 2007-12-05
Ok, here are the results, the *** at the start of a couple repo's are there to remind me of the ones that i need to enable again after update.


# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release amd64 (20070415)]/ feisty main restricted

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
# deb [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu) ./
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse

# deb [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas all
# deb-src [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas all

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse


deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
# ***deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
# ***deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main


#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main


deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty-security multiverse
#AUTOMATIX REPOS END

---

### Post by PmDematagoda on 2007-12-05
Wait a second, I'm confused here:confused:.

Do you have Ubuntu 7.10 or 7.04?

From the entry for the Ubuntu 7.10 CD-ROM, I feel that you are already using Ubuntu 7.10.

---

### Post by ozfinngeek on 2007-12-05
Sorry about that, I added the 7.10 cd in synaptic as an alternate way of sourcing the upgrade files in case it was an internet routing issue of some sort. I had to burn a copy anyway for another pc. I also have the previous version of the CD delisted so as to redue the chance of me doing something stupid and installing older versions of apps just because I forgot to turn the dsl router on.

BTW, I am really pleased with the fantastic level of community support here. 

To clarify, I am running Ubuntu 7.04 AMD64 and trying to upgrade to the 7.10 AMD64

---

### Post by PmDematagoda on 2007-12-05
I do not think you have all the required repositories.

Get a new sources.list file from [Source-o-matic]("http://www.ubuntu-nl.org/source-o-matic/"). Then backup your old sources.list file and replace it with the new one.

Then do:-

```
sudo apt-get update
```

After that is done, try upgrading again.

---

### Post by ozfinngeek on 2007-12-06
Thanks for that,

The source.list generating site and a nice new clean source.list did the trick. Actually I like the layout of the file produced I thick I will add my other repo's in to it in the same format. Much easier to read that way.

Again, thanks to the community here for the great support. :guitar:

BTW how do I mark this as solved?

---

### Post by jerlinux on 2007-12-13
Hi,
A quick solution will be to remove all third party sources from settings > repositories in synaptic and then try the upgrade.(can also do that by editing /etc/apt/sources.list file). All i mean is that keep only ubuntu repos and disable all the others. Let me know if this works.


I know that this question will not make me appear to the be brightest person on the planet BUT Where do I find this settings folder?

Thanks

_______

---

### Post by Partyboi2 on 2007-12-13
> **ozfinngeek said:**
> Thanks for that,

The source.list generating site and a nice new clean source.list did the trick. Actually I like the layout of the file produced I thick I will add my other repo's in to it in the same format. Much easier to read that way.

Again, thanks to the community here for the great support. :guitar:

BTW how do I mark this as solved?
At the top of the page to your right, you will see a option called "thread Tools" click on that and select "Mark this thread as solved"
:)

---

### Post by Partyboi2 on 2007-12-13
> **jerlinux said:**
> Hi,
A quick solution will be to remove all third party sources from settings > repositories in synaptic and then try the upgrade.(can also do that by editing /etc/apt/sources.list file). All i mean is that keep only ubuntu repos and disable all the others. Let me know if this works.


I know that this question will not make me appear to the be brightest person on the planet BUT Where do I find this settings folder?

Thanks

_______

Hi there,
You click on "System>Admin>Software Sources"
it will ask for your password then another window will open, click on the tab labelled "Third Party Software" Untick all the boxes. Close then try upgrading.
If that does not work post your sources.list 
```
cat /etc/apt/sources.list
```

---

### Post by jerlinux on 2007-12-13
New rule here:

Don't hit send until you have had at least three cups of coffee.  As soon as I hit the send button, I found the sources from settings > repositories in synaptic.  I would have sent this message sooner but my machine was updating to Gutsy.  It looks like everything worked fine.  Thanks.

---

