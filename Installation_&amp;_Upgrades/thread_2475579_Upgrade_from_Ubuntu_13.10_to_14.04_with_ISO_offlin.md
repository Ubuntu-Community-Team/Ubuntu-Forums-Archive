---
title: "Upgrade from Ubuntu 13.10 to 14.04 with ISO offline without booting off the media"
date: 2022-06-01
forum: Installation &amp; Upgrades
---

### Post by cdslinux on 2022-06-01
I'm trying to upgrade offline due to compatibility reasons on my testing machine. 

I want to upgrade Ubuntu 13.10 to 14.04 LTS offline WITHOUT booting off the media live. This is because the live media upgrade erases things that I want to keep.

I decided that I want to upgrade offline using the Ubuntu 14.04 desktop ISO file inserted.

I have no idea what to do in this case. This would have been easy to do if they still had the alternate CDs, but that's no longer the case.

Can anyone help?

Edit: One may ask "Why can't you just do this online upgrade?" This is because I want to upgrade to the ORIGINAL Ubuntu 14.04 LTS (No point releases like 14.04.1 or 14.04.4 etc.). This can't be done with the online network upgrade. I have the ISO image of the original Ubuntu 14.04 LTS.

---

### Post by adfhnapo on 2022-06-01
I don't know the answer, but may have something that may help.
(its been a long time since 13.10!)

Most of the updates are driven via the apt configuration. I would assume that the distribution upgrade would match this. is it _do-release-upgrade_ that far back?

So i would be trying to manually add the CD to the list of apt sources. you may have an example of the line(s) you need in the current files, if you installed from CD, IIRC.

something like the following:
# deb cdrom:[Ubuntu 14.04.3 LTS _Trusty Tahr_ - Beta amd64 (20150805)]/ trusty main restricted

(without the comment, of course)

---

### Post by sudodus on 2022-06-01
Why are you upgrading to a version of Ubuntu that reached end of life several years ago (April 2019)? There will be no updates, not even security updates. And we (who help here) have forgotten the details about 14.04, so we will not be very good at helping.

---

### Post by cdslinux on 2022-06-01
I have my main Ubuntu machine which is always up to date. However, this testing machine has a program which just does not work with the latest versions.

---

### Post by cdslinux on 2022-06-01
What command would I run next to get the distribution upgrade offline working?

---

### Post by sudodus on 2022-06-01
I see. But why not continue with 13.10? What advantage would there be with 14.04?

---

### Post by cdslinux on 2022-06-01
> **sudodus said:**
> I see. But why not continue with 13.10? What advantage would there be with 14.04?

A new feature with that program only works with 14.04.

---

### Post by sudodus on 2022-06-01
If you are working in a professional context with this program, that needs old Ubuntu versions, maybe you could consider professional help from Canonical, the company, that creates and maintains Ubuntu.

See [this link](https://ubuntu.com/about/release-cycle) and particularly [Ubuntu Advantage subscription](https://ubuntu.com/advantage).

---

### Post by cdslinux on 2022-06-01
The program is not a necessity, but I would like to have that new feature.

---

### Post by sudodus on 2022-06-01
This is beyond my skill. Let us hope that @parcelistsupport or someone else will be able to help you.

---

### Post by ActionParsnip on 2022-06-01
If you have data you want to keep, you have backups.....right?

Reinstall with Ubuntu 22.04 then reinstate the user data using your backups

---

### Post by Impavidus on 2022-06-01
With 13.10 and 14.04 being long dead, you've got a second reason to avoid online upgrades: you should keep both releases offline for security.

When you install Ubuntu, the installer gives you a sources.list file that starts with an entry for the cdrom (which is actually a usb, usually). It will be commented out. That is the repository from where Ubuntu is installed and you may need it after installation to install some additional tools that you may need to get network access. You should be able to make it point to the 14.04 live disk. It will only upgrade the packages present on the live disk, obviously.

You can also try a fresh install and restore your precious files from backups. Maybe you can upgrade by installing (install the new release over the old release without formatting). It works now, but I don't know whether that option existed for 14.04.

Peculiar... A new feature that only works with one specific obsolete release of Ubuntu. With proprietary software you occasionally have such weird things and there's nothing really an end user can do about it. Have you considered a virtual machine?

---

### Post by armadefuego on 2022-06-02
(parcelistsupport, but on my personal account)
Oldest thing i have found, so far is 15.04.
I still have options to check.

---

### Post by MAFoElffen on 2022-06-02
I can understand if it was a disposable VM instance for testing... Or for nostalgic sentiment.

What you have not mentioned is the specific application or feature that you are trying to get... That you think was only available on 14.04(?) You mentioned those separately, as the same.

You can do it, but is some work and skill level on your part. There is no easy way, that I am aware of, to do this for  beginner. 

The Alternate ISO was ended before 14.04 (initial release). So to do offline, you would have to create a local repo instance. Although doing that, you said you wanted to do "initial release" version, instead of a point release... You would not be able to create a local repo of 14.04 without the latest, last point release of 14.04. Why because the archived repo's of 14.04 are the last point release of that version when they were archived.

The basic instructions for creating a local repository out there are for creating it on a server on your network. I do not know your infrastructure. Since I sometimes have to support people "Onsite", I have a USB Storage Drive that I created a local repo on, that I can plug into a machine, then change the sources list to, to change the machine's sources.list pointers. That makes my Onsite Support portable and more open to possible solutions to my customers.

If you do not understand what I just described, then I would suggest you read up on those things to bring your skill level up to be able to do that. That is not a 'dis' or talking over or down to you at all. I truly care that you are supported and get answers you can understand. It's just that it would require you to know some things to be able to do it. I do not initially know your skill level, nor at what level I should address the response to yet. I support people that range from Beginners who know nothing about computers (let alone Linux), through System Architects...

---

### Post by guiverc on 2022-06-02
[Ubuntu Release Upgrader]("https://launchpad.net/ubuntu/+source/ubuntu-release-upgrader") tool 

[LIST]
[*]downloads from the internet, thus being online is required (*or you'll need to spoof the internet via your own network servers etc*)
[*]won't *release-upgrade* you to an *unsupported* release anyway (*though 14.04 is in ESM thus shows as supported on the [meta file]("https://changelogs.ubuntu.com/meta-release")*)
[/LIST]

There is no QA-*tested *and *supported* method to upgrade an *unsupported* system off-line as the tools were not intended for that.

---

### Post by Impavidus on 2022-06-03
> **MAFoElffen said:**
> You would not be able to create a local repo of 14.04 without the latest, last point release of 14.04. Why because the archived repo's of 14.04 are the last point release of that version when they were archived.
Wouldn't disabling the -updates, -backports and -security repos do the trick?

Anyway, best to keep this system completely offline.

---

### Post by grahammechanical on 2022-06-03
I do not know if this will help but in Software & Updates>Ubuntu Software there is a box called Installable from CD-ROM. It usually lists the original install medium that Ubuntu was installed from. This option is usually disabled otherwise we will be prompted to put the DVD/USB stick into the machine every time we try to update.

This Ubuntu Wiki page shows that if we insert a CD-ROM into the drive we should be able to update from the install medium. I have no idea if it is possible to upgrade from one version to the next this way.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

As a wild guess it might help if the usual Ubuntu repositories are disabled. They are not active anyway. It may avoid confusion.

P.S. You may need to set Notify me of a new Ubuntu version to any new version. you never know you might just get an option to upgrade. If the original 13.10 was kept up to date then it is possible that the package to upgrade to the next version is up to date.

Regards

---

