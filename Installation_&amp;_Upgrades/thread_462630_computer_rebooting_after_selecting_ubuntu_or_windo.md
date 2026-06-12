---
title: "computer rebooting after selecting ubuntu or windows xp at startup!"
date: 2007-06-02
forum: Installation &amp; Upgrades
---

### Post by ezekielnin on 2007-06-02
Hi,

I wanted to test ubuntu using WUBI on my laptop but now I can't load any os , not even win xp. Someone help please! :(

When I try to reboot and wheter I select ubuntu or windows XP the computer reboot completely 

Is this easy to fix? Right now I'm using Knoppix live cd 5 ... I'm so happy i had this... i don't want to format ... i got some unsaved work. If possible i'd like to repair this.

-- here's my boot.ini file content... perhaps this can be fixed here --

[I][boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professionnel" /noexecute=optin /fastdetect
c:\grldr="Ubuntu"[/I]

---

### Post by ezekielnin on 2007-06-02
Ok, tried to modify the boot.ini to this :

[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professionnel" /fastdetect /NoExecute=OptIn

And it still reboot automatically, the only difference is that it doesn't ask for a OS choice.

Anyone has an idea what can solve this issue?

thks

---

### Post by ezekielnin on 2007-06-03
I'll try to use windows xp cd recovery console.

---

### Post by abn91c on 2007-06-03
you need to check you spelling when you edit your file in the entry microsoft windows xp professional, If you are able to get into windows xp go to my computer>properties.hardware>hardware profiles changed the time to something like 20 or 30 seconds

---

### Post by ezekielnin on 2007-06-03
when you go there, it's the boot.ini that you modify. Like you can see above it's already to 15 seconds, which doesn't make any difference since there only one choice it will boot the first one (xp) right away.

---

### Post by ezekielnin on 2007-06-07
well anyways - only weay to solve this .. i had to format and re-install windows xp... I'm sad... i thought that WUBI was a NO-RISK installer ... I guess I'll have to wait until it's not beta anymore.

---

