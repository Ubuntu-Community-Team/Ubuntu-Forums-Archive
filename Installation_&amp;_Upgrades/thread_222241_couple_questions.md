---
title: "couple questions"
date: 2006-07-24
forum: Installation &amp; Upgrades
---

### Post by linuxnoob40 on 2006-07-24
i have files on another drive i wish to put on my main partition i have already copied them to the main drive but dont see an option for move. now being a former windows user i know that copy is not the same as move is this also the case with linux and if so how do i move the files so they are permanently on the main partition.

also one other question (for now) how concerned should i be with virus protection i have tried installing clam antivirus but it wont go gives me errors. i only ask because i have been told that there are no virus written for linux, knowing how people can be i find this hard to imagine

Steve

---

### Post by Ziox on 2006-07-24
there has only been like 1 virus written for linux and it only had minimual damage to a couple systems. So I, personally, don't see the point of running a virus scanner.  As for copying files, do you mean copying from the command line, or just graphically?  Graphically is the same way as windows.  The command line is a little tougher...

---

### Post by linuxnoob40 on 2006-07-24
well i graphically copied the files but want the files to be permanent so when i remove the other drive they dont just show as dead links

---

### Post by Ziox on 2006-07-24
unless you specifically copied links, the files will be permenent on that drive

---

### Post by catlett on 2006-07-24
```
mv
```mv is the command for mv. If you wanted to move something from /documents/work/scedule to /home/catlett/documents then you would write it like this 
```
sudo mv /documents/work/scedule /home/catlett/documents 
```
Your second question about viruses. I do not know of any linux viruses. It is not because people do not try but because of the open source way of linux.
Window's problems stem mostly from how there applications are written. There were major flaws in outlook express and internet explorer that got exploited. Since windows was the only entity that knew how these aplications were written and were the only ones who could re-write them, the errors did not get fixed immediately and hackers exploited the bad code.
In linux everything is open source. Everyone can see the source code. If an application is writtenb with flaws in it or is written in a way that can compromise a system, it wouldn't get far. The "peer review" that comes with open source would identify it and the errors would be corrected.
The thousands of application in the repositories that you can access through synaptic package manager have all been gone through by countless users who know code and have had full access to it. 
It would be almost impossible for a program with severe flaws to end up in the repositories.
Then there are the secondary issues of how linux runs. In linux you are a user and you do not run under administrative powers. If you need to make an administrative change you have to enter a password before the change takes place.
In windows you run as an administrator. Anything can be changed in your system without any prompt, warning or password given. This means that if someone accesses you computer through internet explorer or outlook express, they can make system wide changes to your sytem. That can either cripple your system or just change your home page.
Those are the 2 main reason for no viruses in linux. Applications are open source and subject to "peer review". User run as users not administrators. The last which may be significant, most hackers run linux and why infect your own system :twisted:

---

### Post by linuxnoob40 on 2006-07-24
Thank you very much lots of this is all very g(r)eek to me :D  but given time ill learn it. its great to have this type of forum where a noob can ask questions and not be chastised for not knowing. as a long time windows user i became very frustrated with the wga crap and having to call them everytime you made a change to the system. i have turned my back on microsoft for good

---

