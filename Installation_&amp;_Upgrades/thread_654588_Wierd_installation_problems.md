---
title: "Wierd installation problems"
date: 2007-12-31
forum: Installation &amp; Upgrades
---

### Post by ftaylor on 2007-12-31
Hello,

I have ubuntu 7.10 gutsy installed and working absolutely fine on my laptop.

I'm so impressed with it that I recommended it to a friend. He installed it on his desktop using my live cd.

There are a number of things missing from system>administration in his install - most notably software sources and synaptic package manager. Has he done something wrong?

Any help appreciated.

---

### Post by meindian523 on 2007-12-31
Well,only he can reply to that.

And I agree,that's weird.

---

### Post by ftaylor on 2007-12-31
Any known wrong moves in installation folks?

---

### Post by meindian523 on 2007-12-31
Other than partitioning,I can't think of any...that's where most people go wrong.Also,Ubuntu doesn't have any Advanced Install unlike Mandriva,so what could be the problem.

Ask your friend to try to install from command-line.

```
sudo apt-get install software-properties-gtk
```
and
```
sudo apt-get install synaptic
```

Hopefully,we won't come across:

> The program "apt-get" is not installed.To install,please type "sudo apt-get install apt". LOL.

---

### Post by ftaylor on 2007-12-31
Yes, but without software sources, I dont know how that's gonna work. From live CD I suppose. Think he's gonna reinstall anyway.

---

### Post by meindian523 on 2007-12-31
I think since he has just installed,the CD-ROM itself would be a source of packages,so he would be able to install from CD ROM that is IF apt-get is installed.

---

### Post by meindian523 on 2008-01-04
Would you please respond to the thread you created yourself?Or if your friend reinstalled and everything worked out fine,please mark the thread solved.

---

