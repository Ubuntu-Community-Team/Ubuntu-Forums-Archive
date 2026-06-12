---
title: "Lubuntu Lucid Alpha 3 fails to install"
date: 2010-03-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by auh2o on 2010-03-18
Is it ok to ask a question about Lubuntu here even though it's not officially maintained yet? I thought I'd give the latest release a try on a low-spec laptop, but about 50% into the installation process, it fails. Screenshot included of the info; I don't know what to make of it. I checked the md5sum of the iso before installing, and have tried twice with the same result. Should I write it off as being alpha-related? Should I maybe file a bug report on Launchpad? But I don't know what the bug would be, exactly. I'd appreciate some input.

---

### Post by phillw on 2010-03-18
Hi,

The beta1 for all the 10.04 families are due today.

Lubuntu can lag 24 hours behind, the image will be available from [https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)  soon !

You can catch the team on IRC channel #lubuntu, details can be gotten from the the above wiki page.

I've not seen that error, I'll update this thread once the beta1 is posted and ask if anyone else has seen it.

/edit one of the people on #lubuntu has had a look at the thread, and, apart from waiting for the beta1 as it is unclear if you checked just the image as downloaded, or the written cd suggests that you run an md5checksum on the cd you're trying to install from. I'd add that ensure you burnt the cd @ 4X speed, not at something like 48X, as this is known to cause issues for some.



Regards,

Phill.

---

### Post by RTrev on 2010-03-18
Something I see asked often, but answered in varying ways, is whether it's a good idea to do a clean reinstall when moving from the alphas to the first beta, and also from beta to beta, and beta to final.  Some say yes, some say no.  Does anyone know of a decisive answer?  TIA

---

### Post by phillw on 2010-03-18
Hi RTrev,

You can run all the way from the pre-alpha release to full release by updating. Full re-installs are only for if you have 'tweaked' things to deal with a know bug and want to confirm that bug has been solved.

The 'definitive' answer (or as near as you'll get) can be found here --> [http://ubuntuforums.org/showthread.php?t=1343449](http://ubuntuforums.org/showthread.php?t=1343449)

That forum is also where Lucid-Testing is.

Regards,

Phill.

---

### Post by RTrev on 2010-03-18
Ahah.. the mother lode!  Thanks Phill!

---

### Post by auh2o on 2010-03-18
Phil, thanks for the reply. I did check both the iso file before burning, and then ran a test on the disk after the first installation attempt failed. No errors. I attempted a clean installation on an empty drive. But I'll toss the alpha disc and have another go when the beta is out!

---

### Post by phillw on 2010-03-19
The beta is out :-)

Regards,

Phill.

---

### Post by auh2o on 2010-03-20
Thanks Phill, I have downloaded and installed it. Everything went flawless and just as intended this time, or at least that's how it appeared until after I restarted when the installation was done... Then I got the message included as a photo below. Message will repeat upon keypress.

My knowledge on the subject is limited, but it seems like a Grub problem, does it not? Is it something I can rectify by going into recovery mode from the Live CD? I don't know what might've caused this; I did a clean install with all default options.

---

### Post by phillw on 2010-03-20
> **auh2o said:**
> Thanks Phill, I have downloaded and installed it. Everything went flawless and just as intended this time, or at least that's how it appeared until after I restarted when the installation was done... Then I got the message included as a photo below. Message will repeat upon keypress.

My knowledge on the subject is limited, but it seems like a Grub problem, does it not? Is it something I can rectify by going into recovery mode from the Live CD? I don't know what might've caused this; I did a clean install with all default options.

I've seen that error in a thread before, let me go see if I can find it for you.

Regards,

Phill.

---

### Post by phillw on 2010-03-20
Hi,

there seem to be a couple of possibilities

1) You installed over an older version of ubuntu without erasing the hard drive and have the old grub left on.

2) Grub is, whatever reason, confused.

Try re-installing grub --> Section 13 of this HowTo --> [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

I've seen it gotten around by manually editing some of the grub stuff, but I think a re-install of grub should sort it.

Post back how you get on.

Regards,

Phill.

---

### Post by auh2o on 2010-03-20
> **phillw said:**
> Hi,

there seem to be a couple of possibilities

1) You installed over an older version of ubuntu without erasing the hard drive and have the old grub left on.

2) Grub is, whatever reason, confused.

Try re-installing grub --> Section 13 of this HowTo --> [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

I've seen it gotten around by manually editing some of the grub stuff, but I think a re-install of grub should sort it.

Post back how you get on.

Regards,

Phill.

Well, I did install it on top of the failed alpha installation, but I assumed the option to use the whole drive and the subsequent partitioning would wipe out any trace of it. I will reinstall Grub and report back. Thank you for your help!

---

### Post by phillw on 2010-03-20
> **auh2o said:**
> Well, I did install it on top of the failed alpha installation, but I assumed the option to use the whole drive and the subsequent partitioning would wipe out any trace of it. I will reinstall Grub and report back. Thank you for your help!

Evidently, unless you choose 'erase disk' the MBR stays there, that would account for a thoroughly confused GRUB ;-)

(Keeps fingers crossed that is the issue)

Regards,

Phill.

---

### Post by kansasnoob on 2010-03-20
Are you able to run any Debian based Live CD on that machine? Even Damn Small Linux? Maybe Knoppix?

I know Damn Small is in a bit of a quandary right now but it could be useful. I'm particularly curious about the system specs and thought it could be useful to see the output of the following:

```
cat /proc/meminfo
```

```
cat /proc/cpuinfo
```

---

### Post by kansasnoob on 2010-03-20
> **phillw said:**
> Evidently, unless you choose 'erase disk' the MBR stays there, that would account for a thoroughly confused GRUB ;-)

(Keeps fingers crossed that is the issue)

Regards,

Phill.

That really shouldn't be true if you choose to install the new grub to the mbr.

Edit: From what I've seen there is no "alternate install" for Lubuntu yet. (Could be wrong)! And I'm thinking a text based install is needed.

I haven't looked to see if there's a minimal install of Ubuntu yet.

---

### Post by phillw on 2010-03-20
> **kansasnoob said:**
> Are you able to run any Debian based Live CD on that machine? Even Damn Small Linux? Maybe Knoppix?

I know Damn Small is in a bit of a quandary right now but it could be useful. I'm particularly curious about the system specs and thought it could be useful to see the output of the following:

```
cat /proc/meminfo
```

```
cat /proc/cpuinfo
```

I've seen a few threads on it, [http://ubuntuforums.org/showthread.php?t=1284332&page=3](http://ubuntuforums.org/showthread.php?t=1284332&page=3) and [http://ubuntuforums.org/showthread.php?t=1344402](http://ubuntuforums.org/showthread.php?t=1344402) being two - they all seem to point back to a confused grub, others have solved it by wiping the disk & re-installing, hence my thinking it  is a grub confused error.

Phill.

---

### Post by kansasnoob on 2010-03-20
> **phillw said:**
> I've seen a few threads on it, [http://ubuntuforums.org/showthread.php?t=1284332&page=3](http://ubuntuforums.org/showthread.php?t=1284332&page=3) and [http://ubuntuforums.org/showthread.php?t=1344402](http://ubuntuforums.org/showthread.php?t=1344402) being two - they all seem to point back to a confused grub, others have solved it by wiping the disk & re-installing, hence my thinking it  is a grub confused error.

Phill.

Quite possible. Where I was going with wanting to know if the OP could run any Debian based "Live Desktop" (including Lubuntu) on that machine is that we could get a look at both system specs and then the output of the Boot Info Script:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by auh2o on 2010-03-20
Well, I reinstalled Grub from the Live CD. In terminal: "Installation finished. No error reported."

However, upon rebooting, the same problem remains.

I will reformat & wipe the drive completely and then try again from scratch. However, that will have to wait until tomorrow.

Kansasnoob - > Yes, I can run the Lubuntu Live CD just fine. I will give you the output of those commands tomorrow. No more time right now, I'm afraid.

---

### Post by phillw on 2010-03-20
> **auh2o said:**
> Well, I reinstalled Grub from the Live CD. In terminal: "Installation finished. No error reported."

However, upon rebooting, the same problem remains.

I will reformat & wipe the drive completely and then try again from scratch. However, that will have to wait until tomorrow.

Kansasnoob - > Yes, I can run the Lubuntu Live CD just fine. I will give you the output of those commands tomorrow. No more time right now, I'm afraid.

auh2o, before you do the erase, could you run and post the output of the scripts Kansasnoob is asking for, it may well help in tracking down why it has happened.

And then, if you'd be so kind, would you do this --> [http://forum.phillw.net/viewtopic.php?f=4&t=35](http://forum.phillw.net/viewtopic.php?f=4&t=35)

That thread does do as it says, I'd just like to know, for future reference if it can solve this issue. It's a bit more drastic than re-installing grub, but a lot less drastic than a full erase and install.

Thanks,

Phill.

---

### Post by auh2o on 2010-03-21
Phill, reinstalling the kernel and updating Grub didn't help.

I found this thread, which describes the exact same error I got:

[http://ubuntuforums.org/showthread.php?t=1337254](http://ubuntuforums.org/showthread.php?t=1337254)

Apparently not all that uncommon (on some hard drives on some laptops). In any case my problem does not seem to be related specifically to the Lubuntu beta.

I have booted with a floppy of Gujin instead of the faulty Grub, and Lubuntu works just fine after that. I will study that thread and see if the solutions presented solve my problem, instead of reinstalling.

---

### Post by phillw on 2010-03-21
if you are on a thread with drs305 answering questions, you are in very good hands :D

Had you not found that thread, I'd have been sending him a PM for advice. There's a couple of the guyz really clued up with grub.

Leave a note on there of where you're upto if you get stuck, drs305 does keep an eye on the threads.

Regards,

Phill.

---

### Post by xebian on 2010-03-21
Looks like it's only 32-bit?  When will the 64-bit edition available?  I know i can install from the repo but this may not be good considering there isn't a 64-bit beta.

---

### Post by phillw on 2010-03-21
> **xebian said:**
> Looks like it's only 32-bit?  When will the 64-bit edition available?  I know i can install from the repo but this may not be good considering there isn't a 64-bit beta.

From memory, as lubuntu is for "older, small RAM'd" machines, I don't think they're working on a 64 bit version. I could be wrong, though.

> Lubuntu is targeted at "normal" PC users running on low-spec hardware. Such users may not know how to use command line tools, and in most cases they just don't have enough resources for all the bells and whistles of the "full-featured" mainstream distributions.

A Pentium II or Celeron system with 128 Mb RAM is probably a bottom-line configuration that may yield slow yet usable system with Lubuntu. It should be possible to install and run Lubuntu with less memory, but the result will likely not be suitable for practical use.

Regards,

Phill.

---

### Post by auh2o on 2010-03-22
I'm marking this as solved! It is indeed a [**bug**]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/403408"), but with the information given in the other thread I straightened it out. It was as stated a problem with the* UUID* line in grub.cfg. A solution can be found [**here**]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search"). Thanks for your input, everyone!

---

