---
title: "major bug causes crash if dsl cable is unplugged"
date: 2012-06-10
forum: Installation &amp; Upgrades
---

### Post by Pedroski55 on 2012-06-10
Hi, I have a new installation of Ubuntu 12.04. I  like it. Before this I used Fedora 16, which had a problem: every time I unplugged the dsl cable, the computer froze! Nearly a year ago, I reported this to bugzilla, but no solution was ever offered. I installed the latest Fedora 17, **and this problem was gone!!** But, Fedora 17 was not very good, had other problems, so I went for Ubuntu. 

Now I have the same old problem back: **unplug the dsl cable, machine freezes.** Linux cannot reboot, even if I choose recovery mode. The only way to get Linux started is to boot Windows, then reboot.

[SIZE=4]Does anyone here have any idea what this is?? [/SIZE]

I have a Toshiba Satellite C600D with an ATI Radeon 6310 Graphics chip. I am not using the proprietary graphics driver.

I don't need high end graphics, I only use this computer for school really.

---

### Post by kesman on 2012-06-25
Did you find a solution to this yet? I'm having similar problem with Acer eMachines E625 on Ubuntu 12.04. It wouldn't even boot to LiveCD without the network cable plugged.

If I unplug it, XORG freezes and I have to restart the machine by accessing terminal with ctrl-alt-f2 with ```
sudo shutdown -r now
```

I found this from AskUbuntu: [http://askubuntu.com/questions/134647/system-crashes-when-internet-connection-is-unplugged](http://askubuntu.com/questions/134647/system-crashes-when-internet-connection-is-unplugged) it's very similar!

---

### Post by Pedroski55 on 2012-06-25
Yeah well, you're lucky, I can't do anything if I unplug the dsl cable. Just press the off switch, until the machine goes off, then boot windows. I'm pretty sure this has to do with Network Manager.

---

