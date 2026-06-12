---
title: "Ubuntu 10.10 won't run on Lenovo laptop"
date: 2011-01-24
forum: Installation &amp; Upgrades
---

### Post by ro1208984 on 2011-01-24
Dear all,

I have a problem that Ubuntu 10.10 won't run on my Lenovo Ideapad laptop. I have managed to install it over ethernet a few weeks ago an it worked fine, but whenever I try to install it from a cd, installation completes successfully, but the Ubuntu won't start. A black screen with a lot of text on it and then everything freeze. 
I have tried it without installing and it worked (live cd). I have also tried to install it on my desktop machine and it worked fine.
On my laptop, I already have a Windows 7 (64 bit) on another partition. 

Did anyone have a similar problem? Please, help

---

### Post by amsterdamharu on 2011-01-24
Can you start the laptop from harddisk and when it freezes switch it off. Then start with the CD and choose "try Ubuntu without installing". Mount the partition where Ubuntu is installed and check the following file:

(partition where Ubuntu is installed)/var/log/kern.log

There might be a hint as to why it's crashing, you cold post the last 20 or so lines here if you want.

Could you please post the output of the following command as well (from live cd):
```
sudo lspci -k
```

To execute the command(s) you can press alt + F2, type gnome-terminal and click run. Then copy one command and paste it in the terminal (black screen that showed up after you clicked run). Use the mouse to paste commands in the terminal.
Then you can select all the text in the terminal, right click and select copy. When pasting it here please wrap it in code tags: &#91;code][COLOR=Red]Your pasted stuff[/COLOR]&#91;/code]

Here is another thing to try
When you boot and get the menu where you can choose Windows or Ubuntu you can highlight Ubuntu and press e to edit the command, replace "quiet splash" with:
```
xforcevesa noapic noapci nosplash irqpoll
```

---

