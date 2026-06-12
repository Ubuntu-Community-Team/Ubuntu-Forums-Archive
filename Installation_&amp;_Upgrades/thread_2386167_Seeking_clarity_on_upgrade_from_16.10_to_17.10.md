---
title: "Seeking clarity on upgrade from 16.10 to 17.10"
date: 2018-03-01
forum: Installation &amp; Upgrades
---

### Post by ciordia9 on 2018-03-01
Yes, I missed my upgrade windows and I'm kicking myself for not following along closer. For some reason I thought I had more time. I didn't.

I'm trying to follow the instructions here:
[https://andreas.scherbaum.la/blog/archives/950-Upgrade-from-Ubuntu-16.10-yakkety-to-17.10-artful.html](https://andreas.scherbaum.la/blog/archives/950-Upgrade-from-Ubuntu-16.10-yakkety-to-17.10-artful.html)

I'm just confused on it's first replacement since mine don't line up at all due to VPS:

*sed -**i -e*[I] 's/de.archive/old-releases/' /etc/apt/sources.list
It might not be "de.archive" in your sources.[/I]*list**, but rather another TLD. After that, edit the file and comment out the entries for "partner" and "security".*

I use linode mirrors and none of them are archive or de.archive--

eg: deb [http://mirrors.linode.com/ubuntu/](http://mirrors.linode.com/ubuntu/) yakkety main restricted, deb [http://mirrors.linode.com/ubuntu/](http://mirrors.linode.com/ubuntu/) yakkety-updates main restricted, etc.


So with that in mind, what am I looking to change to put this on track?

---

### Post by Impavidus on 2018-03-02
Yes, you missed the upgrade window by about 8 months.

There have been some threads here that the end of life upgrade from 16.10 doesn't work. Maybe it's best to try a clean install right away.

---

### Post by ciordia9 on 2018-03-02
Heya Impavidus, I'm trying to do some search vectors to find the EOL upgrade failure points but having trouble. Do any come to mind? This is a server install running a pretty clean LAMP stack.

---

