---
title: "Can't find where repository sources are stored"
date: 2010-04-16
forum: Installation &amp; Upgrades
---

### Post by placidrage on 2010-04-16
I am running a fresh install of ubuntu karmic koala on my new laptop, and today I ran into a frustration while restoring my backups.

I was in nautilus, in my backup files of /etc/apt/sources.list and /etc/apt/sources.list.d/*

When I wanted to double click on sources.list, to my surprise, it opened a GUI dialog to me asking me whether it should replace or add the software repositories, so I chose replace.

Now when I went back to my /etc/apt/sources.list on my system, finding it empty got me frustrated, and no it's not in /etc/apt/sources.list.d either.

But opening the repositories list, via software-properties-gtk, shows up my repositories, and I am able to modify the list and update it but still with an empty sources.list.

I would like to know where it's storing that information in case I wanted to backup.

To my knowledge, those modifications are to be saved in /etc/apt/sources.list, and /etc/apt/sources.list.d/

Thanks in advance for the help.

placidrage

---

### Post by RedSingularity on 2010-04-16
What happens when you go to /etc/apt/sources.list and double click the file?  Does it open your "software sources" window?

---

### Post by zvacet on 2010-04-16
```
gksudo gedit /etc/apt/sources.list
```

and then you can use this one

> #deb cdrom:[Ubuntu 9.10 _Karmic_Koala - Release i386 (20081029.1)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse

You can also add Medibuntu repo following [this.]("https://help.ubuntu.com/community/Medibuntu")


```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by placidrage on 2010-04-17
Thanks for the answers, but that doesn't quite answer my question.

I still have my repositories in software-properties-gtk (software sources).

And if I click on /etc/apt/sources.list, it does open up software-properties-gtk but the file itself is empty.

what I wanted to know is where it is storing them for me, and no it's not in /etc/apt/sources.list.d either.

And thanks for the tip on installing the medibuntu repo, but I already added this.

Basicaly, I have a list of repositories on the gui side, that I can't find where I thought I should find them: /etc/apt/sources.list and /etc/apt/sources.list.d/*

Thanks again for the help

---

### Post by snowpine on 2010-04-17
It is a text file. You can open it with gedit:

```
gksu gedit /etc/apt/sources.list
```

---

### Post by placidrage on 2010-04-17
Thanks for answering, but could you please read my post before trying to answer next time?

First of all, it's usually in /etc/apt/sources.list or the files under /etc/apt/sources.list.d/

And I have quite a list with my dropbox repo, gnome-colors and the like, that are not in those 2 places, my /etc/apt/sources.list is empty.

What I would like to know (read this line very carefully) where could it be storing the info other then those 2 places.

Thanks!

---

### Post by snowpine on 2010-04-17
> **placidrage said:**
> Thanks for answering, but could you please read my post before trying to answer next time?

First of all, it's usually in /etc/apt/sources.list or the files under /etc/apt/sources.list.d/

And I have quite a list with my dropbox repo, gnome-colors and the like, that are not in those 2 places, my /etc/apt/sources.list is empty.

What I would like to know (read this line very carefully) where could it be storing the info other then those 2 places.

Thanks!

I did read your post, and I don't think you understood my answer. :)  Please post the output of:

```
cat /etc/apt/sources.list
```

---

### Post by zvacet on 2010-04-17
Only place where you can find source list is /etc/apt/sources.list .Other repos like Medibuntu (and some others) are in /etc/apt/sources.list.d . I don´ think you can find source list in any other place.Put source list I posted to you in /etc/apt/sources.list.Do it with 

```
gksudo gedit /etc/apt/sources.list
```

and then copy/paste source list in that file.Save and close file.

```
sudo apt-get update && sudo apt-get upgrade
```

Let as know if you get any errors.

---

### Post by placidrage on 2010-04-17
Ok I explained in the first post the fact that I know of the 2 usual locations of apt to save the repo list, which is sources.list and the files under sources.list.d, and yet most of the replies I got are about looking into those files.

Now, I found the problem. When I double clicked on the sources.list backup, it showed a dialog and proposed to either cancel, add or replace, to which I replied replace.

What it did is replace my sources.list with the repo lines found in this backup file:

It replaced all the characters in my sources.list with white spaces.
Then it copied the links from the backup file without the comments by appending it to the end of the sources.list

So when I opened it, I thought it was empty because the n00bs who programmed this feature did think about the fact that a content should start at the top of a file, and not 100 lines down the file.

I checked the file's size that got me to think about scrolling down with the less command.

Again, gui done wrong with poor coding.

And seriously, some of you should get back to school and learn how to read!

Thanks again,
This is solved now

---

