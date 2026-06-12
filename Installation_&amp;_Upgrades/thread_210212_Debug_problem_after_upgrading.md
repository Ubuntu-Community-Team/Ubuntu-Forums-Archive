---
title: "Debug problem after upgrading"
date: 2006-07-06
forum: Installation &amp; Upgrades
---

### Post by pinic on 2006-07-06
Hi all,
I'm not sure if this is the right forum to post my issue but I will glad for any help.

After upgrade my breezy to dapper a weird problem in my workstation appear.
I am running remote debugger (from my intellij IDE) attached to weblogic running on localhost, in java 1.5 environment.
After upgrading ubuntu, the debugger become lazy, every step taking about 20 seconds.
no mater what the code executing (even 'String str = "aaaa";').

I try to download and install again the j2se
trying to Install the IDEA also. but without any success, the debugger still giving me hard time.
any ideas?

---

### Post by pinic on 2006-08-01
If you find yourself with the same problem so ...
I will reply to my self :)

A DESCRIPTION OF THE PROBLEM :
Debugging under Linux 2.6.15 and higher is horribly slow because of remote debuggings use of many small packets and TCP_NODELAY being set on. (While we can control the socket on the debugger client the socket in the JDK probably *shouldn't* set TCP_NODELAY for debugger sockets or at least their should be an option to not enable TCP_NODELAY) The slow down increases with with size of the debug frame. (The more variables the larger the slow down.)

STEPS TO FOLLOW TO REPRODUCE THE PROBLEM :
Fire up netbeans, eclipse, Intellij or any debugger and attach to a JDK on Linux while running kernel 2.6.15 or higher. Set some break points and start stepping through code. If the frame has a collection with say 100 items in it step through a for loop of each item. It will take an hour or so. In order to at least partially disable Nagles Algorithm run "**sudo sysctl -w net.ipv4.tcp_abc=0**" as root and then rerun the test. It will perform as expected.

Work Around:
1) Use a linux kernel before 2.6.15 (this is a change in 2.6.15)
2) run "sudo sysctl -w net.ipv4.tcp_abc=0" as root to disable Nagles prior to debugging. However this disables it system wide may not be appropriate.

for more details :
[http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6401245](http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6401245)

---

