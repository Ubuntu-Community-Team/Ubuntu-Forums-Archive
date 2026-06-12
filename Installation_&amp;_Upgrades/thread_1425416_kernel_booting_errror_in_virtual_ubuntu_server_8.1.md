---
title: "kernel booting errror in virtual ubuntu server 8.10"
date: 2010-03-09
forum: Installation &amp; Upgrades
---

### Post by savin on 2010-03-09
Hello Friends help me in this-Am getting tis error after installing  ubuntu server 8.10 in sun virtual box and trying to boot for the first time...  
 
"This kernel requires following features not present on the cpu 
pae 
unable to boot please use the appropriate kernel for your cpu." 

 currently am using ubuntu desktop edition 9.04. on d top of it i installed virtual ubuntu server8.10

---

### Post by johnson.d on 2010-03-09
You can try the following steps:

1) Right click on the VM in Virtual Box
2) Click settings
3) A window will open, click System-> Processor
4) At Extended features, Check the Box which shows Enable PAE/NX
5) Click OK

Now try rebooting Ubuntu 8.10 Server Again.

---

### Post by savin on 2010-03-09
a very much thank you brother
thanks a lotttttttttttttttttttttttttttttttttttttttttttttt.....................:KS:KS:KS:KS:KS:KS

Its workin.........

---

