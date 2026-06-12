---
title: "VirtualBox &amp; Wine won't start at all- no error msgs"
date: 2011-04-01
forum: Installation &amp; Upgrades
---

### Post by RoninISC on 2011-04-01
Searched through forums & didn't see anything on this.
Trying to run windows only apps. I installed Wine first from software center.
Most progs I try to run only give me the 'working' icon for 20 seconds then nothing. I did modify properties to allow .exe to run.
I Dl'ed & installed the VirtualBox package w sw center and same deal- nothing. No error messages or anythng.

Running Ubuntu maverick.  My Cpu is a compaq presario laptop CQ50, dual core intel T3200.
Not the best but should at least start the progs yes?

Can't really troubleshoot as I have no feedback at all.

---

### Post by Robut on 2011-04-12
I am having the same problem.

I am trying to use WINE to run a windows program. At first it exited with errors about MSVCP60.dll so I found this file online and put it in my windows/system folder. Now when running the program from terminal it just exits immediately with no WINE errors and no errors in from the program itself.. 

Any ideas?

EDIT: I started getting an error on the command line when i try to run it: [http://pastebin.com/fFVcxUNb](http://pastebin.com/fFVcxUNb)

---

### Post by Darris on 2011-04-21
I fixed it by opening a system monitor (rightclick on a panel, add to panel, system monitor- when its on the panel, just click it) and then I found the wine processes in the processes tab and ended them 
the next time i opened wine it worked. 
It was a windows-y fix lol

---

