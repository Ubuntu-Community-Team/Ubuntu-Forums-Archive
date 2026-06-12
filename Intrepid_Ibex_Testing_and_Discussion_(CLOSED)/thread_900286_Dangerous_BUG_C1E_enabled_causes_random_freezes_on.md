---
title: "Dangerous BUG: C1E enabled causes random freezes on P5Q mobo"
date: 2008-08-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by grigio on 2008-08-25
I've reported the bug here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/260639](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/260639)

Some interesting thread about this issue, that could also DAMAGE your hardware:
[http://vip.asus.com/forum/view.aspx?id=20080713214821640&board_id=1&model=P5Q&page=1&SLanguage=en-us](http://vip.asus.com/forum/view.aspx?id=20080713214821640&board_id=1&model=P5Q&page=1&SLanguage=en-us)
[http://vip.asus.com/forum/view.aspx?id=20080701022733828&board_id=1&model=P5Q&SLanguage=en-us&page=3](http://vip.asus.com/forum/view.aspx?id=20080701022733828&board_id=1&model=P5Q&SLanguage=en-us&page=3)

---

### Post by jaymode on 2008-08-25
I wonder if that is the only motherboard affected. I am experiencing random freezes also. I will try to disable C1E and see how it goes.

---

### Post by autocrosser on 2008-08-25
I have found this to be happening on my system--added to the bugreport--Gigabyte GA-P35-DS3L.

---

### Post by leech on 2008-08-25
I haven't had this problem on mine yet (fingers crossed) but someone on those forum posts said they didn't have the issue under Linux, only Windows (non-safe mode).

I also haven't updated my bios yet, though was thinking about doing so.

Leech

---

### Post by jaymode on 2008-08-28
Disabling C1E solved my issues on an Abit AB9 Pro.

---

