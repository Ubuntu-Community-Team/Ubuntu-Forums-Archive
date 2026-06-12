---
title: "Anyone know why acroread is no longer in the repos?"
date: 2009-09-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-09-25
Seems to have gone awol.

---

### Post by LKjell on 2009-09-25
Why do you need it? Isn't evince good enought? Just wonder...

---

### Post by froggyswamp on 2009-09-25
Sorry I don't know, but I'm not missing it, do you? Any particular must-have feature? Just wondering..

---

### Post by philinux on 2009-09-25
Yes, evince still has no firefox plugin and some pdf's usually more complicated ones fail to read properly with evince.

---

### Post by lucazade on 2009-09-25
Use moz-plugger to embed evince into firefox ;)

---

### Post by philinux on 2009-09-25
Nah like I said evince fails with complicated pdfs. Ok for the simple stuff. I'll wait for acroread to reappear.

I tried the force architecture with a 32 deb from adobe but you dont get the plugin for FF.

---

### Post by andrewabc on 2009-09-25
[http://en.wikipedia.org/wiki/Okular](http://en.wikipedia.org/wiki/Okular)
Is supposed to be decent pdf viewer (kde). I use default evince though.

---

### Post by Paqman on 2009-09-25
Acroread isn't in Medibuntu any more, it's in the Canonical Partner Repository:

[https://help.ubuntu.com/community/Medibuntu#Note%20about%20Adobe%20Acrobat%20Reader%20%28acroread%29](https://help.ubuntu.com/community/Medibuntu#Note%20about%20Adobe%20Acrobat%20Reader%20%28acroread%29)

---

### Post by philinux on 2009-09-25
I've got partner enabled in karmic. But no acroread.

---

### Post by LKjell on 2009-09-25
I don't like okular. kpdf and kdvi is much better than okular.. kdvi is best dvi viewer I can find. So we have kpdf, kdvi > evince > okular.

---

### Post by philinux on 2009-09-26
Can anyone answer this? I assume something is going on behind the scenes.

---

### Post by Slug71 on 2009-09-26
I'd like to know this too.

Tried installing the .deb on 64bit will --force architecture and still didnt install. Would be nice to have this back.

---

### Post by Stereotypical Rage on 2009-09-26
I think you can download the acroread deb from Adobe's site though.

---

### Post by philinux on 2009-09-26
> **Stereotypical Rage said:**
> I think you can download the acroread deb from Adobe's site though.

Need the 64 bit. It's in Jaunty but not karmic.

---

### Post by nanog on 2009-09-26
[U]Why acroread is essential.
[/U]

Evince fails to open complex or large pdfs (I have thousands of pdfs that are over 100 megs in size for my work).

Evince is incredibly slow even when it does open large pdfs.

Evince does not allow precise cropping of image and text data from pdfs. This essential in any enterprise environment.

And did I mention its achingly slow at rendering pdfs...

---

### Post by kansasnoob on 2009-09-26
I see it's not present in 64bit:

[http://www.khattam.info/2009/08/20/howto-installing-adobe-reader-9-to-ubuntu-9-10-karmic-koala-alpha-4/](http://www.khattam.info/2009/08/20/howto-installing-adobe-reader-9-to-ubuntu-9-10-karmic-koala-alpha-4/)

also found this (depends on 32bit libs and nspluginwrapper):

[http://packages.medibuntu.org/karmic/acroread.html](http://packages.medibuntu.org/karmic/acroread.html)

Sadly it's a tarball:(

---

### Post by philinux on 2009-09-26
> **kansasnoob said:**
> I see it's not present in 64bit:

[http://www.khattam.info/2009/08/20/howto-installing-adobe-reader-9-to-ubuntu-9-10-karmic-koala-alpha-4/](http://www.khattam.info/2009/08/20/howto-installing-adobe-reader-9-to-ubuntu-9-10-karmic-koala-alpha-4/)

also found this (depends on 32bit libs and nspluginwrapper):

[http://packages.medibuntu.org/karmic/acroread.html](http://packages.medibuntu.org/karmic/acroread.html)

Sadly it's a tarball:(

Yes I found both those. The Medibuntu link to the 64 bit deb gives 404 not found.
[http://packages.medibuntu.org/pool/non-free/a/acroread/acroread_9.1.0-7jaunty2+medibuntu1_amd64.deb](http://packages.medibuntu.org/pool/non-free/a/acroread/acroread_9.1.0-7jaunty2+medibuntu1_amd64.deb)

---

### Post by dinxter on 2009-09-26
i'm not sure why theres no amd64 version in karmic, package seems to build and work fine on karmic, must be some other reason i suppose

---

### Post by philinux on 2009-09-26
> **dinxter said:**
> i'm not sure why theres no amd64 version in karmic, package seems to build and work fine on karmic, must be some other reason i suppose

Could it be a eula thing or branding whatever.

---

### Post by dinxter on 2009-09-26
> **philinux said:**
> Could it be a eula thing or branding whatever.
a change like that would affect a new acroread version across all releases, this is only the dropping of amd64 support in karmic, perhaps theres more trouble than its worth in supporting an acroread 32 bit binary over the ia32 compatibility layer on 64 bit, sounds complicated enough to say it :)

---

### Post by moviemaniac on 2009-09-26
> **LKjell said:**
> Why do you need it? Isn't evince good enought? Just wonder...

I regularly copy+paste whole paragraphs of text from pdf-press releases. The resulting formatting is a nightmare with evince, Acrobat (and I hate to say that because I HATE it having to upgrade it 10 times a year due to vulnerabilities...) works much better for that particular job.

---

### Post by slakkie on 2009-09-26
Haven't looked at all the pages, but I have it, just enable the partner repo, see my sources.list.

```

apt-cache policy acroread
acroread:
  Installed: (none)
  Candidate: 9.1.0-7jaunty2
  Version table:
     9.1.0-7jaunty2 0
        500 http://archive.canonical.com karmic/partner Packages

```

```

# Uncomment deb-src if you really need them

## Keepers
deb http://archive.ubuntu.com/ubuntu/ karmic main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ karmic main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu karmic-security main restricted universe multiverse
#deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted universe multiverse

# Optional, but recommended
deb http://archive.ubuntu.com/ubuntu/ karmic-updates main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ karmic-updates main restricted universe multiverse

# Optional, remove if you don't like them
deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://archive.ubuntu.com/ubuntu/ karmic-proposed main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ karmic-proposed main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

# Medibuntu repositories, check http://www.medibuntu.org/ for more details
deb http://packages.medibuntu.org/ karmic free non-free

## Taskwarrior
# http://taskwarrior.org/projects/show/taskwarrior/
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 11c351db2428f4e244d892565af518810cd6364d
deb http://ppa.launchpad.net/ultrafredde/ppa/ubuntu jaunty main
#deb-src http://ppa.launchpad.net/ultrafredde/ppa/ubuntu jaunty main

# Quicker boot times..
#deb http://ppa.launchpad.net/ubuntu-boot/ppa/ubuntu karmic main
#deb-src http://ppa.launchpad.net/ubuntu-boot/ppa/ubuntu karmic main

```

---

### Post by dudude on 2009-09-26
I would like to use Evince or Okular over Acroread, but I can't seem to open some links in some pdfs that I've gotten before.

But knowing Abobe, the official version of the reader will not support 64 bit for another 5 years and still be buggy.:lolflag:

---

### Post by philinux on 2009-09-27
> **slakkie said:**
> Haven't looked at all the pages, but I have it, just enable the partner repo, see my sources.list.


#9 partner enabled.

---

### Post by philinux on 2009-09-27
[https://bugs.launchpad.net/ubuntu/+source/acroread/+bug/437566](https://bugs.launchpad.net/ubuntu/+source/acroread/+bug/437566)

Would some kind person change the status to confirmed please.

---

### Post by komodojay on 2009-10-05
I enable the Partner repository but it still didn't show up in the Software Center. When I did an apt-get install acroread it found it and installed it fine. Must be a BETA Bug.

---

### Post by rogerdean on 2009-10-05
my synaptic says acroread was installed from archive.canonical.com/main rather than local/partner. installable for me, anyway
cheers

---

### Post by philinux on 2009-10-05
> **komodojay said:**
> I enable the Partner repository but it still didn't show up in the Software Center. When I did an apt-get install acroread it found it and installed it fine. Must be a BETA Bug.

I think it's a 64 bit bug.

---

