---
title: "Java. &quot;sun-java5.bin is not available in any software channel&quot;"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by woofcat on 2006-06-01
'sun-java5-bin' is not available in any software channel

I am using synamptic or ehh, Add/Remove Applications and i have all my repositorys selected aswell as "Show Unsported applications" and "Show Commecial Applications" using an AMD box. I can give further specs but i don't think that is the problem since i had java on this computer 1 hour and 27 minutes ago before my format. Any help would be great. Thanks!

---

### Post by johnc4510 on 2006-06-01
It is available in the mutiverse repository.
To enable extra repositories:
System>Administration>Synaptic Package Manager
Click on settings. Click on repositories and put a check in all empty boxes
Then close that window
Then Reload, then Mark all Upgrades, then apply
Now the app should be in the synaptic window ready to install

---

### Post by ubuntu_demon on 2006-06-01
you should make sure multiverse and universe are added and uncommented in your /etc/apt/sources.list

$sudo gedit /etc/apt/sources.list

If you run x86 instead of 64 bit you might want to take a look at my sources.list in my signature.

---

### Post by woofcat on 2006-06-01
Thanks guys. I updated my sources list and did it the good old apt-get way.

---

### Post by Amar_ze on 2006-06-01
How about Java Runtime enviroment? My firefox is asking for that plugin (when trying to play some online games) but can't install it or find it on appt.Hope this is good thread for this I am new here :).Regards

---

### Post by ubuntu_demon on 2006-06-02
[QUOTE=Amar_ze]How about Java Runtime enviroment? My firefox is asking for that plugin (when trying to play some online games) but can't install it or find it on appt.Hope this is good thread for this I am new here :).Regards[/QUOTE]
sun-java5.bin contains the Java Runtime Environment.

$ sudo apt-get install sun-java5-bin

To make the sun java the default :
$ sudo update-alternatives --config java
and choose the sun one

In the old days you had to create some links to get firefox working with java. I don't think that's necessary anymore.

---

### Post by Amar_ze on 2006-06-02
When I run sudo apt-get install sun-java5-bin
 I got this: E: Couldn't find package sun-java5-bin . Maybe I need some mirror for app that provides java?

---

### Post by woofcat on 2006-06-02
[http://www.ubuntuforums.org/showthread.php?t=185760](http://www.ubuntuforums.org/showthread.php?t=185760)
Use "Ubuntu_Demon"'s source list. Its what i used and its great and installed java fine.

Welcome to the Ubuntu party.

---

### Post by Patrick J. Anderson on 2006-06-02
I modified my apt sources based on instructions above, but sun-java **is not found** in the repositories

---

### Post by ubuntu_demon on 2006-06-02
[QUOTE=Patrick J. Anderson]I modified my apt sources based on instructions above, but sun-java **is not found** in the repositories[/QUOTE]
Please post your sources.list

Here's a guide for enabling the multiverse and universe repositories :
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by Amar_ze on 2006-06-02
I installed and now I have Sun Java 5,0 Web Start under Internet menu, but firefox still asks for runtime enviroment plugin (I am tryng to play game [here]("http://miniclip.com/8ball.htm") maybe someone can try.. )

---

### Post by ubuntu_demon on 2006-06-02
[QUOTE=Amar_ze]I installed and now I have Sun Java 5,0 Web Start under Internet menu, but firefox still asks for runtime enviroment plugin (I am tryng to play game [here]("http://miniclip.com/8ball.htm") maybe someone can try.. )[/QUOTE]

Don't forget to install the plugin :
$sudo apt-get install sun-java5-plugin

To make the sun java the default :
$ sudo update-alternatives --config java
and choose the sun one

Also restart firefox.

If it still doesn't work find another internet site to test java.

You could also go here for other methods of installing java :
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by Amar_ze on 2006-06-02
When I did sudo apt-get install sun-java5-plugin everything works great now.Thanks alot

---

### Post by ubuntu_demon on 2006-06-02
no problem :)

I also created a guide about these types of problems. A howto for multimedia (including java). see :

[http://www.ubuntuforums.org/showthread.php?t=186792](http://www.ubuntuforums.org/showthread.php?t=186792)

---

