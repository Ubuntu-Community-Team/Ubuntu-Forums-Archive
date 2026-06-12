---
title: "apt update error"
date: 2020-04-05
forum: Installation &amp; Upgrades
---

### Post by candidoaramburu on 2020-04-05
Hi,

My flavor is Ubuntu 18.04.3 LTS  Bionic.  When I have tried  install PHP  ```
sudo apt update && sudo apt --fix-missing install php
``` the process has broken with these warning:

[B]Err:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-updates/main amd64 php7.2-common amd64 7.2.19-0ubuntu0.18.04.2
  404  Not Found [IP: 91.189.88.142 80]
Err:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-updates/main amd64 php7.2-json amd64 7.2.19-0ubuntu0.18.04.2
  404  Not Found [IP: 91.189.88.142 80]
.....
E: Fallo al obtener [http://security.ubuntu.com/ubuntu/pool/main/p/php7.2/php7.2_7.2.19-0ubuntu0.18.04.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php7.2/php7.2_7.2.19-0ubuntu0.18.04.2_all.deb)  404  Not Found [IP: 91.189.88.142 80]
E: Anulando la instalación.
[/B]

The complete warnings and content of sources.list are in the attatched files.

I suppose that sources.list is corrupted and I need clean it ...but how must I do reedit it? 

Thanks in advance

---

### Post by manziscw on 2020-04-05
Hello,

have you tried to only run 

```

sudo apt update

```

and what is the console output there?

Seems like the List and address of available Packages on your system is out of date.

Greetings

---

### Post by candidoaramburu on 2020-04-05
> **manziscw said:**
> Hello,

have you tried to only run 

```

sudo apt update

```

and what is the console output there?

Seems like the List and address of available Packages on your system is out of date.

Greetings

Hello,

Yes, I have first tried ```
sudo apt update 

```

I attatched the console output file.

Regards
Cándido

---

### Post by manziscw on 2020-04-05
It seems so that apt is trying to download some old files that doesn't exist anymore

maybe u should try just

```

sudo apt update && sudo apt install php

```

Whats the console output here?

Greets

---

### Post by deadflowr on 2020-04-05
You're hitting repositories that have no armhf architecture based archives.
So it tells you those are not found and is erring out. 
When that happens it reverts to a known safe state which holds older package lists.

Some readings:
[https://askubuntu.com/questions/705895/how-to-fix-a-failed-to-fetch-binary-armhf-packages-error-during-apt-get-update]("https://askubuntu.com/questions/705895/how-to-fix-a-failed-to-fetch-binary-armhf-packages-error-during-apt-get-update")
[https://answers.launchpad.net/ubuntu/+question/641318]("https://answers.launchpad.net/ubuntu/+question/641318")

---

### Post by candidoaramburu on 2020-04-05
I have attached the file of the output command:

```
sudo apt update && sudo apt install php
```

I don't know if the repository of arm architecture can disturb the process  on amd64 

Regards
Cándido

---

### Post by deadflowr on 2020-04-05
> I don't know if the repository of arm architecture can disturb the process on amd64

Just having the architecture type affects apt.
Since having it tells the system to look for it in the archives, which it does and does not find, leading to the issue at hand.

---

### Post by candidoaramburu on 2020-04-05
Thanks,

I have change "deb" for "deb [arch=amd64]" in source.list and know I can install php ..... maybe know the arm cross-compiler have problems . I must learn how to install arm tools for outbox development.

Regards
Cándido

---

