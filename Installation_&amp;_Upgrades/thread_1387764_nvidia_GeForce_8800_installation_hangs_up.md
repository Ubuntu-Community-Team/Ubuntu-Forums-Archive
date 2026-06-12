---
title: "nvidia GeForce 8800 installation hangs up"
date: 2010-01-22
forum: Installation &amp; Upgrades
---

### Post by pschalkx on 2010-01-22
Hi all,

After a good year and a half of good service, I migrated from Ubuntu 8.04 to 9.10. All goes weel for the moment except for the fact that the installation process for my nvidia GeForce 8800 hangs up.

What I did is go to proprietary drivers, where I can see e a list of available nvidia drivers. I selected nvdia... 185 (the recommended version). The progress bar shows, and fills up to about 30% and then hangs up. An hour later: still hangs.
I rebooted the laptop and tried again with the same driver, and then with the other nvidia drivers, all with the same result.

Any ideas/suggestions?

Rgds,

Philip

---

### Post by tommcd on 2010-01-22
Have you tried installing the driver from the terminal?
```
sudo apt-get install nvidia-glx-185
```
Try that and post any errors you get.
Do you currently have another older nvidia driver installed? If so uninstall it first
How did you upgrade from 8.04 to 9.10? Did you do a clean install of 9.10? Or did you do a dist-upgrade to 9.10?

---

### Post by pschalkx on 2010-01-22
Hi Tom,

Thanks for the tip, I found the problem!

When I ran the manual install as you indicated, apt-get asked to insert the installation CD. So I aborted the install, went to Synaptic and noticed that I had checked the CDROM as one of the repositories.

After unchecking this from the repositories, I started the hardware drives app again and it worked fine. Many thanks.

BTW, I had done a clean install. I keep ny /home on a separate partition to keep my date between migrations.

Cheers,

Philip

---

### Post by Zannax on 2010-02-06
> **pschalkx said:**
> Hi Tom,

Thanks for the tip, I found the problem!

When I ran the manual install as you indicated, apt-get asked to insert the installation CD. So I aborted the install, went to Synaptic and noticed that I had checked the CDROM as one of the repositories.

After unchecking this from the repositories, I started the hardware drives app again and it worked fine. Many thanks.

Thanks, I had the same problem! :)

---

