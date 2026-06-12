---
title: "Java Firefox plugin"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by rveska on 2008-06-08
Hi.
I upgraded to Ubuntu 8.04 from 7.10, and suddenly Java stopped working in Firefox (I don't know if anything els uses Java). Instead of starting the applet, a Grey box appears and the browser says:

starting applet...
Applet loaded.
Start: applet not initialized

Does anyone know why this has happened? I didn't problems with Java on 7.10.
Everything els is working amazingly well. I have tried to reinstall all the Java-components I could find in the package manager.

   BG
    Rasmus

---

### Post by CameO73 on 2008-06-08
Hmmm... I had a similar problem. But only with signed applets (which I use a lot for my work). It seems OpenJDK (the open source version of Java that is included in Ubuntu 8.04) has currently no support for signed applets.

My solution (for this case) was to remove all OpenJDK packages (search for **icedtea** in Synaptic) and install the Sun version. Search for **sun-java** in Synaptic; you must have enabled the Multiverse for this to work: Settings -> Repositories -> check 'Software restricted by copyright or legal issues (multiverse)'. You only need the **sun-java5-jre** or **sun-java6-jre** and the **sun-java5-plugin / sun-java6-plugin**. Go for version 6 if you have no special reason to use 5.

---

### Post by jashin on 2008-06-08
> **Skannrup said:**
> Hi.
I upgraded to Ubuntu 8.04 from 7.10, and suddenly Java stopped working in Firefox (I don't know if anything els uses Java). Instead of starting the applet, a Grey box appears and the browser says:

starting applet...
Applet loaded.
Start: applet not initialized

Does anyone know why this has happened? I didn't problems with Java on 7.10.
Everything els is working amazingly well. I have tried to reinstall all the Java-components I could find in the package manager.

   BG
    Rasmus

Installing firefox java plugin via apt-get etc. didn't solved this problem on my computer. But this finally helped me:
1. [FONT="Courier New"]locate ns7/libjavaplugin_oji.so[/FONT] (you will get the path of libjavaplugin_oji.so - if you have java installed) 
2. [FONT="Courier New"]locate -r /firefox/plugins$[/FONT] (to get the full path of firefox plugins directory)
3. create symlink of libjavaplugin_oji.so in firefox/plugins directory (in my case [FONT="Courier New"]sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins/[/FONT]
4. restart firefox

---

### Post by CameO73 on 2008-06-09
Hmmm... the solution **jashin** suggests is usually only required if you manually install a Sun Java version (e.g. from [www.java.com]("http://www.java.com")). But if all else fails...

Btw, you can see what plugin you use for Java in Firefox:

[LIST]
[*]type **about:plugins** in the Firefox address bar
[*]look for the Java plugin (somewhere at the bottom)
[*]if all is well, you see something like **filename: **  **libjavaplugin_oji.so, Java(TM) Plug-in 1.6.0_06**
[/LIST]

---

### Post by RikardSvenningsen on 2008-06-15
I upgraded from Ubuntu 7.10 to 8.04 on serval pc's without any problems but i got to pc's in particular one xubuntu upgraded from 6.06 to 8.04 all working whit my bank (SUN java) including 8.04, but on my ubuntu 6.06 upgraded to ubuntu 7.10 no problem whit my bank then upgraded to 8.04 now I got problem whit my bank I get this

You didn't accept the certificate from the bank
Restart your browser and accept the certificate
whit grant or grant always.

But I don't get this question at all..!
Now I checked my Java on [www.java.com](www.java.com) to check my Java version. I don't get an error but I don't get the figure as I should I only get at grey box.

I tried Jashin's post but it didn't work for me.
/usr/lib/jvm/java-6-sun-1.6.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so
/usr/lib/firefox/plugins

as sudo su i did this:
ln -s /usr/lib/jvm/java-6-sun-1.6.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins/

Do anyone know what's the wrong?

---

### Post by rveska on 2008-06-19
> **CameO73 said:**
> Hmmm... the solution **jashin** suggests is usually only required if you manually install a Sun Java version (e.g. from [www.java.com]("http://www.java.com")). But if all else fails...

Btw, you can see what plugin you use for Java in Firefox:

[LIST]
[*]type **about: plugins** in the Firefox address bar
[*]look for the Java plugin (somewhere at the bottom)
[*]if all is well, you see something like **filename: **  **libjavaplugin_oji.so, Java(TM) Plug-in 1.6.0_06**
[/LIST]

Hi again.
I've tried both methods now, and I do get the right information from the **about: plugins**, but the applets still wan't work proberly...
Now it is something about security class not found...

Guess it is the same thing as Rikard reports

---

### Post by rveska on 2008-06-19
I've just tried java.com to see if they had any points, and it turned out, that my java worked there as it should, so I guess the problem is at the other end of the line.
Anyway thanks for the help.

   Rasmus

---

