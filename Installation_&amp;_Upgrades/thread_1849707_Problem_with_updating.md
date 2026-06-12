---
title: "Problem with updating"
date: 2011-09-25
forum: Installation &amp; Upgrades
---

### Post by rj7 on 2011-09-25
When i update my ubuntu 10.04 i get this error message.
Someone tell me whats happening and how to solve!!
```

W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A8AA1FAA3F055C03

```

---

### Post by raja.genupula on 2011-09-25
try to change your server from update manager->setting--> 1st tab(ubuntu software), change your server and then try again.

All the best

---

### Post by rj7 on 2011-09-25
the same problem occurs i tried main server and then two three different servers
```

W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A8AA1FAA3F055C03

```

---

### Post by raja.genupula on 2011-09-25
Hi try this

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A8AA1FAA3F055C03

```


all the best

---

### Post by Awareness on 2011-09-25
does this fixed it for you? because im having why my keys and all the servers (local and main) since yesterday.... may it be is not just me?

greets!

---

### Post by raja.genupula on 2011-09-25
I have seen a thread which is solved by the answer that i have given to him.

you can try that.But 1st option which i known is first you have to change your server to another mirror and then you have to update again. If that error still exists then you can go with my 2nd post.

Hope this information will be helpful to you.

---

### Post by rj7 on 2011-09-29
sorry, guys this fixed it
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A8AA1FAA3F055C03
```

Actually first i tried it but nothing processed...
Only today processed something like this...
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A8AA1FAA3F055C03
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys A8AA1FAA3F055C03
gpg: requesting key 3F055C03 from hkp server keyserver.ubuntu.com
gpg: key 3F055C03: "Launchpad PPA for Daniel Richter" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

```

Thanks you guys... I was out of town for two days that's why dint reply sorry guys!!! 


Thank you guys.... i was out of town thats w

---

### Post by amran859 on 2011-09-29
[IMG]http://www.mpfun.com/diz/mpfun_logo.gif[/IMG]
[FONT=Comic Sans MS][SIZE=4]For free downloading mp3 & other staff you must visit the site bellow. It is really a good site for download.[/SIZE][/FONT][FONT=Comic Sans MS][SIZE=4][COLOR=DarkOrange]

The link is down bellow:[/COLOR][/SIZE][/FONT]
[B][I][SIZE=4][COLOR=Blue][http://www.mpfun.com/](http://www.mpfun.com/)

[/COLOR][/SIZE][/I][/B]:confused:

---

### Post by raja.genupula on 2011-09-29
> **amran859 said:**
> [IMG]http://www.mpfun.com/diz/mpfun_logo.gif[/IMG]
[FONT=Comic Sans MS][SIZE=4]For free downloading mp3 & other staff you must visit the site bellow. It is really a good site for download.[/SIZE][/FONT][FONT=Comic Sans MS][SIZE=4][COLOR=DarkOrange]

The link is down bellow:[/COLOR][/SIZE][/FONT]
[B][I][SIZE=4][COLOR=Blue][http://www.mpfun.com/](http://www.mpfun.com/)

[/COLOR][/SIZE][/I][/B]:confused:


please dont post things like here .

---

