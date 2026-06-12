---
title: "No application, just &quot;java applet window!"
date: 2007-08-05
forum: Installation &amp; Upgrades
---

### Post by puppy on 2007-08-05
Hi folks - when running some java chat programs from the web, rather than get the application actually starting, I just get a grey window with "java applet window" in the middle of it  :confused:

running sudo update-alternatives --config java I get:

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/lib/jvm/java-6-sun/jre/bin/java
*+        2    /usr/lib/j2se/1.4/bin/java

Press enter to keep the default[*], or type selection number: 

Can anyone advise what I might need to do to get this working? I might as well not have java installed at the moment... :(

---

### Post by woyzeckswoe on 2007-08-06
i've got the same problem, and by typing:

~$ java -version

i get this:

java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)

it should run, i really dunno whats goin on

thanks

edit: i installed epiphany and with that browser java will work!

---

### Post by sHaDYvB on 2007-08-15
also the same problem with many applications , 

limewire , prayertimes , and others

the window opens to an empty grey space with nothing inside , tried to change version using :

sudo update-alternatives --config java

but no luck .. this is really annoying me on my first ubuntu installation ..

tried reinstalling java and no luck also .. plz advise ..

---

### Post by sHaDYvB on 2007-08-21
after some experiments , found that the problem resides in using Beryl when opening the programs ..

to solve the problem ( the only method i found till now ) :

1- Disable your Beryl Manager ( from Beryl Manager Choose "Select Window Manager" , "Metacity" )

2- Open your application ( limewire or etc )

3- Restore your Beryl interface by choosing "Beryl" from "Select Window Manager"

this should work just fine till other fixes come soon ..

---

