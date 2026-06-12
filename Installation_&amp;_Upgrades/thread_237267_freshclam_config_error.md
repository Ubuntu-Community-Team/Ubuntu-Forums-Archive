---
title: "freshclam config error"
date: 2006-08-15
forum: Installation &amp; Upgrades
---

### Post by Kurt_Alan on 2006-08-15
**[SIZE="5"][/SIZE]**
Hi,

 I am an Ubuntu newbie compiling for the first time, okay, the second or third time.  I have sucessfully
compiled clamav and run the program from the shell.  However, my virus
definitions are out-of-date and when I execute freshclam I receive this
error message:

Error: Need to edit config file /usr/local/etc/freshclam.conf
Error: Need to edit config file /usr/local/etc/clamd.conf
Error: Cannot parse config file/usr/local/etc/clamd.conf                                   [-o< 

Further, the clamav documention states that I should review the document
clamd.conf(5) for the purpose of configuration.

I have read this document on-line.  I do not understand what I am looking at
or what to do.
If you can help, please state explicit and concrete steps that I should
perform . . .

---

### Post by geezerone on 2007-02-22
Hi

Getting same error anyone to help? 

sudo freshclam
ERROR: Please edit the example config file /usr/local/etc/freshclam.conf.
ERROR: Please edit the example config file /usr/local/etc/clamd.conf.
ERROR: Can't parse the config file /usr/local/etc/clamd.conf

---

### Post by Chemist on 2008-04-09
i'm getting this error too, can anyone help?

---

### Post by freemant on 2008-06-26
Just comment out (or delete) the line in the two .conf 
files that says:

[FONT="Courier New"]   # Comment it out
   Example[/FONT]

This is one of the stupidest requirements that I've 
seen.

---

