---
title: "Cannot install updates"
date: 2011-03-07
forum: Installation &amp; Upgrades
---

### Post by Bender09 on 2011-03-07
When I go to install updates it finds the updates and then ask me to authenticate with my password. When i do it just sits there with the authenticate button. I also does this when installing programs that have me authenticate. What is causing this and how can I fix it. 

Thank you,
Bender

---

### Post by oldos2er on 2011-03-07
Can you run **sudo apt-get update** in a terminal, and post the output here?

---

### Post by Bender09 on 2011-03-07
It pulled the updates and said reading package list 100%.

---

### Post by Bender09 on 2011-03-08
Any Ideas? thanks

---

### Post by Bender09 on 2011-03-08
I try to apply updates and this is the error i recieve.

---

### Post by lupo1939 on 2011-03-08
I have the same problem.  Monitor says apt-get is running at 50% of cpu.

sudo apt-get update reply is:

E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/

Any help greatly appreciated.

---

### Post by oldos2er on 2011-03-08
I wanted to see the terminal output so we can determine which repository is missing its gpg key. Try **sudo apt-key update**

[https://help.ubuntu.com/community/SecureApt](https://help.ubuntu.com/community/SecureApt)

---

### Post by Bender09 on 2011-03-08
oh ok sorry. misunderstood you. I will re run it when i get home and copy/paste the output here.

---

### Post by wojox on 2011-03-08
> **lupo1939 said:**
> I have the same problem.  Monitor says apt-get is running at 50% of cpu.

sudo apt-get update reply is:

E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/

Any help greatly appreciated.

Reboot. You have to many package managers open.

---

### Post by Bender09 on 2011-03-16
i got it going. thanks everyone.

---

