---
title: "karmic - dvb-t adapter bad registration"
date: 2009-09-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by oyankee on 2009-09-29
Hi,
have anyone found solution for this?
After inserting dvb-t adapter with ec168 chip(modules are configured and installed), system (following dmesg) recognize adapter and says thats working. It used to make new directory /dev/dvb/adapter0 but now it only creates this right in /dev/

dvb0.demux0
dvb0.dvr0
dvb0.net0
dvb0.frontend0

Links to /dev/dvb/adapter0 not working. Thanks for advice.

---

### Post by oyankee on 2009-09-29
OK, I found this

Based on kernel version 2.6.31. Page generated on 2009-09-16 22:26 EST.

1   The DVB subsystem currently registers to the sysfs subsystem using the
2   "class_simple" interface.
3   
4   This means that only the basic informations like module loading parameters
5   are presented through sysfs. Other things that might be interesting are
6   currently *not* available.
7   
8   Nevertheless it's now possible to add proper udev rules so that the
9   DVB device nodes are created automatically.
10   
11   We assume that you have udev already up and running and that have been
12   creating the DVB device nodes manually up to now due to the missing sysfs
13   support.
14   
15   0. Don't forget to disable your current method of creating the
16   device nodes manually.
17   
18   1. Unfortunately, you'll need a helper script to transform the kernel
19   sysfs device name into the well known dvb adapter / device naming scheme.
20   The script should be called "dvb.sh" and should be placed into a script
21   dir where udev can execute it, most likely /etc/udev/scripts/
22   
23   So, create a new file /etc/udev/scripts/dvb.sh and add the following:
24   ------------------------------schnipp------------------------------------------------
25   #!/bin/sh
26   /bin/echo $1 | /bin/sed -e 's,dvb\([0-9]\)\.\([^0-9]*\)\([0-9]\),dvb/adapter\1/\2\3,'
27   ------------------------------schnipp------------------------------------------------
28   
29   Don't forget to make the script executable with "chmod".
30   
31   1. You need to create a proper udev rule that will create the device nodes
32   like you know them. All real distributions out there scan the /etc/udev/rules.d
33   directory for rule files. The main udev configuration file /etc/udev/udev.conf
34   will tell you the directory where the rules are, most likely it's /etc/udev/rules.d/
35   
36   Create a new rule file in that directory called "dvb.rule" and add the following line:
37   ------------------------------schnipp------------------------------------------------
38   KERNEL="dvb*", PROGRAM="/etc/udev/scripts/dvb.sh %k", NAME="%c"
39   ------------------------------schnipp------------------------------------------------
40   
41   If you want more control over the device nodes (for example a special group membership)
42   have a look at "man udev".
43   
44   For every device that registers to the sysfs subsystem with a "dvb" prefix,
45   the helper script /etc/udev/scripts/dvb.sh is invoked, which will then
46   create the proper device node in your /dev/ directory.




But I dont understand this:

 0. Don't forget to disable your current method of creating the device nodes manually.

How can I do that?

---

### Post by andersja on 2009-10-06
Any luck in progressing this? I'm considering purchasing an ec168 based USB stick myself, would be good to hear if it's well-supported in Karmic or not. 

Have you tried raising a bug?

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by oyankee on 2009-10-26
No progress, I did not find out how to register it normaly.



Ed: I am stupid. There is a mistake. It should be:


KERNEL=="dvb*", PROGRAM="/etc/udev/scripts/dvb.sh %k", NAME="%c"

---

