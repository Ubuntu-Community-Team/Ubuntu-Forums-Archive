---
title: "Can't boot --&gt; /dev/sda8 contains a file system with errors, check forced."
date: 2020-05-12
forum: Installation &amp; Upgrades
---

### Post by risqi-r on 2020-05-12
I installed ubuntu LTS 18.04 in dual boot with Windows 8.1.

I did a linux update and appeared about a partial upgrade.
I ignored it and continued to update as usual.
After updating 2-3 times without partial upgrading, my ubuntu can't boot then the message appears as shown below.
Does someone know how to solve the issue?

I don't know if this partial upgrade is related to this issue, I'm just guessing maybe this has something to do.

Thank you in advance.

[[IMG]https://i.ibb.co/QpZt5Jk/20200511-180635.jpg[/IMG]]("https://ibb.co/173jS0M")

---

### Post by dino99 on 2020-05-12
How have you made that 18.04 installation ? 
fsck is not a linux command, but a windows one ;)

and if you takes the risk of doing a partial upgrade, be sure to understand what that means; otherwise avoid it

---

### Post by risqi-r on 2020-05-12
Oh, I forgot to explain that I installed Ubuntu in dual boot with windows.

I have already found out about partial upgrades but I don't really understand so as you say I avoid it.
I'm new to linux, so I don't want to do stupid things.

---

### Post by yancek on 2020-05-12
You are told what to do, run fsck from the prompt on the partition so do: 

>  e2fsck /dev/sda8   

Hit the Enter key to run a filesystem check and do watch the output for additional errors.

---

### Post by risqi-r on 2020-05-14
> **yancek said:**
> You are told what to do, run fsck from the prompt on the partition so do: 

[COLOR=#000000]*e2fsck /dev/sda8*[/COLOR]

Hit the Enter key to run a filesystem check and do watch the output for additional errors.

After I run fsck then come out like this.
[[IMG]https://i.ibb.co/9TmsTdT/20200514-155734.jpg[/IMG]]("https://ibb.co/SnDRnZn")

I don't know what that means, but after that I run the exit command.
Then, it restarts and finally my ubuntu can boot again.
If after this there is still a problem, I will report it again.

Thank you for your help, I really appreciate it.

---

### Post by yancek on 2020-05-14
The filesystem errors/inconsistencies reported in your initial post have been repaired.  I would suggest that you watch for this and if you see it frequently, you may need a new drive.  Backups!

---

