---
title: "Ubuntu Software Centre, 100% processor load"
date: 2010-03-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by mörgæs on 2010-03-07
Hi.

On a lot of occasions, Software Centre pulls 100% processor load, for example:

Open Gkrellm or another tool for watching processor activity.
Open Ubuntu Software Centre.
In the pane to the right, single-click on 'System'.

The processor load reaches 100% in several minutes. It happens on two different computers.


Do anyone have an explanation or a workaround for this?

---

### Post by robert shearer on 2010-03-07
Happens here too on occasion.

Seems to be caused and then corrected by new updates so I assume it is just 'normal' Alpha behavior and will be stable in the final release.

When it happens it is fortunate that synaptic and apt-get still work flawlessly. :D

---

### Post by rockyjones on 2010-03-07
I see the same thing running Lucid in VirtualBox using Karmic.

---

### Post by NCLI on 2010-03-07
This is an alpha, unstable and buggy software is to be expected, do not take this as a measure of the final product, blah blah blah, you know the drill.

/thread



In all seriousness, I expect the USC to be much better by the time Lucid is released.

---

### Post by dinamic1 on 2010-03-07
> **NCLI said:**
> This is an alpha, unstable and buggy software is to be expected, do not take this as a measure of the final product, blah blah blah, you know the drill.

/thread



In all seriousness, I expect the USC to be much better by the time Lucid is released.

but.. the same thing happens in 9.10 

amd 2500+ nvidia 7600gs

---

### Post by mörgæs on 2010-03-09
I have opened a bug in Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/535292](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/535292)

Great if someone would confirm it.

---

### Post by tekstr1der on 2010-03-09
Confirmed.

EDIT: It's best to use ubuntu-bug to report, so apport can collect relevant data.

---

### Post by mörgæs on 2010-03-09
Thanks, do you have some links describing ubuntu-bug?

---

### Post by tekstr1der on 2010-03-09
```
man apport-bug
```

@mörgæs: I filed a bug by this method for the same issue. Is it okay if I dupe your report?

---

### Post by mörgæs on 2010-03-09
Feel free to do whatever it takes to get attention to the bug! 

I have updated my report with Apport.

---

