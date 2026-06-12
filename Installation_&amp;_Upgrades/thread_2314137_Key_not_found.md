---
title: "Key not found"
date: 2016-02-18
forum: Installation &amp; Upgrades
---

### Post by marcosmelendezsantiago on 2016-02-18
Hello Ubuntu Forums, I come to you with an issue. I just ran the sudo apt-get update command in ubuntu 15.10 and I got this error.

```
GPG error: [https://download.01.org](https://download.01.org) wily InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D14BDB0DB3438B6C
```

I tried some suggestions online but it did not work. How should I fix this issue and is it harmful in anyway?

Thanks

---

### Post by newbie-user on 2016-02-18
Just add the key:
```
apt-key adv --recv-key --keyserver keyserver.ubuntu.com D14BDB0DB3438B6C
```

It's only potentially harmful if the source is not a reputable source and you don't trust it. By using the above command, you're telling your computer to trust the packages that come from the repo.

---

### Post by marcosmelendezsantiago on 2016-02-18
This is the error that Im getting after I did the command:

gpg: requesting key B3438B6C from hkp server keyserver.ubuntu.com
gpgkeys: key D14BDB0DB3438B6C not found on keyserver
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

---

### Post by newbie-user on 2016-02-18
That just means you'll have to try another key server. This webpage has a list of keyservers: [http://www.rossde.com/PGP/pgp_keyserv.html#pubserv]("http://www.rossde.com/PGP/pgp_keyserv.html#pubserv")

If the keyservers can't find the key, you can still install packages from that repository. Ubuntu will just tell you that they're unsigned and ask for verification before installing.

---

### Post by oldos2er on 2016-02-19
The key is here: [https://download.01.org/gfx/RPM-GPG-KEY-ilg-3](https://download.01.org/gfx/RPM-GPG-KEY-ilg-3)

```
wget https://download.01.org/gfx/RPM-GPG-KEY-ilg-3

sudo apt-key add RPM-GPG-KEY-ilg-3

sudo apt-get update
```

---

