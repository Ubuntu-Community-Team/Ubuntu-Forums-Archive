---
title: "apt-get problem; GPG error"
date: 2007-03-09
forum: Installation &amp; Upgrades
---

### Post by Timtro on 2007-03-09
Hello all,

I must have done something bad. I had to do a couple of improper shutdowns, but I can't see why that would cause this error.

I did an update today through update manager (I got the bubble notification that updates were available). It looked like minor stuff, so I jut went ahead with it.

Now, when I run ```
sudo apt-get update
```, I get the following 


```

.
.
.
Fetched 43.1kB in 1s (30.8kB/s)
Reading package lists... Done
W: GPG error: http://mirror2.ubuntulinux.nl edgy-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
W: GPG error: http://wine.budgetdedicated.com edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: GPG error: http://mirror.ubuntulinux.nl edgy-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
W: You may want to run apt-get update to correct these problems

```

Fetching seems to go well, but this whole keys business seems to be causing a problem (sorry, I'm not to apt-get, I don't know much about it).

I'm using a sources.list automatically generated at [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

and it has been working fine until today. I just tried generating a new sources.list from this website, same results.

Here are a few other things I've tried to fix it. I've removed a few of the particularly stupid ones to save face:
```

  485  apt-get install ubuntu-keys
  486  sudo apt-get install ubuntu-keys
  487  sudo apt-get install ubuntu-keys -t experimental
  488  sudo apt-get install keys
  489  sudo apt-get update
  490  sudo apt-get install ubuntu-keyring
  491  sudo apt-get update
  492  sudo apt-get install ubuntu-keyring
  493  sudo apt-get autoremove ubuntu-keyring
  494  sudo apt-get install ubuntu-keyring
  495  sudo apt-get update
  496  gksu "update-manager -c"
  497  history

```

Clearly, none of it worked, so now I'm posting here.

Thank you all very much.

---

### Post by Kateikyoushi on 2007-03-09
I use this, replace KEY with the keys you want to install for example. 49A120FD1135D466
```
gpg --keyserver subkeys.pgp.net --recv KEY
gpg --export --armor KEY | sudo apt-key add -
```

---

### Post by zvacet on 2007-03-09
When you created source list nex thing you see is something like this(jus example)
> # Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://hr.archive.ubuntu.com/ubuntu](http://hr.archive.ubuntu.com/ubuntu) edgy main restricted 
deb [http://hr.archive.ubuntu.com/ubuntu](http://hr.archive.ubuntu.com/ubuntu) edgy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://hr.archive.ubuntu.com/ubuntu](http://hr.archive.ubuntu.com/ubuntu) edgy universe multiverse 
deb [http://hr.archive.ubuntu.com/ubuntu](http://hr.archive.ubuntu.com/ubuntu) edgy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe multiverse

# Upstream Wine
# GPG key: 387EE263
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main 



# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -




replace KEY with number(example:KEY=387EE263)



Do it with all keys source list needs.

---

### Post by Timtro on 2007-03-09
Thanks to both of you. If only I had read the file.

I had just assumed I had screwed something up, since the error only appeared today.

Thanks again.

Warm regards,


Tim.

---

### Post by roddersg on 2007-10-10
Man, it works!
Thanks very much for the tip!

---

