---
title: "Sudden Multi-System - Network related?"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by John Schuster on 2009-12-03
Hello everyone,

I'm running Ubuntu release 9.10 as I upgraded in early November.

I'm also running an HTTP server, an FTP server, and an SMTP server.  No volume mind you, but they all worked until about last Saturday.  I can't be sure it wasn't even Thursday or Friday as I hosted a Thanksgiving Dinner and had my brother visiting.

At first I thought it was just Apache2 that was broken, but later found the FTP and mail issues.  It turns out I could hit localhost and pull up my homepage.  I cannot see this page from other machines.

I can send mail out but cannot send mail in.

I can get the FTP server to say "Connected to.." my site, but then it times out saying "Connection closed by remote host."

I believe there is some common thread to all this - it is as if all the servers have been in some manner disconnected or made unable to hear the outside world.

I am not a network engineer but it seems like there is a single root cause to my woes.

Any thoughts appreciated!

Thanks,

John Schuster

PS - I'm also new to using the Ubuntuforums so please forgive any posting errors.

---

### Post by John Schuster on 2009-12-03
All seems repaired now.

I believe by correcting a corrupted /etc/network/interfaces file, I have restored all functionality.

I'm not sure what happened, but I am trying harder to manage my configurations.  It is enough trouble to make something work the first time, so if I'm smart, I write down how I made it work once.

---

