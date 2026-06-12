---
title: "Problems updating packages"
date: 2007-11-20
forum: Installation &amp; Upgrades
---

### Post by Dooley on 2007-11-20
Hi there,

I have a problem updating/installing new packages. 
This is the error I get. 

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2007i-0ubuntu0.7.04_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2007i-0ubuntu0.7.04_all.deb)
  Could not resolve ':@http'


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/l/lzo2/liblzo2-2_2.02-2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/l/lzo2/liblzo2-2_2.02-2_i386.deb)
  Could not resolve ':@http'


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/t/twolame/libtwolame0_0.3.8-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/t/twolame/libtwolame0_0.3.8-1_i386.deb)
  Could not resolve ':@http'


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/mencoder_1.0~rc2-0ubuntu1~feisty1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/mencoder_1.0~rc2-0ubuntu1~feisty1_i386.deb)
  Could not resolve ':@http'


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/mplayer_1.0~rc2-0ubuntu1~feisty1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/mplayer_1.0~rc2-0ubuntu1~feisty1_i386.deb)
  Could not resolve ':@http'

---

### Post by reckless2k2 on 2007-11-20
i have this problem here and there if repos are down for one reason or another. try throwing your country prefix in front. i'm from US so i put us.

understand or no? you'd have to edit in synaptic or in terminal the source list.

---

### Post by Dooley on 2007-11-20
I kinda understand, but where exactly do I put US or IE for Ireland, where I am? :D

---

### Post by Dooley on 2007-11-20
Can anyone help or have this problem, I have tried looking though apt config files but no luck!!

---

### Post by forestpixie on 2007-11-20
you need to change you're sources list if you want to follow reckless2k2 advice

I'd backup the file first 

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```

to edit it 

```
gksudo gedit /etc/apt/sources.list
```

some of mine for example look like this - deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe

---

### Post by Dooley on 2007-11-20
Cheers forestpixie,
However when I add us or gb or ie to my repos I have the same error.

Here when I try reload my repos.

The same error comes up...

[http://us.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg:) Could not resolve 'http'
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_IE.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_IE.bz2:) Could not resolve 'http'

I was playing around with proxies before, could this be the problem?

I can still ping from the CLI and the internet works fine.

---

### Post by Dooley on 2007-11-20
Anyone? I really dont have a notion on this one. I have no proxy set up on the system.
apt.conf is empty and this is my sources file

## UBUNTU REPOSITORIES
## -------------------
##
## Feisty (Ubuntu 7.04)
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse  
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse 
##
## Proposed Updates
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed main restricted universe multiverse 
##
## Bug Fixes
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse 
##
## Security Updates
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse 
##
## Backports
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

---

### Post by forestpixie on 2007-11-21
I've never had too many problems with apt sources - not usre that I can help much but you could always try doing a new sources list - [this]("http://www.ubuntu-nl.org/source-o-matic/") seems to work ok.

---

