---
title: "Error in sources.list"
date: 2022-08-27
forum: Installation &amp; Upgrades
---

### Post by theintelfrog on 2022-08-27
I need help fixing the following error that I receive when I try to update or download anything in Ubuntu: 

Malformed line 2 in source list /etc/apt/sources.list.d/signal-xenial.list (type)

I have no clue what this is even referencing or how to find it and correct it, so if someone would be willing to help walk me through it, that'd be great.

---

### Post by ubfan1 on 2022-08-27
What version of Ubuntu are you trying to update?  The file you reference is for 16.04, which is EOL (although there is extended security maint for security from Canonical).

---

### Post by Holger_Gehrke on 2022-08-27
The text file /etc/apt/sources.list and the text files in the directory /etc/apt/sources.list.d/ tell apt (advanced package tool) where to look for packages. Something is wrong with one of the files in /etc/apt/sources.list.d/ namely the file signal-xenial.list. Now the 'xenial' part of the name makes me wonder if perhaps you're still on Ubuntu 16.04 which was code named Xenial Xerus ... If you are and aren't using extended security maintainance, then it's way past time to upgrade. For the mainline Ubuntu Desktop and Ubuntu server support ended in 2021, for the various community flavours even before that. On the other hand the installation instructions for signal still tell you to create a file named like that, so I don't know.

If you're not using signal anymore, you could just remove that file or use the 'Software & Updates' settings tool to deactivate this source and remove the signal-desktop package. Otherwise you should post the contents of that file, so we can see what's wrong with it and tell you how to fix it.

Holger

---

### Post by theintelfrog on 2022-08-28
20.04 is the version I'm running currently.

---

### Post by deadflowr on 2022-08-28
Post the output from 
```
cat /etc/apt/sources.list.d/signal-xenial.list
```

---

### Post by theintelfrog on 2022-08-28
I get nothing.  A big block of nothing several lines long and then a new input line: 

osint@osint1:~$ cat /etc/apt/sources.list.d/signal-xenial.list









osint@osint1:~$

---

### Post by theintelfrog on 2022-08-28
Can you walk me through how to use Software & Updates settings to deactivate the source and remove the signal-desktop package?

---

### Post by &amp;KyT$0P# on 2022-08-28
> **theintelfrog said:**
> I get nothing.  A big block of nothing several lines long and then a new input line: 

It would be safe for you to run this command in Terminal to just delete the offending file -
```
sudo rm -v /etc/apt/sources.list.d/signal-xenial.list
```

Then, to apply the change, run
```
sudo apt-get update
```

---

### Post by theintelfrog on 2022-08-28
That seems to have worked!  Thanks so much for your help!

---

### Post by mIk3_08 on 2022-08-29
On how to mark this thread as solve,
Please Click the "Solve thread" link below. Regards and cheers.

---

