---
title: "New Jaunty install root partition full"
date: 2009-04-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by brianbourke75 on 2009-04-03
Hello all,

  I have a Jaunty install with 4 partitions

/dev/sda1 ntfs boot 19GB 
/dev/sda2 ext3 /  19GB
/dev/sda3 swap    2 GB
/dev/sda4 extended
  /dev/sda5 ext3 /home  80GB

I have been going through and using it normally for about 4 days without to many issues, but today I have noticed that df is returning that my root partition is full exactly at 100% with zero bytes available.  I have confirmed that this is not the case using the disk usage analayzer to evaluate that there is only about 3 gigs work of data on the root drive.  I can also create new files.

I have forced a disk check on reboot which did not find any errors.

Some programs still work, except for those which check for disk space prior to performing the tasks :)

Any suggestions to resolve this?

Bi

---

### Post by nystire on 2009-04-03
du -f /

That should show you each folder and how much of them is used.

---

### Post by brianbourke75 on 2009-04-03
Well, I just gave up and reinstalled jaunty after reformating the partition, figured it would take less time than trying to figure out what went wrong and how it happened.

ps: there is no "-f" argument for du

---

### Post by nystire on 2009-04-04
True. My bad. I meant '-h' :S

---

