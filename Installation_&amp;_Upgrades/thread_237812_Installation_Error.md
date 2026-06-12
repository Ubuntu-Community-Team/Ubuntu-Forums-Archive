---
title: "Installation Error"
date: 2006-08-16
forum: Installation &amp; Upgrades
---

### Post by Seldoms on 2006-08-16
While trying to install, I get to the part where I choose how to partition the drive (step 5). I click the first option so I can dual boot but I get error thats theres not enough free space. 

After right clicking and viewing the properties of the C:\ drive i find that I have 21.7 gb free space out of 37.2 gb total.

What should I do? I want to have enough to download games and stuff on ubuntu but I do not want to put all my space there. 

Also, while I tried to manually partition it, I click next and it takes forever and never stops loading.=/

---

### Post by avtolle on 2006-08-16
Not meant to be condescending, but did you defrag your HDD first? Given the way Windows saves files, there might be data scattered all over the drive, not leaving enough free/unallocated space for the partitioner to do its thing. HTH.

---

### Post by Seldoms on 2006-08-16
Im trying to defrag and get error:

Disk Defragmenter has detected that ChkDsk is scheduled to run on the volume: (C: ).

Please run ChkDsk /f.

---

### Post by avtolle on 2006-08-16
I have been away from Windows for quite a while, but it sounds like you need to run ChkDsk, which suggests there may be some problems with your drive, such as a bunch of bad sectors, etc. As I don't know what version of Windows you have, get to what used to be called a Dos Prompt, and type Chkdsk, hit a return, and let it do its thing. IIRC, this will take a bit of time. Best of luck.

---

### Post by Seldoms on 2006-08-16
I am running Windows XP home SP2.

I opened command prompt, typed in chkdsk, and got error thats its read only and cannot continue. So, I dont know where chkdsk it located so I used the search file and found the following: 

CHKDSK c:\I386
CHKDSK.EXE-0C6DCB55.pf
CHKDSK c:\windows\system32

None of them are in read only format.

---

### Post by avtolle on 2006-08-16
I hesitate to comment further, as I have zero knowledge or experience w/XP. Regrettably, I must leave now, but as a final suggestion, at the Command Prompt type in:c:\windows\system32\CHKDSK, hit the Return, and see what happens. HTH, and best of luck. Surely, someone with more up-to-date knowledge and information can assist, and point out the errors in my thinking.

---

### Post by Seldoms on 2006-08-16
I got to Stage 3 out of 3, and it said it found errors. It said to run it with the /f (fix) extension. So, I tried that and of course, it said it cannot because its in read only mode. >.<

---

### Post by avtolle on 2006-08-17
This is more an attempt to get the thread back on the first page than anything else. Obviously, you have a permission problem. Is there anyone out there who can take a look at the OP and his issues, and suggest a way to proceed?

---

### Post by avtolle on 2006-08-17
After doing a Google search (somewhat limited, to be sure) I have learned that to be able to run chkdsk /f that you must be a member of the Administrator's Group (as I understood what I read). Are you on some network? How to put you in the said group is beyond me at this point. Hopefully, someone else will be able to point you in the right direction. Commentary: this makes no sense to me, given you are on XP Home edition; I may have misread the Google article on chkdsk f, but that's what I have noted on my (ever dependable) sheet of paper. Good luck.

---

