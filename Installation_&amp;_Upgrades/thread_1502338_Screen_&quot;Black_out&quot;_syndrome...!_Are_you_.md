---
title: "Screen &quot;Black out&quot; syndrome...! Are you also facing it?"
date: 2010-06-05
forum: Installation &amp; Upgrades
---

### Post by Saurabhdua on 2010-06-05
Hi There!:(

One or some other reason keep the users detracted from Ubuntu!

Screen "Black Out" syndrome has become quite a common phenomenon with Ubuntu 10.04!

After 30-45 minutes of usage, Screen goes "Black out" & only option left is to give a manual FORCE shutdown!

Is anyone facing the same trouble!? Any suggestions?:(

---

### Post by kansasnoob on 2010-06-05
That sounds like a graphics problem. Post the output of:

```
lspci | grep VGA
```

That will display the specific graphics chip info.

---

### Post by Saurabhdua on 2010-06-05
Yes Dear!

Here it goes:::


saurabhdua@saurabhdua-desktop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
saurabhdua@saurabhdua-desktop:~$

---

### Post by Saurabhdua on 2010-06-07
Hello Kansasnoob!

Iam still awaiting your reply...!!? Where are you?

Please do not abort my issue like this! I need someone's help!

Is anyone one there(echo::)!!? Hello...Forum Moderators & administrators..where r you?

---

### Post by Saurabhdua on 2010-06-15
Is there any information whether above mentioned 'Graphics Chip Info.' is posing issues with other users!?

Are there any USB Mice issues as well, like 'Shaking cursor'?

---

