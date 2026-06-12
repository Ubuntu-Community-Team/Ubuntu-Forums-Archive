---
title: "Installing Java Runtime Environment"
date: 2007-01-31
forum: Installation &amp; Upgrades
---

### Post by rwyankees on 2007-01-31
I have or what I thought installed "Java Runtime Environment" about 5 times now, all attempts have failed. I am using Ubuntu 6.10 (edgy) and Firefox 2.0.  When I go to sites it still says I am missing plugins when I click install missing plugins it says Java Runtime Environment.  I then cancel that knowing that you can't install it that way.  I have looked Up Mulitiple step by step instructions on how to install it and nothing works.  If anyone can help me please let me know.
](*,)  ](*,)  ](*,)

---

### Post by phossal on 2007-01-31
When a web page tells you that you don't have the JRE installed, it means that you haven't installed the plugin for the browser. That isn't quite the same as installing the JRE to run programs on your desktop. 

In the upper left corner of the forum webpage is a search box. Type in "Java Plugin" and you'll get a list of tutorials. 

Good luck.

---

### Post by meng on 2007-01-31
You have to install the packages:
sun-java5-jre
sun-java5-plugin

---

### Post by Sef on 2007-01-31
Easiest way to install Java is this:

Applications > Add/Remove > Search > Sun Java 5.0 > click ok > follow directions to install. (click ok a couple of more times.)

---

### Post by phossal on 2007-02-01
[COLOR="SlateGray"]**Installing JAVA doesn't install the plugin necessarily!**[/COLOR]

If you installed Java, which you claim to have done 5 times, there is a folder with the "java" command in it. It's the executable for the JRE. There are a lot of ways to find it, but I'll give you a simple one. In that folder, in another folder, in another folder, is the plugin.so that Firefox wants installed. Here is how you find out where it is:

```
sudo locate */plugin/i386/ns7/libjavaplugin_oji.so
``` 

That's going to give you an answer something like this:
```
[COLOR="DimGray"]bash 3.1:[/COLOR]sudo locate */plugin/i386/ns7/libjavaplugin_oji.so
*[COLOR="Blue"]/usr/lib/Java6/jre/plugin/i386/ns7/libjavaplugin_oji.so[/COLOR]*
```

Then, using that full path (which is the path to the plugin), you're going to make a symbolic link in the browser plugins folder. The firefox folder is typically in: /usr/lib/firefox

Install the link like so:
```
sudo ln -s /usr/lib/Java6/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins
```

Open up firefox: Toolbar -> edit ->preferences -> enable java
Restart firefox and enjoy your life. ;)

---

### Post by dcstar on 2007-02-01
> **rwyankees said:**
> I have or what I thought installed "Java Runtime Environment" about 5 times now, all attempts have failed. I am using Ubuntu 6.10 (edgy) and Firefox 2.0.  When I go to sites it still says I am missing plugins when I click install missing plugins it says Java Runtime Environment.  I then cancel that knowing that you can't install it that way.  I have looked Up Mulitiple step by step instructions on how to install it and nothing works.  If anyone can help me please let me know.
](*,)  ](*,)  ](*,)

There is an issue with the JRE install where it requires you to acknowledge the licence agreement, and some system are not configured correctly to show you the question (so you can actually answer it..........)

The install process carries on but doesn't actually install the package.

If this is what is happening to you, do a forum search because I recall some posts with detailed instructions on making a change to your install dialog settings to fix this issue.

---

### Post by rwyankees on 2007-02-01
OK I have done EVERYTHING stated above .. and I thank you for your input but it still isn't working.  When I go to a site like Yahoo! Games... it still says I dont have it I have got to edit>Prefrences> Content > Enable Java ... and still doesn't work.

---

### Post by rwyankees on 2007-02-01
SO I just got fed up with Firefox and installed swiftfox... Java works like a charm now

---

### Post by LaneLester on 2007-02-03
> **rwyankees said:**
> SO I just got fed up with Firefox and installed swiftfox... Java works like a charm now

I, too, jumped through lots of hoops without getting Java to work in Firefox. I installed Swiftfox, and no luck there. I searched in Synaptic again and found Java 6 is now out. I installed it, and now I have Java in both Firefox and Swiftfox! :) 

Now to try to figure out why Jedit and GFP can't find Java... :( 

Lane

---

### Post by phossal on 2007-02-03
If you have firefox with a working Java plugin, it's because the .so or a link to it is in the /usr/lib/firefox/plugins folder. There isn't any way *around* that, although you can *install* it in a variety of ways. If you want to use the third party JDK 6 package (sun-java6-jdk) from backports, or if you want to install sun-java5-jdk, or if you want to download it from SUN direct, or if you want to use automatix - it doesn't matter. Your method, or you personally, will have to put the file or  the link in the browser plugin directory. It isn't magic. 

Once you know what you're doing, it's as simple as making the symlink from the java/plugins directory to the /firefox/plugin directory.

---

### Post by LaneLester on 2007-02-03
> **phossal said:**
> Your method, or you personally, will have to put the file or  the link in the browser plugin directory. It isn't magic.

I'm sure it isn't magic, but it sure seems like it. I had the plugin or its symlink in every folder that anyone on here mentioned... without success.

As I described above, I only succeeded when I used Synaptic to install Java 1.6. Synaptic's install of Java 1.5 didn't do it.

Lane

---

### Post by Fh_Squirrel on 2007-02-03
> **meng said:**
> You have to install the packages:
sun-java5-jre
sun-java5-plugin

This is what i did in terminal Using
Sudo apt-get install sun-java5-jre
Sudo apt-get install java5-plugin

Works great no moving this to that or anything just that!! and I am now playing yahoo games with no errors in Firefox

---

### Post by phossal on 2007-02-03
> **LaneLester said:**
> I'm sure it isn't magic, but it sure seems like it. **I had the plugin or its symlink in every folder that anyone on here mentioned**... without success

I don't even know what to say. I'm glad you're up and running regardless of how you did it. Enjoy your day/evening. For testing, you could delete every occurrence of the libjavaplugin_oji.so that exists within your browser directories, one by one, until you realized a) where *the on you need* is located and b) where the one you *need* is *living* (assuming it's a link.).
Cheers!

---

### Post by zeddock on 2007-02-11
> **Fh_Squirrel said:**
> This is what i did in terminal Using
Sudo apt-get install sun-java5-jre
Sudo apt-get install java5-plugin

Works great no moving this to that or anything just that!! and I am now playing yahoo games with no errors in Firefox


Might work OK if you use sudo versus Sudo.

But why DL that big thing if version 6 is out?

zeddock

---

### Post by Rajia on 2007-02-18
> **phossal said:**
> [COLOR="SlateGray"]**Installing JAVA doesn't install the plugin necessarily!**[/COLOR]

If you installed Java, which you claim to have done 5 times, there is a folder with the "java" command in it. It's the executable for the JRE. There are a lot of ways to find it, but I'll give you a simple one. In that folder, in another folder, in another folder, is the plugin.so that Firefox wants installed. Here is how you find out where it is:

```
sudo locate */plugin/i386/ns7/libjavaplugin_oji.so
``` 

That's going to give you an answer something like this:
```
[COLOR="DimGray"]bash 3.1:[/COLOR]sudo locate */plugin/i386/ns7/libjavaplugin_oji.so
*[COLOR="Blue"]/usr/lib/Java6/jre/plugin/i386/ns7/libjavaplugin_oji.so[/COLOR]*
```

Then, using that full path (which is the path to the plugin), you're going to make a symbolic link in the browser plugins folder. The firefox folder is typically in: /usr/lib/firefox

Install the link like so:
```
sudo ln -s /usr/lib/Java6/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins
```

Open up firefox: Toolbar -> edit ->preferences -> enable java
Restart firefox and enjoy your life. ;)



Thank you, Phossal, life is truly more enjoyable with functional java.

---

### Post by phossal on 2007-02-20
You're very welcome, of course. Everyone has their own preference for the version of Java they want to use, along with their preferred method of installation. If you decide to upgrade to version 6, or to grab an update from SUN, [consider following the six steps I've laid out here]("http://ubuntuforums.org/showthread.php?t=332674#1"). It doesn't get an easier, and it's a great way to keep current.

---

### Post by LaneLester on 2007-02-20
> **phossal said:**
> You're very welcome, of course. Everyone has their own preference for the version of Java they want to use, along with their preferred method of installation. If you decide to upgrade to version 6, or to grab an update from SUN, [consider following the six steps I've laid out here]("http://ubuntuforums.org/showthread.php?t=332674#1"). It doesn't get an easier, and it's a great way to keep current.
Something is messed up in my Feisty system such that no one's method, including this one, gets me javascript functionality in Firefox. I have done everything anyone suggested, including manually confirming that the plugins are in all the Firefox plugins directories (there are more than one).

I just finished following your tutorial, which was very specific. Since I had tried other approaches and had other Javas on my system, I ran this:
```
 update-alternatives --config java
```
and selected the new one.

It's all very strange to me why I can't get this very basic function to work. I guess I should delete all my Javas and start over again.

Later: OK, I found the answer: I needed to delete the ~/.mozilla directory that I had copied over from my Edgy partition. With a fresh start, Firefox now has Javascript. And I have a zillion passwords for it to start memorizing and 20 or so addons to add on again. :(

Lane

---

### Post by cmreinke on 2007-02-27
Here's what I had to do to get it to work:
After following the instructions from the "Plugin Required" window (manual installation),
[LIST=1]
[*]cd to /opt/firefox/plugins/
[*]rm the existing libjavaplugin_oji.so, which was **not** a symbolic link
[*]create a sybolic link to the newly installed .so (i.e.: "ln -s /usr/local/java/jre1.5.0_09/plugin/i386/ns7/libjavaplugin_oji.so" for my system)
[*]restart firefox (2.0.0.2 in my case).
[/LIST]
After that, everything works correctly (so far, anyway).

-Charles

---

### Post by phossal on 2007-02-27
> **cmreinke said:**
> Here's what I had to do to get it to work:
After following the instructions from the "Plugin Required" window (manual installation),
[LIST=1]
[*]**cd to /opt/firefox/plugins/**
[*]rm the existing libjavaplugin_oji.so, which was **not** a symbolic link
[*]create a sybolic link to the newly installed .so (i.e.: "ln -s /usr/local/java/jre1.5.0_09/plugin/i386/ns7/libjavaplugin_oji.so" for my system)
[*]restart firefox (2.0.0.2 in my case).
[/LIST]
After that, everything works correctly (so far, anyway).

-Charles

Nice. The difference between my suggestion and that above is the directory where Firefox is living?

---

### Post by Arup on 2007-02-27
Only Phossal's was of installing Java from JDK solved my problem of slow Opera, now Opera runs normally, earlier, Opera would just drag with Java JRE installed the sudo apt-get way, many thanks to Phossal, as Opera is my default browser and mail client, life without Opera was getting very hard to contemplate. Many thanks Phossal.

---

### Post by phossal on 2007-02-27
:) You're very welcome, of course. Cheers!

---

