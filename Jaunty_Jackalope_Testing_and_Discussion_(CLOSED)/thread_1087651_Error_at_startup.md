---
title: "Error at startup"
date: 2009-03-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by eNry92 on 2009-03-05
when i start my jaunty i see this error when jaunty booting (i haven't uspalsh):

exec of program '/sbin/' failed


and


synaptic was reset on resume, see synaptics_resume_reset if you have trouble on resume




i'm the only??

---

### Post by Darkshade on 2009-03-05
No such errors here.

---

### Post by MacUntu on 2009-03-05
Maybe related to this: [https://bugs.launchpad.net/ubuntu/+source/wireless-crda/+bug/336915/comments/4](https://bugs.launchpad.net/ubuntu/+source/wireless-crda/+bug/336915/comments/4)

---

### Post by nyarnon on 2009-03-05
Fine here, why don't you have usplash? How did you remove it?

---

### Post by eNry92 on 2009-03-05
> **nyarnon said:**
> Fine here, why don't you have usplash? How did you remove it?

i use boot up manager

```
sudo apt-get install bum
```

so.. i have a problem with wireless, network manager and wicd don't connect to my wireless connection, ethernet too...

with other wireless all ok :(:(

---

### Post by Darkshade on 2009-03-05
> **eNry92 said:**
> i use boot up manager

```
sudo apt-get install bum
```



I'm using start-up manager for that.

```
sudo apt-get install startupmanager
```

---

### Post by nyarnon on 2009-03-05
Well with this kind of info my best guess is you BUMmed your configuration. But without pun, how did you remove usplash. I seriously suspect your problem starting there.

I take that back just looked up bum. My first remark sticks. Go back to square one, do not pass start, you do not collect a bonus.

---

### Post by ronacc on 2009-03-05
I had kerneloops catching that until I moved to the 2.6.29 rc's .

---

