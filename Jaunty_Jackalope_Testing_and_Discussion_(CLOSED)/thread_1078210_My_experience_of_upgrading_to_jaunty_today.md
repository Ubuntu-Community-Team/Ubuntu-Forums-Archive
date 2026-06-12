---
title: "My experience of upgrading to jaunty today"
date: 2009-02-23
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by tgpraveen on 2009-02-23
so i couldnt resist the tempation any longer and i did upgrade to jaunty
overall it was smooth no data loss. system boots up.

but i do seem to be affected by a bug
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/332017](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/332017)

it has a fix committed so soon this problem should go away.

apart from that 

1. some weird stuff like epiphany browser installed itself automatically. dont know how? anybody else experienced this?

2. totem is something i use a lot. and was glad to see that now one feature that was added to it was i being able to manually select the subtitle file which is nice.

3. the new notifications finally look like how mark had showed on the mockup on his blog. and they look WONDERFUl absolutely gorgeOUS.

4.the new feature which sets the font size automatically didnt work well for me either and hence i ended up with big font size. so i just had to manually change it back.

so basically no showstoppers. and i fell good. with the new version of all programs and all. till now i havent explored much of this new version so will see what else is intresting and post.


another thing is taht for me somehow the boot time has not changed at all from intrepid in fact it has increased by a few second. currently from the time i switch on the desktop to the time i get the desktop it takes aroun 2:15 secs. before u freak i have a p4 2.4ghz process and 1.5gb ram. so maybe that might be the cause of the delay. also i have 2 screenlets enabled. and one panel applet. which might be adding a few secs.

also note while timing the whole start up process grub was skipped instantly by selecting the os. and the time for putting in password was subtracted.


so if any of u wanna add anything or wanna give some solutions then pls reply.

---

### Post by Ng Oon-Ee on 2009-02-23
I was just reading about a bug in compiz vis-a-vis gnome-wm. Could you try disabling compiz totally and see if that helps?

---

### Post by mc4100 on 2009-02-23
> **tgpraveen said:**
>  currently from the time i switch on the desktop to the time i get the desktop it takes aroun 2:15 secs. before u freak i have a p4 2.4ghz process and 1.5gb ram. so maybe that might be the cause of the delay. also i have 2 screenlets enabled. and one panel applet. which might be adding a few secs.

I get from selecting the kernel to a usable desktop in just over a minute. With a 1.6 GHz first-gen Intel Core Duo and 1 GB of memory.

---

### Post by jmmL on 2009-02-23
Is it possible some of these problems are from doing an upgrade, rather than a fresh install?

Could that explain the very slow boot?

I get from grub to desktop in just under a minute with a core 2 duo at 1.6GHz (t5450), 2GB of RAM and a 160GB, 5400rpm HDD.

---

### Post by theromanone on 2009-02-26
I thought the way to get the fast 9.04 boot time was to use ext4 formatting? I'm guessing you stayed with intrepid's ext2/3?

---

### Post by BGFG on 2009-02-26
My upgrade attempt last night failed miserably. But i do have all kinds of crap in here, so i'll just do a fresh again...

---

### Post by rburkartjo on 2009-02-26
just upgrade to 9.04 works like a charm. only problem i had was with vlc cant get it to work but that is it

---

### Post by BGFG on 2009-02-26
I have quite a few programs and libraries installed from tar.gz archives. the upgrade said that I would have to upgrade something like 1200+ packages so i think that is why it bummed out. In addition to which many programs i currently have installed would not work afterwards.

Finally changed my server to United States and did a reload, then all was well.

---

### Post by taavikko on 2009-02-27
Use "bootchart" to chart the boottime...
Good to see where the time is used.

[IMG]http://forum.ubuntu-fi.org/index.php?action=dlattach;topic=13017.0;attach=2515;image[/IMG]

---

### Post by tgpraveen on 2009-02-27
k.now the bug of p4 systems cpu freq seems to be fixed and my boot time has gone down by few secs.

---

### Post by Kow on 2009-02-27
> **BGFG said:**
> My upgrade attempt last night failed miserably. But i do have all kinds of crap in here, so i'll just do a fresh again...

Not a good time to upgrade to jaunty. The repository is in the midst of a major dep upgrade (python 2.5->2.6). All kinds of things are knowingly broken.

---

### Post by BGFG on 2009-02-27
> **Kow said:**
> Not a good time to upgrade to jaunty. The repository is in the midst of a major dep upgrade (python 2.5->2.6). All kinds of things are knowingly broken.

Ahh. thanks :0 cause everything was going along swimmingly, Upgrade manager had calculated that everything would take around 3 hrs and had started downloading, then i left and came back and saw 'upgrade aborted'.

No biggie though. The jaunty feedback speaks to speed and stability so a 'fresh' will be an enjoyable experience. Just wanted to upgrade to see if i could help with bugs....

---

