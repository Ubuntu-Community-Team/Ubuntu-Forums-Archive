---
title: "not updating to the latest version"
date: 2008-08-11
forum: Installation &amp; Upgrades
---

### Post by quizzelsnatch on 2008-08-11
Just did a fresh install of ubuntu on my computer, and when I try to update it doesn't update to the latest version. Like with kde4, it only sees 4.0.5 as the latest, and not 4.1.0, or with my kernel, it sees 2.6.24.20 as the latest, not 2.6.26.2

Am I missing something? I feel like I am missing something very obvious.

---

### Post by coffeecat on 2008-08-11
You will only get what's available in the repositories, not necessarily what is only recently released upstream. With the kernel, you will probably never get > 2.6.24 in Hardy. If newer features are needed, they'll patch them into the 2.6.24 kernel. I don't know whether KDE 4.1 will get into the Ubuntu repos. Don't forget that it takes time for the devs for a particular distro to recompile and QA an upstream release.

---

### Post by coffeecat on 2008-08-11
Just remembered - if you want KDE 4.1 on Ubuntu, you could try [this softpedia howto]("http://news.softpedia.com/news/How-To-Install-KDE-4-1-On-Ubuntu-8-04-91034.shtml"). It worked for me in my virtualised (in VirtualBox) Ubuntu, but how well it will be maintained and how it will compare to an "official" Ubuntu KDE 4.1 (if there ever is one) I really don't know.

---

