---
title: "How to re-enable third party software"
date: 2018-09-03
forum: Installation &amp; Upgrades
---

### Post by satimis on 2018-09-03
Hi all,

Just upgrade Ubuntu 16.04.4 to Ubuntu 18.04.  During upgrade a warning popup```

.... You can re-enable third party software after upgrade

```

Please advise what shall I add to /etc/apt/source.list

Thanks

Regards
satimis

---

### Post by Impavidus on 2018-09-03
Use the GUI, go to your software sources and click a few checkboxes. Or open /etc/apt/sources.list in your favourite text editor and uncomment some lines.

---

### Post by satimis on 2018-09-03
> **Impavidus said:**
> Use the GUI, go to your software sources and click a few checkboxes. Or open /etc/apt/sources.list in your favourite text editor and uncomment some lines.
Hi,

Thanks for your advice.

On Terminal```

$ cat /etc/apt/sources.list > source_list.txt

```

source_list.txt is attached here. Please advise which line/lines I have to uncomment?

Thanks

Regards
satimis

---

### Post by westie457 on 2018-09-03
Probably the only one to uncomment is the very last line to enable updates to virtualbox.

---

### Post by satimis on 2018-09-03
> **westie457 said:**
> Probably the only one to uncomment is the very last line to enable updates to virtualbox.
Thanks.

Performed following steps;

1) Uncomment the line suggested
2) Rebooted PC
3) Ran Software updater
Nothing installed.  The computer is up-to-dauy

satimis

---

