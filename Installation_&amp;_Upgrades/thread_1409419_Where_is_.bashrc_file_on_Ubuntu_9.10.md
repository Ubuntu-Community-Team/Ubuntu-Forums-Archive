---
title: "Where is .bashrc file on Ubuntu 9.10"
date: 2010-02-17
forum: Installation &amp; Upgrades
---

### Post by joyboyhardik@yahoo.com on 2010-02-17
I am very new to Linux. I am using Ubuntu 9.10. I was installing network simulator 2. After installation I get the following message.

[I]Please put /home/administrator/Downloads/ns-allinone-2.34/bin:/home/administrator/Downloads/ns-allinone-2.34/tcl8.4.18/unix:/home/administrator/Downloads/ns-allinone-2.34/tk8.4.18/unix
into your PATH environment; so that you'll be able to run itm/tclsh/wish/xgraph.

IMPORTANT NOTICES:

(1) You MUST put /home/administrator/Downloads/ns-allinone-2.34/otcl-1.13, /home/administrator/Downloads/ns-allinone-2.34/lib, 
    into your LD_LIBRARY_PATH environment variable.
    If it complains about X libraries, add path to your X libraries 
    into LD_LIBRARY_PATH.
    If you are using csh, you can set it like:
        setenv LD_LIBRARY_PATH <paths>
    If you are using sh, you can set it like:
        export LD_LIBRARY_PATH=<paths>

(2) You MUST put /home/administrator/Downloads/ns-allinone-2.34/tcl8.4.18/library into your TCL_LIBRARY environmental
    variable. Otherwise ns/nam will complain during startup.


After these steps, you can now run the ns validation suite with
cd ns-2.34; ./validate

For trouble shooting, please first read ns problems page 
[http://www.isi.edu/nsnam/ns/ns-problems.html](http://www.isi.edu/nsnam/ns/ns-problems.html). Also search the ns mailing list archive
for related posts.
[/I]
My friend suggested that it is something to do with .bashrc file. I fund files like .bash.bashrc. can you anyone pleaes guide me

---

### Post by joyboyhardik@yahoo.com on 2010-02-17
bouce

---

### Post by Satoru-san on 2010-02-17
```
nano ~/.bashrc
```as user.

```
export PATH=$PATH:/home/administrator/Downloads/ns-allinone-2.34/bin:/home/administrator/Downloads/ns-allinone-2.34/tcl8.4.18/unix:/home/administrator/Downloads/ns-allinone-2.34/tk8.4.18/unix
```add that to that file. copy and paste with ctl +&#12288;shift + v

it will look similar to this
[view it by doing echo $PATH]

```
/usr/local/bin:/usr/bin:/bin:/opt/bin:/usr/i686-pc-linux-gnu/gcc-bin/4.3.4:/usr/games/bin:/home/administrator/Downloads/ns-allinone-2.34/bin:/home/administrator/Downloads/ns-allinone-2.34/tcl8.4.18/unix:/home/administrator/Downloads/ns-allinone-2.34/tk8.4.18/unix

```
If you have any questions about what the commands do, ask someone!

if something breaks, or you mess up your path... its an easy fix

```
source /etc/profile
```

Please mark this as solved.

:D Welcome to the forums! Enjoy it here! :D
**DONT BLINDLY RUN COMMANDS THAT PEOPLE ON THE FORUMS TELL YOU**
[I]some times people will post malicious command that will destroy your 
install[/I]

---

### Post by joyboyhardik@yahoo.com on 2010-02-19
I tried to run a simple NS code i get this

administrator@ubuntu:~/Downloads/ns-allinone-2.34/ns-2.34$ ns ns-simple.tcl
CBR packet size = 1000
CBR interval = 0.0080000000000000002
ns: finish: couldn't execute "nam": permission denied
    while executing
"exec nam out.nam &"
    (procedure "finish" line 7)
    invoked from within
"finish"
 help

---

### Post by nxw0016 on 2010-04-02
I have the same problem (permission denied). Anybody can help?
When I try to execute the nam command from ../ns-allinone-2.34/nam-1.14 folder, it seems OK. But ns2 can not launch nam.
 
Thanks a lot!!
 
> **joyboyhardik@yahoo.com said:**
> I tried to run a simple NS code i get this
 
administrator@ubuntu:~/Downloads/ns-allinone-2.34/ns-2.34$ ns ns-simple.tcl
CBR packet size = 1000
CBR interval = 0.0080000000000000002
ns: finish: couldn't execute "nam": permission denied
while executing
"exec nam out.nam &"
(procedure "finish" line 7)
invoked from within
"finish"
help

---

### Post by ran1063 on 2012-03-14
i am trying to install but i am not getting installed what can i do for this


IMPORTANT NOTICES:

(1) You MUST put /root/ns-allinone-2.34/otcl-1.13, /root/ns-allinone-2.34/lib, 
    into your LD_LIBRARY_PATH environment variable.
    If it complains about X libraries, add path to your X libraries 
    into LD_LIBRARY_PATH.
    If you are using csh, you can set it like:
        setenv LD_LIBRARY_PATH <paths>
    If you are using sh, you can set it like:
        export LD_LIBRARY_PATH=<paths>

(2) You MUST put /root/ns-allinone-2.34/tcl8.4.18/library into your TCL_LIBRARY environmental
    variable. Otherwise ns/nam will complain during startup.


After these steps, you can now run the ns validation suite with
cd ns-2.34; ./validate

For trouble shooting, please first read ns problems page 
[http://www.isi.edu/nsnam/ns/ns-problems.html](http://www.isi.edu/nsnam/ns/ns-problems.html). Also search the ns mailing list archive
for related posts.

---

### Post by oldos2er on 2012-03-14
ran1063, please start a new thread in Absolute Beginners, and add as many details about your problem as possible.

---

