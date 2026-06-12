---
title: "Buffer I/O Error"
date: 2006-07-16
forum: Installation &amp; Upgrades
---

### Post by Hakase on 2006-07-16
Hi.  I'm trying to install Ubuntu on my system but I keep running into the same problem.  The computer boots off of the CD and I tell it to install at the menu.  After it uncompresses Linux it says that it's booting the kernel.
This is when I get an error like:
[a long number]BUFFER I/O ERROR on hda: Logical Drive 0
[a long number]BUFFER I/O ERROR on hda: Logical Drive 1
[a long number]BUFFER I/O ERROR on hda: Logical Drive 2
.
.
.
[a long number]BUFFER I/O ERROR on hda: Logical Drive 9

Then it will keep trying to do something and repeat the same error but with a different series of numbers.

So can anyone help me with my problem?  Do you have any idea what I can do to fix or get around this?

---

### Post by encompass on 2006-07-16
Sounds like a bad cd...
Where did you get the cd?
Other possible problems could be a bad cd drive or dirty disk.

---

### Post by Hakase on 2006-07-16
I downloaded the ISO and burned the image on a CD.

The message says the error is on hda, so why do you think the CD has a problem?

---

### Post by encompass on 2006-07-16
I would try to reburn the cd... if that doesn't fix it redownlaod and burn yet again.  And when all else fails... order the cd for free ¶:
You cna double check your download with a program called md5 sum... are you in linux right now?

---

### Post by Hakase on 2006-07-16
I downloaded a new copy of the ISO and then reburned it.  I got the exact same error at the exact same spot.  Why do you think the problem is the CD anyways?

Does anybody else have any ideas?

---

### Post by AhrenBa on 2006-07-16
Yeah, I am having the exact same problem. I have no clue how to fix it.

It is doing it on Ubuntu and Xubuntu. Does anyone know?

---

### Post by encompass on 2006-07-17
It sounds like what I get when I don't burn the cd correctly... there is a program to check the original download to see if it is correct.  it is called md5sum... look it up... it is not hard to use, and it comes for windows too.

---

### Post by AhrenBa on 2006-07-17
Where do I get the MD5sum for xubuntu?

---

### Post by AhrenBa on 2006-07-17
Oh wait, never mind, I found it. It's in the FTP files.

But when I did the check it said the sums were the same.

---

### Post by encompass on 2006-07-17
What is your system... could be low on memory... or worse, your memory could be bad.  There are many of these errors, copy the error and pop it in google.  You'll get piles, same with this forum.

---

### Post by AhrenBa on 2006-07-17
> **encompass said:**
> What is your system... could be low on memory... or worse, your memory could be bad.  There are many of these errors, copy the error and pop it in google.  You'll get piles, same with this forum.

Memory is a problem that I was suspecting since it says on the Ubuntu page that I need at least 192mb of RAM and I only have 160MB. However, people have been having the exact same error who have more than enough memory, and plus, some people said that you can install ubuntu on 128 MB RAM. I am even using Xubuntu, which in theory should require less RAM.

I have also put the errors into google, and there are a ton of threads, but with no answers that have actually worked. ](*,)

I don't know if this means anything but when I first pop in the CD, an error comes up saying, "ACPI: unable to locate RSDP".

Plus when I tried using the alternate install cd, it gets a little further but stops on an error that says "cannont mount cd".

---

### Post by jimmygoon on 2006-07-17
Run the "Check Memory" utility on that Ubuntu install disc :)

---

### Post by AhrenBa on 2006-07-17
Ok, I am running it right now. What will this tell me?

---

### Post by jimmygoon on 2006-07-17
> **AhrenBa said:**
> Ok, I am running it right now. What will this tell me?

Honestly, I'm not 100% sure but I'm imaging it will tell you if your memory is okay. It seems that some above me thought that that may be your problem.

---

### Post by AhrenBa on 2006-07-17
Ok, I ran the Mem. Test and it passed all the tests, but the ubuntu boot still has the same errors.

---

### Post by encompass on 2006-07-17
I thik there is a memory test program on the install cd... run that, could be bad memory.  Happened to me twice. :-#  Lost from here, kind sir... no idea what has happened, out of the fact your out of memory, I have 200 mb on my lappy with xubuntu and it works fine.

---

### Post by AhrenBa on 2006-07-17
Yep, I ran the mem test (one post above yours) and it passed. I have no clue why it isn't booting. Hmmm... thanks for the suggestions though.

Can you recommend any other good distros? Thanks

---

