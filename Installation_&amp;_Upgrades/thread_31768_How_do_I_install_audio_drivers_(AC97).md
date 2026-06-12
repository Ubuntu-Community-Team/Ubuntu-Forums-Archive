---
title: "How do I install audio drivers? (AC97)"
date: 2005-05-04
forum: Installation &amp; Upgrades
---

### Post by hoeken_ on 2005-05-04
How do I get the sound to work?
I have a MSI K8T Motherboard with AC97 audio chipset.

---

### Post by alastair on 2005-05-04
AC97 should be available with the default install - as modules probably.

Firstly a sanity check - look through your log file :

/var/log/syslog

for lines that are relevant to your chipset/sound chip e.g. I have AC97 on my laptop. I see lines on boot like :

intel8x0_measure_ac97_clock: measured 49465 usecs
intel8x0: clocking to 48000

Yours might NOT be "intel" - but look for "ac97" somewhere.

Also - list PCI devices found :

lspci

I see :

0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)

Also - list modules loaded :

lsmod

You might see a module like "snd_ac97_codec"

Anything?

---

### Post by hoeken_ on 2005-05-05
[QUOTE=alastair]AC97 should be available with the default install - as modules probably.

Firstly a sanity check - look through your log file :

/var/log/syslog

for lines that are relevant to your chipset/sound chip e.g. I have AC97 on my laptop. I see lines on boot like :

intel8x0_measure_ac97_clock: measured 49465 usecs
intel8x0: clocking to 48000

Yours might NOT be "intel" - but look for "ac97" somewhere.

Also - list PCI devices found :

lspci

I see :

0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)

Also - list modules loaded :

lsmod

You might see a module like "snd_ac97_codec"

Anything?[/QUOTE]

My syslog contains only 5 lines or something, but I have one called syslog.0, but there I can't find "ac97" anywhere, I have tried searching the document for "ac97".

---

