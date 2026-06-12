---
title: "WUBI.exe causes continuous &quot;No Disk&quot; error."
date: 2011-02-23
forum: Installation &amp; Upgrades
---

### Post by FoxEWolf on 2011-02-23
I am installing Ubuntu on one of my my PC using WUBI for the first time (Not the first time for Ubuntu, but for WUBI) When Trying to run... I get this:

[IMG]http://i171.photobucket.com/albums/u315/Miles_Tails_Prower_3/untitled-12.png[/IMG]

The Problem is that I have never seen this error message before in the way it behaves. I have seen a "No Disk" error before but it doesn't prompt the message constantly after clicking cancel or OK. 

What could be causing this? I tried this on another machine and it worked fine.

---

### Post by FoxEWolf on 2011-02-23
I have found out that my System Drive had been labeled "I" instead of "C" It seems to have changed due to me re-install on a brand new SATA drive caused it. This PC has the 4 in 1 card reader which took Drive letters C, F, G, H. So it isn't a WUBI Issue, but a Windows Issue. Although I am surprised that WUBI actually has a problem with not having the Windows Drive "C".

---

### Post by bcbc on 2011-02-23
The problem is not that the C drive is taken, it's that there are assigned drives that are empty. This is a problem with the python code used in Wubi - or more precisely a coding problem in Wubi that is common with programs written in python.

The solution is - as you found - to remove the card reader.

---

