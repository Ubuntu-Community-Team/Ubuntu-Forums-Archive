---
title: "Error when trying to start Apache James on Ubuntu 8.04 Server"
date: 2008-09-08
forum: Installation &amp; Upgrades
---

### Post by carljokl on 2008-09-08
I am having the following error when I try and start Apache James on my Ubuntu Server:

java.lang.NullPointerException
        at org.apache.avalon.phoenix.frontends.CLISetup.parseCommandLineOptions(
CLISetup.java:202)
        at org.apache.avalon.phoenix.frontends.CLIMain.main(CLIMain.java:122)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.
java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAcces
sorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:597)
        at org.apache.avalon.phoenix.launcher.Main.startup(Main.java:135)
        at org.apache.avalon.phoenix.launcher.Main.main(Main.java:84)

It looks like something is going wrong in the phoenix library but I am not clear as to why this is happening and the underlying cause. Searching on the internet I haven't found much or any information about this problem and wondered if anyone has had similar problems when trying to run Apache James on Ubuntu. I have happily been able to install James on Windows several times and am not new to Linux. I installed Tomcat with no problems but James doesn't seem to want to work.

---

### Post by jamesstansell on 2008-09-09
It doesn't like something about your command-line parameters.  Are you using the same options as you use on windows?

---

### Post by carljokl on 2008-09-10
I have been looking into the problem further including the source code where the problem is occuring as well as some other experiments. What I have noted is that the startup process gets a lot further when I run it as me but falls over when it tries to open ports. This makes perfect sense though as only root users are able to open ports bellow 1024. The null pointer exception occurs when run as super user i.e. sudo. I am aware that the super user doesn't pick up any of the environment variables which I have set in the general etc/environment file. To get around that the init.d startup script sets those variable. I have re-checked those variables but don't seem to find any problem with them. I wonder if I set up James to run as a less privilaged user and then used IPTables to redirect traffic to ports it would be running on. That could work perhaps.

It would help to know a bit more about customising the environment for the super user as Ubuntu is the first Linux distro I have used which locks down the root user account. I am used to installing applications as as the root user and then setting them up to run with a less privilaged user. I seem to be forever faced with the problem that the unprivilaged user has the correct environment but lacks permissions to manipulate files or open ports etc but if I use super user permissions are not a problem but the environment is not set.

---

