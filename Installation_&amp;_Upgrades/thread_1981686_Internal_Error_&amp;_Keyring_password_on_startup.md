---
title: "Internal Error &amp; Keyring password on startup"
date: 2012-05-17
forum: Installation &amp; Upgrades
---

### Post by bladefallcon on 2012-05-17
I recently installed 12.04 on my system. After a few days I began to get this message popping up saying that a program wanted access to my keyring "default" and I needed to enter the password. If I cancel it, it just pops up 1-2 more times before goign away. (often if I do this, the system soon restarts automatically without warning or noticable cause) If I enter the password, all seems fine most of the time. 

After about a week or two, A new message started coming up at startup every time along with the keyring message: "Sorry, Ubuntu 12.04 has experienced an internal error"

I was going to copy down the details, but there is a lot of it, so I took screenshots. The first thing in the details is the executable path, which I would assume is the problem area is as follows:

/usr/lib/i386-linux-bnu/colord/colord

Package:

colord 0.1.16-2


Oddly, The date of the crash says Tuesday May 15th at 7:55 2012. I say Oddly, because This happened just 10 minutes ago, at 6:40 Thursday may 17th 2012.

These two thigns come up absolutely every time I start up my computer. Any Ideas what might be wrong? 

Computer Details:
Motherboard: ASRock z68 Extreme3 Gen3
CPU: Intel® Core™ i3-2100 CPU @ 3.10GHz × 4 
3.7 GiB
Ubuntuo 12.04

---

