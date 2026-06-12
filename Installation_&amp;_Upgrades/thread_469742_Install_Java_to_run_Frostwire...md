---
title: "Install Java to run Frostwire.."
date: 2007-06-10
forum: Installation &amp; Upgrades
---

### Post by Znort_Ubern00b on 2007-06-10
Hello peeps,

Can someone help me, I am an Ubern00b and am stuck trying to install Java so as I can run Frostwire or Limewire. I have followed the instructions on the Java website but get this when I type rpm -i jre-6u1-linux-i586.rpm

 error: Failed dependencies:
        /bin/basename is needed by jre-1.6.0_01-fcs.i586
        /bin/cat is needed by jre-1.6.0_01-fcs.i586
        /bin/cp is needed by jre-1.6.0_01-fcs.i586
        /bin/gawk is needed by jre-1.6.0_01-fcs.i586
        /bin/grep is needed by jre-1.6.0_01-fcs.i586
        /bin/ln is needed by jre-1.6.0_01-fcs.i586
        /bin/ls is needed by jre-1.6.0_01-fcs.i586
        /bin/mkdir is needed by jre-1.6.0_01-fcs.i586
        /bin/mv is needed by jre-1.6.0_01-fcs.i586
        /bin/pwd is needed by jre-1.6.0_01-fcs.i586
        /bin/rm is needed by jre-1.6.0_01-fcs.i586
        /bin/sed is needed by jre-1.6.0_01-fcs.i586
        /bin/sort is needed by jre-1.6.0_01-fcs.i586
        /bin/touch is needed by jre-1.6.0_01-fcs.i586
        /usr/bin/cut is needed by jre-1.6.0_01-fcs.i586
        /usr/bin/dirname is needed by jre-1.6.0_01-fcs.i586
        /usr/bin/expr is needed by jre-1.6.0_01-fcs.i586
        /usr/bin/find is needed by jre-1.6.0_01-fcs.i586
        /usr/bin/tail is needed by jre-1.6.0_01-fcs.i586
        /usr/bin/tr is needed by jre-1.6.0_01-fcs.i586
        /usr/bin/wc is needed by jre-1.6.0_01-fcs.i586
        /bin/sh is needed by jre-1.6.0_01-fcs.i586


can anyone help??? I have followed the instructions to a T and still no luck

site address is [http://www.java.com/en/download/help/5000010500.xml#selfextracting](http://www.java.com/en/download/help/5000010500.xml#selfextracting) and I used the self extracting rpm file.

Any help would be great...I am very new to linux so be kind...


Znort

---

### Post by Vola on 2007-06-10
Just type in terminal

sudo apt-get install sun-java6-jdk


Anyway ubuntu doesn't use rpm package system.

---

### Post by Znort_Ubern00b on 2007-06-10
OK I have done that but still no response from either application...go to terminal and type frostwire to run it and get:

Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com) [java = SableVM]
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)

try limewire and get:
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. LimeWire works best with Sun JRE available at [http://www.java.com](http://www.java.com) [java = SableVM]
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)

Any help will be greatly appreciated.

---

### Post by Eric_Jardas on 2007-06-10
run:
```
sudo update-alternatives --config java
```

and set the correct option.

---

### Post by Znort_Ubern00b on 2007-06-10
Many thanks to you both for your help it is now all sorted and working...again thanks.
:popcorn:


slight update, have just run it and when finished configuring all i get is a a blank page...any ideas???

---

### Post by odiseo77 on 2007-06-10
> **Znort_Ubern00b said:**
> slight update, have just run it and when finished configuring all i get is a a blank page...any ideas???

Are you using beryl or compiz?? Beryl/compiz are not compatible with java (java apps need to be tweaked in order to work with beryl or compiz)

---

### Post by Znort_Ubern00b on 2007-06-10
I'm using Beryl...do you know how to tweak them?? if so please help me...

when i run in terminal i get this message:
java.lang.Exception: Stack trace
        at java.lang.Thread.dumpStack(Thread.java:1206)
        at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
        at irc.ListenerGroup.sendEventEx(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.gui.pixx.PixxTaskBar.enter(Unknown Source)
        at irc.gui.pixx.PixxTaskBar.addStatus(Unknown Source)
        at irc.gui.pixx.PixxMDIInterface.statusCreated(Unknown Source)
        at irc.gui.pixx.PixxMDIInterface.sourceCreated(Unknown Source)
        at irc.IRCApplication.sourceCreated(Unknown Source)
        at irc.IRCServer.enumerateSourcesAsCreated(Unknown Source)
        at irc.IRCApplication.newServer(Unknown Source)
        at irc.IRCApplication.init(Unknown Source)
        at com.limegroup.gnutella.gui.chat.ChatMediator.tryToStartAndAddChat(ChatMediator.java:143)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:104)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:72)
        at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:122)
        at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:219)
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:327)
        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:597)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@18e18a3
current thread is Thread[main,5,main]

---

### Post by Znort_Ubern00b on 2007-06-10
Ok something wierd just happened....have just gone back to my desktop and lo and behold it is now working...or seems to be...not sure as to why as I have beryl running.

 Thank you all for your help its been a godsend.

Regards

---

### Post by odiseo77 on 2007-06-10
This is not 100% effective (I've tested it with mercury messenger on java 1.5 and I had to disable the trayicon functionality, which is annoying), but take a look at this: [http://wiki.beryl-project.org/wiki/Java](http://wiki.beryl-project.org/wiki/Java)

As for the messages you get in the terminal, I have no idea what they mean, sorry (I guess it's normal java output).

---

