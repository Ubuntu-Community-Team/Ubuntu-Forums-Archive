---
title: "No Pubkey?"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by AlmightyMalachi on 2006-06-03
I've been a long user of Ubuntu, i know I need a key, but Can't seem to be able to export it, It wont read some of my custom backports I put in. Heres the error message I keep getting
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release: Unknown errorexecuting gpgv
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release: Unknown error ex ecuting gpgv
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release: Unknown errorexecuting gpgv
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release: Unknown error executinggpgv
W: GPG error: [ftp://cipherfunk.org](ftp://cipherfunk.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4CF19C3233BAC1B3
W: You may want to run apt-get update to correct these problems

Anyone else have this problem?

---

### Post by ubuntu_demon on 2006-06-04
go to system->adminstration->software preferences->authentication and click on restore defaults.

if that doesn't work :

When a repository in this list has a GPG key, you may need to add that to the APT trusted keys. You can do this with the following commands (replace KEY with the key ID)
```

      gpg --keyserver subkeys.pgp.net --recv KEY
      gpg --export --armor KEY | sudo apt-key add -

```

the key keys are :
437D05B5
FBB75451
33BAC1B3

---

### Post by bozo8787 on 2006-10-17
> **ubuntu_demon said:**
> go to system->adminstration->software preferences->authentication and click on restore defaults.

if that doesn't work :

When a repository in this list has a GPG key, you may need to add that to the APT trusted keys. You can do this with the following commands (replace KEY with the key ID)
```

      gpg --keyserver subkeys.pgp.net --recv KEY
      gpg --export --armor KEY | sudo apt-key add -

```

the key keys are :
437D05B5
FBB75451
33BAC1B3

K, i've been going at this for hours now. Trying to get EasyUbuntu working I kept getting
W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718
W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718
W: GPG error: [http://easyubuntu.cafuego.net](http://easyubuntu.cafuego.net) main Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY
580E2519969F3F57

Now i'm only getting 
W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718
W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718

I keep getting this:
dre@dre-laptop:~$ gpg --keyserver subkeys.pgp.net --recv 12B83718
gpg: requesting key 12B83718 from hkp server subkeys.pgp.net
gpg: key 12B83718 was created 2926556 seconds in the future (time warp or clock problem)
gpg: key 12B83718 was created 2926556 seconds in the future (time warp or clock problem)
gpg: key 12B83718 was created 2926556 seconds in the future (time warp or clock problem)
gpg: key 12B83718 was created 2926556 seconds in the future (time warp or clock problem)
gpg: key 12B83718 was created 2926556 seconds in the future (time warp or clock problem)
gpg: key 12B83718 was created 2926556 seconds in the future (time warp or clock problem)
gpg: key 12B83718 was created 2926556 seconds in the future (time warp or clock problem)
gpg: key 12B83718 was created 2926556 seconds in the future (time warp or clock problem)
gpg: key 12B83718 was created 2926556 seconds in the future (time warp or clock problem)
gpg: key 12B83718 was created 2926556 seconds in the future (time warp or clock problem)
gpg: key 12B83718: no valid user IDs
gpg: this may be caused by a missing self-signature
gpg: Total number processed: 1
gpg:           w/o user IDs: 1
dre@dre-laptop:~$ gpg --export --armor 12B83718 | sudo apt-key add -
Password:gpg: WARNING: nothing exported


I've also done this:
wget [http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg](http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg) -O- | sudo apt-key add -

And nothing.

Can someone rescue me. I've searched, read and read some more.

---

### Post by ubuntu_demon on 2006-10-18
The only thing I know is :
[http://doc.ubuntu-fr.org/doc/plf](http://doc.ubuntu-fr.org/doc/plf)

Why do you need PLF? You can find w32codecs and dvd-support in my Customization Guide if that's what you need PLF for.

good luck!

---

### Post by deanjm1963 on 2006-10-18
You are better off using Seveas dapper repositories. I've found the codecs far better than those offered by PLF. Also, PLF have shut down working on files for Ubuntu (for the present moment).

---

### Post by ubuntu_demon on 2006-10-18
> **deanjm1963 said:**
> You are better off using Seveas dapper repositories. I've found the codecs far better than those offered by PLF. Also, PLF have shut down working on files for Ubuntu (for the present moment).
They created an Edgy repo some time after they said they were going to shut down. So I guess they found some volunteers.

---

### Post by bozo8787 on 2006-10-18
> **ubuntu_demon said:**
> The only thing I know is :
[http://doc.ubuntu-fr.org/doc/plf](http://doc.ubuntu-fr.org/doc/plf)

**Why do you need PLF?** You can find w32codecs and dvd-support in my Customization Guide if that's what you need PLF for.

good luck!
Short answer: [EasyUbuntu]("http://easyubuntu.freecontrib.org/overview.html")

> **deanjm1963 said:**
> You are better off using Seveas dapper repositories. I've found the codecs far better than those offered by PLF. Also, PLF have shut down working on files for Ubuntu (for the present moment).

1st thanx for the reply. 

I am only following the steps to enable [EasyUbuntu]("http://easyubuntu.freecontrib.org/overview.html")

C, being a n00b of linux, it's the configurations that where I got stuck in the past(way b4 Ubuntu came along) so I run into this cute proggie called Easy Ubuntu and since i'm very much "duh" when it comes to linux, naturally I had to get it.

BTW, here's another one of my, duh moments. I go to the EasyUbuntu site and in bold and caps it states "**WE USE THE PLF REPOSITORY. WE ARE NOT RESPONSIBLE FOR PLF UPTIME. SO PLEASE DO NOT FILE BUGS ON PLF BEING DOWN, YOUR BUG REPORT WILL BE IGNORED**."

My bad! I just can't to see error messages popping up durings installations,lol.

---

### Post by arhipov_alexey on 2007-03-24
> xI've been a long user of Ubuntu, i know I need a key, but Can't seem to be able to export it, It wont read some of my custom backports I put in. Heres the error message I keep getting
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release: Unknown errorexecuting gpgv
W......


Check your date and time. I had the same problem when my clocks were not good.

---

