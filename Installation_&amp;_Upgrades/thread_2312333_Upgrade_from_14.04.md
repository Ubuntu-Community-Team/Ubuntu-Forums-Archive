---
title: "Upgrade from 14.04"
date: 2016-02-03
forum: Installation &amp; Upgrades
---

### Post by Sarah_Young on 2016-02-03
I have Ubuntu 14.04 but its becoming slow so need an upgrade. Can anybody please suggest a good upgrade?

---

### Post by QIII on 2016-02-03
Hello!

What do you mean by "becoming slow"?

---

### Post by Sarah_Young on 2016-02-03
Everything slows down and becomes grey. Especially the Software Centre

---

### Post by Vladlenin5000 on 2016-02-03
> **Sarah_Young said:**
> Everything slows down and becomes grey. Especially the Software Centre

That usually suggests memory (or memory management) issues.

---

### Post by Sarah_Young on 2016-02-03
I thought so too but my memory is fine.

---

### Post by Vladlenin5000 on 2016-02-03
Let's see the hardware details. Please run      ```
sudo lshw -sanitize > lshw.txt
``` 


 and post lshw.txt in CODE tags or as an attachment.
Thank you.

---

### Post by ian-weisser on 2016-02-03
> **Sarah_Young said:**
> I have Ubuntu 14.04 but its becoming slow so need an upgrade. Can anybody please suggest a good upgrade?

I think you are asking the wrong question.
Unlike Windows, your Ubuntu system does not slow down with normal use.
If your system is slowing, there must be a reason.

If you really don't care what the reason is, then simply reinstall 14.04.
Or you can wait until May 2016 and upgrade to the newly-released 16.04.

If you do care what the reason is, we might be able to help you investigate. To us, that's fun.

---

### Post by grahammechanical on 2016-02-03
When application windows grey out it is because the application is busy. In some cases it might be because data has to be paged in and out of the swap partition.

Sometimes it is a something to do with the application. I am running 16.04 development version and it has Libreoffice 5 and I am finding that large Writer documents that loaded quickly in Libreoffice 4 now take longer to load in Libreoffice 5 and the window will grey out. Also the Find function seems to take a lot longer to give results.

I tell you this so that you do not expect upgrading of the OS to be a magic solution. Upgrading hardware, now that is a different proposition.

Anyway, you are on Ubuntu 14.04 and you can directly upgrade to 16.04 when it comes out at the end of April. Be patient. Wait until the beginning of May. If you upgrade to 15.10 you will soon have to upgrade to 16.04 because 15.10 only has 9 months support that started in October 2015. So, wait until 16.04 is released and then think about upgrading.

Regards.

---

### Post by QIII on 2016-02-03
Sometimes the "application X" in "this happens when I run application X" is a red herring.

What might help sort out what is happening, you might want to run top from the terminal and watch what happens in the memory column when you are doing whatever it is that appears to be causing the issue.  Just make sure the memory column is the sorted column so that the largest consumer of memory is at the top.

When the "grey-out" happens, take a look at what the culprit is -- if it's obvious.  Sometimes you don't see the hog.

---

