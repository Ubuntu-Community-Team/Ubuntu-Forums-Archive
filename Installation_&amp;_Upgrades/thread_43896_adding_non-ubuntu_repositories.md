---
title: "adding non-ubuntu repositories"
date: 2005-06-23
forum: Installation &amp; Upgrades
---

### Post by jefffq on 2005-06-23
I was using Mepis before Ubuntu. It had some more things in its repository, that I wouldn't mind having access to with Synaptic in Ubuntu. I know that it's better to use Ubuntu repositories. I would use them for everything that I could. But it should still be safe to use Mepis of Debian repositories, shouldn't it?

I'm having difficulty finding the URLs of such repositories. I'd love to add the main Debian one, if anyone could give me the URL.

Thanks.

---

### Post by Leif on 2005-06-23
No, it isn't really safe to mix with debian repositories. You could easily end up with quite tricky problems. What apps are you looking for ? And have you already enabled universe, multiverse, backports ?

---

### Post by jefffq on 2005-06-23
I have Universe, what's Multiverse?

I've never had any problems installing .deb packages. And if there is software that I want, that I can't get through the Ubuntu repository, then I must download a .deb package anyway. So I may as well have the ease of Synaptic to do it. I'm not big on source, I'm lazy and like an easy way to uninstall and/or upgrade.

---

### Post by SGC on 2005-06-23
Add this to apt-get's sources file to enable multiverse and backport repositories:

# Multiverse Repositories
```

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

```

## Backports Repositories
```

deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

```

## Debian Repositories (Highly unrecommanded)
```

deb http://ftp.us.debian.org/debian/ stable main non-free contrib
deb-src http://ftp.us.debian.org/debian/ stable main non-free contrib
deb http://non-us.debian.org/debian-non-US stable/non-US main contrib non-free
deb-src http://non-us.debian.org/debian-non-US stable/non-US main contrib non-free

```

---

### Post by jefffq on 2005-06-23
Thank you very much. That multiverse, or the backport not sure which one, had what I wanted. Except for one tool, which is available in the Debian ones. I'll leave the Debian ones disabled unless I need them.  :smile:

---

### Post by shamrog12 on 2005-07-13
[QUOTE=SGC]Add this to apt-get's sources file to enable multiverse and backport repositories:

# Multiverse Repositories
```

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

```

## Backports Repositories
```

deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

```

## Debian Repositories (Highly unrecommanded)
```

deb http://ftp.us.debian.org/debian/ stable main non-free contrib
deb-src http://ftp.us.debian.org/debian/ stable main non-free contrib
deb http://non-us.debian.org/debian-non-US stable/non-US main contrib non-free
deb-src http://non-us.debian.org/debian-non-US stable/non-US main contrib non-free

```[/QUOTE]


Where is apt-get which I'd have to modify to get those other repositories?  I'm a noob, sorry :)

---

### Post by Leif on 2005-07-13
You can do it either through synaptic, by adding the relevant info under settings->repositories. So for example, for multiverse, you'd put :

URI [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
Distro hoary
Sections multiverse

And lick refresh.

Or you can "sudo gedit /etc/apt/sources.list" from the command line, and just append the lines to the end. Then do "sudo apt-get update". 

Read ubuntuguide.org for more info

---

### Post by shamrog12 on 2005-07-13
I'm pretty sure I followed those directions properly.  i get the following error:

archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_main_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_multiverse_binary-powerpc_Packages) - stat (2 No such file or directory)

---

### Post by Leif on 2005-07-13
Do you still get that error after doing a sudo apt-get update ? If so, please attach your /etc/apt/sources.list

---

