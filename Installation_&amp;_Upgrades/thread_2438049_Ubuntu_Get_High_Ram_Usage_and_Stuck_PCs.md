---
title: "Ubuntu Get High Ram Usage and Stuck PCs"
date: 2020-03-04
forum: Installation &amp; Upgrades
---

### Post by thushantkm on 2020-03-04
I'm using  i7 7th Gen, 8 GB Ram and 4 GB VGA  Laptop, I did set up Ubuntu to my PC and working well , but sometime i worked with couple of processes like VM Box ,Chrome(10 Tabs) and few applications which is perform well in windows 10, but in Ubuntu my PC got slow and stuck, It takes high Ram usage to the processes. When i was setting up Ubuntu, I allocated 1 GB space for Swap. Can Anyone help me to solve this problem?

---

### Post by vidtek on 2020-03-05
> **thushantkm said:**
> I'm using  i7 7th Gen, 8 GB Ram and 4 GB VGA  Laptop, I did set up Ubuntu to my PC and working well , but sometime i worked with couple of processes like VM Box ,Chrome(10 Tabs) and few applications which is perform well in windows 10, but in Ubuntu my PC got slow and stuck, It takes high Ram usage to the processes. When i was setting up Ubuntu, I allocated 1 GB space for Swap. Can Anyone help me to solve this problem?

Running VM's can take a lot of ram depending on how you set the VM up in the first place.  You can change the VM's memory allocation, try that as a first step.

In the early days we always set up swap files to be equal to the physical ram, but modern machines have much more ram and swap files can actually slow things down.  I have no swap files at all on my 16gb machines.  I'm unsure about 8gb though.  Check your running processes and stop the unneeded ones.

Tony.

---

### Post by ajgreeny on 2020-03-05
Give us more detail about your 4 GB VGA graphics; that could easily be the cause of your problems but we need many more details.

Let's see the output of ***inxi -Fxz*** in terminal for a start and we can work from there.

Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

