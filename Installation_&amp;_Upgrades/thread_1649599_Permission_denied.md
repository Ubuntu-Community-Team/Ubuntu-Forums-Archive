---
title: "Permission denied"
date: 2010-12-20
forum: Installation &amp; Upgrades
---

### Post by smss on 2010-12-20
hi
how to fix this erorr
[U]bash: ./configure: Permission denied

[/U]

---

### Post by wojox on 2010-12-20
Need more info.

Is it in your home directory?

Is it executable?

What is it your trying to accomplish?

---

### Post by smss on 2010-12-20
Not
 This directory is located in the Media
I also tried Properties and permission get it fix but every once the automatic mode prior to the return

---

### Post by oostue on 2010-12-20
do a "sudo chmod 777 /foldername" this should take care of your permission issue

---

### Post by tommcd on 2010-12-20
> **smss said:**
> Not
 This directory is located in the Media
I also tried Properties and permission get it fix but every once the automatic mode prior to the return
Is any part of that supposed to be a coherent and complete sentence? If you are not a native English speaker, then I can understand. But please tell us what exactly you are trying to do so we can help you.
What are you trying to run via *./configure*???
If you are trying to compile a program, then tell us what program it is.
See this website for great beginner help to get started in Ubuntu:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by smss on 2010-12-20
this chmod -R 777 [file name] doesnt work for me!.
I think before this command to other things requires.
But I do not know what needs.
(Yes, I'm trying to./configure)

---

### Post by ajgreeny on 2010-12-20
> **smss said:**
> this chmod -R 777 [file name] doesnt work for me!.
I think before this command to other things requires.
But I do not know what needs.
(Yes, I'm trying to./configure)
But why from /media?

I assume you mean /media, and that the Media folder you talk of is not a folder you have made in your own home folder.

---

### Post by wojox on 2010-12-20
It would also help if you told us what your trying to configure. There is probably an easier way to install whatever this is. ;)

---

### Post by smss on 2010-12-21
I'm trying to compile a program language C Plus Plus by the command . /configure
 But I am faced with this error:
 bash:. / configure: Permission denied
 I had seen that person before the problem was resolved by ordering Chmd
 Examples:
 chmd -R 777 [file name]
 This command does not work for me
 And I think that should be the first command with other commands to install
Or use this command before other commands require

---

### Post by dino99 on 2010-12-21
is it mounted ?

---

### Post by tommcd on 2010-12-21
> **smss said:**
> I'm trying to compile a program language C Plus Plus by the command . /configure
If you could provide a link to where you got this program it would help.
> **smss said:**
> 
 But I am faced with this error:
 bash:. / configure: Permission denied
Assuming your C++ program was downloaded to the /media directory, post the output of:
```
ls -l /media
```
> **smss said:**
> 
 I had seen that person before the problem was resolved by ordering Chmd
 Examples:
 chmd -R 777 [file name]
 This command does not work for me
Just to be clear, the command is **chmod**, not *chmd*.
 You have marked this thread as solved, so please tell us how you solved it after all.

---

