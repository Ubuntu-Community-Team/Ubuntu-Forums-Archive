---
title: "Upgrade HELP!"
date: 2006-05-15
forum: Installation &amp; Upgrades
---

### Post by majkmil on 2006-05-15
I am upgrading to dapper through update manager. I have two problems so far. The first one was ( unable to loade image text-editor ). The install resumed only to stick at configuring pcmcia-cs.  Anyone know what I should do?   Thanks

Edit:  I think system froze. Anything I can do?

---

### Post by Sef on 2006-05-15
What are your system specs?

---

### Post by majkmil on 2006-05-15
asus a7n8x, athlonxp 2000, ati 9600,  1Gb ram,  Do you need anything else?    Thanks

---

### Post by majkmil on 2006-05-16
My dapper install stalled at pcmcia probe or something. Had to hard boot and can only get into a 686 kernel but not everything is there. It did upgrade because the GUi is a little different. I dont have internet so I cant dist upgrade again. Am downloading live cd and will try with synaptic. Unless you think I can do anything from the command line.   Thanks

---

### Post by Sef on 2006-05-16
Maybe use 'noapic nolapic' when you try the live CD

---

### Post by majkmil on 2006-05-16
Thanks Sef,  I was able to get into a different kernel with limited usability but I was able to edit my network interfaces file and got onto the network. Then I (dpkg --configure -a) and it finished the install. I think I saw it fail the pcncia thing and just finished. Everything seems to be OK.   Thank You

I want to say I am sorry for having two threads going at the same time.

---

### Post by Sef on 2006-05-16
You're welcome.   As for the two threads, we all make mistakes.  It is learning from them that is important.

---

