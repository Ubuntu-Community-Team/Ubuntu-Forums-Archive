---
title: "HPLIP installation on Ubuntu 16.04 64 bit"
date: 2016-06-06
forum: Installation &amp; Upgrades
---

### Post by sir.Evan on 2016-06-06
Good day,
I have been using Ubuntu for more than 3 years and like it but I am not too familiar with the programning etc, so help is needed sometimes.,:D

I have installed Ubuntu 16.04 64 bit on my old laptop. 
Used to have 14.04 working with HPLIP for my HP deskjet 2540 printer.

I have not been able to install HPLIP on 16.04 using this support page
[http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html](http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html)

After trying to install the dependencies this can't be found
E: Unable to locate package python3.4-dev
E: Couldn't find any package by glob 'python3.4-dev'
E: Couldn't find any package by regex 'python3.4-dev'

Python3 should be installed as default as far as I understand but something isn't working

I tried to carry on using the ./configure command but was told 
bash: ./configure: No such file or directory

Migth be part of the Python???

Looking forward to hear from the clever people.

cheers
Evan

---

### Post by kansasnoob on 2016-06-06
Both hplip and hplip-gui are in the repos so why not just:

```
sudo apt-get install hplip hplip-gui
```

---

### Post by sir.Evan on 2016-06-06
Thank you so much Kansanoob,

such a simple answer and it works first time.!!!! I love the KISS principle.
Dont understand why other people makes it so difficult.

Once again thank you:D
[COLOR=#DD4814][COLOR=#000000]
[/COLOR][/COLOR]

---

### Post by bob brazie on 2017-01-01
Thanks. The version in the repos is 3.16.3.
There is a newer version 3.16.11.
How can I up grade to the newer version.
Thanks in advance.

---

### Post by lubuntalb on 2017-03-15
> **kansasnoob said:**
> Both hplip and hplip-gui are in the repos so why not just:

```
sudo apt-get install hplip hplip-gui
```

Thank you very much!!!
I had the same problem and your suggestion worked very fine.
I just needed to add the printer using ubuntu printer menu.

---

