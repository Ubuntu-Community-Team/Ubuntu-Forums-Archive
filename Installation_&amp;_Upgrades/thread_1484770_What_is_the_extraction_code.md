---
title: "What is the extraction code?"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by adeee on 2010-05-16
The lampp code of extraction is this..


tar xvfz xampp-linux-1.7.3a.tar.gz -C /opt

and it works..
now i want to extract phpbb3 to /opt/lampp/htdocs from the desktop.
so what code i use to extract..

remeber phpbb3 are in .zip format.



and also explain in upper code what is

tar?

xvfz?

-C?

i mean what the function of these codes?

---

### Post by Cynical on 2010-05-16
Tar is the archiving utility you are using.

x = extract
v = verbose (meaning to output file names as you are extracting)
f = file (meaning that you will provide a path to a file at the end of the command)
z = filter the archive through gzip (used if the file ends in .tar.gz instead of just .tar)

-C = change to directory (extracting to the defined directory instead of the current one)

You can find all this information by typing 'man tar' in a terminal.

To handle zip files you will need to install the package 'unzip' and then run the command 'unzip file'. If you need more information type 'man unzip' into a terminal after installing the program.

---

### Post by adeee on 2010-05-16
> **Cynical said:**
> Tar is the archiving utility you are using.

x = extract
v = verbose (meaning to output file names as you are extracting)
f = file (meaning that you will provide a path to a file at the end of the command)
z = filter the archive through gzip (used if the file ends in .tar.gz instead of just .tar)

-C = change to directory (extracting to the defined directory instead of the current one)

You can find all this information by typing 'man tar' in a terminal.

To handle zip files you will need to install the package 'unzip' and then run the command 'unzip file'. If you need more information type 'man unzip' into a terminal after installing the program.


oBoy Cynical tell me the procedure how i extract files you just telling me the code.

i dont know how i use these codes..:(

---

### Post by CharlesA on 2010-05-16
> **adeee said:**
> oBoy Cynical tell me the procedure how i extract files you just telling me the code.

i dont know how i use these codes..:(

Put them in a terminal and point it to the file you want to untar?

---

### Post by lisati on 2010-05-16
> **adeee said:**
> oBoy Cynical tell me the procedure how i extract files you just telling me the code.

i dont know how i use these codes..:(

Forget code - that's programming. Use the unzip command as has already been suggested.

---

### Post by 3rdalbum on 2010-05-16
> **adeee said:**
> The lampp code of extraction is this..


tar xvfz xampp-linux-1.7.3a.tar.gz -C /opt

and it works..
now i want to extract phpbb3 to /opt/lampp/htdocs from the desktop.
so what code i use to extract..

remeber phpbb3 are in .zip format.

I assume that you're using a desktop... so why not just double-click the archive and extract it to your Desktop folder, and then copy it to the location you want it? (remember, you'll need to open a file browser as root in order to copy to /opt, because it's outside your home directory).

---

### Post by adeee on 2010-05-17
> **3rdalbum said:**
> (remember, you'll need to open a file browser as root in order to copy to /opt, because it's outside your home directory).

how i become a  root..

in terminal i become root as sudo command..

how mannualy can i become?:KS

---

### Post by Dayofswords on 2010-05-17
> **adeee said:**
> how i become a  root..

in terminal i become root as sudo command..

how mannualy can i become?:KS

you can just put 'sudo' in front of the command to run it with root powers

---

### Post by adeee on 2010-05-17
> **Dayofswords said:**
> you can just put 'sudo' in front of the command to run it with root powers

no no boy i know to put sudo in front to being root. as 3rdalbum says.. 

**remember, you'll need to open a file browser as root in order to copy to /opt, because it's outside your home directory**

i want to direct copy paste file in opt folder.

that need root permission thats why i ask..

---

### Post by Dayofswords on 2010-05-17
if you want to open the file manager as root so you can just copy/paste it over, open a terminal and type```
sudo nautilus
```a new window will open and you can do everything root can.  (don't close or force close the terminal though)

---

