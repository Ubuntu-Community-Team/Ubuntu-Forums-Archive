---
title: "Various Issues after gutsy upgrade (fan, synaptic, update, evolution)"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by seul on 2007-10-23
I upgraded from ubuntu feisty to gutsy yesterday using the update manager. Unfortunately there is little good (Belkin Wireless finally works) and loads of bad news ever since. The trouble is this:

1. My fan is continously working at top speed

2. The desktop experience is quite slow, too. Not incredibly slow, but just like trying to walk under water (no effects enabled). It is slow when connected to internet both wired and wireless and when not connected

3. I can connect to websites using firefox, however it is very slow (with iPv6 disabled in FF), sometimes close to 56k experience (this being the reason for posting after not too extensive a search in the forum, if I missed anything that is already there: my apologies, I couldn't get to it)
Trying to watch a video on youtube it loaded pretty quickly but only played in intervals (1 sec play - 1sec stop - 1 sec play - etc ad fin.)
BUT: Although Firefox does connect, Evolution does not

4. Synaptic only shows some 1500 packages available. I got a new sources.list through source-o-matic, on trying to reload, synaptic doesn't connect, it just keeps saying "downloading file 1 of 17" but nothing ever happens. I tried to change the location from Ireland to main to uk, no success

5. update manager: It showed 66 available updates, then it read "fetching file 1 of 66" but in the  progress window one "failed" after another appeared. After fetching the new sources.list it says "your system is up to date", but there is still the update notifier in the task bar

For 3-5: It does not make a difference whether I connect wireless or plug the machine into the router.

Again, if I missed a post addressing the same problems, sorry, but it is just so slow. Any help appreciated and thanks for the support in advance.


**update**
When I switch my machine on, I get 5 ubuntu options for booting:
- Ubuntu 7.10, Kernel 2.6.22-14-generic
- Ubuntu 7.10, Kernel 2.6.22-14-generic (recovery mode)
- Ubuntu 7.10, Kernel 2.6.20-16-generic
- Ubuntu 7.10, Kernel 2.6.20-16-generic (recovery mode)
- Ubuntu 7.10, memtest 86+

I don't know what they mean, but all of the above problems occurred on Ubuntu 7.10, Kernel 2.6.22-14-generic. When I boot into Ubuntu 7.10, Kernel 2.6.20-16-generic, it is different:
1. The Fan is pretty relaxed
2. Desktop feels like walking on solid ground again.
3. Firefox is back to the speed I experienced with Feisty and the youtube video plays all right, however, Evolution still does not connect
4. Synaptic shows 23000+ packages listed, but on a reload still nothing happens -- update: Synaptic managed to reload and is now down to 1500+ packages (with original sources.list)
5. Update manager still shows 66 updates available with the original sources.list and still fails. With the new sources.list, it still says system is up to date.
6. Belkin Card does not work with this kernel


The original sources.list after the update reads like this:

```
]# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main multiverse universe
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

```



The one I fetched from source-o-matic reads like this:

```
# Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)




# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) gutsy main restricted 
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) gutsy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) gutsy universe multiverse 
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) gutsy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe multiverse


deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
```

I believe I have company [here]("http://ubuntuforums.org/showthread.php?p=3610383") and [here]("http://ubuntuforums.org/showthread.php?t=586395")
Since I can't find any ideas anywhere helping to approach the problems, I'll try a clean Install later today. I'll post back if that helped anything

---

### Post by seul on 2007-10-25
Clean install -- same thing: it is slow, it is loud and it sucks. 

On the first boot after installation it was quite, fast and promising -- until around about the moment (though not exactly AT the moment) when I inserted my wireless card. Slowed down and the fan started shrieking again. 
Reboot without the wireless card, disabling network altogether, reboot,... I'm expecting the fan to kick the bucket for good any minute.

Synaptic: does not work, neither with sources.list after clean install nor with one of the two above.

Could somebody be so kind and post a sources.list that definitely works?

---

### Post by seul on 2007-10-25
I don't think the list is the issue. I tried various and it never works.

I also tried the solutions suggested here [http://ubuntuforums.org/showthread.php?t=587225](http://ubuntuforums.org/showthread.php?t=587225) but with no success.

---

### Post by seul on 2007-10-26
Tried openSUSE 10.3 with no luck so I'm back to feisty.

---

### Post by Inbetweener on 2007-10-27
I hade very similar issues when upgrading, fan went haywire, firefox wouldn't start, everything was extremely slow, even opening a picture file would be like browsing the internet in 1998. Backed everything up and did a fresh install, all seems to be working fine now.

---

### Post by seul on 2007-11-30
After buying a new computer and installing gutsy again, I still had the issue that synaptic wouldn't connect. Wille Faler [suggests it is a Router issue]("http://faler.wordpress.com/2007/10/14/ubuntu-linux-710-gutsy-gibbon-on-a-sony-vaio-sz4-xwn/") (DLINK) and also has a workaround via [OpenDNS]("https://www.opendns.com/start?device=ubuntu"). It finally did the trick for me.

---

