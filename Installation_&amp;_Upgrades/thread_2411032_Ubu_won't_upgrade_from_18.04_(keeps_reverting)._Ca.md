---
title: "Ubu won't upgrade from 18.04 (keeps reverting). Can't &quot;upgrade&quot; from ISO either. Help"
date: 2019-01-23
forum: Installation &amp; Upgrades
---

### Post by Mugsy323 on 2019-01-23
I have Ubuntu 18.04 installed and working with all my programs installed & configured.

For some reason, Ubuntu refuses to install the upgrade (18.10). I *can* install updates to 18.04 just fine, but every time I try to upgrade to 18.10, it fails and reverts back to 18.04.

Steps I've tried:

(Naturally) Performing the upgrade from the desktop.
Booting into the Recovery Console and performed a filecheck and dpkg repair (which required Network access to complete) then trying to upgrade from the Desktop again.
Booting the ISO from a flashdrive, but the only options are "Erase", "Erase Disk", and "Other" (which only offers repartitioning. No "repair" option.)

Is there a way to "fix" Ubuntu 18.04 so it'll properly upgrade, or install 18.10 without destroying my current configuration? TIA

---

### Post by CatKiller on 2019-01-23
Without more information about where it's failing, we can't help you diagnose a fix.

However, I'd advise against upgrading to 18.10 in any case. 18.04 is a Long Term Support release, whereas upgrading to 18.10 would keep you on the upgrade treadmill until 2020.

---

### Post by Mugsy323 on 2019-01-23
> **CatKiller said:**
> Without more information about where it's failing, we can't help you diagnose a fix.

Thx for the reply. I grabbed a couple of screenshots:

It screen sits on this for ten minutes before failing.

[ATTACH=CONFIG]282301[/ATTACH]

[ATTACH=CONFIG]282302[/ATTACH]

---

### Post by monkeybrain20122 on 2019-01-23
But why would you anyway? 18.04 is a LTS, 18.10 has only 9 month support and probably has more bugs and most of which won't be fixed in the cycle. In any case, forget about "upgrade", if you DO want 18.10, back up your data and do a clean install, save you lots of headaches. 

P.S. Your problem is probably caused by third party sofware like proprietary driver or ppa, but TBH I don't really care to look into it, either stay with 18.04 or do a clean install is my suggestion.

---

### Post by Mugsy323 on 2019-01-24
I reported a couple of bugs in 18.04 about 6-8 months ago to the Ubuntu Launchpad page that drive me nuts. They confirmed it and I wanted to see they were ever fixed.

I'm also concerned that if I can't upgrade from 18.04, will I be able to upgrade to ANY future version?

---

### Post by coffeecat on 2019-01-24
> **Mugsy323 said:**
> I'm also concerned that if I can't upgrade from 18.04, will I be able to upgrade to ANY future version?

Did you notice this from monkeybrain20122?

> **monkeybrain20122 said:**
> P.S. Your problem is probably caused by third party sofware like proprietary driver or ppa

Or this from your second screenshot?

> Unofficial software packages not provided by Ubuntu

That's what I would put my money on for the underlying reason for your problem. And, yes, if this is so it would prevent you from upgrading 18.04 to 20.04 when the 20.04 LTS is released next year. If you are really determined to upgrade to 18.10, then you need to post more information about your software sources so that forum members can help you. A start would be the output of these two terminal commands:

```
cat /etc/apt/sources.list
ls -l /etc/apt/sources.list.d/
```

I have to say that I agree with what monkeybrain20122 and CatKiller advise. You are trying to escape a couple of bugs in the LTS 18.04 by upgrading to an interim 9-months support only release which is far less likely to have bugs resolved. Not a good idea in view of your stated reason, imo.

---

### Post by slickymaster on 2019-01-24
@Mugsy323:

Please do not post large images into your posts. Many of our users have slow internet connections and data limits. Large images can take a long time to load -- and may even cost a user extra money. Use the attachment functionality provided by the paperclip button above the text entry box.

---

### Post by Mugsy323 on 2019-01-24
> **coffeecat said:**
> Did you notice this from monkeybrain20122?

Or this from your second screenshot?

That's what I would put my money on for the underlying reason for your problem. And, yes, if this is so it would prevent you from upgrading 18.04 to 20.04 when the 20.04 LTS is released next year. If you are really determined to upgrade to 18.10, then you need to post more information about your software sources so that forum members can help you. A start would be the output of these two terminal commands:

If your question is "are you ignoring what people post", then No. :(

I can check for the bug fixes simply by running the iso, so that's not my top concern (though I would like to have those fixes if they were made.)

My top concern is not having the ability to upgrade *at all* to any future version due to some corruption that needs to be fixed.

Attached are the results of the two requested terminal commands:

> **slickymaster said:**
> @Mugsy323:
Please do not post large images into your posts. Many of our users have slow internet connections and data limits. Large images can take a long time to load -- and may even cost a user extra money. Use the attachment functionality provided by the paperclip button above the text entry box.

The first image is < 3M. The second is only 32K. I doubt either pose a strain on anyone's Data Limits.

```
# deb cdrom:[Ubuntu 18.04 LTS _Bionic Beaver_ - Release amd64 (20180426)]/ bionic main restricted
# deb cdrom:[Ubuntu 17.04 _Zesty Zapus_ - Release amd64 (20170412)]/ zesty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ bionic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ bionic universe
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu zesty partner

deb http://security.ubuntu.com/ubuntu bionic-security main restricted
deb http://security.ubuntu.com/ubuntu bionic-security universe
deb http://security.ubuntu.com/ubuntu bionic-security multiverse

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu bionic partner

# deb-src http://security.ubuntu.com/ubuntu bionic-security main restricted
# deb-src http://security.ubuntu.com/ubuntu bionic-security universe
# deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse
# deb https://dl.winehq.org/wine-builds/ubuntu/ bionic main
```

```
total 72
-rw-r--r-- 1 root root  73 Jan 22 15:23 commendsarnex-ubuntu-winedri3-bionic.list
-rw-r--r-- 1 root root  73 Jan 23 20:51 commendsarnex-ubuntu-winedri3-bionic.list.distUpgrade
-rw-r--r-- 1 root root  73 Oct 19 15:30 commendsarnex-ubuntu-winedri3-bionic.list.save
-rw-r--r-- 1 root root 191 Jan 22 15:23 google-chrome.list
-rw-r--r-- 1 root root 191 Jan 23 20:51 google-chrome.list.distUpgrade
-rw-r--r-- 1 root root 191 Oct 19 15:30 google-chrome.list.save
-rw-r--r-- 1 root root  71 Jan 22 15:23 graphics-drivers-ubuntu-ppa-bionic.list
-rw-r--r-- 1 root root  71 Jan 23 20:51 graphics-drivers-ubuntu-ppa-bionic.list.distUpgrade
-rw-r--r-- 1 root root  71 Oct 19 15:30 graphics-drivers-ubuntu-ppa-bionic.list.save
-rw-r--r-- 1 root root   0 Oct  4 22:19 home:strycore.list
-rw-r--r-- 1 root root   0 Oct  4 22:19 home:strycore.list.save
-rw-r--r-- 1 root root  73 Jan 22 15:23 oibaf-ubuntu-graphics-drivers-bionic.list
-rw-r--r-- 1 root root  73 Jan 23 20:51 oibaf-ubuntu-graphics-drivers-bionic.list.distUpgrade
-rw-r--r-- 1 root root  73 Oct 19 15:30 oibaf-ubuntu-graphics-drivers-bionic.list.save
-rw-r--r-- 1 root root   0 Oct  4 22:15 paulo-miguel-dias-ubuntu-pkppa-bionic.list
-rw-r--r-- 1 root root   0 Oct  4 22:15 paulo-miguel-dias-ubuntu-pkppa-bionic.list.save
-rw-r--r-- 1 root root 173 Jan 22 15:23 plexmediaserver.list
-rw-r--r-- 1 root root 173 Jan 23 20:51 plexmediaserver.list.distUpgrade
-rw-r--r-- 1 root root 173 Oct 19 15:30 plexmediaserver.list.save
-rw-r--r-- 1 root root   0 Oct  4 22:14 relan-ubuntu-exfat-bionic.list
-rw-r--r-- 1 root root   0 Oct  4 22:14 relan-ubuntu-exfat-bionic.list.save
-rw-r--r-- 1 root root 150 Jan 22 15:23 yannubuntu-ubuntu-boot-repair-bionic.list
-rw-r--r-- 1 root root 150 Jan 23 20:51 yannubuntu-ubuntu-boot-repair-bionic.list.distUpgrade
-rw-r--r-- 1 root root 148 Oct 19 15:30 yannubuntu-ubuntu-boot-repair-bionic.list.save


```

---

### Post by coffeecat on 2019-01-24
> **Mugsy323 said:**
> If your question is "are you ignoring what people post", then No. :(

Sigh. No, that was not my question. I was trying to focus you on what might be the underlying problem.

> **Mugsy323 said:**
> I can check for the bug fixes simply by running the iso, so that's not my top concern (though I would like to have those fixes if they were made.)

I think you are missing the point of what is being said. Running the ISO simply allows you to check what is already an out-of-date state of the operating system at its release. You can check for the bugs that are affecting you now in 18.04, but you won't be able to exclude bugs that might get introduced with updates. By their very nature, interim releases are more likely to get bugs that are never fixed.

> **Mugsy323 said:**
> My top concern is not having the ability to upgrade *at all* to any future version due to some corruption that needs to be fixed.

Indeed, that is exactly what I was trying to determine by looking at your repository sources

> **Mugsy323 said:**
> The first image is < 3M. The second is only 32K. I doubt either pose a strain on anyone's Data Limits.

Cut the sarcasm please. By posting large images, you are also being inconsiderate of those using mobile devices to view the forum. There are many who do. I see that you decided to post your terminal outputs as text file attachments.  It is far more convenient for those helping you to post complete text outputs between code tags, rather than attach text files that have to be downloaded and read in a text editor. For the sake of anyone else who might wish to help you, I have added your two text files within code tags for easier reading in your post.

And they confirm possible causes for your problem. In the first - your main sources.list - you have a residual line for the Zesty (17.04) partner repository. That could be as issue.

And then there are the 3rd party repositories. Oh dear, oh dear, oh dear. There are far more than I would tolerate on any of my systems. The more 3rd party repositories you have, the more likely you are to encounter package version conflicts and the sort of problem you are seeing now. I wouldn't know where to begin with that lot, but the one that springs out for me is relan-ubuntu-exfat-bionic.list. Why have a ppa for exfat when there is a perfectly good set of exfat packages in the Universe repository? Perhaps others will see things in that list that may also need dealing with.

---

### Post by CatKiller on 2019-01-24
> **Mugsy323 said:**
> I reported a couple of bugs in 18.04 about 6-8 months ago to the Ubuntu Launchpad page that drive me nuts. They confirmed it and I wanted to see they were ever fixed.

If a fix has been released, it will say so on the bug tracker where you reported the bug. You'll then likely be able to just upgrade those packages to see if the released fix solves whatever the bug is. 

Upgrading everything on the off-chance, and losing out on support, doesn't seem like the best approach to me. 

> I'm also concerned that if I can't upgrade from 18.04, will I be able to upgrade to ANY future version?

I concur with the others, and the information you got at the time, that it's likely to be all the packages from all the PPAs that are causing the package manager problems.

When the time comes to upgrade, the command *ppa-purge* (which isn't installed by default) will remove the packages installed from a given PPA and put them to the version you'd have had from the standard repositories. That should help with whichever ones have been blocking the previous upgrade attempts.

---

