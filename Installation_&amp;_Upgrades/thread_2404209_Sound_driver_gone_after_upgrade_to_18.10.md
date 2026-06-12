---
title: "Sound driver gone after upgrade to 18.10"
date: 2018-10-21
forum: Installation &amp; Upgrades
---

### Post by goodidea on 2018-10-21
I did upgrade from 18.04 to 18.10 and completely list sound.
Here are some result of some commands:
aplay -l
aplay: device_list:272: no soundcards found...

lspci | grep -i audio
00:1f.3 Audio device: Intel Corporation 100 Series/C230 Series Chipset Family HD Audio Controller (rev 31)
01:00.1 Audio device: NVIDIA Corporation GP106 High Definition Audio Controller (rev a1)

cat /proc/asound/card0/codec* | grep Codec
Codec: Realtek ALC898

---

### Post by dino99 on 2018-10-21
Are the Settings -> Sound settings correctly set ? (from top right bar icon menu then tool icon on bottom left menu)

---

### Post by goodidea on 2018-10-21
Sound settings are empty! Nothing to set...[ATTACH=CONFIG]281400[/ATTACH]

---

