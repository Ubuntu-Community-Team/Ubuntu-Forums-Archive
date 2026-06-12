---
title: "can not install synaptic package manager on ubuntu 18.04"
date: 2020-02-03
forum: Installation &amp; Upgrades
---

### Post by umbravitae on 2020-02-03
Hi, I am a newbie to ubuntu; just installed 18.04. But when I came to installing synaptic package manager, it won`t go either way: 1) I tried via GUI, but synaptic package manager is not displayed when searched for 2) Next thing I tried via terminal, and I got this message:  >  Reading package lists... Done Reading state information... Done Package synaptic is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source   (Of course, I hit >  sudo apt upgrade before that)  I have searched for similar issue, but haven`t found any.  Any ideas why is this happening and how to resolve it? Thanks!

---

### Post by wildmanne39 on 2020-02-03
Probably a typo, please do:
```
sudo apt install synaptic
```

---

### Post by umbravitae on 2020-02-03
Hello wildmanne39!

I have copied the codeline from your post in the terminal, it throws back the same message :(

---

### Post by CatKiller on 2020-02-03
Synaptic is in the Universe repository; it's possible you're using one of the versions that doesn't have that enabled by default, or that you've disabled it.

---

### Post by wildmanne39 on 2020-02-03
> **CatKiller said:**
> Synaptic is in the Universe repository; it's possible you're using one of the versions that doesn't have that enabled by default, or that you've disabled it.
+1, I was just looking to see what repository synaptic is in but I was ninja'd.:)

---

### Post by umbravitae on 2020-02-03
I found an older post regarding repositories issue:
>  [https://askubuntu.com/questions/1081243/why-do-i-need-to-enable-universe-repo-in-18-04-isnt-it-default-enabled](https://askubuntu.com/questions/1081243/why-do-i-need-to-enable-universe-repo-in-18-04-isnt-it-default-enabled)  and it says that there was a bug on older versions (repos installed, but not enabled). However
this bug should have been fixed since 18.04.2 (I have 18.04.4)
How do I found out which repos are enabled on my system, an which are disabled?

---

### Post by CatKiller on 2020-02-03
> **umbravitae said:**
> How do I found out which repos are enabled on my system, an which are disabled?

I'd imagine there's a GUI tool that shows it, but I don't use Gnome so I couldn't tell you exactly what it's called. The repositories are listed in /etc/apt/sources.list, though.

---

### Post by umbravitae on 2020-02-03
Here is what I get when I open /etc/apt/sources.list using sudo nano:

```

# deb cdrom:[Ubuntu 18.04.3 LTS _Bionic Beaver_ - Release amd64 (20190805)]/ bi$

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://mk.archive.ubuntu.com/ubuntu/ bionic main restricted
# deb-src http://mk.archive.ubuntu.com/ubuntu/ bionic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mk.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
# deb-src http://mk.archive.ubuntu.com/ubuntu/ bionic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb-src http://mk.archive.ubuntu.com/ubuntu/ bionic universe
# deb-src http://mk.archive.ubuntu.com/ubuntu/ bionic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu


```

Now, from what I understand reading wiki and some other things regarding repos,
I should uncomment these lines (to enable universe):
```

# deb-src http://mk.archive.ubuntu.com/ubuntu/ bionic universe
# deb-src http://mk.archive.ubuntu.com/ubuntu/ bionic-updates universe
```
 then upgrade again
and then try install synaptic - provided that the repo was the original problem?

---

### Post by deadflowr on 2020-02-04
> I should uncomment these lines (to enable universe):
No, those are for the source repository.
(deb-src = source packages
deb = deb packages)

You want to add universe for the deb packages..
```
sudo add-apt-repository universe
```

---

### Post by umbravitae on 2020-02-04
[QUOTE=deadflowr]
You want to add universe for the deb packages..
```
sudo add-apt-repository universe 
```
[/QUOTE]


Thanks deadflowr, worked like charm!
1) installed universe, 2) then upgraded, 3) then I was able to install the Synaptic Package Manager easily!

Finally, do I need to add other repositories which are not enabled in ubuntu 18.04.4 by default?

---

### Post by deadflowr on 2020-02-04
Managing the repositories 101:
[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

