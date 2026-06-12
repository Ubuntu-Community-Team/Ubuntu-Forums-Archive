---
title: "Hard disk space lost after unistalling wubi"
date: 2010-04-17
forum: Installation &amp; Upgrades
---

### Post by minws on 2010-04-17
Hi,

I installed ubuntu 9.10 with wubi in my vista allocating 35Gb of hard disk space, when I had the problems with the kernel upgrades I then decided to unistall and wait until 10.04 is out. Somehow this was not done smoothly and I'm left with the entry when the window boots and a hard drive short by 35Gb, I've managed to corect the boot entry but I'm still looking for my 35Gb. As this is a laptop I need the hard disk space back.

Thank you.

---

### Post by oldfred on 2010-04-18
Is there still the root.disk file there? That was your wubi install.

---

### Post by minws on 2010-04-19
if you are talking about the file created in C under the name ubuntu is deleted

---

### Post by minws on 2010-04-19
Hi 

I worked this out as following. I installed a defrag program other than the vista one (I will not mention the name as I'm not sure if I can do this) which I ran and in the list of file that could not be defragged  was a file 25Gb big I then deleted the folder which contained the file. The other 10Gb was reserved by virtual box even though I deleted the hard drive of the virtual mashine after unistalling, When I unistalled vm box I got all the missing space back.:P

---

