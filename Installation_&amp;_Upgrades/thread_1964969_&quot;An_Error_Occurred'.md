---
title: "&quot;An Error Occurred'"
date: 2012-04-24
forum: Installation &amp; Upgrades
---

### Post by TheSingingCoyote on 2012-04-24
I've been attempting for ages, to install updates on my ubutu acer netbook, but it appears none of them are going through that I can tell...I tried googling the error, but nothing came up, oddly enough. Here's what it says:


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8k-7ubuntu8.8_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8k-7ubuntu8.8_i386.deb)
  404  Not Found [IP: 91.189.92.179 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8k-7ubuntu8.8_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8k-7ubuntu8.8_i386.deb)
  404  Not Found [IP: 91.189.92.179 80]



I remember you all being very helpful before with my old Dell PC that I built, so I'm posting in hopes of some help!



-Coyote

---

### Post by Penguinnerd on 2012-04-24
What version of Ubuntu are you running?

---

### Post by matt_symes on 2012-04-24
Hi

That deb file is not on the server, hence your error. Can we take a look at your sources ?

Please post the output of

```
cat /etc/apt/sources.list /etc/apt/sources.list.d/*
```

Kind regards

---

### Post by TheSingingCoyote on 2012-04-25
I'm running Ubuntu 10.04. Matt, here is what I have...and yes, my computer's name is "Babby" in reference to an internet meme :P


```

mallory@Babby:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://us.archive.ubuntu.com/ubuntu/ lucid-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-security restricted main multiverse universe #Added by software-properties
deb http://us.archive.ubuntu.com/ubuntu/ lucid-security universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-security multiverse
mallory@Babby:~$ /etc/apt/sources.list.d*
bash: /etc/apt/sources.list.d: is a directory
```

Thanks in advance!

---

### Post by matt_symes on 2012-04-26
Hi

Your sources.list file looks fine but we need to see your ppas and you made a slight typo on that command.

Please post the output of

```
cat /etc/apt/sources.list.d/*
```The package is referenced here...

[https://launchpad.net/~ubuntu-security/+archive/ppa/+build/3136550]("https://launchpad.net/%7Eubuntu-security/+archive/ppa/+build/3136550")

however lucid seems to be using this

[http://packages.ubuntu.com/lucid/i386/libssl0.9.8/download](http://packages.ubuntu.com/lucid/i386/libssl0.9.8/download)

A different version number.

Have you installed any software that might have installed that version of ssl ?

Kind regards

---

### Post by TheSingingCoyote on 2012-04-26
I'm tired, so I'm not sure if I (once again) made a typo :P

When I typed this into the terminal, I got this:

```
mallory@Babby:~$ cat etc/apt/sources.list.d/*
cat: etc/apt/sources.list.d/*: No such file or directory
mallory@Babby:~$ cat /etc/apt/sources.list.d/*
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/talkplugin/deb/ stable main
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/talkplugin/deb/ stable main
# deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu lucid main # disabled on upgrade to lucid
deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu karmic main
mallory@Babby:~$ 

```

Also, I'm not sure which software could be affecting this. Would you like a list of my software/programs?

---

### Post by matt_symes on 2012-04-27
Hi

I'm pretty sure you need libssl0.9.8_0.9.8k-7ubuntu8.11_i386.deb but you have libssl0.9.8_0.9.8k-7ubuntu8.8_i386.deb installed by the looks of it as that is what it wants to update.

You can check with

```
dpkg -l | grep libssl
```

Some questions. 

This was an upgrade from karmic ?
Have you pinned the libssl version using apt or dpkg ?
When did updates stop working ?

Have you considered installing the version of libssl for Lucid from the repos and uninstalling the version of have ? I am not sure if that would break anything on your system though.

Kind regards

---

### Post by TheSingingCoyote on 2012-04-27
I attempted to check, but this is what I got:

```
mallory@Babby:~$ dpkg -1 | grep libssl
dpkg: unknown option -1

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
mallory@Babby:~$ 
```


I looked for more information, but I didn't see a way to get more...


As for your questions:

> This was an upgrade from karmic ?

I don't know, since it simply came from my computer. When I checked for updates under System-Administration-Update Manager, that's what came up. I'm not even quite sure what "karmic" is, in regards to computers. :P

> Have you pinned the libssl version using apt or dpkg ?

I'm not sure what that means...

> When did updates stop working ?

I'm not entirely sure. Likely months ago. I rarely use this computer, so I just left it as is for a while. Of course, it started getting a tad slow. I'm not sure if it's due to the hardware (being a netbook), or the updates.

> Have you considered installing the version of libssl for Lucid from the repos and uninstalling the version of have ? I am not sure if that would break anything on your system though

I have not. I'm a little worried about doing that considering what you said, though...By breaking the system, would that imply that I cannot re-install Ubuntu,l and the computer itself would be essentially destroyed?


I apologize for my lack of knowledge! I love computers,and the linux operating system, but I'm not nearly as knowledgeable as a lot of people yet. :P



Thanks in advance!

---

### Post by critin on 2012-04-27
> I'm not entirely sure. Likely months ago. I rarely use this computer, so  I just left it as is for a while. Of course, it started getting a tad  slow. I'm not sure if it's due to the hardware (being a netbook), or the  updates.

if there is nothing on the system that you want to keep, and if you haven't used it in so long there probably isn't.  You know, files, docs and pics.  Why not download a new 11.04 or 11.10 iso on cd or usb stick and install it fresh?  It will work.

> By breaking the system, would that imply that I cannot re-install  Ubuntu,l and the computer itself would be essentially destroyed?


No, the computer would not be destroyed.  You can always reinstall ubuntu fresh and usually fix a system that has broken packages.  Your version of ununtu is out of date.

---

### Post by TheSingingCoyote on 2012-04-29
Okay, I reinstalled Ubuntu. Now it's slow as ever, and is refusing to install skype. It just won't do anything now...

---

