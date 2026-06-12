---
title: "Unable to lock the administration directory (/var/lib/dpkg/) warning"
date: 2015-07-12
forum: Installation &amp; Upgrades
---

### Post by shoaib2 on 2015-07-12
in ubuntu 14.04 i m facing a problem by updating and upgrading it.. during updating or upgrading i m getting this error, i tried every solution but failed, need a useful solution !!

or contact me on skype:   shobi.kayani


E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by dino99 on 2015-07-12
> **shoaib2 said:**
> in ubuntu 14.04 i m facing a problem by updating and upgrading it.. during updating or upgrading i m getting this error, i tried every solution but failed, need a useful solution !!

or contact me on skype:   shobi.kayani


E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

as the error says, you only can use one updating/upgrading tool at once; so close the other one locking the second one

---

### Post by shoaib2 on 2015-07-12
sir i dnt know how to do it.. kindly tell me, sep by step plzzz...

---

### Post by PaulW2U on 2015-07-12
I've changed the thread title to something more meaningful.

As dino99 has asked are you using more than one application to perform updates and upgrades at any one time.

Which application(s) are you using?

---

### Post by shoaib2 on 2015-07-12
sir dino, and sir paul i am a new user of ubuntu,, actualy i really dnt know that which application i am using... kidnly help me to solve my issue .. plz ..

THaNKS TEAm !!

---

### Post by PaulW2U on 2015-07-12
> **shoaib2 said:**
> sir kindly contact me on skype.plzzz

That's not how we like to do things here. If a question is asked on the forums then that's where we answer it. Not only can many think about helping but others can learn.

Which applications have you been using? software centre, synaptic, apt-get, aptitude?

If you can let us know which ones then we can help. You might of course have started the same application twice.

---

### Post by shoaib2 on 2015-07-12
okay.. i agree, alright 
sir i m using apt-get 
i mostly use it.. !!
now whts the next step for me ??

---

### Post by PaulW2U on 2015-07-12
Ok, so you're using apt-get in a terminal window.

Are you prefixing that command with sudo? 

Do you have apt-get also running in another terminal window?

---

### Post by Vladlenin5000 on 2015-07-12
Ok, some explanation is in order...

Frequently - daily - the OS runs an automatic check of the software repositories, looking for updates. That's usually what happens when we try to install something while the background process is active.
When exactly the error message appears? What are trying to do just before it shows?

---

### Post by shoaib2 on 2015-07-12
yes sir i m using apt-get command, 
i use this with "sudo su" admin mode

no sir, i only use one terminal.. 

i also changed my server, and choose the best sever, then  i also update and upgrade, but the same problem is coming in terminal that is "0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."

sir valdlenin, actually i m updating my packages and version, but it didnt, before that i use some commands or stuff related to apptitude, i think this thing creates an issue..


[COLOR=#111111][FONT=Ubuntu]in terminal to remove the lock
[/FONT][/COLOR]sudo rm /var/lib/dpkg/lock    
sudo rm /var/cache/apt/archives/lock

yes i m using apt-get, but now only one terminal is working ...!!

---

### Post by PaulW2U on 2015-07-12
Ok, so you have used something else other than apt-get. Please type the following command into your terminal and then post the output.

```
ps -a
```

That will tell us if aptitude is still running somewhere.

---

### Post by shoaib2 on 2015-07-14
sir, as i type ps -a on my terminal, i got this output


root@ubuntu:/home/shoaibubuntu# ps -a
   PID TTY          TIME CMD
  3121 pts/6    00:00:00 sudo
  3123 pts/6    00:00:00 su
  3124 pts/6    00:00:00 bash
  3229 pts/6    00:00:00 ps

any solution???

---

### Post by matt_symes on 2015-07-16
Hi

Open a terminal and type

```
sudo apt-get install htop
```

Copy and paste the entire output, from that command, from the terminal into your next post.

That will give us more debug information.

Kind regards

---

### Post by shoaib2 on 2015-07-22
after entering the command "sudo apt-get install htop"
i got this reply.
```
shoaibubuntu@ubuntu:~$ sudo apt-get install htop
[sudo] password for shoaibubuntu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
htop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
shoaibubuntu@ubuntu:~$
```

---

### Post by Vladlenin5000 on 2015-07-22
> **shoaib2 said:**
> htop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

This means 

a) htop is already installed
and
b) APT worked.

---

### Post by PaulW2U on 2015-07-22
shoaib2, so htop is already installed but you no longer need to use it.

As Vladlenin5000 has said your apt-get command completed successfully. We'll probably never know what the the problem was but it is now time to move on. If you have any further problems then it is probably best to start a new thread describing in as much detail as possible what the problem is and any error messages that you see.

---

### Post by shoaib2 on 2015-07-22
okay.. thank to all of you.. see u in a new thread..

---

### Post by matt_symes on 2015-07-23
Hi

Sod's law. I had to pick a utility (htop) you already have installed :D

Anyway, it looks like it's fixed.

Kind regards

---

