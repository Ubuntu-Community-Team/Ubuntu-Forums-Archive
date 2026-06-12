---
title: "E: Couldn't find package ..."
date: 2008-09-24
forum: Installation &amp; Upgrades
---

### Post by mmaru on 2008-09-24
I am new to Linux. I am using Ubuntu Server 8.04 on VMware Workstation 6.0.5. In order to install finger, I did the following:

$sudo apt-get install finger

This is the response I get:

Reading package lists... Done
Reading state information... Done
E: Couldn't find package finger

I know it is trying to look in E: which is a CD ROM drive. What do I need to do to instruct it to go online to look for the package?

I am using the shell only.

Thank you.

Maru

---

### Post by Pumalite on 2008-09-24
Post your sources.list

---

### Post by mmaru on 2008-09-24
I am new to Linux. Where do I look for sources.list?

---

### Post by coolethan on 2008-09-24
if you have internet you should be able to download and install the program or what have you using synaptic. I think what Pumalite means is type sources.list into the terminal.

---

### Post by Pumalite on 2008-09-24
Post:
cat /etc/apt/sources.list

---

### Post by cariboo on 2008-09-24
If you are looking for finger, it is part of Network Tools. Go to System-->Administration-->Network Tools-->Finger.

Jim

---

### Post by mmaru on 2008-09-24
Pumalite,

I must say thank you for helping me. I was able to display the contents of source.list on the terminal. I am not sure what to do to get that info to my Windows browser where I am accessing this forum. I do appreciate your help on this.

Maru

---

### Post by Pumalite on 2008-09-24
Maybe you need to make a text file with your editor. Save to your Desktop and then copy and paste here.

---

### Post by mmaru on 2008-09-24
I copied sources.list to my home directory and name it sources.txt. I was able to open it using Vim. I do not know how to save the file on to my desktop. 

Regards,

Maru

---

### Post by Pumalite on 2008-09-25
Copy it and paste it here

---

### Post by mmaru on 2008-09-25
I am sorry. How can I copy it from Vim to pate it here?

---

### Post by mmaru on 2008-09-25
I am staring to learn Linux. How do I copy it from Vim and past it here?

Regards,

Maru

---

### Post by tuxxy on 2008-09-25
> **mmaru said:**
> I am staring to learn Linux. How do I copy it from Vim and past it here?

Regards,

Maru

Open a terminal and enter

```
gedit /etc/apt/sources.list
```

Now copy and paste them as normal

---

### Post by lisati on 2008-09-25
> **mmaru said:**
> I am new to Linux. I am using Ubuntu Server 8.04 on VMware Workstation 6.0.5. In order to install finger, I did the following:

$sudo apt-get install finger

This is the response I get:

Reading package lists... Done
Reading state information... Done
E: Couldn't find package finger

I know it is trying to look in E: which is a CD ROM drive. What do I need to do to instruct it to go online to look for the package?

I am using the shell only.

Thank you.

Maru
BTW: in Linux, the "E:" in the error message doesn't refer to the disk drive....

---

### Post by mmaru on 2008-09-26
I am staring to learn Linux. How do I copy it from Vim and past it here?

Regards,

Maru

---

### Post by niksea on 2009-04-14
The problem you faced here is actually your update was out of date. So Update it first and then install.

Try these commands

sudo apt-get update

then

sudo apt-get install vim

This will definitely solve your problem! :)

---

### Post by arunkrishnan on 2010-06-10
I am facing the same problem.
Tried updating but still the error exists ........
any help??

---

