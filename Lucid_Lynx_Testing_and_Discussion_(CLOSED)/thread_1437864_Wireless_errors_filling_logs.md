---
title: "Wireless errors filling logs"
date: 2010-03-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by rockyjones on 2010-03-24
Since yesterdays update, I continually get the following error in syslog:

kernel: [  212.803390] iwlagn 0000:03:00.0: free more than tfds_in_queue (1:2)

I see one every second or two as long as wireless is turned on.  It doesn't seem to cause a big problem other than filling the log although I would assume it slows things down a bit due to the logging.  The updates so far today have not fixed this.

Anyone know the fix for this (if there is one yet) ?

Joe

---

### Post by bhaverkamp on 2010-03-25
Yup, me too! Probably should file a bug.

---

### Post by kurros on 2010-03-25
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/545585](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/545585)

---

### Post by rockyjones on 2010-03-25
I decided to go back to 2.6.32.16 until a new kernel with the fix comes out.  It doesn't have the problem.

---

