---
title: "Ubuntu instalation problems"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by aleczandru on 2011-10-15
Today I decided to install Ubuntu and while trying to instaling via Wubi I kept getting this error:

Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {14e3da26-95e8-11e0-8b2b-cfd37bd5893d} device partition=B:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.

I tryed instaling it via bios and it kept bloking at keyboard layout(10.04 and the in the 11.10 i can't seem to figure out how to instal it next to windows not delete windows and instal ubuntu).I tryed runing it in windows vista compatibility mode(some people suggested i should try it) but still no luck , I even tryed formating windows 7 and im still geting the error

Any suggestions on what should I do?

---

### Post by Rubi1200 on 2011-10-16
Hi and welcome to the forums :-)

Please check in the Windows Disk Management utility and report back if the disks are labeled as Dynamic.

Thanks.

---

### Post by aleczandru on 2011-10-16
Yes the partitions are Dynamic

---

### Post by Rubi1200 on 2011-10-17
Unfortunately, Dynamic disks are a Windows-only thing and trying to install Ubuntu, whether with Wubi or a regular install, could cause potentially serious issues such as data loss etc.

The only thing I can recommend is to buy an external hard-drive and install Ubuntu on to it.

We can provide guides if you decide to take this route.

---

### Post by aleczandru on 2011-10-17
Thanks alot I managed to convert my dynamic disk to basic and Wubi worked perfectly

---

### Post by Rubi1200 on 2011-10-17
> **aleczandru said:**
> Thanks alot I managed to convert my dynamic disk to basic and Wubi worked perfectly

And that is the other alternative ;)

The only reason I did not suggest that previously was because I do not have enough knowledge of this to know whether the process is reliable (i.e. no data loss etc.).

In any event, glad you got things sorted out and up and running.

Enjoy Ubuntu :)

Please mark this thread Solved using the Thread Tools near the top of the page.

---

