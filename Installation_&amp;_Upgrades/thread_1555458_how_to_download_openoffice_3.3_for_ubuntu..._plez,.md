---
title: "how to download openoffice 3.3 for ubuntu... plez, anyone can help me"
date: 2010-08-18
forum: Installation &amp; Upgrades
---

### Post by clumsy and dizzy on 2010-08-18
hye, im need some help...
can anyone help me how to download openoffice 3.3 in ubuntu? plez....teach me step by step coz im new in using ubuntu..

---

### Post by xangua on 2010-08-18
there is no OpenOffice 3.3

---

### Post by slooksterpsv on 2010-08-18
For the beta1 3.3 you can download an untested deb file depending on your architecture (32-bit or 64-bit) from here:
[http://download.openoffice.org/all_beta.html#untested-full](http://download.openoffice.org/all_beta.html#untested-full)

---

### Post by Sef on 2010-08-18
> For the beta1 3.3 you can download an untested deb file depending on your architecture (32-bit or 64-bit) from here:
[http://download.openoffice.org/all_b...#untested-full](http://download.openoffice.org/all_b...#untested-full)

Please note that since it is beta, it is not recommended for production use, only testing.  Only use it on a machine that you can afford to reinstall the os.

---

### Post by clumsy and dizzy on 2010-08-19
**[SIZE=2][COLOR=Black]Owh, ok.. thanx 4 ur information... ok, now can u teach me how to install openoffice 3.2.1 in ubuntu... i've download that version, but dont know how to install...[/COLOR][/SIZE]**

---

### Post by dcollier on 2010-08-19
Sounds like you have download a tar or tar.gz file, you will have to extract and compile the application.  Try opening up a command prompt and enter "sudo apt-get install openoffice"

---

### Post by slooksterpsv on 2010-08-19
If you're using Ubuntu, it's installed by default, for Writer, Calc, and Presentation. If you need Base (database), Drawing (Mind Map/drawing) you'll need to go to Software Center and search for it.

Applications -> Software Center

---

### Post by frogotronic on 2010-09-24
> **clumsy and dizzy said:**
> **[SIZE=2][COLOR=Black]Owh, ok.. thanx 4 ur information... ok, now can u teach me how to install openoffice 3.2.1 in ubuntu... i've download that version, but dont know how to install...[/COLOR][/SIZE]**

Do yourself a favour and use the PPA repos.

[https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)

- CH


                :guitar:

---

### Post by Hagar Delest on 2010-09-24
dpkg is you friend...

See [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68) Same process, except that there is no integration package, you've to create the shortcuts by yourself.

---

