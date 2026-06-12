---
title: "apt/synaptic error, PLEASE HELP"
date: 2006-08-07
forum: Installation &amp; Upgrades
---

### Post by Mooie on 2006-08-07
Hi, I use kubuntu 6.06 dapper (I also have Ubuntu gnome installed).  I am trying to upgrade kde because I read on the Kubuntu site that it is supported, and has a lot of but fixes.  Synaptic shows Kubuntu-desktop at its latest version, and when I reload my package info (the reload button in synaptic and i have also tried "sudp apt-get update") it gives me the error

W: GPG error: [http://ubuntu.moshen.de](http://ubuntu.moshen.de) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC0A1CC62F306651

any help you could give me would REALLY   er.....  help! :D

---

### Post by mlind on 2006-08-07
> **Mooie said:**
> Hi, I use kubuntu 6.06 dapper (I also have Ubuntu gnome installed).  I am trying to upgrade kde because I read on the Kubuntu site that it is supported, and has a lot of but fixes.  Synaptic shows Kubuntu-desktop at its latest version, and when I reload my package info (the reload button in synaptic and i have also tried "sudp apt-get update") it gives me the error

W: GPG error: [http://ubuntu.moshen.de](http://ubuntu.moshen.de) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC0A1CC62F306651

any help you could give me would REALLY   er.....  help! :D


You're downloading package from untrusted source. If you want to make it trusted:
```

gpg --recv-keys --keyserver pgp.mit.edu FC0A1CC62F306651
gpg --export --armor FC0A1CC62F306651 | sudo apt-key add -

```

---

### Post by Mooie on 2006-08-08
When I ran the commands the second one gave me the error
> usage: gpg [options] [filename]
gpg: no valid OpenPGP data found.
could the server be having problems (I'm guessing not because I havent seen anybody else with the same problems)

---

### Post by mlind on 2006-08-08
> **Mooie said:**
> When I ran the commands the second one gave me the error

could the server be having problems (I'm guessing not because I havent seen anybody else with the same problems)

Looks like there was a typo, should be working now.

---

### Post by Mooie on 2006-08-08
thanks, I will try it out when it get home :D

---

### Post by Mooie on 2006-08-08
It worked! thanks!

it still shows kubuntu-desktop as at the newest version...  I guess I will read through the forums on htat issue, I must have to add a new repo or somthing for that

---

### Post by Mooie on 2006-08-08
I found the repo, and am upgrading now, thanks for the help! :D

---

