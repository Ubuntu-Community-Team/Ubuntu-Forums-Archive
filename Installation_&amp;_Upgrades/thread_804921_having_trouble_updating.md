---
title: "having trouble updating"
date: 2008-05-23
forum: Installation &amp; Upgrades
---

### Post by REXXER on 2008-05-23
Hello,

Im fairly new to linux and im having trouble updating. I try using synaptic package manager and apt-get, but it keeps saying "failed to fetch" and then the website it was trying to get to. An example is:   "W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)" they all look pretty similar (just different websites). I have tried changing my dns on my router (i couldn't figure out how to do it on my laptop), and it still doesn't work.

I am using an HP dv2000cto, with Ubuntu 8.04.

Please help,

Ronen

---

### Post by hal8000 on 2008-05-23
Have you set up your network?
It looks as though you have no connectivity. From a terminal, what is the output of:
ping -c4 google.com

---

### Post by REXXER on 2008-05-23
i forgot to mention that it used to work before i got my wireless to work, than i set up my wireless and now it doesn't work (im using verizon fios broadband internet and a PPPoE connection).

here is the results of ping -c4 google.com


r3xx3r@Ronen-Laptop:~$ ping -c4 google.com
PING google.com (64.233.187.99) 56(84) bytes of data.
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=1 ttl=241 time=31.7 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=2 ttl=241 time=31.2 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=3 ttl=241 time=32.2 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=4 ttl=241 time=32.2 ms

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3009ms
rtt min/avg/max/mdev = 31.273/31.884/32.288/0.418 ms

---

### Post by hal8000 on 2008-05-23
OK, internet is working, try
sudo apt-get update 
from a terminal. If the same error persists, it may be nothing more than the US mirror you are using is down. Try changing the mirror from System, software sources.

---

### Post by JustAl1 on 2008-05-26
I have the same problem, I cannot update . I tried changing software sources and still doesn't work. The internet is working allright and there is no packet loss with .I tried the ping thing , when I try to update this is what comes up:
W: Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2](http://archive.linux.duke.edu/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.
                      Any help would be appreciated 
P.S. this problem started since I updated to Hardy 
P.S.S frostwire doesn't work either since I updated to hardy.It worked fine with the older distribution.(the one before hardy).When I run click on the frostwire icon on the menu ,nothing happens and when I try to run frostwire on the terminal this is the message that I get :
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0]
Configuring environment...
Loading FrostWire:
java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/motif21/libmawt.so
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1666)
	at java.lang.Runtime.load0(Runtime.java:787)
	at java.lang.System.load(System.java:1022)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1767)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1684)
	at java.lang.Runtime.loadLibrary0(Runtime.java:840)
	at java.lang.System.loadLibrary(System.java:1047)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:67)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:47)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.awt.Toolkit.loadLibraries(Toolkit.java:1610)
	at java.awt.Toolkit.<clinit>(Toolkit.java:1632)
	at com.limegroup.gnutella.gui.Main.showInitialSplash(Main.java:67)
	at com.limegroup.gnutella.gui.Main.main(Main.java:39)


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0"
OpenJDK Runtime Environment (build 1.6.0-b09)
OpenJDK Client VM (build 1.6.0-b09, mixed mode, sharing)


           As you can see I have java1.6.0.
 Any help would be appreciated ,this is the first time ever I've had trouble with ubuntu that I couldnt fix quickly :(

---

### Post by JustAl1 on 2008-05-26
I've got the update problem fixed by going to synaptic
 package manager and unistalling anon-proxy and restarting the pc. I've read this solution by reading another thread and thanks to Kouki who had the same problem and posted the answer.[http://ubuntuforums.org/showthread.php?t=803733&highlight=111+Connection+refused+hardy]("http://ubuntuforums.org/showthread.php?t=803733&highlight=111+Connection+refused+hardy")
     Frostwire is still not working though I dont know whats wrong with it, any leads
       here is the message I get when I try to run it from the terminal:


Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0]
Configuring environment...
Loading FrostWire:
java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/motif21/libmawt.so
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1666)
	at java.lang.Runtime.load0(Runtime.java:787)
	at java.lang.System.load(System.java:1022)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1767)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1684)
	at java.lang.Runtime.loadLibrary0(Runtime.java:840)
	at java.lang.System.loadLibrary(System.java:1047)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:67)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:47)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.awt.Toolkit.loadLibraries(Toolkit.java:1610)
	at java.awt.Toolkit.<clinit>(Toolkit.java:1632)
	at com.limegroup.gnutella.gui.Main.showInitialSplash(Main.java:67)
	at com.limegroup.gnutella.gui.Main.main(Main.java:39)


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0"
OpenJDK Runtime Environment (build 1.6.0-b09)
OpenJDK Client VM (build 1.6.0-b09, mixed mode, sharing)


           Thanks in advance for the help :)

---

### Post by JustAl1 on 2008-05-26
Got the solution, looked it up on frostwire forums here [http://www.frostwire.com/forum/viewtopic.php?f=1&t=4219]("http://www.frostwire.com/forum/viewtopic.php?f=1&t=4219")

---

