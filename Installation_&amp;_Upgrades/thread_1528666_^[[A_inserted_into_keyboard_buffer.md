---
title: "^[[A inserted into keyboard buffer"
date: 2010-07-11
forum: Installation &amp; Upgrades
---

### Post by PerJensen on 2010-07-11
Community,

I have bought an old'lish FujitzuSiemens SCALEO H with a doublecore AMD x64 processor.

It is now installed with Ubuntu 10.04 32bit version and there is 1 very anoying problem. 

The keyboard buffer is slowly, as every 6-8 secs, filled with "^[[A" characters- The character is interpreted as "arrow up" in menus and in the console.

In GTK dialogs it is intrepreted as "Shift Tab" so that focus changes from field to field - very annoying.

It displays the behavior even when then keyboard is not attached, so it is apparently not a keyboard error.

Has anyone else seen this behaviour before - and if yes, what was the fix

Regards
Per

---

### Post by PerJensen on 2010-07-11
Ok - problem fixed, but not solved.

The machine had a Pinnacle framegrabber card installed. The messages logfile contained lots of the following entries:

Jul 11 12:40:10 pj-desktop kernel: [21664.972030] i2c IR (Pinnacle PCTV): unknown key: key=0x66 raw=0x66 down=0
Jul 11 12:40:15 pj-desktop kernel: [21670.480030] i2c IR (Pinnacle PCTV): unknown key: key=0x66 raw=0x66 down=1
Jul 11 12:40:15 pj-desktop kernel: [21670.588039] i2c IR (Pinnacle PCTV): unknown key: key=0x66 raw=0x66 down=0
Jul 11 12:40:21 pj-desktop kernel: [21676.096029] i2c IR (Pinnacle PCTV): unknown key: key=0x66 raw=0x66 down=1
Jul 11 12:40:21 pj-desktop kernel: [21676.204030] i2c IR (Pinnacle PCTV): unknown key: key=0x66 raw=0x66 down=0
Jul 11 12:40:27 pj-desktop kernel: [21681.712033] i2c IR (Pinnacle PCTV): unknown key: key=0x66 raw=0x66 down=1
Jul 11 12:40:27 pj-desktop kernel: [21681.820031] i2c IR (Pinnacle PCTV): unknown key: key=0x66 raw=0x66 down=0
Jul 11 12:40:32 pj-desktop kernel: [21687.328051] i2c IR (Pinnacle PCTV): unknown key: key=0x66 raw=0x66 down=1
Jul 11 12:40:32 pj-desktop kernel: [21687.440034] i2c IR (Pinnacle PCTV): unknown key: key=0x66 raw=0x66 down=0


I saw it yesterday, but as the logfile entries came more often than the keyboard buffer entries I ignored it.

I have taken out the Pinnacle card and the problem has vanished.

Next problem: how to make the Pinnacle card work ?

---

