---
title: "HOWTO: Enable Quick Search on Synaptic (Intrepid)"
date: 2008-08-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by artir on 2008-08-19
This is really easy:

1. Enable universe and multiverse repositories. 
2. Click here: [apt://apt-xapian-index]("apt://apt-xapian-index")

---

### Post by Oldsoldier2003 on 2008-08-22
Moved from T&T moderation. A couple comments on why:

II is not released yet so II specific tutorials are not yet appropriate. 

Also, please see [here]("http://ubuntuforums.org/showthread.php?t=677396") for further information on tutorials.

---

### Post by andrewsomething on 2008-08-22
You shouldn't have to do this by the time Alpha 5 comes out. They've made room on the CD for apt-xapian-index and it will now be installed with synaptic by default. I'm really glad they did this as it's a neat new feature and if you didn't know to install apt-xapian-index it seemed broken. 

synaptic (0.62.1ubuntu7) intrepid; urgency=low

  * debian/control:
    - add apt-xapian-index to the recommends again, we have some
      space on the CDs again (thanks to Steve Langasek)

 -- Michael Vogt < [email]michael.vogt@ubuntu.com[/email]>   Thu, 19 Jun 2008 14:45:42 +0200

---

### Post by ronacc on 2008-08-22
unless they can make it work better than it does now I would not favor it being made a depends of synaptic only a "recomends" .

---

