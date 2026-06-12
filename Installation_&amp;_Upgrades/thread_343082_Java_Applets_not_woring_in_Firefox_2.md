---
title: "Java Applets not woring in Firefox 2"
date: 2007-01-20
forum: Installation &amp; Upgrades
---

### Post by tknee on 2007-01-20
Hi

I have installed  and reinstalled most everything I can find on Java yet Firefox 2 does not display some appplets on web pages. Java is enabled in the preferences of Firefox. and i have rebooted.

Anyone have any ideas?

---

### Post by taurus on 2007-01-20
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
java -version
```

---

### Post by ssavelan on 2007-01-21
As I am having the same problem as the user above... I will pick up as if I am him.

biouser@reishi-tsunami:~/Desktop$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-14ubuntu7)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.


Thanks for asking :grin:

---

### Post by taurus on 2007-01-21
That's a wrong version.  You need to install the java version either from Blackdown or Sun.

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by tknee on 2007-01-21
Hi

My output from the java -version command is:

java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)

I guess that means I need to install Sun as well?

Thanks

---

### Post by tknee on 2007-01-21
Hi

In addition to the above I visited the following site from Sun to test the Java installation:

[http://www.java.com/en/download/installed.jsp?jre_version=1.5.0_06&vendor=Sun+Microsystems+Inc.&os=Linux&os_version=2.6.15-27-386](http://www.java.com/en/download/installed.jsp?jre_version=1.5.0_06&vendor=Sun+Microsystems+Inc.&os=Linux&os_version=2.6.15-27-386)

It says I do not have the latest version installed (see following message):

[I]You do NOT have the latest version of Java software.
The latest version of Java software = Java Runtime Environment Version 5.0 Update 10[/I]

I downloaded and installed the latest version from the Sun site but still have the same problem. Any ideas anyone?

---

### Post by taurus on 2007-01-21
Fire up firefox.  In Edit -> New Tab, type

```
about:plugins
```
Do you see java plugin on that list?

---

### Post by tknee on 2007-01-21
HI

The about:plugins results in the follwoing:

[I]Java(TM) Plug-in Blackdown-1.4.2-02

    File name: libjavaplugin_oji.so
    Blackdown Java-Linux Java(TM) Plug-in 1.4.2[/I]

With a list of all of the java stuff installed. It is not the same as the Sun Java 1.5.0 that i have been installing. Is it possible that I should uninstall the Blackdown version and re-install the latest Sun version?

---

### Post by tknee on 2007-01-22
HI

I uninstalled everything that was java and then reinstalled Sun Java from the Gnome APT interface.

My installed version is now:

java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)

In Firefox I checked the about:plugins but there is no mention of java. For some reason Firefox 2.0 is not recognizing java on my system. Java is enabled in the preferences.

Any ideas

---

### Post by tknee on 2007-01-22
Problem solved!

A weird way of doing things perhaps but it works. I was trying another approach after uninstalling everything and searched for Mozilla in my Places - Search menu. It displayed a deb file called j2re mozilla plugin blah blah. I decided to install it and it worked. Java applets now working in Firefox!

Not the most logical approach but not bad for a newbie LOL

---

### Post by taurus on 2007-01-22
You need to copy java plugins to either ~/.mozilla/plugins or /usr/lib/firefox/plugins (with the sudo command).

---

### Post by wxnker on 2007-01-23
[COLOR="Silver"]A weird way of doing things perhaps but it works. I was trying another approach after uninstalling everything and searched for Mozilla in my Places - Search menu. It displayed a deb file called j2re mozilla plugin blah blah. I decided to install it and it worked. Java applets now working in Firefox!

Not the most logical approach but not bad for a newbie LOL[/COLOR]

I am having the exact same problem but I cannot find the deb file mentioned.
What is the exact name?
I only have: java-common....
[U]
My output from java -version:[/U]
[COLOR="Red"]java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing)[/COLOR]

[COLOR="Silver"]You need to copy java plugins to either ~/.mozilla/plugins or /usr/lib/firefox/plugins (with the sudo command).[/COLOR]

Can you please describe a bit further as I'm a bit of a newbie (but very happy ubuntu user).

What is the fil name? What is the terminal line to make the copy?

---

### Post by wxnker on 2007-01-23
Sorry. I found a guide that told me to enable multiverse. Then I found the plugin and it works.

Problem solved. :biggrin:

---

### Post by venik212 on 2007-01-24
Could you please be a little more specific?  Please give the code you used to install the package, and its name.
Thanks

---

### Post by taurus on 2007-01-24
> **venik212 said:**
> Could you please be a little more specific?  Please give the code you used to install the package, and its name.
Thanks

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by venik212 on 2007-01-24
Specifically-- which of the numerous java packages is needed for Java to work with FireFox (or Opera, for that matter).

---

