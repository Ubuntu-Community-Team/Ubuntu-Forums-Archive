---
title: "Local Update Server -- possible?"
date: 2008-11-27
forum: Installation &amp; Upgrades
---

### Post by r0b0h0b0 on 2008-11-27
We've recently replaced a bunch of windows machines here at work with Ubuntu 8.10 and so far, so good. The frequent updates are nice, but here in South Africa, bandwidth is really expensive.

Is there a way to set up one machine on the network as a kind of an "update server" where IT downloads all the latest updates, and then the other machines update from IT? Once each machine has downloaded the necessary stuff from this local update server, it then searches the repositories for updates specific to the software installed on it.

It breaks my heart (and my bank) to watch four machines download the exact same xxxMB of updates, individually.

---

### Post by ajgreeny on 2008-11-27
Have a look at aptoncd.  It allows you to update one machine and then transfer the downloaded files to the others simply by creating an iso file (or burning a CD) of all the .deb files in /var/cache/apt/archives and copying it to the other computers.  I use it all the time for my two machines.

---

### Post by cariboo on 2008-11-27
This:

[http://www.debuntu.org/how-to-set-up-a-repository-cache-with-apt-cacher](http://www.debuntu.org/how-to-set-up-a-repository-cache-with-apt-cacher)

may bw what you are looking for.

Jim

---

### Post by r0b0h0b0 on 2008-11-28
Jim, I haven't tried it yet, but by the looks of it, that is *exactly* what I am looking for. Many thanks.

---

### Post by ideewoww on 2008-11-28
[img]http://www.ideewomen.com/cn/uploads/200811111137220.jpg[/img]Women's beauty sourses from heart, just like the IDee jewelry reveals unique beauty carelessly, palpitates the will of the people easily. The IDee accessories are all designed uniquely, both elegant and fashion. Especially the series of mounting is matched by luxurious swarovski quartz, pearl, agate and so on, sparkles the eye-catching ray. The intoxicant appearance will let you unfold the graceful makings all the time. How can&#8217;t you be moved?  Wearing the charming IDee jewelry, your mood will be bright everyday. The IDee jewelry is worth possessing!

---

