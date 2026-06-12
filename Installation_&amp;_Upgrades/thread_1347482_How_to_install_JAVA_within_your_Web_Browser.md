---
title: "How to install JAVA within your Web Browser?"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by Saurabhdua on 2009-12-06
Hi Guys!

Please do not alienate this query only on the basis of my Joining Date of this Forum(it can be deceptive to a Gr8 deal!).;)

Please guide me on how to install the JAVA within the Web Browser(Firefox).

The respective Web page that asks me for the same takes me to::

[http://java.com/en/download/linux_manual.jsp?host=java.com&locale=en-US](http://java.com/en/download/linux_manual.jsp?host=java.com&locale=en-US)

....& there are plethora of options to choose from..etc. etc. etc.?!

Please guide me on everything in this regard...! :popcorn:

---

### Post by phillw on 2009-12-06
Hi, if you head over to [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)  lovinglinux keeps an excellent aera for things FireFox.

Regards,

Phill.

---

### Post by wojox on 2009-12-06
Open your terminal and run:

```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

---

### Post by phillw on 2009-12-06
And don't get caught by 

> [COLOR=#cc0000][SIZE=4]Removing Conflicting Plugins[/SIZE][/COLOR]

Ubuntu comes with swfdec plug-in, but it doesn't work on several sites. Installing the version from Adobe might solve this problem and improve performance. 

To remove other flash plug-ins and install only the one from Adobe open "Applications >> Accessories >> Terminal", then paste (CTRL+SHIFT+V) the code below in the terminal window and hit enter:

 	

In which case you'll need

```
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree 
```

Unless you're running 64 Bit - in which case it's a totally different game-plan !!

Phill.

---

