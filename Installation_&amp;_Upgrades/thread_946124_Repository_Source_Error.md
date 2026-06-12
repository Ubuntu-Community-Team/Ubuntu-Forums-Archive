---
title: "Repository Source Error"
date: 2008-10-13
forum: Installation &amp; Upgrades
---

### Post by joebrueske on 2008-10-13
I hadn't used my laptop for a while and of course there were updates that needed to be installed. The kernel was updated and I restarted. The next time I ran the update command I received the following error. Bare in mind that this did not happen the first time.
```
W: GPG error: http://apt.wicd.net hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FEC820F4B8C0755A
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/Release.gpg  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/main/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/restricted/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/universe/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg  Could not resolve 'archive.canonical.com'

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2  Could not resolve 'archive.canonical.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-proposed/Release.gpg  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-proposed/restricted/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-proposed/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-proposed/universe/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://tobias.rautenkranz.ch/debian/stable/Release.gpg  Could not resolve 'tobias.rautenkranz.ch'

W: Failed to fetch http://tobias.rautenkranz.ch/debian/stable/en_US.bz2  Could not resolve 'tobias.rautenkranz.ch'

W: Some index files failed to download, they have been ignored, or old ones used instead.
```
On updates doesn't Ubuntu automatically update the repos? Or am I getting this error for a different reason? If these are the wrong repos what are the corrections that I need to make to the file?

Thanks guys

---

### Post by tommcd on 2008-10-13
Post the contents of your /etc/apt/sources.list. Since you use the USA repos your sources list should be the same as mine. I'll post mine just as soon as I reboot into Ubuntu.

---

### Post by joebrueske on 2008-10-13
contents of /etc/apt/sources.list
```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-proposed restricted main multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-proposed restricted main multiverse universe #Added by software-properties
deb http://tobias.rautenkranz.ch/debian stable/
deb http://ppa.launchpad.net/fta/ubuntu hardy main
deb http://apt.wicd.net hardy extras
deb http://us.archive.ubuntu.com/ubuntu hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu hardy universe #Added by software-properties
deb http://wine.budgetdedicated.com/apt hardy main
deb http://security.ubuntu.com/ubuntu/ hardy-security restricted main multiverse universe
deb-src http://security.ubuntu.com/ubuntu/ hardy-security restricted main multiverse universe #Added by software-properties
```

---

### Post by tommcd on 2008-10-13
Here is my sources.list. I don't have the **src** repos enabled. I also don't have all the third party repos you have either. The third party repos are not the problem though. You are having a problem connecting to 'us.archive.ubuntu.com' for some reason.
```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release Candidate i386 (20080417)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports restricted main multiverse universe

```
I just ran "sudo apt-get update" so I know mine works. Perhaps you could try my sources.list. Back up your sources.list first and then replace it with mine. Then just add in the third party repos you have. Or compare mine to yours and look for any differences. As near as I can tell, all of your main Ubuntu repos are pretty much the same as mine, except you have the src repos enabled and I don't.

---

### Post by tommcd on 2008-10-13
After reading your error messages more closely, I think I now see your problem. It is this line in the beginning:
```
 GPG error: http://apt.wicd.net hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FEC820F4B8C0755A

```
 Forget about using my sources.list. The problem is Ubuntu can't resole the GPG public key (or whatever it is called) that verifies the repos for authenticity. See this thread to (hopefully) resolve your problem.
[http://ubuntuforums.org/showthread.php?t=933985&highlight=GPG+error](http://ubuntuforums.org/showthread.php?t=933985&highlight=GPG+error)

---

### Post by joebrueske on 2008-10-13
Yup, that did the trick. Now just the Canonical archives that can't be reached. I don't think it's a big deal. Even if there was a security update in there somewhere, the chances of someone hacking a linux distro is a lot lower than a windows machine.

---

### Post by tommcd on 2008-10-13
Are you still getting error messages? If you are then post them here. Or search these forums for the error messages. THere may be another key you are missing.

---

### Post by joebrueske on 2008-10-13
When I attempt to update the sources list for apt-get, I receive the following error.
```
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg  Could not resolve 'archive.canonical.com'

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2  Could not resolve 'archive.canonical.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
```
I haven't found any solution for it yet.

---

### Post by tommcd on 2008-10-14
Try commenting out the hardy-partner line in your sources.list. And then run "sudo apt-get update". 
Or open synaptic package manager and click on settings > repositories, and uncheck the option for hardy-partner, and then click the reload button, and see if you still get the errors.

You must be still missing a GPG key somewhere. I'm not entirely sure if it is the hardy-partner repo, but since that is part of the error message you posted it can't hurt to try, and you can easily replace it if it doesn't work.

---

### Post by joebrueske on 2008-10-14
The one aspect of computers that I have found challenging is that from day to day the symptoms of a problem change so easily.

I commented out the partner and the tobias deb repo because the update function was getting hung up on that too. While I did that I also went into the Software Sources and changed the option to download from the Main Server instead of Custom Servers. However, that did not make any difference when I uncommented the partner lines, I still received the same error for those repos.

**Edit**

Wait, nope. There it goes! You know what, I think this may have more to do with my wireless connection. I turned my laptop a different direction and it was able to hit and read all the lists in one fowl swoop. My guess is that if I had it hooked up to a hard line I probably wouldn't have gotten those errors.

Yeah, I just ran update again and now it's not hitting any of the servers. lol Wow. Well, it's not critical. Thanks for the help!

---

