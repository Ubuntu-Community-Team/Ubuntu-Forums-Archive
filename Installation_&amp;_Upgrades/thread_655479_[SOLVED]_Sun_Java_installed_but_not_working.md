---
title: "[SOLVED] Sun Java installed but not working"
date: 2008-01-01
forum: Installation &amp; Upgrades
---

### Post by eamann on 2008-01-01
Hello and a very happy New Year to you all!

Since I upgraded to 7.10 I cannot get Sun-Java to work with Firefox. This prevents me from using my bank's website, thus forcing me much to my annoyance to resort to MS Windows...

I have Sun-Java jre, bin, plugin and fonts installed, but when I go to abou: :plugins, there is no mention of Sun-Java.

I have read a lot of other posts about GCJ and Java but have not found an answer to my problem. Sometimes the solutions put forward - especially creating symbolic links - are too technical for me to follow them properly.

I have uninstalled the GCJplugin, in case that was conflicting with the Sun-java plugin.

Thank you for taking time to help me!

---

### Post by oldsoundguy on 2008-01-01
your answer is on this link:
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)
You should book mark that link and keep it at hand .. VERY handy as all you have to do to install from it is to open a terminal and cut and paste!

---

### Post by OBXSoulSurfer on 2008-01-01
I went round and round with this one for a couple of days .. maybe it shouldn't have been all that hard, but I am new to Ubuntu so that might explain it .. here is my backstory and how I solved my problem.

Opened up Firefox on a new Ubuntu 7.10 install and visited a page that required Java where I was asked to install the missing plugin .. I was offered four choices, being lazy I choose the first one rather than doing some research .. big mistake .. it installed the GCJ Java Plugin, which worked for some sites, but not all, and a visit to [www.java.com](www.java.com) to verify my installation would result in a notice that I was running 1.4.2 and needed to upgrade, I would hen install the newest java (plugins, fonts. etc) but a return to verify installation would yield the same result.  I then uninstalled the GCJ Plugin with "sudo apt-get remove gcjwebplugin".  Now when I visited a site requiring java I was prompted a new to select one of the four plugin choices, this time I selected JRE 6, but then it said it was already installed, but no change in behavior, so I was in a loop.

THE SOLUTION: for me was to (1) run "sudo update-alternatives --config java" and select the choice that lists Java 6, then (2) remove a broken link to the GJC Plugin with "rm /usr/lib/firefox/plugins/libjavaplugin.so" and then (3) to create a new link with "ln -s /usr/lib/jvm/java-6-sun-1.6.0.03/jre/plugin/i386/ns7/libjavaplugin_oji.so libjavaplugin_oji.so" .. note that your file path may vary depending where you installed firefox and java

hope this provides some help to at least one person

---

### Post by eamann on 2008-01-02
Thanks very much for both your suggestions!

I followed your instructions, OBXSoulsurfer, and I think that they were accepted, but Java still refuses to work and there is no mention of Java in "about:plugins". Any further ideas?

 Here's a copy of my Terminal; I would appreciate it very much if you would kindly check that the instructions were properly entered and implemented.

eamann@Dell:~$ sudo update-alternatives --config java
[sudo] password for eamann:

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*+        1    /usr/lib/jvm/java-6-sun/jre/bin/java
          2    /usr/bin/gij-4.2
          3    /usr/bin/gij-4.1

Press enter to keep the default[*], or type selection number: 1
Using `/usr/lib/jvm/java-6-sun/jre/bin/java' to provide `java'.
eamann@Dell:~$ 
eamann@Dell:~$ sudo su
root@Dell:/home/eamann# rm /usr/lib/firefox/plugins/libjavaplugin.so
root@Dell:/home/eamann# ln -s /usr/lib/jvm/java-6-sun-1.6.0.03/jre/plugin/i386/ns7/libjavaplugin_oji.so libjavaplugin_oji.so
ln: creating symbolic link `libjavaplugin_oji.so' to `/usr/lib/jvm/java-6-sun-1.6.0.03/jre/plugin/i386/ns7/libjavaplugin_oji.so': File exists
root@Dell:/home/eamann#

---

### Post by apmjoshi on 2008-01-02
I too am stuck at the same point for the last few days. From what I can tell, the symbolic link belongs to 'root' so even though the sudo command seems to work, it is not effective. I guess logging in as root would be the solution, but how does one do that in Ubuntu?

If you find a solution, please let me know.

Regards

---

### Post by OBXSoulSurfer on 2008-01-04
you could be correct in that you have to be logged in as root to make this work properly .. as I mentioned, I'm new to Ubuntu, so I'm not sure what the downside to this habit is, but whenever I log into terminal to do something the first thing I do is 'sudo -s' which logs you in as root and leaves it that way until you type 'exit' .. your terminal log is correct per my instructions ..  maybe being in as root will make the differnece or maybe your problem is different than mine was .. here's to hoping that it is the former.

---

### Post by GTO123 on 2008-01-15
> **OBXSoulSurfer said:**
> 
THE SOLUTION: for me was to (1) run "sudo update-alternatives --config java" and select the choice that lists Java 6

Posting to say that this worked for me when the default java (gij) had somehow become the preferred choice for the 'java' commmand

---

### Post by eamann on 2008-01-15
Sorry to say that trying this solution as root did not make any difference in my case...

This afternoon I thought I had found a solution. I was creating a database in OpenOffice and a window opened informing me that I needed to install a JRE. A further box gave me a choice between Java Sun 6 and another programme whose name began with Black... - something I installed some time ago as I try various solutions to this problem. I chose Java Sun and OpenOffice went ahead and created the database. Great, I thought to myself: perhaps for some unknown reason Java Sun was only partially installed and now it is properly installed. Sadly that did not prove to be true -  when I try to log on to a site that requires JRE, I still get the window announcing that I need to install JRE and when I click to install JRE the computer tells me that it is already installed...

When I go to Firefox About:plugins, there is no mention of Java, even though in the Preferences / Content window I have "Jave enabled". Perhaps in my case it is just the Firefox plugin that is missing, rather than the JRE in its entirity. What do the experts think about that? And if it is the case, how do I go about installing the plugin?

Thanks in advance for any further suggestions!

---

### Post by ljd65536 on 2008-01-15
I am also struggling to get java plugin to work with firefox in 7.10. So far, I have found that putting a link in /usr/lib/mozilla/plugins seems to have no effect. But I do see the Jav plugin in about:plugins if I put the symbolic link in /usr/lib/firefox/plugins. I installed Java from sun  by converting the Java rpm with alien.

 But when I go to the sun sight to test the plugin, it fails. If I learn anything more, I will let you know

---

### Post by flaggh on 2008-01-15
Have you guys tried to install the sun-java6-plugin?  It worked for me:

```

sudo apt-get install sun-java6-plugin
```

---

### Post by ljd65536 on 2008-01-15
I finally got it to work. I was unsuccesful inserting the links manually after installing java from sun. I searched the forums and found the instructions to install the plugin with apt-get. You have to apt-get at least two different packages that set the links automatically. 

First, you have to go to system->software sources and check the multiverse box. Without this, it cannot find the package. Then type:

sudo apt-get install sun-java6-jre

sudo apt-get install sun-java6-plugin

After installation, the symbolic links look like this:

/usr/lib/mozilla/plugins/ has these links
lrwxrwxrwx 1 root root 39 2008-01-15 20:19 libjavaplugin.so -> 

/usr/lib/firefox/plugins also has this link. Based on my previous messing around, I believe this is the one that matters rather than the mozilla link.
llrwxrwxrwx 1 root root      39 2008-01-15 20:19 libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so

/etc/alternatives then has all these links:
/etc/alternatives/mozilla-javaplugin.so
lrwxrwxrwx 1 root root 64 2008-01-15 20:19 /etc/alternatives/firefox-javaplugin.so -> /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so
lrwxrwxrwx 1 root root 64 2008-01-15 20:19 /etc/alternatives/iceape-javaplugin.so -> /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so
lrwxrwxrwx 1 root root 64 2008-01-15 20:19 /etc/alternatives/iceweasel-javaplugin.so -> /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so
lrwxrwxrwx 1 root root 30 2008-01-15 18:05 /etc/alternatives/java -> /usr/java/jre1.6.0_03/bin/java
lrwxrwxrwx 1 root root 32 2008-01-15 18:01 /etc/alternatives/java.1.gz -> /usr/share/man/man1/gij-4.2.1.gz
lrwxrwxrwx 1 root root 39 2008-01-15 20:16 /etc/alternatives/java_vm -> /usr/lib/jvm/java-6-sun/jre/bin/java_vm
lrwxrwxrwx 1 root root 38 2008-01-15 20:16 /etc/alternatives/javaws -> /usr/lib/jvm/java-6-sun/jre/bin/javaws
lrwxrwxrwx 1 root root 48 2008-01-15 20:16 /etc/alternatives/javaws.1.gz -> /usr/lib/jvm/java-6-sun/jre/man/man1/javaws.1.gz
lrwxrwxrwx 1 root root 64 2008-01-15 20:19 /etc/alternatives/midbrowser-javaplugin.so -> /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so
lrwxrwxrwx 1 root root 64 2008-01-15 20:19 /etc/alternatives/mozilla-javaplugin.so -> /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so
lrwxrwxrwx 1 root root 64 2008-01-15 20:19 /etc/alternatives/xulrunner-javaplugin.so -> /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so

I don't understand why manually installing the links didn't work. In other versions of Linux, just the one link suffices. But apparently at least some of the other links here must be important.

---

### Post by eamann on 2008-01-16
A breakthrough for me at last!!!

(Thank you Flaggh for your suggestion but unfortunately it did not help me.)

Following ljd's example I did the apt-get part but the JRE and the plugin were already installed.

I then checked my files and discovered that there were no Java links in either usr/lib/mozilla/plugins or usr/lib/firefox/plugins. There was however a link in usr/lib/mozilla but it reads libjavaplugin_oji.so 

Can someone tell me why the apt-get did not install the links as it seems to have done for ljd? 

How do I install the links?

What do I do with ibjavaplugin_oji.so ? Move it into the plugins directory?

When I go to etc/alternatives, I find a whole batch of links to Java. Can someone please tell me whether they are OK or not? Perhaps there are too many and they contradict each other (Java, Icedtea, GCJ...)? 

When I browse the file with Nautilus I see that the firefox link is broken:
/etc/alternatives/firefox-javaplugin.so 35 bytes (link broken) Is that perhaps the origin of my problems. If so, how do I repair the link?

Here are the Java-related links in etc/alternatives:

                                                           firefox-javaplugin.so -> /usr/lib/gcj-4.2/libgcjwebplugin.so

lrwxrwxrwx   1 root root    35 2007-12-21 23:00 iceape-javaplugin.so -> /usr/lib/gcj-4.2/libgcjwebplugin.so

lrwxrwxrwx   1 root root    35 2007-12-21 23:00 iceweasel-javaplugin.so -> /usr/lib/gcj-4.2/libgcjwebplugin.so

lrwxrwxrwx   1 root root    36 2008-01-02 10:08 java -> /usr/lib/jvm/java-6-sun/jre/bin/java

lrwxrwxrwx   1 root root    46 2008-01-02 10:08 java.1.gz -> /usr/lib/jvm/java-6-sun/jre/man/man1/java.1.gz

lrwxrwxrwx   1 root root    24 2007-12-22 22:40 javac -> /usr/bin/gcj-wrapper-4.2

lrwxrwxrwx   1 root root    40 2007-12-22 22:40 javac.1.gz -> /usr/share/man/man1/gcj-wrapper-4.2.1.gz

lrwxrwxrwx   1 root root    19 2007-12-22 22:40 javah -> /usr/bin/gjavah-4.2

lrwxrwxrwx   1 root root    35 2007-12-22 22:40 javah.1.gz -> /usr/share/man/man1/gjavah-4.2.1.gz

lrwxrwxrwx   1 root root    39 2007-12-22 22:48 java_vm -> /usr/lib/jvm/java-6-sun/jre/bin/java_vm

lrwxrwxrwx   1 root root    28 2008-01-10 17:50 javaws -> /usr/lib/j2se/1.4/bin/javaws

lrwxrwxrwx   1 root root    38 2008-01-10 17:50 javaws.1.gz -> /usr/share/man/man1/javaws.j2se14.1.gz

lrwxrwxrwx   1 root root    41 2008-01-10 17:50 javaws.ja.1.gz -> /usr/share/man/ja/man1/javaws.j2se14.1.gz

lrwxrwxrwx   1 root root    40 2007-12-22 22:48 jcontrol -> /usr/lib/jvm/java-6-sun/jre/bin/jcontrol

lrwxrwxrwx   1 root root    43 2007-12-28 21:39 keytool -> /usr/lib/jvm/java-7-icedtea/jre/bin/keytool

lrwxrwxrwx   1 root root    62 2008-01-10 17:50 libjavaplugin_oji_mozilla_firefox.so -> /usr/lib/j2se/1.4/jre/plugin/i386/mozilla/libjavaplugin_oji.so

lrwxrwxrwx   1 root root    62 2008-01-10 17:50 libjavaplugin_oji_mozilla_snapshot.so -> /usr/lib/j2se/1.4/jre/plugin/i386/mozilla/libjavaplugin_oji.so

lrwxrwxrwx   1 root root    62 2008-01-10 17:50 libjavaplugin_oji.so -> /usr/lib/j2se/1.4/jre/plugin/i386/mozilla/libjavaplugin_oji.so

lrwxrwxrwx   1 root root    35 2007-12-21 23:00 midbrowser-javaplugin.so -> /usr/lib/gcj-4.2/libgcjwebplugin.so

lrwxrwxrwx   1 root root    35 2007-12-21 23:00 mozilla-javaplugin.so -> /usr/lib/gcj-4.2/libgcjwebplugin.so

lrwxrwxrwx   1 root root    40 2007-12-28 21:39 orbd -> /usr/lib/jvm/java-7-icedtea/jre/bin/orbd

lrwxrwxrwx   1 root root    43 2007-12-28 21:39 pack200 -> /usr/lib/jvm/java-7-icedtea/jre/bin/pack200

lrwxrwxrwx   1 root root    54 2007-12-28 21:39 pluginappletviewer -> /usr/lib/jvm/java-7-icedtea/jre/bin/pluginappletviewer

lrwxrwxrwx   1 root root    46 2007-12-28 21:39 policytool -> /usr/lib/jvm/java-7-icedtea/jre/bin/policytool

Looking forward to a reply which will help me solve this problem at last!

Eamann

---

### Post by eamann on 2008-01-22
See the following post to learn how I solved my problem:

[http://ubuntuforums.org/showthread.php?t=673335](http://ubuntuforums.org/showthread.php?t=673335)

---

