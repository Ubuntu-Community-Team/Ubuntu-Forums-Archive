---
title: "Xubuntu core 14.04.2 installer"
date: 2017-01-18
forum: Installation &amp; Upgrades
---

### Post by sergio372 on 2017-01-18
Where i can find an installer for Xubuntu core v14.04.2 x64 and x86?

:(

---

### Post by howefield on 2017-01-18
Not sure what exactly you are looking for ?

[https://xubuntu.org/news/introducing-xubuntu-core/](https://xubuntu.org/news/introducing-xubuntu-core/)

---

### Post by sergio372 on 2017-01-18
I want the old version of Xubuntu core specifically 14.04 (if exist)
That link redirect-me to version 16.10

---

### Post by sergio372 on 2017-01-18
In what version they start to do the core edition someone know?

---

### Post by ajgreeny on 2017-01-18
There is no point in installing 14.04.2 as it uses a no longer supported hardware enablement stack; you need either the 14.04, 14.04.1 or 14.04.5 versions to get an HWE that is fully supported.

Unfortunately I can not find a download site for either the 14.04 nor the 14.04.1 versions of Xubuntu at present. I'll keep looking for it.

---

### Post by Bucky Ball on 2017-01-18
You grab the 14.04 LTS mini.iso, which should be about somewhere, and do this:

> ... download the mini.iso, install, and when prompted, install the Xubuntu minimal installation task. If you’d prefer to wait until after the installer finishes to install the Xubuntu core task, you can simply type sudo apt-get install xubuntu-core^ (don’t forget the caret!) and away it’ll go.

[From here]("https://unit193.net/xubuntu/"). ;)

Any reason you want 14.04 specifically? That is out of support this year in April (Xubuntu has three years support for LTS releases). 16.04 LTS might be a better option unless there is a reason not to go there as supported until 2019 .

Xubuntu-core doesn't come in a regular ISO for anything but [the latest release, 16.10]("https://unit193.net/xubuntu/core/"). 16.04 LTS used to be available on that page but disappeared unfortunately. If think they started with 15.10. That was the first community ISO I saw and when I heard about it.

---

### Post by sudodus on 2017-01-18
Maybe there is only the meta-package **xubuntu-core**. If this is the case, you can install it from the Ubuntu mini.iso or Ubuntu Server (without installing any server packages). This is how to install **lubuntu-core**, and the correspoinding method might work also for Xubuntu.

---

### Post by Bucky Ball on 2017-01-18
> **sudodus said:**
> This is how to install **lubuntu-core**, and the correspoinding method might work also for Xubuntu.

The method for both with the mini ISO is same as far as I know. User chooses lubuntu-core installation task or xubuntu-core one or uses lubuntu-core^ or xubuntu-core^.

---

### Post by sudodus on 2017-01-18
off-topic:

I tried to write "ninja'd by Bucky Ball :-)" into the 'last edited' field, but the forum system did not let me do it.

Anyway, glad to see you :-)

---

### Post by Bucky Ball on 2017-01-18
> **sudodus said:**
> off-topic:

I tried to write "ninja'd by bucky ball :-)" into the 'last edited' field, but the forum system did not let me do it.

Anyway, glad to see you :-)

):p

---

