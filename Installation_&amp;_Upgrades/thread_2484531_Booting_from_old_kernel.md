---
title: "Booting from old kernel"
date: 2023-03-02
forum: Installation &amp; Upgrades
---

### Post by aayush25 on 2023-03-02
[https://paste.ubuntu.com/p/bZkW5QCMBn/](https://paste.ubuntu.com/p/bZkW5QCMBn/)

Reverted back to default graphic card driver nouveau, now the wifi, ethernet, touchpad, bluetooth is not working. Currently booting through a liveUSB. What should I do?

Help is hugely appreciated!

---

### Post by TheFu on 2023-03-02
Maybe the first step is to say what the issue is?

---

### Post by MAFoElffen on 2023-03-02
+1 on describing your problem.
> **aayush25 said:**
> [https://paste.ubuntu.com/p/bZkW5QCMBn/](https://paste.ubuntu.com/p/bZkW5QCMBn/)

[COLOR=#ff0000]Reverted back to default graphic card driver nouveau[/COLOR], now the wifi, ethernet, touchpad, bluetooth is not working. Currently booting through a liveUSB. What should I do?

Help is hugely appreciated!

I am guessing that your kernel updated recently and nvidia-dkms had an error building on the new kernel. Guessing that on boot, you had a black screen. Right?

Please run the [UbuntuForums 'system-info' script]("https://github.com/UbuntuForums/system-info") and post the URL of where the report is uploaded to, so we can get an idea of the hardware and config you have, to get an idea of how to help you.

---

