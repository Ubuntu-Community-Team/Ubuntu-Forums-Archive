---
title: "Extracting the upgrade failed"
date: 2011-05-23
forum: Installation &amp; Upgrades
---

### Post by Rob George on 2011-05-23
Hi.

I have been running Handy Heron for 2 years, and finally got round to attempting an upgrade.

In the Update manager there is an invitation to upgrade to 10.04.1 LTS.  

When I press the "upgrade" button I get a page of release notes and a further upgrade button.  I press that and get the message:

[SIZE=3]"Failed to extract. : Extracting the upgrade failed.  There may be a problem with the network or the server"[/SIZE]

I know there is no problem with the network or the server because I have just used the same screen to do the normal routine updates.

I have had the same negative result on about 10 tries over 24 hours.  I have also tried changing the server by means of opening the Synaptic Package manager.  I am sure that this action will also change the server for the Update manager, because, when I switch server from "Australia" to "Main Server", the download speed changes within the update manager.

Can anyone give me advice about this problem, or perhaps tell me how to report the fault to whomever it might concern.

---

### Post by zvacet on 2011-05-24
Is Hardy up-to-date?Just for check run 

```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
```

Remove all third party repos if you have them.Try again and post again if you run in troubles.

---

### Post by Rob George on 2011-05-24
Thank you zvacet for replying to my post.

I think that Hardy is completely up to date.  Surely that is what the Update manager is for; and indeed I have run it repeatedly recently.

I tried your command line suggestion and this caused a new mystery.  I got many messages of the form:

"Failed to fetch <some url>.  Could not resolve 'proxy.cyber.com.au' " 

 The end result was no updates or upgrades or package removals or anything.

But I know that doing an update via the Update manager does succeed in downloading and installing files.  It seems to know how to get through the proxy.  (These are matters I don't understand.)

Whatever... I don't think that is the problem.  It looks more like some problem with the actual upgrading program in the archive, given that normal updates work fine.

Or could it be that when and only when doing an upgrade, one must in some way avoid the proxy.  IE the update manager might know how to get updates but not how to get the upgrade.

By the way, what are "third party repos"?   Are they non-Ubuntu programs?

Regards, Rob George

---

### Post by zvacet on 2011-05-24
If you are getting messages like 

**"Failed to fetch <some url>. Could not resolve 'proxy.cyber.com.au' "**

you have problem.If you can avoid proxy do it.I´m sure you will find something about upgrading behind proxy on this forum.I never did it so I can not help you with that,but if you can avoid proxy then it will be standard (let call that way) procedure.
Third party repos are **Medibuntu**(for example) or other repos you added to your sources list.Source list without third party repos look like this one

> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
#deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
#deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---

### Post by Rob George on 2011-05-24
Thank-you again, zvacet

I will follow your suggestion, viz to research on how to upgrade behind a proxy.  Meanwhile the first link in your attached quote, which was simply to [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) has  been very informative.

It looks like I'm going to have to learn something about command line methods.  (which I have been long avoiding)

Regards, Rob George

---

### Post by mörgæs on 2011-05-24
If you have tried 10 times already, you could consider a fresh install. This will also give you GRUB 2 automatically, whereas an upgrade (if it succeeds) will remain on GRUB 1.

---

### Post by Rob George on 2011-06-02
Thanks again to both respondents.

The upgrade has now been successful.

The reason that i could not get the upgrade while I had previously done numerous successful updates was as follows.

1) Neither I nor the company which set up my system for me knew that they had inadvertently left their own proxy in a file called:  apt.conf which is found in  /etc/apt.  This configuration file is used by apt and, I believe, the synaptic package manager and the Update programs both use apt.  So unbeknownst to them, I had been getting all my updates through their proxy.

2) By an annoying coincidence, that company was running maintenance in just exactly the 24 hours during which I was attempting to upgrade.  I found all this out when I rang them to ask for telephone help.

They gave me the instructions for removing the proxy used by apt.

First make a safe copy
sudo cp -p /etc/apt/apt.conf /etc/apt/apt.coonf-20110526

Then edit the apt.conf file.  In GEDIT you just find the line referring to the offending proxy, and just delete it, and save changes.  In my case there was only one line.
sudo gedit /etc/apt/apt.conf &

These instructions worked, and I was able to upgrade.

Regards Rob George

---

