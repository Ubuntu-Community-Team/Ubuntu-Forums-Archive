---
title: "Cannot load by commandline the drivers form my Brother printer in 18.04"
date: 2018-11-29
forum: Installation &amp; Upgrades
---

### Post by rapidrob on 2018-11-29
I just downloaded Ubuntu 18.04 by a upgrade ( 32 bit) and have lost all my drivers. I went to Brother and downloaded a software that is zipped.
linux-brprinter-installer-2.2.1-1.gz It is sitting my Downloads file.
I open the command line and try to open this file to load the software and every time I get a "cannot locate file" error.
I have tried unzipping the file and load it and it fails also.
I'm at a loss as I'm sure I'm using the wrong commands but don't know how to correct the problem.
I've gone to the net for help and tried several commands with the same results. The file is not found,but is in the Downloads file.
Please help,I really need my printer and it did work in 16.04.
I new to Ubuntu.

---

### Post by yancek on 2018-11-29
There's no way for us to know if you are using the wrong commands as you did not post which commands you used.
You should be able to navigate to your Downloads directory in the file manager and right click and select extract to see what files are in the extracted directory.  Should be an executable or install file.

---

### Post by SeijiSensei on 2018-11-30
If you are trying to execute linux-brprinter-installer from the command prompt, and you are in the same directory as the program file, it won't run.  Try instead using appending "./" to the file name like this:

```
$ ./linux-brprinter-installer-2.0.0-1 
```

replacing the version number with whatever the version you have uses.

This is an ancient security feature of Unix to prevent accidental executions of files.  You could also run it by specifying its full path name, like "/home/seiji/linux-brprinter-installer-2.0.0-1".  In that case the "./" is not required.

---

### Post by rapidrob on 2018-12-01
If I try that I get this:
rob@rob-desktop:~$ cd Downloads
rob@rob-desktop:~/Downloads$ $ ./linux-brprinter-installer-2.0.0-1
$: command not found
rob@rob-desktop:~/Downloads$ 
***********************************************
I then tried a few more ideas:
rob@rob-desktop:~$ /home/rob@rob/cd folder
bash: /home/rob@rob/cd: No such file or directory
rob@rob-desktop:~$ /home/rob@rob/Downloads
bash: /home/rob@rob/Downloads: No such file or directory
rob@rob-desktop:~$ cd Downloads
rob@rob-desktop:~/Downloads$ unzip linux-brprinter-installer-2.2.1-1.gz
Archive:  linux-brprinter-installer-2.2.1-1.gz
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of linux-brprinter-installer-2.2.1-1.gz or
        linux-brprinter-installer-2.2.1-1.gz.zip, and cannot find linux-brprinter-installer-2.2.1-1.gz.ZIP, period.
rob@rob-desktop:~/Downloads$ 
**********************************************************
rob@rob-desktop:~$ cd Downloads
rob@rob-desktop:~/Downloads$ sudo apt install linux-brprinter-installer-2.2.1-1.gz
[sudo] password for rob: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-brprinter-installer-2.2.1-1.gz
E: Couldn't find any package by glob 'linux-brprinter-installer-2.2.1-1.gz'
E: Couldn't find any package by regex 'linux-brprinter-installer-2.2.1-1.gz'
rob@rob-desktop:~/Downloads$ 

The file is sitting in my downloads as a zipped and un-zipped file. Neither can be found

---

### Post by SeijiSensei on 2018-12-01
OK, let's start from scratch.  

> rob@rob-desktop:~/Downloads$ unzip linux-brprinter-installer-2.2.1-1.gz

The .gz extension means the file is archived with "gzip" so you have to use "gunzip" to expand it.

```
rob@rob-desktop:~/Downloads$ gunzip linux-brprinter-installer-2.2.1-1.gz
```

That should create linux-brprinter-installer-2.2.1-1 in the Downloads directory.  Now you'll need to mark the file as executable then run it like this

```
rob@rob-desktop:~/Downloads$ chmod a+x linux-brprinter-installer-2.2.1-1
rob@rob-desktop:~/Downloads$ ./linux-brprinter-installer-2.2.1-1
```

---

### Post by rapidrob on 2018-12-01
It's fighting me:
rob@rob-desktop:~$ cd Downloads
rob@rob-desktop:~/Downloads$ gunzip linux-brprinter-installer-2.2.1-1.gz
gzip: linux-brprinter-installer-2.2.1-1 already exists; do you wish to overwrite (y or n)? y
rob@rob-desktop:~/Downloads$ chmod a+x linux-brprinter-installer-2.2.1-1
rob@rob-desktop:~/Downloads$ sudo chmod a+x linux-brprinter-installer-2.2.1-1
[sudo] password for rob: 
rob@rob-desktop:~/Downloads$ ./linux-brprinter-installer-2.2.1-1
Only root can perform this operation.
rob@rob-desktop:~/Downloads$ sudo ./linux-brprinter-installer-2.2.1-1
Input model name ->3180CDW

Driver-packages cannot be found.
 Confirm the model name.

rob@rob-desktop:~/Downloads$ HL-3180CDW
HL-3180CDW: command not found
rob@rob-desktop:~/Downloads$ sudo HL-3180CDW
sudo: HL-3180CDW: command not found
rob@rob-desktop:~/Downloads$

---

### Post by SeijiSensei on 2018-12-02
> 
Input model name ->3180CDW

Driver-packages cannot be found.
Confirm the model name.


The model name is "HL-3180CDW" not "3180CDW".

---

### Post by rapidrob on 2018-12-03
After re-booting and trying again, the software loaded. The Test Print is normal.
Thank you for your help, I really do appreciate it

---

