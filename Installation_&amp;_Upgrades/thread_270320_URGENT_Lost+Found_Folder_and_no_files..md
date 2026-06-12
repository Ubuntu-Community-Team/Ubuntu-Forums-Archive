---
title: "URGENT: Lost+Found Folder and no files."
date: 2006-10-03
forum: Installation &amp; Upgrades
---

### Post by orgy on 2006-10-03
Hi,

I have 2 partitions. 1 for dapper and 1 for all my documents. Today I decided to format my pc. So I did all the normal procedure, I chose NOT to format the partition with my documents. Everything went normal, but when i logged in and looked for my documents all i found was a folder called "Lost+Found" and i have no permission to access it. I accessed it with sudo and its empty!.

Where are all my documents, and where did this "lost+found" folder come from?

---

### Post by confused57 on 2006-10-03
Maybe this "howto" can help:

[http://psychocats.net/ubuntu/mountlinux](http://psychocats.net/ubuntu/mountlinux)

---

### Post by orgy on 2006-10-03
thx for your answer ;) , that gave me write permissions to the partition, but still cant see my old files, and where did that "lost+found" folder come from?

---

### Post by orgy on 2006-10-03
bump

---

### Post by dannyboy79 on 2006-10-03
it might be a matter of simply incorrect mounting parameters etc. do you know for sure that what drive and partition your info is on? what does sudo fdisk -l say? then if you go to disks under system, administration, does it say that that particular drive and partition are for sure mounted?? JUST DON'T FORMAT ANYTHING AGAIN UNTIL YOU TRY EVERYTHING!!!

---

### Post by orgy on 2006-10-04
> **dannyboy79 said:**
> it might be a matter of simply incorrect mounting parameters etc. do you know for sure that what drive and partition your info is on? what does sudo fdisk -l say? then if you go to disks under system, administration, does it say that that particular drive and partition are for sure mounted?? JUST DON'T FORMAT ANYTHING AGAIN UNTIL YOU TRY EVERYTHING!!!

yes im sure thats the partition my info is on. This is what i get with fdisk -l:

Disco /dev/hda: 41.1 GB, 41174138880 bytes
255 cabezas, 63 sectores/pista, 5005 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/hda1            2963        3047      682762+  82  Linux swap / Solaris
/dev/hda2            3048        5005    157 27635   83  Linux
/dev/hda3               1        2962    23792233+  83  Linux

The partition im talking about its hda2.

thx for your answer btw.

---

### Post by dannyboy79 on 2006-10-04
you didn't answer me about whether or not your docs folder actually has hda2 mounted to it? what has happened to me in the past was that I thought I certain drive partition were mounted and the folder it was suppose to be mounted to was there but when I clicked on properties it actually said it was  showing me the data that was written to the folder above it. like my home patition. i have a home parition that is 10 gb and i have another folder within home that is named 400gb-ext3. when I would view the folder 400gb-ext3 it was showing me what was on the home patition because my 400gb hard drive partition wasn't being mounted. hope you find your stuff man, i know the feeling.

---

### Post by orgy on 2006-10-05
yep, its being mounted.

---

### Post by orgy on 2006-10-06
bump

---

### Post by orgy on 2006-10-08
bump again

---

### Post by dannyboy79 on 2006-10-10
> **orgy said:**
> bump again




i can tell you that i accidentally overwrote a flash drive when i was trying to make is a linux boot flash drive. i downloaded a free recovery tool for windows, it actually WORKED, it showed me all my folders and files and that they were still there. The particular one I had even could OPEN the file if the native application was installed on the machine. For example, ther was a word doc on my flash drive, using this recovery tool, i simply double clicked on the word file and it actually opened. I simply did a save as to a new name onto my GOOD hard drive and now I had my file back. This company is so dumb, they give you a free trial, the free trial won't let you simply copy and paste the files or folders from the formated drive or whatever drive you want to retrieve your stuff from but like I said, the free trial allows you to open the file if the computer has the native app on it so in my case this free trial WAS AWESOME and it allowed me to save almost everything that I had lost. I think they was like $70 dollars to purchase it but if it's just docs, excel, pics, and whatnot, you simply open  them and do a save as. Here is the link to the free trial. oh, this was a flash drive previously formatted as fat32 so if you are trying to retrieve from ext2 or 3 or reiserfs than you'll have to look else where.
[http://www.runtime.org/faq_gdb.htm](http://www.runtime.org/faq_gdb.htm), oh it also can retrieve from NTFS. I know you're probably saying this sounds to good to be true and that's what I thought, but I downloaded it, tried it and sure as s__t, it worked! You have nothing to lose, the program is tiny!

---

