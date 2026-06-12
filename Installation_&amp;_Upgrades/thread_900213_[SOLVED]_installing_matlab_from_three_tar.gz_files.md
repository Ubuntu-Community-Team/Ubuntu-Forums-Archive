---
title: "[SOLVED] installing matlab from three tar.gz files."
date: 2008-08-25
forum: Installation &amp; Upgrades
---

### Post by electronique on 2008-08-25
hello,
Our university is providing matlab .
Though not clear to me :confused: the installation instructions have been given:).
The instructions are like this:

1. Select a disk partition and make a directory matlabcd and enter the directory ie:
    i) mkdir matlabcd
   ii) cd matlabcd
2. Next ftp the required product cds (matlab6.5-cd*.tar.gz) from the above site.

**[SIZE="4"]doubt one:this matlabcd directory can be any where(like in downloads)right?[/SIZE]**
 
3. Unzip the cd as follows
     gunzip matlab6.5-cd*.tar.gz
4. Untar the product as
     tar -xvf matlab6.5-cd*.tar.gz
5. Make a directory /usr/local/matlab/etc and copy license.dat residing on 
     [ftp://ftp.iitb.ac.in/IITb/software/Matlab/6.5/Unix/](ftp://ftp.iitb.ac.in/IITb/software/Matlab/6.5/Unix/)
6. Make entries into /etc/hosts for activating the licenses through the network.
     10.100.10.1             license1.iitb.ac.in  license1
     10.100.10.2             license2.iitb.ac.in  license2
     10.100.10.3             license3.iitb.ac.in  license3
     These are license servers for Matlab 6.5.

**[SIZE="4"]Doubt two:there is no hosts directory in etc ... should i create it?[/SIZE]**

7. From the directory matlabcd run the script install as
     ./install
  This needs to be done for every cd separately.

please clear my doubts.
thank you in advance.

---

### Post by Partyboi2 on 2008-08-25
> **[SIZE=4]doubt one:this matlabcd directory can be any where(like in downloads)right?[/SIZE]**Thats correct.
> **[SIZE=4]Doubt two:there is no hosts directory in etc ... should i create it?[/SIZE]**/etc/hosts is a file not a directory, so you can open it up with a text editor like gedit, nano etc... and make the adjustments.

```
sudo gedit /etc/hosts
```

---

### Post by prshah on 2008-08-25
> **electronique said:**
> 
**doubt one:this matlabcd directory can be any where(like in downloads)right?**
 
**Doubt two:there is no hosts directory in etc ... should i create it?**


Yes and [s]yes[/s]. EDIT: Oops, misread post. Doubt2 advice is wrong.

For doubt 1: You can have the directory anywhere you like on your system; but preferably not on the desktop (better to _avoid_ Desktop, but no rule against it).

For doubt 2: (EDIT: Misread post, so everything here was irrelevant)

---

### Post by electronique on 2008-08-25
Thank you for your responses.
I would install matlab, but for a few clarifications from my 
institute.

As partyboi2 has said ... I can choose any of the directories
from my working home directory(except desktop , yeah ... good suggestion).
I would like to ask if it is the "conventional" place to keep the matlab
installation files.

Can I delete the matlabcd directory after completion of installation?
If not I think many sort of files would be created which I would not like
to keep in my working account directory!

---

### Post by Partyboi2 on 2008-08-25
Really comes down to personal preference, you could create a folder in your /home directory.
You should be ok to delete the matlabcd directory after you have finished compiling, deleting it will not harm the program.

---

### Post by electronique on 2008-08-26
Thank you very much ... 
I can now actually install matlab.

---

### Post by prshah on 2008-08-26
> **electronique said:**
> 
I can now actually install matlab.

If this issue is resolved, can you mark the thread solved? Near the top right hand side of the page, click on "Thread Tools"-"Mark thread as solved"

---

