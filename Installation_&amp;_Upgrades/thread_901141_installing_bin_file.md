---
title: "installing bin file"
date: 2008-08-26
forum: Installation &amp; Upgrades
---

### Post by Achilles124 on 2008-08-26
I have problems with installing a bin file. It is located in the download file on my comp.

I have used the terminal to go the directory hz2008 and typed ls
It shows: 
bin share

I searched the internet but the command chmod +x didnt work.
What could be the problem?

---

### Post by iaculallad on 2008-08-26
> **Achilles124 said:**
> I have problems with installing a bin file. It is located in the download file on my comp.

I have used the terminal to go the directory hz2008 and typed ls
It shows: 
bin share

I searched the internet but the command chmod +x didnt work.
What could be the problem?

Say, you downloaded the BIN file to your desktop: Change directory to the location:

```
cd ~/Desktop/hz2008
sudo ./name_of_file.bin
```

---

### Post by Achilles124 on 2008-08-26
the command sudo ./name_of_file.bin gives a problem:

the name of the file is bin...
so, it becomes: sudo. /bin.bin

and to make matters worse: 
ecmpeek@ecmpeek-desktop:~/Downloads/hz2008/bin$ ls

gives:
hz2008d  hz2008ux

so, the bin file is a directory.

so, what to do?

---

### Post by iaculallad on 2008-08-26
> **Achilles124 said:**
> the command sudo ./name_of_file.bin gives a problem:

the name of the file is bin...
so, it becomes: sudo. /bin.bin

and to make matters worse: 
ecmpeek@ecmpeek-desktop:~/Downloads/hz2008/bin$ ls

gives:
hz2008d  hz2008ux

so, the bin file is a directory.

so, what to do?

With the post above (ls), you still need to traverse to either hz2008d or  hz2008ux sub-directories. Try locating the files in those sub-folders and execute the **sudo ./filename.bin**.

---

### Post by Achilles124 on 2008-08-26
What do you mean with "traverse to either hz2008d or hz2008ux sub-directories"? The cd-command doesnt work because the above files are not directories.

---

### Post by iaculallad on 2008-08-26
> **Achilles124 said:**
> What do you mean with "traverse to either hz2008d or hz2008ux sub-directories"? The cd-command doesnt work because the above files are not directories.

Post whatever outputs when you issue the two commands below (when you're inside the ~/Downloads/hz2008/bin directory):

```
file hz2008d
file hz2008ux
```

---

### Post by Achilles124 on 2008-08-26
Double-clicking on the hz2008ux file gives the desired result: the program starts. Didn't know that hz2008ux is an exe file.

Thanks for answering iaculallad

Greetz,
Achilles124

---

### Post by Achilles124 on 2008-08-26
ecmpeek@ecmpeek-desktop:~/Downloads/hz2008/bin$ file hz2008d
hz2008d: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.0.0, dynamically linked (uses shared libs), stripped

ecmpeek@ecmpeek-desktop:~/Downloads/hz2008/bin$ file hz2008ux
hz2008ux: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.0.0, dynamically linked (uses shared libs), stripped

I am interested: how to run the program with the terminal? Do you know that?

---

### Post by iaculallad on 2008-08-26
> **Achilles124 said:**
> ecmpeek@ecmpeek-desktop:~/Downloads/hz2008/bin$ file hz2008d
hz2008d: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.0.0, dynamically linked (uses shared libs), stripped

ecmpeek@ecmpeek-desktop:~/Downloads/hz2008/bin$ file hz2008ux
hz2008ux: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.0.0, dynamically linked (uses shared libs), stripped

I am interested: how to run the program with the terminal? Do you know that?

What's the actual name of the application you're trying to install? You might be needing WinE in order for you to run that EXE file.

---

### Post by Achilles124 on 2008-08-26
[http://www.toeslagen.nl/download/116.html]("http://www.toeslagen.nl/download/116.html")

it is a program with which you can fill in your changes in your situation for the Dutch taxes.

it comes with an autopackage and with a tarball. Autopackage didn't work, so I downloaded the tarball. Running the ux-file does the trick. 

Wine also works as I have found out by a search on the internet.

Thank you again, 
Greetz.

---

