---
title: "Driver help..."
date: 2011-01-18
forum: Installation &amp; Upgrades
---

### Post by word327 on 2011-01-18
Hello all. I've got a box with an Asus M4N68T-M V2. Ubuntu 10.04 installed without a hitch. I've scoured the internet for about a week, but I simply can't find the onboard LAN drivers, and I can't an my old PCI NIC laying around anywhere. The LAN chipset is RTL8211CL-VB. If anyone knows a way around my problem (even a driver wrapper, or anything I can at least TRY), please advise.
Thank you all for your time!

---

### Post by amsterdamharu on 2011-01-18
Just to make sure what's in your machine could you execute the following command and post the output?

```
sudo lspci -k
```

To execute the command you can press alt + F2, type gnome-terminal and click run. Then copy the command and paste it in the terminal (black screen that showed up after you clicked run). Use the mouse to paste commands in the terminal.
Then you can select all the text in the terminal, right click and select copy. When pasting it here please wrap it in &#91;code] &#91;/code] tags. In other words: &#91;code]Your pasted stuff&#91;/code]

---

### Post by dino99 on 2011-01-18
into a terminal, try either:

sudo update-initramfs -v -u -k `uname -r`
sudo update-initramfs -u

---

### Post by egolfb@gmail.com on 2011-03-15
So did any of these produce a solution? I have just built a server using this motherboard and ubuntu 10.10 Server and have the same issue. I had to install and old lan card to do the install, but would like to use the Gb onboard card if possible.

Thanks for any help,

---

