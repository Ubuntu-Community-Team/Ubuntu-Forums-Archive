---
title: "Upgrade of JabRef"
date: 2010-06-28
forum: Installation &amp; Upgrades
---

### Post by virsto on 2010-06-28
I am running JabRef 2.5 on a Ubuntu 10.04 platform. There is an upgrade JabRef 2.6 currently available in the form of a jar file.

How can I upgrade to JabRef 2.6?

Note, I have Java installed, as follows

```
$ java -version
java version "1.6.0_18"
OpenJDK Runtime Environment (IcedTea6 1.8) (6b18-1.8-0ubuntu1)
OpenJDK Server VM (build 14.0-b16, mixed mode)

```

and I have downloaded JabRef-2.6.jar.

Any suggestions would be appreciated.

--V

---

### Post by virsto on 2010-06-29
Finally a solution :D

My objective was to upgrade from JabRef 2.5 to JabRef 2.6. The problem was that JabRef 2.6 was not recognized in "Synaptic Package Manager" and I could not figure out how to upgrade to 2.6.

I used the following steps to upgrade to 2.6 and place its executable icon in the right panel. Albeit, some of the steps seem awkward and the procedure could probably be improved.

[COLOR=#000000][FONT=Sans Serif]1) Download JabRef-2.6.jar  from[/FONT][/COLOR]

    [COLOR=#000000][FONT=Sans Serif]     [http://sourceforge.net/projects/jabref/files/jabref/2.6](http://sourceforge.net/projects/jabref/files/jabref/2.6)[/FONT][/COLOR]
    [COLOR=#000000][FONT=Sans Serif]     (select JabRef-2.6.jar)[/FONT][/COLOR]
[COLOR=#000000][FONT=Sans Serif]
[/FONT][/COLOR][COLOR=#000000][FONT=Sans Serif]to[/FONT][/COLOR]

    [COLOR=#000000][FONT=Sans Serif]     /home/virgil/Downloads[/FONT][/COLOR]
 
 [COLOR=#000000][FONT=Sans Serif]2) Unpack it: [/FONT][/COLOR]
 
 ```
 $ java -jar /home/virgil/Downloads/JabRef-2.6.jar
``` [COLOR=#000000][FONT=Sans Serif]  [Note: a directory JabRef-2.6 will be created which will contain[/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans Serif]  the extracted contents of the jar file][/FONT][/COLOR]

 [COLOR=#000000][FONT=Sans Serif]3) Set permissions: [/FONT][/COLOR]
 
 ```
$ sudo chmod 511 /home/virgil/Downloads/JabRef-2.6.jar
``` [COLOR=#000000][FONT=Sans Serif]4) Copy JabRef-2.6.jar to desktop[/FONT][/COLOR]

 [COLOR=#000000][FONT=Sans Serif]5) Move JabRef-2.6.jar from desktop to right panel[/FONT][/COLOR]

 [COLOR=#000000][FONT=Sans Serif]6) In Properties (right-mouse click on icon in right panel) change to[/FONT][/COLOR][COLOR=#000000][FONT=Sans Serif]
  
  java -jar /home/virgil/Downloads/JabRef-2.6.jar[/FONT][/COLOR]
 
 [COLOR=#000000][FONT=Sans Serif]7) In Properites (left-mouse click on icon) change icon. Navigate[/FONT][/COLOR][COLOR=#000000][FONT=Sans Serif] to [/FONT][/COLOR][COLOR=#000000][FONT=Sans Serif]

  /home/virgil/Downloads/JabRef-2.6/images[/FONT][/COLOR][COLOR=#000000][FONT=Sans Serif]

and click on[/FONT][/COLOR][COLOR=#000000][FONT=Sans Serif]

  JabRef-icon.svg[/FONT][/COLOR][COLOR=#000000][FONT=Sans Serif]

In Properties enter in Name field: JabRef 2.6[/FONT][/COLOR]

And "Th-the-tha-that's all folks!"
--V :)

---

### Post by kaktux on 2010-07-31
i´ve used the .deb from launchpad

[https://launchpad.net/ubuntu/maverick/i386/jabref/2.6+ds-3](https://launchpad.net/ubuntu/maverick/i386/jabref/2.6+ds-3)

---

### Post by Arimethys on 2012-05-16
download newest package
[http://sourceforge.net/projects/jabref/files/jabref/]("http://sourceforge.net/projects/jabref/files/jabref/")

copy to /usr/share/jabref/
make link and rename as jabref.jar and copy to /usr/share/java/

It worked for Mint, 
run jabref --vesrion to check the folder of jabref

---

