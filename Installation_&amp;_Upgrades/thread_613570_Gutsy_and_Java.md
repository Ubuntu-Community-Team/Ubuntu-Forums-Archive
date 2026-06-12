---
title: "Gutsy and Java"
date: 2007-11-15
forum: Installation &amp; Upgrades
---

### Post by Cloudedbrains on 2007-11-15
I am having problems installing Java on Gutsy

I have tried from add/remove, synaptic and terminal window but it still isnt working
I have downloaded the bin file manually but what do I do with it

Also tried uninstalling and reinstalling and nothing at all

But can someone tell me in simple term how I can sort this out PLEASE

---

### Post by Sef on 2007-11-15
1) Have you received any errors messages when installing?  If so, then please post them here.  

2) What are your system specs?

---

### Post by Cloudedbrains on 2007-11-15
No errors

SYtem specs - 2400+ AMD Athlon XP Chip, 512ddram, 250gig hdd, XPand Gutsy dual boot

---

### Post by jespdj on 2007-11-15
"No errors". Tell us exactly and in detail what the problem is, otherwise it will be hard to solve the problem... ](*,)

What did you try? Why didn't it succeed?

First try installing it with the following command:
```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

Then, in a terminal, type "java -v" to see which version of Java is installed and is used by default. If it doesn't say Sun Java 1.6.0_03, try:
```
sudo update-alternatives --config java
```
to set Sun Java as the default Java.

---

### Post by Cloudedbrains on 2007-11-15
I am trying to use a couple of website that use Java to run broadband speed tests and at present the websties wont work !!

I've tried installing via terminal and tried configuring as you said but it gives me 6 options for java !!

---

### Post by PmDematagoda on 2007-11-15
6 options? Could you give the choices given by doing the command given by jespdj?

---

### Post by Cloudedbrains on 2007-11-15
> **PmDematagoda said:**
> 6 options? Could you give the choices given by doing the command given by jespdj?

There are now 9 options :confused:

```
  Selection    Alternative
-----------------------------------------------
          1    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
*+        2    /usr/lib/j2se/1.4/bin/java
          3    /usr/lib/jvm/java-6-sun/jre/bin/java
          4    /usr/bin/gij-4.2
          5    /usr/bin/java-sablevm
          6    /usr/bin/jamvm
          7    /usr/bin/cacao
          8    /etc/alternatives/kaffe-system/bin/java
          9    /usr/lib/jvm/java-gcj/jre/bin/java

```

THis is one website I can't access that uses Java that I need to get working :o

[http://speedtester.bt.com/](http://speedtester.bt.com/)

---

### Post by Cloudedbrains on 2007-11-15
Getting weirder now back to 6 options !!

```
  Selection    Alternative
-----------------------------------------------
          1    /usr/lib/jvm/java-6-sun/jre/bin/java
          2    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
          3    /usr/bin/cacao
*+        4    /usr/lib/j2se/1.4/bin/java
          5    /usr/bin/jamvm
          6    /usr/lib/jvm/java-7-icedtea/jre/bin/java

```

---

### Post by PmDematagoda on 2007-11-15
Ok, switch to Java 6 Sun and see if that would solve your problem. But the thing about 6 options is very strange, I do not know why that would happen unless you installed multiple JVMs.

---

### Post by Cloudedbrains on 2007-11-16
I have tried 6 and every other one too but no go with at least ONE particular website :o

[http://speedtester.bt.com/](http://speedtester.bt.com/)

Could it be that that website is windows only ???

---

### Post by meho_r on 2007-11-16
Strange. Sun java didn't work for me neither, but IcedTea works perfectly (even old Java-problems with FrostWire with IcedTea are solved). Some people recommend to uninstall every java and then install IcedTea. BTW, which browser you're using? 32 bit?

---

### Post by Cloudedbrains on 2007-11-16
firefox that came with gutsy

---

### Post by meho_r on 2007-11-16
When type in address bar:
[HTML]about:plugins[/HTML]
can you see java? Did you check out if java is enabled in Edit > Preferences > Content?

---

### Post by Cloudedbrains on 2007-11-16
I've already done the ```
about:plugins
``` - check page 1 of this thread 
Java is enabled

---

### Post by meho_r on 2007-11-17
OK, you said you tried uninstall and than again install. Did you try uninstall ALL javas and then install ONLY IcedTea java? This worked for me, so you may give it a try.

---

### Post by Cloudedbrains on 2007-11-17
Tried but no joy

---

### Post by Cloudedbrains on 2007-11-18
Can anyone help me sort Java out at all :confused:
I need java working, if I cant get it working I will have to just switch back to windows :(

---

### Post by Cloudedbrains on 2007-11-18
Due to java not working on ubuntu I am back onto windows alone the quick way

I did this by doing the following:
1) used xp disc to wipe the ubuntu partitions
2) then rebooted and used the xp disc to enter the repair console
3) then used the FixMBR command 
4) rebooted and here I am back under windows on its own

---

