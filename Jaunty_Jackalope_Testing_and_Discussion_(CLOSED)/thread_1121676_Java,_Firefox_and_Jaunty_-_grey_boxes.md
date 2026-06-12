---
title: "Java, Firefox and Jaunty - grey boxes?"
date: 2009-04-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by cfogelberg on 2009-04-10
Hello all,

I'm trying to get java to work in Firefox on the 64bit Jaunty beta that I have installed on my Dell XPS M1330 laptop.

The problem is that whever I try to use a web page with a java plug in (e.g. facebook add photos) I get a grey box where the java plug in should be.

I have installed sun-java6-plugin and sun-java6-jre and all of their dependencies. When I run java -version I get:

> java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.4.1) (6b14-1.4.1-0ubuntu4)
OpenJDK 64-Bit Server VM (build 14.0-b08, mixed mode)

And about:plugins tells me:
>     File name: IcedTeaPlugin.so
    The IcedTea Java Web Browser Plugin 1.4.1 (6b14-1.4.1-0ubuntu4) executes Java applets.
And it is enabled for all MIME types.

Any suggestions or tests I could do much appreciated! :)
Christo

---

### Post by cl333r on 2009-04-10
OpenJDK is glitchy (also its plugin), remove it (and the plugin), then:
```

sudo aptitude install sun-java6-jre sun-java6-plugin

```
It will install both Sun's Java runtime and its plugin.

---

### Post by cfogelberg on 2009-04-10
OK, so I ran sudo apt-get remove -purge sun-java6-* and that uninstalled the bin, jre and plugin.

I then ran "sudo aptitude install sun-java6-jre sun-java6-plugin", but when I run "java -version" I get the same output:

> java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.4.1) (6b14-1.4.1-0ubuntu4)
OpenJDK 64-Bit Server VM (build 14.0-b08, mixed mode) 

And unfortunately I still can't get the FB photo java app working either - it's the same grey square. So two questions now, plus the original problem:

1) Why does "sudo apt-get install sun-java6-jre" and the equivalent aptitude command both install the open JDK??

2) What is the difference between "sudo apt-get install ..." and "sudo aptitude install ..."?

Thanks,
Christo

---

### Post by cl333r on 2009-04-10
You had to remove the openjdk, not sun's jdk.
However since you got them both installed you can just configure Ubuntu to run by default Sun's JDK:
```

sudo update-alternatives --config java

```
and type the number under which sun's java will be highlighted.


Like this:
> 
fox@fox-desktop:~$ sudo update-alternatives --config java
[sudo] password for fox: 

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
 +        1    /usr/lib/jvm/java-6-openjdk/jre/bin/java
*         2    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 2
Using '/usr/lib/jvm/java-6-sun/jre/bin/java' to provide 'java'.
fox@fox-desktop:~$ 



---

### Post by cl333r on 2009-04-10
2) apt-get is deprecated but is still widely used cause it works well and ppl are used to it.
aptitude - is the newer way to do the stuff that apg-get is doing.
apt-get has actually been deprecated quite a bunch of years ago.

However, don't mix them both, either stick with apt-get or with aptitude.

```

1) Why does "sudo apt-get install sun-java6-jre" and the equivalent aptitude command both install the open JDK??

```
It doesn't. It installed sun's jre, but since you already have the open jre installed Ubuntu picked it to be used by default hence you can't use sun's jre until you configure it to be the default Java which is to be done by issuing the update-alternatives command.

---

### Post by cfogelberg on 2009-04-10
Great, thank you for clarifying all of that for me. I haven't restarted firefox but I think it will work because when I run java -version I get HotSpot now, not Iced Tea.

Is aptitude related to the Applications|"Add/Remove" and System|Administration|"Synaptic Package Manager" - i.e. does clicking one or both of these run aptitude?

Thanks,
Christo

---

### Post by cl333r on 2009-04-10
I don't know but googling might help, like this:
[http://en.wikipedia.org/wiki/Aptitude_(program)](http://en.wikipedia.org/wiki/Aptitude_(program))

---

### Post by cfogelberg on 2009-04-10
OK, follow up. I did the update-alternatives as you suggested, and that changed what java -version would print, but Firefox about:plugins still showed IcedTea and the FB photo adding app was still a grey box.

The question is: how do I change which plugin Firefox uses, i.e. why isn't update-alternatives working completely, and what do the + and * in its output mean?

The facts are:
Now when I run update-alternatives a couple of times I get this kind of output:

> [1940][christo@christo-lt2 ~]
$ sudo update-alternatives --config java
[sudo] password for christo: 

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
 +        1    /usr/lib/jvm/java-6-openjdk/jre/bin/java
*         2    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 2
Using '/usr/lib/jvm/java-6-sun/jre/bin/java' to provide 'java'.

[1940][christo@christo-lt2 ~]
$ sudo update-alternatives --config java
[sudo] password for christo: 

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
 +        1    /usr/lib/jvm/java-6-openjdk/jre/bin/java
*         2    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 2
Using '/usr/lib/jvm/java-6-sun/jre/bin/java' to provide 'java'.

[1940][christo@christo-lt2 ~]
$

This bug appears to be related: [https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/344705]("https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/344705")

Incidentally, I think that if I run update-alternatives while FF is running then according to top, java flatlines the CPU(s) at 100% until I log out and log back in. This could be related to the 100% CPU utilisation talked about in the bug report I link to above.

Thanks again for your help with this :)
Christo

---

### Post by taavikko on 2009-04-10
You can use "update-java-alternatives" see: "man update-java-alternatives"
To set the browser plugin to use.

---

### Post by Zorael on 2009-04-10
See [https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/344705](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/344705).

---

### Post by cfogelberg on 2009-04-10
> **taavikko said:**
> You can use "update-java-alternatives" see: "man update-java-alternatives"
To set the browser plugin to use.

Thanks, "sudo update-java-alternatives -s java-6-sun" seems to have fixed it :)

EDIT: Any idea how to change the subject of the thread so that it's prepended with [SOLVED]?

---

### Post by dro0g on 2009-04-13
I had a slightly different problem resulting in the same symptoms. 

Java was hanging firefox with a gray box. Only the Sun JRE was installed and I confirmed in about:plugins the Sun plugin was being used. However, it seems that there's a newer plugin which works better in some circumstances. 

The actual problem may be related to the Intel xorg driver in combination with Java, I'm not really sure.

The fix I found was to delete anything java related from the following directories:

/usr/lib/xulrunner-addons/plugins/
/usr/lib/mozilla/plugins/
/usr/lib/firefox/plugins/

I then created a symlink to the newer Java plugin:
cd $HOME/.mozilla/plugins 
ln -s /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so libnpjp2.so

I manage a few Cisco ASA firewalls and their GUI (ASDM) uses Java and was hanging, after the fix above it's now working.

Here are some links where I found the info above:
[https://bugs.launchpad.net/sun-java/+bug/288397](https://bugs.launchpad.net/sun-java/+bug/288397)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/238629](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/238629)

---

