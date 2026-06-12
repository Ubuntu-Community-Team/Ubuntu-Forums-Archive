---
title: "Server 6.10 problems"
date: 2007-03-25
forum: Installation &amp; Upgrades
---

### Post by rstacey on 2007-03-25
I have installed an Ubuntu 6.10 Edgy LAMP server and loaded lots of packages and lots of data to it. But in the process I have broken several packages. It is looking like re loading the server software would be easier than trying to fix all the broken packages. But, I don't want to loose my data.

Is it possible to reload the LAMP server without formating the had drives and keeping the existing   directory/file structure?

---

### Post by louieb on 2007-03-25
> **rstacey said:**
> I ...But, I don't want to loose my data. Is it possible to reload the LAMP server without formating the had drives and keeping the existing   directory/file structure?
In theory its possible. I've tried to reinstall over an existing installation a couple of times (once w/Ubuntu).  I got mixed results and some things still did not work right. Now when I've screwed things up so bad it's reinstall time or I just want to upgrade, I back up my data do a clean install and restore data. Its a pain and time consuming.
 I've got my /var, and /home on separate partitions now. Thinking about putting /opt on its own partition, but just don't want to figure out how much space to give it. Want to see how the Feisty install goes once it gets released. BTW I'm still running Dapper.

---

### Post by rstacey on 2007-03-25
Thanks for the reply. 

Things were so messed up at the end that on the last reboot all I got was a "busybox" shell. I've never heard of or seen that shell before . I could not remotely access the box at all. I tried doing a recovery from the install CD but it puts you into a busybox shell also and I don't know what to do from there, so it didn't help. 

What I ended up doing is getting another small hard drive, disconnecting my original,(so I didn't format it by mistake) connecting the small one and doing a server install to it, using the same names. I then left the small one connected, and re-connected the original (powered down & off of course).

So I have the server up and the data drive connected; but not yet accessible.  If I can access the large hard drive I'll leave it like this, which is similar to how you said you have yours.

So my problem now is quite simple. How do you mount a hard drive? Will my new root account have access to the drive?

---

### Post by louieb on 2007-03-25
You don't mount a hard drive. A hard drive is divided into partitions. It may have only one partition that takes up the entire hard drive. Or the drive could have a dozen or more partitions on it. It is the partition that get mounted. Without seeing how your drives are partitioned it would be a guessing game for me to try and show you how its done.  and besides there are a bunch of posts on this forum that show how to do it.  
The easy questions answer is once mounted the root account will have access to everything on both drives.
 
Log on as root to the server and use the command
```
fdisk -1
```(as in little)   
This should list partition information for the two hard drives. 
or better yet get a Puppy live CD  set, up internet access, run the fdisk command, and post the output here. 
You could use the Ubuntu or Knoppix Live CD's but Puppy is my favorite for this kind of thing.

---

