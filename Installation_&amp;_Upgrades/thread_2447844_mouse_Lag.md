---
title: "mouse Lag"
date: 2020-07-27
forum: Installation &amp; Upgrades
---

### Post by ortollj on 2020-07-27
Hi
 Ubuntu 18.04.4 LTS , FireFox 78.0.2 , SageMath Jupyter notebook 9.1
 When  I use my pc with SageMath, after a while I observe a high response time  with my mouse. I then look at what is happening with the system  monitor, and I see that the memory is occupied at around 90% and that  the swap memory is occupied at around 35%. If I quit Sagemath (I meant  that I kill the terminal window in which I launched SageMat without  & I precise) and I close all Firefox windows, then the memory  occupation goes down to around 60% and the swap memory goes down to  around 25%. But when I look with HTOP, I notice that it is still running  several Sagemath processes. I'll give it a try with Chrome, to see if  it's browser independent. The problem is not specific to a certain  SageMath code, I notice it with different SageMath codes. 
see the system monitor image capture on. As i do not know if the problem is with Ubuntu or SageMath I posted also on SageMath site. I noticed several times that once swap memory is taken, it is never released completely even if the memory comes back to low level.
[URL="https://ask.sagemath.org/question/52707/mouse-lag-after-a-while/"]https://ask.sagemath.org/question/52707/mouse-lag-after-a-while/

[/URL]

---

### Post by ActionParsnip on 2020-07-27
Sounds very specific to sagemath. The forum you have posted in will help more than here, most likely. Is there a bug report logging system for the application?
Does the binary used to launch the application have any switches you can play with or a conf file you can alter?

---

### Post by ortollj on 2020-07-29
you're right, apparently it would come from the way i use Sagemath through Jupyter notebook. look at the answer to my post on the SageMath site given in my first post.

---

