---
title: "Brother printer driver files not running"
date: 2015-06-16
forum: Installation &amp; Upgrades
---

### Post by angel mike on 2015-06-16
I have downloaded three files from the Brother support site to get my Printer HL-3150CDW runing and I get the same error message on all of them. The OS system is 32bit.
Theses are
 linux-brprinter-installer-2.0.0-1.gz
hl3150cdwlpr-1.1.2-1.i386.deb
hl3150cdwcupswrapper-1.1.2-1.i386.deb

```
 michael@michael-GM5066B:~$  gunzip linux-brprinter-installer-2.0.0-1.gz
gzip: linux-brprinter-installer-2.0.0-1.gz: No such file or directory
michael@michael-GM5066B:~$ 
```

Using Ubuntu 14.04

---

### Post by sandyd on 2015-06-16
Can you post the output of
```

ls -l
```

---

### Post by ajgreeny on 2015-06-16
Are you running the command(s) from the folder where the files are sitting, eg Downloads, or wherever you put them when you downloaded them?

---

### Post by angel mike on 2015-06-16
Thanks Sandyd
The output is as follows
```
michael@michael-GM5066B:~$ ls -l
total 160
-rw-rw-r-- 1 michael michael 54961 Jun 15 18:24 Brother printer driver 2.odt
-rw-rw-r-- 1 michael michael 59538 Jun 15 16:50 Brothers Printer Driver Install.odt
drwxr-xr-x 2 michael michael  4096 Jun 15 21:58 Desktop
drwxr-xr-x 4 michael michael  4096 Jun 15 17:51 Documents
drwxr-xr-x 2 michael michael  4096 Jun 16 16:30 Downloads
-rw-r--r-- 1 michael michael  8980 Jun 14 17:35 examples.desktop
drwxr-xr-x 2 michael michael  4096 Jun 14 18:04 Music
drwxr-xr-x 2 michael michael  4096 Jun 14 18:04 Pictures
drwxr-xr-x 2 michael michael  4096 Jun 14 18:04 Public
drwxr-xr-x 2 michael michael  4096 Jun 14 18:04 Templates
drwxr-xr-x 2 michael michael  4096 Jun 14 18:04 Videos
michael@michael-GM5066B:~$ 

```

---

### Post by Vladlenin5000 on 2015-06-16
So you aren't running it from the directory where it has been downloaded...

---

### Post by angel mike on 2015-06-16
Thanks ajgreeny - your on the right track !
 I was in the home directory. I changed that to the Download directory and the gunzip command worked. However I stil cannot run the driver. I used the command sudo su then tried to run the file - the output is as follows

  ```
root@michael-GM5066B:/home/michael/Downloads# bash linux-brprinter-installer-2.0.0-1-hl3150CDW
bash: linux-brprinter-installer-2.0.0-1-hl3150CDW: No such file or directory
root@michael-GM5066B:/home/michael/Downloads# 
```

---

### Post by ajgreeny on 2015-06-16
Ubuntu does not use the sudo su command like many other distros; it simply needs sudo <command> and then your user password, not a root password as the root account is disabled by default in Ubuntu.
See Root-Sudo in my signature for details.

Is that installer file set as executable? In the **Downloads/linux-brprinter-installer-2.0.0-1** folder which is where I think that file will now be, use command ```
ls -l linux-brprinter-installer-2.0.0-1-hl3150CDW
```to see if it is.

---

### Post by angel mike on 2015-06-16
Thanks for the comment Vladlenin500. I do appreciate the speedy responses from the community. As a new user I do find difficult to do what would be a simple operation to download and run a driver in Windows. There are 3 files I must deal with the initial installer an lpr and a cups - is there no easier way ?
Regards Mike

---

### Post by angel mike on 2015-06-16
Hi ajgreeny. The extracted file is in the Downloads directory. Output is as follows
```
michael@michael-GM5066B:~$ cd Downloads
michael@michael-GM5066B:~/Downloads$ ls -l linux-brprinter-installer-2.0.0-1-hl3150CDW
ls: cannot access linux-brprinter-installer-2.0.0-1-hl3150CDW: No such file or directory
michael@michael-GM5066B:~/Downloads$  

```. Thanks for replying. Mike

---

### Post by ajgreeny on 2015-06-17
OK, so let's find out where this installer file really is.
Use command ```
find -name linux-brprinter-installer-2.0.0-1-hl3150CDW
```and if that returns nothing helpful let's try ```
sudo updatedb
locate -i linux-brprinter
```the second of which should find all folders and files that include that linux-brprinter in their name.

Can we also see exactly what is in your Downloads folder with command ```
ls -l Downloads
```

---

### Post by angel mike on 2015-06-17
Thanks for that sequence - I am away for 2 weeks but will try on my return with a reminder to you if I may.
Appreciate your time. Regards Mike

---

### Post by ajgreeny on 2015-06-17
No problem.
I will try to keep an eye open for your return.
If I miss you, send a PM simply to remind me with a link to this thread, and we'll see if we can get this figured out.

---

### Post by angel mike on 2015-06-18
Thanks for that sequence - I am away for 2 weeks but will try on my return with a reminder to you if I may.
Appreciate your time. Regards Mike

---

