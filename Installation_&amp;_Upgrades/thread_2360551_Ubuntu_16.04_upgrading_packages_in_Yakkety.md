---
title: "Ubuntu 16.04 upgrading packages in Yakkety"
date: 2017-05-05
forum: Installation &amp; Upgrades
---

### Post by scojopa on 2017-05-05
I need to update 
ModemManager -> 1.6
which requires libqmi -> 1.16 and libmbim (v1.14)

Each of these have more dependencies that I need to grab and install. which have other dependencies......

How can I use APT to grab these from Yakkety while running Xenial base

I looked at pinning and backports

Can anyone recommend the best way to do tihs?

Thanks

---

### Post by TheFu on 2017-05-05
I cannot recommend you do this, unless you want to be in "APT hell" very quickly. 

I would seek a different tool to accomplish whatever it is that ModemManager does for you or just move to the release you need completely. Mixing packages is a bad idea.

Support for 16.10 will end in July, so I wouldn't spend much time trying to make that work. I'd look to 17.04 since both are NOT LTS releases.

Wish I had more ideas. Maybe someone else will?

---

### Post by scojopa on 2017-05-06
Agree after further reading. Installed Kali 17.1 and mobile adapter working fine. 

Will also try 17.04

Thanks

---

### Post by TheFu on 2017-05-06
Kali should never be used as a desktop.  It is a special purpose distro and should only be used for those special purposes. It is highly non-secure.

---

