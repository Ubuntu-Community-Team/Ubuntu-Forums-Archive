---
title: "[Ubunu 14] ClassicClient failing to install"
date: 2017-06-07
forum: Installation &amp; Upgrades
---

### Post by kavaliermalta on 2017-06-07
Hello everybody,

I am new to this forum:) 

So I am trying to install the following software libclassicclient_7.0.0-b08.01_amd64 and on Ubuntu 14.0.04. Sadly I am encountering some errors resulting in a failed installation.

The following is a link showing the version of Ubuntu.  [http://imgur.com/a/xmUtI](http://imgur.com/a/xmUtI)

To install the following software, I am using terminal with the following command “**sudo****dpkg**** –****i .**** /libclassicclient_7.0.0-b008.0_i138.deb**"

The following link is showing the error that I am receiving. [http://imgur.com/a/Qdlk7](http://imgur.com/a/Qdlk7)

The dependencies for this program are the following:

[LIST]
[*]pcscd
[*]libssl0.9.8
[/LIST]

For both dependencies I first did a "sudo apt-get update" than "sudo apt-get install pcscd" and "sudo apt-get install libssl0.9.8"

Thanks in advance for your support,

Kavaliermalta

---

### Post by deadflowr on 2017-06-07
See what
```
sudo apt-get install -f
``` 
does.
The command will try to fix it if it can.

---

### Post by kavaliermalta on 2017-06-07
Sadly no it did not . I tried that option.

---

### Post by kavaliermalta on 2017-06-09
Anyone can assist me please with this issue? 

Thanks :)

---

