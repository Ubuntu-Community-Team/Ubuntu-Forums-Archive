---
title: "frostwire will not run"
date: 2006-07-01
forum: Installation &amp; Upgrades
---

### Post by underdog512 on 2006-07-01
I recently installed  frostwire so i can have a P2P client.  It installed with errors.  However when I try run it, this is the output that I get: 

Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)


I did install sun-java5 But I am still getting the same output.  HELP!!! lol

---

### Post by woedend on 2006-07-02
sudo update-alternatives --config java

select sun's

---

### Post by underdog512 on 2006-07-02
YES YES!!!! IT WORKS!!!!!!!!!!!!     thanx dude

---

### Post by measure on 2006-07-08
Thanks, this helped me too.

---

### Post by Buddha420 on 2006-07-10
Dito. Thanks for the quick fix woedend... ;)

---

### Post by Edache on 2006-07-15
I would also like to say thanks woedend

---

### Post by Maheriano on 2006-07-16
What have I got done wrong?

> dan@danny:~$ sudo update-alternatives --config java

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*     1        /usr/bin/gij-wrapper-4.1
 +    2        /usr/lib/jvm/java-gcj/jre/bin/java

Press enter to keep the default[*], or type selection number:

---

### Post by woedend on 2006-07-17
you have to instlal sun's java from the repos first

---

### Post by Gummy200 on 2007-07-12
Changed to Metacity... and LimeWire works a dream...(your a Genius!!!!)...However I'm unable to move my Tracks to a folder onto my desktop why???

---

