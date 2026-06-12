---
title: "Apache 2 with Tomcat 5 application server"
date: 2005-06-23
forum: Installation &amp; Upgrades
---

### Post by Huggster on 2005-06-23
Hi all,   I need help.  

As a new linux user (a month now - Why I never made the switch before now I would never know).

I have taken the brave step of setting up Ubuntu command line and so far so good.  However, I am now confused about which advice to follow on setting up Java and Tomcat 5 to work with Apache so that I can have a fully working web server on my network.  I will be working with Struts and web services once I can get it working. Can anyone she any light on the exact process I need to follow.  I should also mention that this is a brilliant piece of software and a great forum.  _ have learned lots so far.

Thanks in advanced.

Huggster
Web Developer

---

### Post by DJ_Max on 2005-06-23
I haven't set up Apache with Tomcat, yet. But it's fairly documented. You first need to install Apache & Tomcate, by default they will run unconnected and on different ports. You will then need to install a connecter, preferably mod_jk.
[http://jakarta.apache.org/tomcat/connectors-doc/index.html](http://jakarta.apache.org/tomcat/connectors-doc/index.html)

There may be binaries for Apache2 & Tomcat5, but I don't like using third-party binaries, especially for such complex software.

---

### Post by Huggster on 2005-06-23
DJ_Max,

Thanks for your advice, however do you know of a detailed installation guide from java all the way through to Tomcat and the connector.  

Is anyone out there able to provide me with this information.  It would be greatly appreciated.

Thanks

Huggster

---

### Post by noodle on 2005-06-24
I have installed apache2 with php. I have also installed tomcat as a standalone on port 8080. 

If I use this connector, will this mean that apache (on 80) will be able to forward jsp file requests to tomcat? 

Does anyone know how to configure the connector to do this?

---

### Post by noodle on 2005-06-24
I wrote a HOWTO on installing Tomcat 5.5. Its published [here](http://www.ubuntuforums.org/showthread.php?p=226828#post226828)

Still don't know how to configure the connector. If anyone knows, a little help please?

---

### Post by DJ_Max on 2005-06-24
[QUOTE=noodle]I have installed apache2 with php. I have also installed tomcat as a standalone on port 8080. 

If I use this connector, will this mean that apache (on 80) will be able to forward jsp file requests to tomcat? 

Does anyone know how to configure the connector to do this?[/QUOTE]
 Thats exactly what it means They will work together. It's all right here. [http://jakarta.apache.org/tomcat/connectors-doc/install/apache2.html](http://jakarta.apache.org/tomcat/connectors-doc/install/apache2.html)

You need to download and compile mod_jk, then you. Look at *Getting mod_jk linked statically with Apache*

Then move along to [http://jakarta.apache.org/tomcat/connectors-doc/config/apache.html](http://jakarta.apache.org/tomcat/connectors-doc/config/apache.html)

Also, look at [http://jakarta.apache.org/tomcat/connectors-doc/howto/apache.html](http://jakarta.apache.org/tomcat/connectors-doc/howto/apache.html) go to the *Simple configuration example*

---

### Post by noodle on 2005-06-25
[QUOTE=DJ_Max]Thats exactly what it means They will work together. It's all right here. [http://jakarta.apache.org/tomcat/connectors-doc/install/apache2.html](http://jakarta.apache.org/tomcat/connectors-doc/install/apache2.html)

You need to download and compile mod_jk, then you. Look at *Getting mod_jk linked statically with Apache*

Then move along to [http://jakarta.apache.org/tomcat/connectors-doc/config/apache.html](http://jakarta.apache.org/tomcat/connectors-doc/config/apache.html)

Also, look at [http://jakarta.apache.org/tomcat/connectors-doc/howto/apache.html](http://jakarta.apache.org/tomcat/connectors-doc/howto/apache.html) go to the *Simple configuration example*[/QUOTE]

I hate to sound like a useless complainer, but I still can't get it to work  ](*,) .

I followed the instructions from jakarta.apache (had to make some adjustments cos i was using jk2_mod) but no luck  :?. Instead of getting apache to handle jsp, i disabled php...don't know how.

Anyway, I guess I will have to wait till someone publishes a detailed HOWTO or a guide for idiots wanting to use the jk2_mod connector. 

Thanks for your help anyway.

---

### Post by Huggster on 2005-06-25
Guys,

Well, I am going to have a go tonight.  I have managed to get apache2, j2sdk and tomcat installed.  Now I will try the mod_jk.  Wish me luck.  I will report back soon.

Huggster

---

