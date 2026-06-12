---
title: "Have to re-install Linux, what to backup?"
date: 2005-06-16
forum: Installation &amp; Upgrades
---

### Post by dolny on 2005-06-16
I have separate partitions for /home/ /usr/ /usr/local/ /var/ /srv/ etc.

I installed it like that cause I was a newbie. Now I have to reinstall Linux because Windows screwed it up totally and I want to save as many programs and settings  I had on my Kubuntu before. Btw. I would like to limit the number of partitions. How do I do that? I mean I want to save home and stuff but don't know how to do that - limit the number of partitions and save the settings.

Can anybody help?

---

### Post by defkewl on 2005-06-16
You could tar the whole partition if you want. Otherwise just leave it as it is, but don't format those partitition when reinstalling it. After you have reinstall Ubuntu, put back the information about your partition on /etc/fstab.

---

