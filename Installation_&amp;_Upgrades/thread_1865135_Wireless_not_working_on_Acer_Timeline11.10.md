---
title: "Wireless not working on Acer Timeline/11.10"
date: 2011-10-19
forum: Installation &amp; Upgrades
---

### Post by solstince on 2011-10-19
Hi all,

I've used Ubuntu casually for a year or so and never had any trouble getting wireless to work on a laptop, after playing with the settings a bit. However I just installed 11.10 on a brand new Acer Aspire Timeline(X 4830T) (using wubi) and its not working...

The wireless is clearly enabled, and all the networks show up. It just tries to connect and then can't, back and forth, perpetually, before giving up. Its definitely not the network the same one works fine when I'm booted in Windows. Doing sudo rfkill list gives

phy0: Wireless LAN Softblocked: no Hardblocked: no

and that's it.

Any advice? I dont want to return this laptop but I also don't want to keep it if I'm not going to be able to get this to work. Should I try 10.04?

- Charlotte

---

### Post by 23dornot23d on 2011-10-19
Have a look in the failed upgrades list below on solved for wireless .....

until someone gets back to you on this one ....

maybe there is already one that gives a solution to this problem.

---

### Post by MARP1961 on 2011-10-19
Try this:
Click the spinning wi-fi icon, click your network and select 'Edit Connections.' Check that you have set it to connect automatically and check the box to enable it for 'All Users.'

I have noticed similar behaviour with a new installation and the above 'treatment' works for me.

---

### Post by solstince on 2011-10-19
Thanks, I'd already checked that it was set to 'all users' and 'connect automatically', and it is.

It IS working now- for the first time- and I didn't change anything. I know it wasn't just the network being strange because I've had a strong signal on this laptop(my old one) the entire time. Very confused as to why it would suddenly decide to work when I literally haven't touched it, I'm sure it won't last long. Are there known wireless problems for this laptop in 11.10?

---

### Post by solstince on 2011-10-22
bump- it doesn't work at all now, and I'm stumped. I'll have to return this laptop in the next few days if I can't get it to work, which is a shame because I love the design and specs of it, but if I can't get wireless on Ubuntu its useless to me.

---

### Post by sat87 on 2011-10-26
I bought Aspire Timeline(X 4830T) few days back and have installed ubuntu 11.10 , out of the box direct after installation, Wired network worked, but not wireless, then after clicking on updating (proprietary) drivers and activating Braodcom wireless drivers, its working now. till now I dint loose the connection, may be after few days I will be able to tell about its stability.

---

