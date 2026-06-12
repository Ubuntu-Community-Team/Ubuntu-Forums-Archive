---
title: "Ubuntu 24.04 RPi5 broken after update"
date: 2024-09-06
forum: Installation &amp; Upgrades
---

### Post by pol2095 on 2024-09-06
[COLOR=#555555][FONT=Roboto]Hello,[/FONT][/COLOR]

[COLOR=#555555][FONT=Roboto]following an update of Ubuntu 24.04 ARM64 on my Raspberry Pi 5, after rebooting the message appears :[/FONT][/COLOR]

> cloud-init : +0000, Datasource DatasourceNone. Up 34.81 seconds
cloud-init : cc_final_message.py[WARNING]: Used fallback datasource

[COLOR=#555555][FONT=Roboto]if I do Ctrl + Alt + F4, I get the console[/FONT][/COLOR]

[COLOR=#555555][FONT=Roboto]there is no Grub, so no recovery mode on the RPi5[/FONT][/COLOR]

[COLOR=#555555][FONT=Roboto]how can I repair Ubuntu?[/FONT][/COLOR]
[COLOR=#555555][FONT=Roboto]thanks[/FONT][/COLOR]

---

### Post by sloancli on 2024-09-06
Since you are not running a cloud instance, you can just disable `cloud-init`.

```
sudo touch /etc/cloud/cloud-init.disabled
```

1. If you just press Enter does it bring you to the terminal login prompt?

2. After the boot fails, can you SSH into the Pi?

---

### Post by pol2095 on 2024-09-07
I tried this but it doesn't fix the problem.
On RPi5 is-it possible to start on an other Kernel like amd64 > advanced options ?

---

### Post by sloancli on 2024-09-07
You could not login, or the command did not work?

Can you switch to another console with CTL-ALT-F3?

---

### Post by pol2095 on 2024-09-07
Sorry, I fixed the problem
> sudo apt update
sudo apt upgrade

---

