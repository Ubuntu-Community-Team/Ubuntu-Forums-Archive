---
title: "Spyder3 and Ubuntu 16.10 Revert Qt4-webkit"
date: 2017-01-05
forum: Installation &amp; Upgrades
---

### Post by siemensgeek on 2017-01-05
I upgraded to Ubuntu 16.10 and immediately found that my Python IDE, Spyder3, was broken. After some research I found that it was broken because Ubuntu 16.10 does not include Qt4-webkit. The Ubuntu team seems to have washed there hands of the issue because Spyder should make the change to Qt5-webkit. I understand that the Ubuntu team consider Qt4-Webkit to be a security risk but that doesn't help me. I tried some other IDEs including Idle3X and it is okay but doesn't hold a candle to Spyder. I don't know enough keyboard karate to use Vim. 

I found a post somewhere that showed how to revert to the QT4-webkit provided with Ubuntu 16.04 for Python 2.7. This fixed the problem for Spyder but not for Spyder3. How can I revert to the Ubuntu Qt4-Webkit provided with Ubuntu 16.04 for Python 3? I may just give up and reinstall Ubuntu 16.04.

I fixed the problem with Spyder by installing Python fro Anaconda. This has created a new set of problems but they are Python related so I will submit a question on  another forum.

---

