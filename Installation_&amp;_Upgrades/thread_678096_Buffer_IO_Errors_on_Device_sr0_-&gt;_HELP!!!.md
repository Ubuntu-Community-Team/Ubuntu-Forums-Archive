---
title: "Buffer I/O Errors on Device sr0 -&gt; HELP!!!"
date: 2008-01-25
forum: Installation &amp; Upgrades
---

### Post by sTpny on 2008-01-25
I recently installed feisty faun on my friends computer with the intention of winning him over from the dark side, and success, he's a convert, but he doesn't know about the logical errors from device sr0.  Being new to linux myself, I'm unsure about how to proceed. I'd like to get the problem fixed before my friend finds out and freaks out and returns to the world of windows and gates, but I haven't got a clue. What is device sr0? 

The computer is a Compaq Deskpro 1Ghz. Should I have used some special options when installing? Could some setting be wrong in the bios? Would an upgrade to gibbon fix this problem, or would it even work? What about a fresh install of gibbon? Is this a know issue that time and updates will fix? Please help. 

The errors are "Buffer I/O error on device sr0, logical block 0".  The logical block number can be different, but the error is the same. I get them just by using the computer to do normal things, and doing something over again doesn't produce the same errors. For instance, I ran the command "sudo lshw | grep usb" over and over again, and every time, The errors are there, but different from the last time. Either different by the logical block or by the number of errors. Sometimes, the command actually  works, but mostly I get those errors, or I get "Binary file (Standard Input) matches".   

Any ideas?  Any Solutions? Any Questions? I' d be happy to help you help me.

---

### Post by kidders on 2008-01-26
Hi there,

That error suggests a faulty optical drive or damaged disc ... at least they're the most likely possibilities.

Other (far less likely) potential causes include a bug or hardware incompatibility of some sort. Although I'd be a bit skeptical, it's at least worth checking out whether other users of your friend's hardware are reporting problems.

---

### Post by sTpny on 2008-01-27
The PC in question has a not quite working usb webcam. Do you think that it could be related?

---

### Post by amo-ej1 on 2008-01-27
Extremely unlikely, try to figure out which drive is failing, if it turns out to be your harddrive, time to create some backups ;)

---

### Post by kidders on 2008-01-27
> **amo-ej1 said:**
> if it turns out to be your harddrive, time to create some backupsI doubt that's necessary. /dev/sr0 normally refers to the "first" SCSI/Firewire optical drive (eg a DVD writer, Blu-ray drive, etc.). The errors sTpny mentioned could simply be the result of a dirty lens or scratched disc ... they don't absolutely *have* to indicate a drive failure, and don't really suggest hard disk problems.

> **sTpny said:**
> The PC in question has a not quite working usb webcam. Do you think that it could be related?Like amo-ej1 says, that not very likely. Having said that, if the webcam is on the same I/O bus as the optical drive, then there could be a connection ... a USB cable or port they both share could be at fault. Otherwise, they're two unrelated issues.

---

### Post by sTpny on 2008-03-16
Thanks guys.  This problem really hasn't been much of a problem.  It is mostly just something that annoys me when I'm using the terminal, but I think it might also be whats stopping the computer from shutting down, and games sometimes will stop for no apparent reason, but not often. 

 There is only a CDRW and a CD in the computer, and a couple of HD's of coarse. I used one older HD cable setting the system up because it was the last long one I had. (sometimes I'm too giving, sigh) Could a bad cable be causing this problem? Is there a program to test for a bad cables?

Sorry for the time delay btw, I get extra busy sometimes.

---

### Post by kidders on 2008-03-16
Hey again,

There's no way to distinguish programatically between a faulty cable & a faulty motherboard/drive/PSU/etc. I suppose you could change all the cables and see if it makes any difference, but the only truly reliable way to check a cable is with a circuit tester.

I would advise sorting this issue out reasonably quickly though ... dodgy cables can damage your hardware, and difficulties shutting down can corrupt your filesystems. It might be worth disconnecting your optical drives for a while, to see if the problem goes away.

---

