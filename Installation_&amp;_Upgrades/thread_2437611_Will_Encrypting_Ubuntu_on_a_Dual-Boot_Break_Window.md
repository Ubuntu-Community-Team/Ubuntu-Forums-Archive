---
title: "Will Encrypting Ubuntu on a Dual-Boot Break Windows?"
date: 2020-02-26
forum: Installation &amp; Upgrades
---

### Post by jbh54enwiler on 2020-02-26
I'm planning on dual-booting Windows 10 and Ubuntu on a new computer I'm buying for college, since my college requires Windows.  I'd like to encrypt my installation during setup for security, but since Windows will also be on the same hard drive, I'd like to know whether encrypting Ubuntu will damage the WIndows partition.  In other words, would the encrypt option only encrypt the Ubuntu partiton or would it encrypt the entire hard drive and cause Windows to stop working?

---

### Post by TheFu on 2020-02-26
When it comes to Linux there are things that are easy, things that are not so easy, things that are hard and things that are impossible.  What you ask isn't impossible, but you are in the very, very, hard area with wiping the entire disk being highly probable.

The ubuntu installer won't do what you seek automatically.  For encryption, it will wipe the entire HDD.
To get a feel for what you are trying to accomplish, look for the Encryption thread here started by Paddy.

Perhaps I could suggest a different alternative?  Use virtual machines.  Choose to have either Windows or Linux as the hostOS.  The system that needs the fastest graphics should be the host. Any guest VMs only get a virtual GPU, which is usually sufficient for low-end games and definitely sufficient for programming, servers, or creating documents.  Only the hostOS needs to be fully encrypted this way.

When doing full encryption, make certain you have perfect backups.  If anything happens to the data on encrypted storage, data recovery efforts won't work.

I've been running Windows as a guest under Linux over 10 yrs.  It works well enough for all my needs, which have become less and less over time.  I'm down to just 2 things where Windows is required now.

---

### Post by EuclideanCoffee on 2020-02-26
Here's a link to Paddy's thread. Very helpful advice. But what you're asking for isn't so easy to do. Good luck. :)

[https://ubuntuforums.org/showthread.php?t=2399092](https://ubuntuforums.org/showthread.php?t=2399092)

---

### Post by jbh54enwiler on 2020-02-26
OK thanks.  I'll just forgo the encryption then.

---

### Post by mastablasta on 2020-02-27
college requires windows 10 for what? if i went to study today i would get a laptop with 8 or 16GB ram and load windows in virtualbox. where i studied the only thing i would have needed windows for would be maybe (really maybe since we had to submit papers anyway) MS office and SPSS. for everything else, linux would be fine. the only thing windows 10 would be needed is specialised app that only works on windows and GPU accelerated app (e.g. games or some GPU development app )

just use virtual box or similar and place it there, then encrypt the host os. problem solved. 

for example - ubuntu inside windows: [https://itsfoss.com/install-linux-in-virtualbox/](https://itsfoss.com/install-linux-in-virtualbox/)
or windows inside ubuntu: [https://itsfoss.com/install-windows-10-virtualbox-linux/](https://itsfoss.com/install-windows-10-virtualbox-linux/)

there are also prepared images of linux. one of them is turnkey linux (Debian based) another one is bitnami (ubuntu based): [https://bitnami.com/stacks](https://bitnami.com/stacks)
so you can just unpack them, load them into virtualbox, select password, and start working. no install needed as these are already preinstalled. this is a good option if all you want to do is test something.

you will find such premeade images of ubuntu on OSboxes.: [https://www.osboxes.org/ubuntu/](https://www.osboxes.org/ubuntu/)

---

