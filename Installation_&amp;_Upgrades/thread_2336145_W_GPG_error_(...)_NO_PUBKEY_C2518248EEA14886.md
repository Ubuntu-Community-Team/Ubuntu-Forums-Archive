---
title: "W: GPG error: (...) NO_PUBKEY C2518248EEA14886"
date: 2016-09-05
forum: Installation &amp; Upgrades
---

### Post by liike on 2016-09-05
Hey guys,
i'm having this error after trying to update:

```
W: GPG error: http://ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C2518248EEA14886
```

I found [another thread]("https://ubuntuforums.org/showthread.php?t=2257304") where the user 'The Big Head One' had the same issue. Hopefully you guys can help me. The solution from the other thread doesn't work for me...


```
root@srv-test01:~$ ls /etc/apt/trusted.gpg.d | wc -l
0

```

After i'm trying to add the public key for the named ppa. i'm getting this error.
```
root@srv-test01:~# gpg --keyserver keyserver.ubuntu.com --recv C2518248EEA14886 gpg --export --armor C2518248EEA14886 | sudo apt-key add - sudo apt-get updategpg: directory `/home/liike/.gnupg' created
gpg: new configuration file `/home/liike/.gnupg/gpg.conf' created
gpg: WARNING: options in `/home/liike/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/home/liike/.gnupg/secring.gpg' created
gpg: keyring `/home/liike/.gnupg/pubring.gpg' created
gpg: "gpg" not a key ID: skipping
gpg: "--export" not a key ID: skipping
gpg: "--armor" not a key ID: skipping
gpg: requesting key EEA14886 from hkp server keyserver.ubuntu.com
gpg: requesting key EEA14886 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
gpg: no valid OpenPGP data found.
 
```

If I search for the key manually on the website from keyserver I dont find any matched key for this ppa. Is there any problem with the public key?


**/etc/apt/apt.conf**
```
Acquire::http::Proxy "http://proxy.mydomain.de:8080";
Acquire::https::Proxy "https://proxy.mydomain.de:8080";
Acquire::ftp::Proxy "ftp://proxy.mydomain.de:2121";

```

---

### Post by howefield on 2016-09-05
Is the key for a VLC launchpad PPA ?

---

### Post by liike on 2016-09-05
No, this is the key for java.

---

### Post by howefield on 2016-09-05
OK, you could try this for a way round it..

Copy the following text 

```
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.1.5
Comment: Hostname: keyserver.ubuntu.com

mI0ES9/P3AEEAPbI+9BwCbJucuC78iUeOPKl/HjAXGV49FGat0PcwfDd69MVp6zUtIMbLgkU
OxIlhiEkDmlYkwWVS8qy276hNg9YKZP37ut5+GPObuS6ZWLpwwNus5PhLvqeGawVJ/obu7d7
gM8mBWTgvk0ErnZDaqaU2OZtHataxbdeW8qH/9FJABEBAAG0DUxhdW5jaHBhZCBWTEOImwQQ
AQIABgUCVsN4HQAKCRAEC6TrO3+B2tJkA/jM3b7OysTwptY7P75sOnIu+nXLPlzvja7qH7Wn
A23itdSker6JmyJrlQeQZu7b9x2nFeskNYlnhCp9mUGu/kbAKOx246pBtlaipkZdGmL4qXBi
+bi6+5Rw2AGgKndhXdEjMxx6aDPq3dftFXS68HyBM3HFSJlf7SmMeJCkhNRwiLYEEwECACAF
Akvfz9wCGwMGCwkIBwMCBBUCCAMEFgIDAQIeAQIXgAAKCRDCUYJI7qFIhucGBADQnY4V1xKT
1Gz+3ERly+nBb61BSqRx6KUgvTSEPasSVZVCtjY5MwghYU8T0h1PCx2qSir4nt3vpZL1luW2
xTdyLkFCrbbIAZEHtmjXRgQu3VUcSkgHMdn46j/7N9qtZUcXQ0TOsZUJRANY/eHsBvUg1cBm
3RnCeN4C8QZrir1CeA==
=CziK
-----END PGP PUBLIC KEY BLOCK-----
```

taken from [http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xC2518248EEA14886](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xC2518248EEA14886) to a text file named java (or whatever you want) then open up the Software and Updates application, go to the Authentication tab and click on Import Key File, navigate to where you stored the text file and ok, enter your password and you should be good to go.

---

### Post by liike on 2016-09-05
Thanks mate! 

I'm using Ubuntu Server (without GUI) but it worked perfectly.

Just created a file with this key above and add this key via 
```
sudo apt-key -add key.txt
```

---

### Post by howefield on 2016-09-05
Cool, thanks for the update and glad you sussed it, feel free to mark the thread as solved. :)

---

