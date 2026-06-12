---
title: "Update manager problems"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by Scubasteve2989 on 2010-05-16
I am new to Ubuntu and am trying to get everything running the way I'd like but ran into a problem. when using the update manager i cant install any of the updates and it says "Another synaptic is running
There is another synaptic running in interactive mode. Please close it first." as far as I know there is no other synaptic running as I had this problem even when I freshly turn the computer on. any help is greatly appreciated.

---

### Post by rjcroy on 2010-05-16
Open a terminal window (Applications > Accessories > Terminal)
Then use the command 
```
ps aux | grep synaptic
```
How may processes called synaptic are there?
Post the results back to this thread if you are not sure how to interpret the results. The first column of the results gives the PID.

Any stay processes can be killed with the kill command with the process identification number PID as the argument
```
kill <PID>
```

---

