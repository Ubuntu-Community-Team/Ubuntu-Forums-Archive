---
title: "Please help: java install and root access"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by vi1985 on 2008-04-25
Hey guys,
I'm a new Ubuntu user (just installed it a few hours ago!). I was trying to install jre 1.6 and ran into a couple of problems:

first of all, I'd like to know how I can get root access. I first tried the manual install of jre, which needs 'alien' to convert from .rpm to .deb, which in turn needs root access. I tried running:
$su
then entered my user password, but was denied access:

vitya@vitya-laptop:~$ su
Password: 
su: Authentication failure

I don't remember setting any other passwords while installing ubuntu. Is there a generic password that I can change somewhere? Is it the BIOS password? (which I'll have to dig up somehow..)

 --------------------------

My second issue is with installing jre 1.6. They said something to the effect that my system must support the DLJ license, I agreed to that, at which point installation ran for some time, until it was aborted with the following error log:

Preconfiguring packages ...
Selecting previously deselected package java-common.
(Reading database ... 96652 files and directories currently installed.)
Unpacking java-common (from .../java-common_0.28ubuntu3_all.deb) ...
Selecting previously deselected package odbcinst1debian1.
Unpacking odbcinst1debian1 (from .../odbcinst1debian1_2.2.11-16build1_i386.deb) ...
Selecting previously deselected package unixodbc.
Unpacking unixodbc (from .../unixodbc_2.2.11-16build1_i386.deb) ...
Selecting previously deselected package sun-java6-bin.
Unpacking sun-java6-bin (from .../sun-java6-bin_6-06-0ubuntu1_i386.deb) ...
user did not accept the sun-dlj-v1-1 license
dpkg: error processing /var/cache/apt/archives/sun-java6-bin_6-06-0ubuntu1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Selecting previously deselected package sun-java6-jre.
Unpacking sun-java6-jre (from .../sun-java6-jre_6-06-0ubuntu1_all.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/sun-java6-bin_6-06-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up java-common (0.28ubuntu3) ...

dpkg: dependency problems prevent configuration of sun-java6-jre:
 sun-java6-jre depends on sun-java6-bin (= 6-06-0ubuntu1) | ia32-sun-java6-bin (= 6-06-0ubuntu1); however:
  Package sun-java6-bin is not installed.
  Package ia32-sun-java6-bin is not installed.
dpkg: error processing sun-java6-jre (--configure):
 dependency problems - leaving unconfigured
Setting up odbcinst1debian1 (2.2.11-16build1) ...

Setting up unixodbc (2.2.11-16build1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 sun-java6-jre

----


Please help guys :)

Thanks a lot!
victor.

---

### Post by vi1985 on 2008-04-25
Ok, second problem solved! :) Got jre up and running!

But i still don't understand how to get root access. Any helo will be much appreciated! 	=D>

~Victor

---

### Post by amingv on 2008-04-25
To execute a command with root privilege:

```
sudo <command>
```

to get a "root console" temporarily:

```
sudo su
```

---

### Post by Unterseeboot_234 on 2008-04-25
Hey guy, I LOVE my jdk1.6.10 install along with NetBeans. The new ui skins in 1.6.10 give a clue what jdk7 will be like -- the Nimbus Look and Feel is total Vector art and only 56k footprint. 

I have tried installing java with Synaptic and with Automatix. It works but it puts everything deep inside the File System. Then it becomes a pain to move files around or to view the API docs and tutorials. Not good for a developer, we need to slam copies, bytecode, graphics, etc.

I used the .rar/.zip bundle from Sun's download location for 64-bit. That does not include the web plug-in (which is another install issue). I put the installation in my Home Folder. NetBeans is nice because it slams the path name to java/bin for every test run you do with your source code, and besides, the code editor is first-rate.

That setup might short-circuit a Text Editor / Terminal coding technique. You might have a simple java exercise and want to 
>$ javac MyCode.java, 
>$ java MyCode 
And, it can't find the java /bin directory. For that, I use the discussion from the 'buntu Forums about java...

[**Custom JDK install**]("http://ubuntuforums.org/showthread.php?t=319138")

But, you shouldn't have any problems with the Sun download, which installs path and pathname. On a 'buntu box, you must CD into a folder with Terminal to do java the old-fashioned way. Make sure you delete your previous efforts of installing. Get the NetBeans, it helps with advanced stuff like making an executable .jar.

Bottom line, I would NOT set up java dev as a Root Administrator. From start to finish, you have nothing but problems.

---

