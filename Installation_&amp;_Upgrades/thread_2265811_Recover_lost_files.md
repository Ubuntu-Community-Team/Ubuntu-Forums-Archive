---
title: "Recover lost files"
date: 2015-02-18
forum: Installation &amp; Upgrades
---

### Post by fr4nky on 2015-02-18
I installed ubuntu 14 on one of drive's. I did side by side option and on that drive I had files on it that last memories of someone close to my family, and as of now ubuntu totally copied over all my files. Is there anything I can do to get my files back?

---

### Post by v3.xx on 2015-02-18
There is TestDisk

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by Mark Phelps on 2015-02-18
What you're calling "drives" are probably just "partitions" on a single drive -- and partitions are formatted using filesystems.  So, was the filesystem that contained these photos formatted for MS Windows?  IF so, you would do better using Windows data recovery apps to get those files back.  But to do that, you would have to remove the drive from your PC and be able to connect it to a Windows PC.

And, you need to STOP using this drive immediately!  Every time you write to this drive you risk overwriting the former files.

If you can remove this drive, you should consider doing the following:
1) Connect this drive to a working Windows PC
2) Download and install a data recovery app on the Windows PC.  "recuva" is a free one.
3) Run recuva to see what it finds.  IF it finds the files, copy them to an external drive or USB stick.
4) IF it doesn't find the files, then consider downloading and installing RecoverMyFiles.  It is free to install and try out -- to at least see if it finds the files you want.  IF it finds the files, you will have to purchase a license online to recover the actual files.

---

### Post by bashiergui on 2015-02-18
Mark Phelps gave a good set of instructions.

Just to be clear, if the memories have been overwritten by new data, then they are forever and permanently gone. If the files have only been deleted (in other words marked as unallocated) then you have a good chance of getting them back.

---

### Post by Penguin360 on 2015-02-18
If free tools failed, then you can try this commercial tool [https://www.grc.com/sr/spinrite.htm](https://www.grc.com/sr/spinrite.htm). I personally never used it, but it was created by a famous guy, I guess it is worth a try if the memory is very important to you.

---

### Post by fr4nky on 2015-02-18
It was label E: in windows, when I was installing Ubuntu (side by side) i though it was going to ask me to make a partition since there was existing data on it. It seems Ubuntu had formatted and took the entire disk space (2TB). I should unplug it and hot box it to my windows and use the data recovery software? Mark, would it be possible if i gave you my email you could help me out? So I can make a partition just for my Ubuntu and reinstall it again? I really want to use Linux as my compute-ring over PC. Everyone that you SO MUCH for the fast replies, it mean so much for me you all took time to reply.

---

### Post by Bucky Ball on 2015-02-18
> **fr4nky said:**
> Mark, would it be possible if i gave you my email you could help me out?

We discourage this, along with PMing other users for support, as it doesn't benefit the community (among other reasons). Working on your issue on the forums gives you access to more input and experience and the fix, if you come to one, is visible to and may help future travelers. 

Try [Photorec]("http://www.cgsecurity.org/wiki/PhotoRec#File_systems"). 

Good luck. ;)

---

### Post by fr4nky on 2015-02-19
Hey Bucky, 

Mark had answered the question for me on the forum. I didn't think it would be issue to ask something in a PM. I just want to ask questions with the steps as I am a newbie and worry about the possible post of others with not so nice opinions which would make me feel uncomfortable.

---

### Post by Bucky Ball on 2015-02-19
> **fr4nky said:**
> ... as I am a newbie and worry about the possible post of others with not so nice opinions which would make me feel uncomfortable.

They don't last long here, so rest assured. Staff and users make a point of fostering a helpful and friendly forum. ;)

---

### Post by Mark Phelps on 2015-02-19
> It was label E: in windows, Which means, you need to connect it to your Windows PC and use the Windows apps to do the data recovery.

---

### Post by fr4nky on 2015-02-20
I am looking for my wires so i can hotbox the HD. Im guessing that once i remove the HD and start the computer up that my master boot would take me to the dual log prompt. How would someone go about changing it back to original load(straight to windows login), this way I could make a partition just for Linux and restart the process of loading Linux correctly.

---

### Post by Mark Phelps on 2015-02-20
I thought your priority was recovering files formerly in the Windows "E:" partition.  IF that's still true, you need to connect the drive to a Windows PC and do the data recovery -- BEFORE you do anything else with that drive.  You need a working Windows PC to do that -- and to connect the damaged drive, NOT boot from it.

Once you have the data recovered, you can them remove all the partitions from that drive using GParted and reuse it to install Ubuntu.

---

