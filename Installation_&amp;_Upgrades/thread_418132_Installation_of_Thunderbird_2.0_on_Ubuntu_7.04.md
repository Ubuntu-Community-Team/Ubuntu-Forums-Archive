---
title: "Installation of Thunderbird 2.0 on Ubuntu 7.04"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by Bawl on 2007-04-22
I'm an old Windoze-user, (wayback since DOS) and relatively new to Linux and Ubuntu.

After having played a little around with previous versions of Ubuntu, SuSE etc. I've finally gone all in, and I'm now (since thursday, that is ;) ) booting directly into Ubuntu 7.04 (still maintaining my WinXP SP2 as a back-up for the things I haven't found ports/counterparts for in Ubuntu (e.g gaming etc.)

Therefore, I'm also sharing my Firefox and Thunderbird-profiles between Windows and Ubuntu. They're placed on a FAT32-drive where both OS'es can use them.

And here's where I run into a "problem". I updated TB from vers. 1.5.0.x to 2.0.0.0 on thursday, while waiting for my Ubuntu-download to finish, and with that, I also updated all the extensions etc.

Now, on Ubuntu 7.04, the respository-version of TB is 1.5.0.3 and 2.0 is nowhere to be found (unless I'm not looking in the right places).
I've checked that all repositories are enabled (Main, Universe, Restricted & Multiverse).

Downloading TB directly from Mozilla, just leaves me with a package "thunderbird-2.0.0.0.tar.gz". As far as I can gather, this new version of TB goes into "/opt", but how do I go on from there?

How do I get Synaptic to recognize the fact that I've got TB 2.0 on my machine? And do I uninstall TB 1.5 through Synaptic, to avoid conflicts etc.

On Windows I would have just installed the program and used it, but I like the idea of Synaptic keeping track of all the programs, so that nothing ends up conflicting.

I guess it goes for any program I would like to install that's not in the repositories, but right now it's just TB I'm on about.


Thx in advance.


- Bawl

Edit: [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/install-file.html]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/install-file.html") doesn't give me the answer I'm looking for

---

### Post by autocrosser on 2007-04-22
Take a look around the Forum. There is a install guide for Thunderbird2. I tried it & it didn't work for me, so I'm waiting for the backport (I would bet as soon as it leaves beta). Anyway, just search for it & you will find it:)

---

### Post by FattyCNS on 2007-04-22
Hi Bawl,

There's instructions on installing the latest version of TBird here:

[https://help.ubuntu.com/community/ThunderbirdNewVersion](https://help.ubuntu.com/community/ThunderbirdNewVersion)

---

### Post by Brian Kendig on 2007-04-22
It might be a good idea to just wait for a .deb package of Thunderbird 2, rather than untarring the files directly.

---

### Post by gmc on 2007-04-27
This seems to be a very complicated howto. Here's what I did...

1. Go download thunderbird2
2. Extract the thunderbird directory into your home directory
3. change system/preferences/proffered applications, and put:
     ~/thunderbird/thunderbird "%s" in the custom mail reader
4. open a terminal and issue the following "ln -s .mozilla-thunderbird .thunderbird" (note the . )
5. go test the new thunderbird2

Gord

---

