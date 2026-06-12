---
title: "newb internet problem"
date: 2007-03-19
forum: Installation &amp; Upgrades
---

### Post by geoffjay on 2007-03-19
i'm not really a newbie but i have a seriously newb type question, hopefully someone will humour me and help me out. 

i've recently installed ubuntu server 6.06, and after some configuration i went to: 
  *sudo apt-get update*

it returns a bunch of connection errors; failed to fetch [http://.](http://.)..

i've done the following to turn off ipv6:
  *echo "alias net-pf-10 off" > /etc/modprobe.d/bad_list*

i only did this because there seems to be a lot of mention of this on the internet as a potential source of problems.

my dns is working, i know this because a ping of [www.ubuntu.com](www.ubuntu.com) returns an ip of 82.211.81.212, but that's all it returns.

thanks in advance

---

### Post by louis_nichols on 2007-03-19
Has this been going on for long? I've been getting that kind of errors from some of the update servers for the past two days, so the problem might not be on your side. The way to check this is to change the country where you fetch packages from.

---

### Post by geoffjay on 2007-03-19
it's been happening for a week. and i'll give what you suggested a try, however, i'm not sure if that's the problem unless the sources that are being used would somehow effect my ability to ping a remote server.

---

