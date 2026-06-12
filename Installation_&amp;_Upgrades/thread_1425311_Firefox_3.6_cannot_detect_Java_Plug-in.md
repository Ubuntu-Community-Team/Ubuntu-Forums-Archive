---
title: "Firefox 3.6 cannot detect Java Plug-in"
date: 2010-03-08
forum: Installation &amp; Upgrades
---

### Post by CSHANKY on 2010-03-08
My Firefox 3.6 plugin check reveals "Unable to Detect Plugin Version" for Java. It detects Totem and Shockwave just fine.

Exact message:
[Java(TM)  Plug-in 1.6.0_15                                 Unable to Detect Plugin Version]("http://www.google.com/search?q=current%20version%20plugin%20Java%28TM%29%20Plug-in%201.6.0_15")

I am running Firefox Ver 3.6 on Ubuntu 9.10. As a result of this, I cannot use VPN to log into my co network which is bit of a handicap.

Hence, any help would be greatly appreciated. BTW I am an absolute non-techie but can follow directions.;)

---

### Post by nortexoid on 2010-03-09
I did a manual install of 3.6 on Kubuntu and I'm having the same issue. I follows some instructions for putting the plugin in the appropriate folder (which has changed from 3.5 to 3.6 apparently) but nothing worked. I'm using the latest dev. builds of Chromium and java works fine. Luckily I only need java once a week for one hour! It would be nice if anyone was able to get it working and could shed some light.

---

### Post by CSHANKY on 2010-03-09
Bump

---

### Post by wojox on 2010-03-09
This is a good thread for installing the latest Java for 32 or 64 bit: [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by drs305 on 2010-03-09
I just did a clean (re)install of 64-bit Lucid. I installed sun-java6-jre and sun-java6-plugin and didn't get java to work. I then added the  icedtea6-plugin and java started working.

Note: I am not running openjdk other than the icedtea6-plugin.

---

### Post by nortexoid on 2010-03-09
I followed the instructions (to a tee) at

[http://buck-nasty.blogspot.com/2010/02/installing-firefox-36-and-java-618.html](http://buck-nasty.blogspot.com/2010/02/installing-firefox-36-and-java-618.html)

and they worked perfectly. Java now works perfectly in Firefox 3.6.

---

### Post by CSHANKY on 2010-03-10
When I got to...

~$ deb [http://ppa.launchpad.net/voronov84/andreyv/ubuntu](http://ppa.launchpad.net/voronov84/andreyv/ubuntu) karmic main

No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)
deb: command not found

Any suggestions to resolve this?

---

### Post by wojox on 2010-03-10
You need to do this part for 9.10:

```

For Ubuntu 9.10 (Karmic), open a terminal and paste the following:

sudo add-apt-repository ppa:mozillateam/firefox-stable

sudo apt-get update

sudo apt-get install firefox-3.6

```

---

### Post by CSHANKY on 2010-03-10
> **wojox said:**
> You need to do this part for 9.10:

```

For Ubuntu 9.10 (Karmic), open a terminal and paste the following:

sudo add-apt-repository ppa:mozillateam/firefox-stable

sudo apt-get update

sudo apt-get install firefox-3.6

```

Been there...done that.

"firefox-3.6 is already the newest version."

When I do:

deb [http://ppa.launchpad.net/voronov84/andreyv/ubuntu](http://ppa.launchpad.net/voronov84/andreyv/ubuntu) karmic main

as instructed, I get:

No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)
deb: command not found

---

### Post by drs305 on 2010-03-10
> **CSHANKY said:**
> Been there...done that.

"firefox-3.6 is already the newest version."

When I do:

[COLOR="Red"]deb [http://ppa.launchpad.net/voronov84/andreyv/ubuntu](http://ppa.launchpad.net/voronov84/andreyv/ubuntu) karmic main[/COLOR]

as instructed, I get:

No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)
deb: command not found

This is not a command you enter in a terminal. It would be the entry in /etc/apt/sources.list to add that repository. If you try running it from the command line, it will think the command is "deb" and produce the error messages you are getting.

Here is the link the the Ubuntu community doc on repositories, if you are interested in learning about them:
[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by CSHANKY on 2010-03-10
> **drs305 said:**
> This is not a command you enter in a terminal. It would be the entry in /etc/apt/sources.list to add that repository. If you try running it from the command line, it will think the command is "deb" and produce the error messages you are getting.

Here is the link the the Ubuntu community doc on repositories, if you are interested in learning about them:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Ok - did that.

Next I did:

 - ~$ sudo ln -s /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so ~/.mozilla/plugins/

[COLOR=Red]ln: target `/home/cshanky/.mozilla/plugins/' is not a directory: No such file or directory
[/COLOR]
](*,)

---

### Post by drs305 on 2010-03-10
The plugins folder may not exist. You can create it with:
```
mkdir ~/.mozilla/plugins
```

If the .mozilla folder doesn't exist, you would have to make it first, but in that case you probably have other problems.  ;-)

---

### Post by CSHANKY on 2010-03-10
> **drs305 said:**
> The plugins folder may not exist. You can create it with:
```
mkdir ~/.mozilla/plugins
```If the .mozilla folder doesn't exist, you would have to make it first, but in that case you probably have other problems.  ;-)

Did that too....

Still same result. Unable to Detect Plugin Version ](*,) 

Here are the steps I followed:

1. Did:  
sudo add-apt-repository ppa:mozillateam/firefox-stable
sudo apt-get update
sudo apt-get install firefox-3.6 <or close the terminal, and run the update manager>

2. Added the JAVA PPA
deb [http://ppa.launchpad.net/voronov84/andreyv/ubuntu](http://ppa.launchpad.net/voronov84/andreyv/ubuntu) karmic main

3. Ran the command gksu nautilus to open a root file browser session. From there navigate to the following location:
/usr/lib/jvm/

4. Found the folder named java-6-sun/ and renamed it to java-6-sun.bak/ (/usr/lib/jvm/java-6-sun.bak)

Also, in the same /usr/lib/jvm/ folder, found a sub folder named java-6-sun618/ or something similar, and renamed it to java-6-sun/ (/usr/lib/jvm/java-6-sun/)

6. Did mkdir ~/.mozilla/plugins

5. From a terminal screen ran the following command:
sudo ln -s /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so ~/.mozilla/plugins/

Result - A BIG FAT ZERO.

Firefox "Unable to Detect Plugin Version"

---

### Post by almozavr on 2010-03-12
The **easiest way** worked for me:

[LIST=1]
[*]Add Java PPA [[COLOR=#000000]https://launchpad.net/~voronov84/+archive/andreyv[/COLOR]]("https://launchpad.net/%7Evoronov84/+archive/andreyv")
[*][COLOR=#000000]Update your packages through Update manager or somehow else[/COLOR]
[*][COLOR=#000000]sudo ln -s /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so /usr/lib/firefox-3.6/plugins[/COLOR][COLOR=#000000][/COLOR]
[/LIST]

---

### Post by redpawn on 2010-03-18
Almozavr, this is the ticket!  Much of the advice including the plugindoc on the about plugins page advise linking to the wrong plugin.  The libnpjp2.so works with firefox 3.6 while libjavaplugin_oji.so does not.  Thanks!

---

### Post by Primefalcon on 2010-03-19
> **almozavr said:**
> The **easiest way** worked for me:

[LIST=1]
[*]Add Java PPA [[COLOR=#000000]https://launchpad.net/~voronov84/+archive/andreyv[/COLOR]]("https://launchpad.net/%7Evoronov84/+archive/andreyv")
[*][COLOR=#000000]Update your packages through Update manager or somehow else[/COLOR]
[*][COLOR=#000000]sudo ln -s /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so /usr/lib/firefox-3.6/plugins[/COLOR][COLOR=#000000][/COLOR]
[/LIST]
That worked great for me too, thx

---

### Post by phreakphish on 2010-06-01
> **almozavr said:**
> The **easiest way** worked for me:

[LIST=1]
[*]Add Java PPA [[COLOR=#000000]https://launchpad.net/~voronov84/+archive/andreyv[/COLOR]]("https://launchpad.net/%7Evoronov84/+archive/andreyv")
[*][COLOR=#000000]Update your packages through Update manager or somehow else[/COLOR]
[*][COLOR=#000000]sudo ln -s /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so /usr/lib/firefox-3.6/plugins[/COLOR]
[/LIST]


Hi all,

 I added the source in Update Manager, don't know if I did it right, still a noob I guess, now I get an error every time I open update/synaptic/add/remove etc., 

"An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 55 in source list /etc/apt/sources.list (dist parse), E:The list of sources could not be read.'"

Any help appreciated. Thanks.

---

### Post by uOpt on 2010-06-01
Firefox 3.6 uses a new plugin API.

You need a recent Java 1.6 build and then use the appropriate different *.so file. It's in the Java FAQ something or other.

I wouldn't bother. I spent a lot of time making that run only to discover that I still went back to Firefox 3.59.

---

### Post by phreakphish on 2010-06-01
Ok, I fixed it, but still don't know where I went wrong, anyone? Thanks.

Jaunty 9.04

---

### Post by ClarkEveretts on 2010-06-01
almozavr's note regarding the correct .so file was the key for me.  I followed the instructions at [this java.com page]("http://www.java.com/en/download/help/testvm.xml"), which gave me java (I put it in /usr/local/jre1.6.0_20 - is there a "more proper" place?), but no working FF plugin.

Like redpawn, I found the plugindoc info not quite up to date.

I tried using the package manager, by the way, but found no sun-java packages in Universe.  I did see various open source JRE's, but I'd read I'd need Sun Java for Webex, which is the main reason I need a working plugin.

After reading almozavr's note, I saw that this was not the symlink to create:
sudo ln -s /usr/local/jre1.6.0_20/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla/plugins/libjavaplugin_oji.so

but rather this one:
sudo ln -s /usr/local/jre1.6.0_20/lib/i386/libnpjp2.so /usr/lib/mozilla/plugins/libnpjp2.so

Putting the symlink in plugins under /usr/lib/mozilla should make the plugin available to all FF users on the system.  [Here]("http://www.java.com/en/download/help/features_java6update10.xml") is some info on why we might be interested in using the new java plugin.  I like the fact that applets run in separate processes from the browser.

Without this forum, I don't know how long it would have taken me to get this working.
Thanks!

---

