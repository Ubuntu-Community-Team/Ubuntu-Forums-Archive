---
title: "tried to upgrade to 10.10"
date: 2010-12-28
forum: Installation &amp; Upgrades
---

### Post by farll007 on 2010-12-28
I don't know how it happened, but now I'm not sure what to do. I just upgraded to 10.10, or so I thought, but after 4 hours and it finally said it was done and restarted i checked and found it is now version 11.04. I am completely new to Ubuntu and in no way shape or form a developer. So what should I do, is there a way to fix this or do i have to back up my files and start over?

---

### Post by Fafler on 2010-12-28
Is 11.04 giving you any problems? If it works, there's no reason you shouldn't just keep it.

Downgrading is possible, but not an easy task, so keep 11.04 or backup and re-install.

---

### Post by Rubi1200 on 2010-12-28
Hi and welcome to the forums :)

Go to Applications > Accessories > Terminal

Run this command:
```
cat /etc/*release
```If it is what I suspect, you have just encountered a known bug that says you are running 11.04 when you are, in fact, not.

Let us know what the output tells you please.

Thanks.

---

### Post by farll007 on 2010-12-28
It appears that I have that bug you mentioned. Is there a fix for that? 


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

I was looking for the new things it shows on the website for 10.10 but I havn't noticed anything different at all, except when I started up this morning my wireless is not working. I had that problem when I first bought the computer, it resolved itself the next day when it downloaded the 163 updates it was behind, but there are no new updated for this since i just downloaded it all.

---

### Post by howefield on 2010-12-28
> **farll007 said:**
> It appears that I have that bug you mentioned. Is there a fix for that? 

Here is the link to the bug.

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/690248](https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/690248)

---

### Post by Rubi1200 on 2010-12-28
Thank you howefield for posting the link.

@farll007: don't worry about it. You have 10.10 installed as you expected and now you know a command to run to check such things in the future.

---

### Post by farll007 on 2010-12-29
Thanks for the help. I'm starting to get this stuff figured out but I still have a lot to learn. I solved the wireless issues, it wasn't the OS, my kids did something to my router. I'm sure I will have many more questions as I explore and tweak my system, thanks again.

---

### Post by Rubi1200 on 2010-12-29
You are more than welcome :-)

Post anytime you have questions.

Enjoy!

---

