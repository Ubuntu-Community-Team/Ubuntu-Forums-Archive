---
title: "Firefox Snap removes non-snap version of Firefox without permission"
date: 2022-08-19
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2022-08-19
I did not do anything but turn on my PC after shutting down earlier and restarting in a new location.  I had removed snap version of Firefox several days ago, and installed non-snap version using instructions on this forum from mozilla team PPA.

Someone or something removed the mozilla ppa from my PC.  I am only one with access to my PC.

What do I need to do to keep Ubuntu, Canonical, or whomever from forcing snap on me?  It kills part of Studio Pro PDF editor.

John

---

### Post by #&amp;thj^% on 2022-08-19
That is kind of mind blower:
 ```

Latest updates

    firefox-esr 16 hours ago
    Successfully built
    firefox-esr 16 hours ago
    Successfully built
    firefox-esr 16 hours ago
    Successfully built
    firefox-esr 16 hours ago
    Successfully built
    firefox-esr 16 hours ago
    Failed to build: arm64 s390x


```
Here's a few ways: <Snip> Bad info
Please refer to oldfred's post #6

---

### Post by vanadium on 2022-08-20
The link given above is almost complete nonsense. Use [this guide](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04) or others available on the web to install the deb version from Mozilla Team PPA *and* make sure that an upgrade will never replace it with the snap version.

---

### Post by #&amp;thj^% on 2022-08-20
> **vanadium said:**
> The link given above is almost complete nonsense. 
How So? >> nonsense<<
And just to be clear your link is the preferred method here in UF and possibly AU as well.
I'm going off the assumption that the OP, used that method already. I could be mistaken though.

---

### Post by &amp;KyT$0P# on 2022-08-20
@cigtoxdoc Please post the output from running these commands in Terminal -
```
GREP_COLORS='ms=:mc=' grep --color=auto -i -P -n '^\s*[^#\s]' /etc/apt/sources.list /etc/apt/sources.list.d/*.list
for i in /etc/apt/preferences.d/*;do echo " -- $i --";cat "$i";done
```

@1fallen
> **1fallen said:**
> How So? >> nonsense<<

 - Their method #1 does not install Firefox, but installs an installer for the snap package of Firefox, and does not say anywhere that this will give you a snap Firefox.

 - Their method #2 points to a PPA that is **not** the actual Ubuntu Mozillateam PPA, but claims it's official.  And that PPA doesn't even have Firefox for Jammy! ](*,)

 - Their method #4 overcomplicates the use of the official tar.bz2 from Mozilla and suggests a pointless and ephemeral moving of a file from the .deb version of Firefox (the *actual* way to get what they're trying to achieve is to purge the .deb)

 - Under "7. How to update the Firefox Browser", what the heck is [FONT=Courier New]sudo upgrade[/FONT] ?

 - Under "8. Uninstall or Remove Firefox from Ubuntu 22.04", their removal of their PPA method adds the repository again??

---

### Post by oldfred on 2022-08-20
you need the steps 4 & 5 in the omgubuntu link.
Those commands reset priority so ppa is before the snap.

I have had no issues when following those instructions. And ppa is lot easier than downloading a .deb.

Remove snap Firefox & use ppa
[https://www.kubuntuforums.net/forum/general/documentation/how-to-s/662503-how-to-set-priority-for-a-ppa-i-e-using-firefox-without-snapd](https://www.kubuntuforums.net/forum/general/documentation/how-to-s/662503-how-to-set-priority-for-a-ppa-i-e-using-firefox-without-snapd)
[https://fostips.com/ubuntu-21-10-two-firefox-remove-snap/](https://fostips.com/ubuntu-21-10-two-firefox-remove-snap/)
[https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04)


```
sudo snap remove firefox
sudo add-apt-repository ppa:mozillateam/ppa

echo '
Package: *
Pin: release o=LP-PPA-mozillateam
Pin-Priority: 1001
' | sudo tee /etc/apt/preferences.d/mozilla-firefox

echo 'Unattended-Upgrade::Allowed-Origins:: "LP-PPA-mozillateam:${distro_codename}";' | sudo tee /etc/apt/apt.conf.d/51unattended-upgrades-firefox

sudo apt install firefox

```

---

### Post by #&amp;thj^% on 2022-08-20
> **halogen2 said:**
> @cigtoxdoc Please post the output from running these commands in Terminal -
```
GREP_COLORS='ms=:mc=' grep --color=auto -i -P -n '^\s*[^#\s]' /etc/apt/sources.list /etc/apt/sources.list.d/*.list
for i in /etc/apt/preferences.d/*;do echo " -- $i --";cat "$i";done
```

@1fallen


 - Their method #1 does not install Firefox, but installs an installer for the snap package of Firefox, and does not say anywhere that this will give you a snap Firefox.

 - Their method #2 points to a PPA that is **not** the actual Ubuntu Mozillateam PPA, but claims it's official.  And that PPA doesn't even have Firefox for Jammy! ](*,)

 - Their method #4 overcomplicates the use of the official tar.bz2 from Mozilla and suggests a pointless and ephemeral moving of a file from the .deb version of Firefox (the *actual* way to get what they're trying to achieve is to purge the .deb)

 - Under "7. How to update the Firefox Browser", what the heck is [FONT=Courier New]sudo upgrade[/FONT] ?

 - Under "8. Uninstall or Remove Firefox from Ubuntu 22.04", their removal of their PPA method adds the repository again??

Thanks halogen2, that makes perfect sense to me. I'll no longer point to that site. ;)
I'll get ahold of Heyan Maurya and let him know those instruction's are now deemed nonsense. :) (I'll say it with proper verbiage though)
Plain to see I'm at times a bit out of touch with Ubuntu now days.

---

### Post by dcroxton on 2022-08-20
Thanks to the people who responded to this post, hopefully it will solve my problem.  I figured out how to re-install a functioning Firefox (I need a non-snap version for some extensions) a while back, but I have been having to reinstall it with increasing frequency recently.  Whatever monster came up with the idea of reinstalling the snap version without warning is evil.

---

### Post by cigtoxdoc on 2022-08-20
Thank you very much for your help.

Sorry for delay in replying.  I have been attending a scientific conference, so just getting back to email.  Several hours after my first report, I removed snap version and reinstalled non-snap version.

For the security gurus, I may not have fully removed snap version, but there is a BIG HOLE in the security of Ubuntu 22.04 when anyone and/or anything can change repositories WITHOUT EXPRESSED AUTHORIZATION FROM THE SYSTEM OWNER.

The terminal output you requested is in the attached PDF file.

John

---

### Post by Holger_Gehrke on 2022-08-20
> **cigtoxdoc said:**
> 
For the security gurus, I may not have fully removed snap version, but there is a BIG HOLE in the security of Ubuntu 22.04 when anyone and/or anything can change repositories WITHOUT EXPRESSED AUTHORIZATION FROM THE SYSTEM OWNER.


Actually, if you don't have an apt configuration that pins Firefox to the origin from the ppa, you have given implicit permission. apt searches for newer versions and the pseudo-deb in the Ubuntu repositories is always considered newer than the same version from the ppa because it has some additional letters at the end of the version number. That pseudo deb then proceeds to install the snap. The script posted by oldfred basically tells apt to consider the firefox from the ppa to be the only choice.

Holger

---

### Post by &amp;KyT$0P# on 2022-08-20
> **cigtoxdoc said:**
> The terminal output you requested is in the attached PDF file.

You do have the Mozillateam PPA enabled and your pinning files should work.  You can verify the pins by running
```
apt-cache policy
```
and to check which Firefox apt wants to install -
```
apt-cache policy firefox
```

Are you still having the issue that the Mozillateam PPA and/or the Firefox deb from there is still being automatically removed?

> **Holger_Gehrke said:**
> apt searches for newer versions and the pseudo-deb in the Ubuntu repositories is always considered newer than the same version from the ppa because 

... its [version's epoch]("https://www.debian.org/doc/debian-policy/ch-controlfields.html#s-f-version") is later than that of the packages in the Mozillateam PPA.

---

### Post by cigtoxdoc on 2022-08-23
So far, whatever I have done has kept snap-Firefox from coming back.

I really would like to know how to protect my application software from being upgraded or deleted without my permission.

John

---

