---
title: "After installing 8.1x Inrepid Beta I'm unable to login"
date: 2008-10-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Ximal on 2008-10-10
I have a dell tower with nvidia video card and intel chip set...

Whenever I get to the login screen I am unable to get into the computer by means of the visual login and it continuously turns grey and then back to normal... switching colors in an ambient type of way... 

If there is a command I can use since EVERYTHING is booting up and running . This means the network adapter is functional .. Can I do something like 

sudo apt-get install update 

or some sort of restricted driver enabling technique I can use ? or command line syntax ?

please help... I could not find the intrepid forum as I do not see a direct link for INTREPID .. just different major brand names and such..

Thanks to any who can help me..

---

### Post by andybleaden on 2008-10-13
Not specificall for ubunut as it is kubuntu but the kubuntu forums has a dedicated section on II 8.10 here

[http://kubuntuforums.net/forums/index.php?board=93.0](http://kubuntuforums.net/forums/index.php?board=93.0)

Not wanted to upgrade myself yet...will wait til November

---

### Post by andybleaden on 2008-10-13
There is also the wiki for intrepid here

[http://ubuntuguide.org/wiki/Ubuntu:Intrepid](http://ubuntuguide.org/wiki/Ubuntu:Intrepid)

---

### Post by devoncatt on 2008-10-13
Most likely the problem is the saqme as I encountered. 8.10 does not always configure the mouse and keyboard. Make sure it is configured in /etc/X11/xorg.conf.
Second easier make sure your home directory is owned by you and the etc/passwd file has the same user Id
Devoncatt

---

