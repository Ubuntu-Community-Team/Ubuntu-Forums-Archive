---
title: "Tomcat Install from repositories"
date: 2008-03-11
forum: Installation &amp; Upgrades
---

### Post by Mr.Macdonald on 2008-03-11
I currently have Apache 2 installed and UNDER NO CIRCUMSTANCES WILL I UNINSTALL IT because i just fought my Network to make it work (A bloody battle).

I desire
[LIST]
[*]To have the ability to run Java servlets from any folder on my site thus if a plugin exists that can do this without breaking Apache 2 then i might prefer that
[*]To install every thing from the repositories (everything needed) unless its not virtually possible
[/LIST]


I have read about connectors and see how they could work for me with Tomcat. But when i install Tomcat i get 2 directories of apparent installation. i don't know which to use, and when i edit the configuration on either it still doesn't work.

I have followed tutorials online but they use and unzip install and that won't work for me, because i wish to install via the repositories.

thanks for any and all help

---

### Post by Another Monkey on 2008-03-27
Not a lot of help I know, but from what I can tell the Tomcat install available via the repositories is borked and simply won't run (there appear to be a few bugs logged about this).  I may, of course, have misunderstood the situation.

The only way I managed to get Tomcat to "sort of" run was by using the tarball method, although I am still having fun in trying to figure out the "best" way to define the variables and to create a launcher; never mind run it on start-up.  *sigh*

---

### Post by Mr.Macdonald on 2008-03-27
Thanks but thats really bad news for me. I guess I will wait till its fixed in repositories but ooh well

If their is a way that i could help then please tell me. I can code in Java (mainly), BASH, and C

BUT i have never made a Debian package and i don't know what it is good for. Basically I am a clueless servant

---

### Post by Another Monkey on 2008-03-28
Cheers, I managed to get a Tomcat launcher to work by means of an intermediary script.  I'm none too clear on why things much be done this was, but it does work.

[FONT="Courier New"]#!/bin/bash
#Variables to let Tomcat launch
export CATALINA_HOME=/opt/apache-tomcat-5.5.26
export JAVA_HOME=/opt/jdk1.5.0_15

bash -i /opt/apache-tomcat-5.5.26/bin/startup.sh[/FONT]

As to the Repository install for Tomcat, I've not looked at it again since totally losing the rag over it a week or so ago!

---

### Post by Mr.Macdonald on 2008-03-29
Off topic but whats with the CATALINA_HOME to me thats an **island of the coast of Southern California**????

---

### Post by TomDaBomb2u on 2008-04-04
> **Mr.Macdonald said:**
> Off topic but whats with the CATALINA_HOME to me thats an **island of the coast of Southern California**????

CATALINA_HOME is the folder where tomcat is installed. i.e "**/home/thomas/apache-tomcat-6.0.16**" is mine. I'm a newbie to this too - just learned this in class the other day actually :-).

Hope this helps! 

-Thomas

---

