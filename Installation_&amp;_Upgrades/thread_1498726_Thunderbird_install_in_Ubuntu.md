---
title: "Thunderbird install in Ubuntu"
date: 2010-06-01
forum: Installation &amp; Upgrades
---

### Post by saurabh_negi on 2010-06-01
Hello All, 

Am trying to install thuderbird in Ubuntu 10.04 though synaptic and getting the following error

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird_3.0.4+nobinonly-0ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird_3.0.4+nobinonly-0ubuntu4_i386.deb)
  Could not connect to us.archive.ubuntu.com:80 (91.189.88.40). - connect (113: No route to host) [IP: 91.189.88.40 80]

Please help, seems like I need to add the repository but am not sure how.

thanks

---

### Post by bowmanr@mailcity.com on 2010-06-01
Looks like a network connectivity issue, not repositories.

Have you tried pinging "us.archive.ubuntu.com", and "91.189.88.40"?

$ ping -c 4 us.archive.ubuntu.com
$ ping -c 4 91.189.88.40

What happens with the above pings please?

---

### Post by saurabh_negi on 2010-06-01
Ur right , Am getting host unreachable error. Any idea what else can be done as I am perfectly able to work on internet from this same machine.

thanks

---

### Post by bowmanr@mailcity.com on 2010-06-01
Hmmm... Not sure really, sorry. Have you tried again? [*1] I occasionally get failures to download and it's all ok if I retry.

Also, try an update of package listings ...

$ sudo aptitude update

See if that can connect ok and get package listings.

You /may/ want to try rebooting your router/gateway?

As a last resort (and this is a blunt instrument!), try the UK repositories :

(copy what's currently there!!)
$ sudo cp /etc/apt/sources.list /etc/apt/sources.list.20100601_XXXX.AS_INSTALLED
^^^ replacing XXXX with the current time

(repoint to UK)
$ sudo nano /etc/apt/sources.list 
... and then, change 'us.' to 'gb.'
Sorry to not be massively helpfull. 

$ sudo aptitude update
$ sudo aptitude install thunderbird

CAVAET :: I'm at work, on a Windows machine! I hope the commands and location of files above is correct

---
[*1] - yikes!! implementing the first 'R' of Windows computing on Linux!!!

---

