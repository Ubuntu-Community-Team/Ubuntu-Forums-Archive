---
title: "Cannot finnish upgrade (apt-get broken?)"
date: 2008-03-26
forum: Installation &amp; Upgrades
---

### Post by JMO707 on 2008-03-26
I left the upgrade program this morning, wich almost downloaded all the packages it needed when I was leaving. I was using Ubuntu 7.10, and everything worked without any problems. I think that someone in my house could cancel the process or something, because now the system is crippled. Nautilus doesn't work, and I can't open synaptic or the upgrade program ("pygtk is missing") When I try to use aptitude or apt-get as root on the command line, I get a "cannot connect to the host [nameofmycomputer]" more or less. 

What can I do to finnish the upgrade? (or at least to have the system functional agaIn)

Thanks a lot.

---

### Post by Pumalite on 2008-03-26
What's the output of:
sudo dpkg --configure -a

---

### Post by carrett on 2008-03-26
Is your computer connected to the internet? Can you 

```
ping google.com
```

? Please paste the exact errors you get when you try

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by JMO707 on 2008-03-26
In all the cases I get

*sudo: unable to resolve host Prometeo3*

---

### Post by Pumalite on 2008-03-26
Check your connection. Reconfigure it if neccessary.

---

### Post by JMO707 on 2008-03-28
I solved the upgrade thing: nowI'm writing from Hardy Heron. The thing is that sudo still doesn't work. Anything with "sudo" in front of it just gives me a

*sudo: unable to resolve host Prometeo3*

---

### Post by Pumalite on 2008-03-28
It would be nice if you told us how you resolved your upgrade problem.

---

### Post by JMO707 on 2008-03-30
Hehe, yes, I'm sorry =P
It was a combination of *sudo apt-get update && sudo apt-get dist-upgrade* and *sudo dpkg --configure -a*, several times. Not very clear, but I't worked in the end.

---

### Post by Pumalite on 2008-03-30
Thank you. It's good to keep this 'whitchcraft' in mind for other times. Glad it worked for you.

---

### Post by agent8131 on 2008-04-24
See **[Ubuntu Bug #32906]("https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/32906")**

---

### Post by jmill00 on 2008-04-28
I'm having the same problem with 8.04.  Anything with sudo in front gives me *"sudo: unable to resolve host "MyHostName""* Did you find a solution for this?

---

