---
title: "No Network Devices Available"
date: 2013-03-26
forum: Installation &amp; Upgrades
---

### Post by Shaun_Yute on 2013-03-26
I performed a normal system update, rebooted, and now I can't connect to the network via wifi or cable. When hovering over the network icon at the top of the screen I get No Network Devices Available. Does anyone know a way to resolve this issue? I would really like to not have to perform a reinstall as I have all kinds of movies, files, and photos on my laptop I don't want to use.


Thank you,
Shaun

---

### Post by MAFoElffen on 2013-03-26
It may help to post what specific make model of computer and what network hardware you have... This will give you the later:
```

lspci -vnn | grep -i Ethernet

```

---

### Post by MAFoElffen on 2013-03-26
After posting the above, then post or attach log: "/var/log/apt/history.log".

All that info will show what hardware you have, what drivers you should be using, what updates were applied... that might have ended up in being broke for you.

---

### Post by Shaun_Yute on 2013-03-26
I have a Pangolin Performance from System76 running Ubuntu 13.04 (which I don't remember installing). Below is the network hardware I have.

03:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 0a)

---

### Post by Shaun_Yute on 2013-03-26
[ATTACH]240589[/ATTACH]


Also I should mention that I was having issues with the update completing so I changed servers and attempted the update which did not work. I went through the software sources and noticed on the additional drivers tab that it said to finish installing the drivers restart your system. That is when the issue started, after the reboot.

---

### Post by MAFoElffen on 2013-03-26
Okay. What I gave you is not returning enough info. Not showing the wireless driver and I need to see 2 lines down to catch what driver it's using, if it is...

Try this```
lspci -nnk | grep -iA2 net
```

---

### Post by Shaun_Yute on 2013-03-27
Sorry this took so long to get to you. I am stationed overseas and am +7 EDT.

---

### Post by Shaun_Yute on 2013-03-27
Ok I may be able to backup the items I want to save so I am thinking of performing a fresh install of Ubuntu 12.10. Thoughts?

---

### Post by MAFoElffen on 2013-03-27
I'm seeing that it has no modules loaded for either network device... But that laptop was built to run Ubuntu and that was it's major selling point.

If you started on a 12.10 LiveCD and tried the option to repair existing install first, it might pick up those NIC drivers... Or to get the wired connection up first, which I think is proabably an e1000. Just a thought before a re-install.

---

### Post by Shaun_Yute on 2013-03-27
Created the LiveCD but I only get the try Ubuntu or install Ubuntu options. Also just tried a liveUSB.....same thing. But when using Ubuntu off of the liveCD or USB I am able to use wireless and connect. So it can see the drivers.

---

### Post by Shaun_Yute on 2013-03-29
Backed up all my information and re-installed 12.10 from scratch. Everything is working again. Thanks for the help.

---

