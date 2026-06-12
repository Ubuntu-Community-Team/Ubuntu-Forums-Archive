---
title: "how do i get adobe flash player in ubunti linux"
date: 2013-06-20
forum: Installation &amp; Upgrades
---

### Post by strictlybizness77 on 2013-06-20
i have ubuntu 13.04 using red hat version linux how do i get java and which 1 and install directions as well as i need a flash player and install directions....please explain in laymens terms i am brand new to linux os.thanx
:confused::confused:

---

### Post by newbie-user on 2013-06-21
So...are you using Ubuntu or Red Hat?

On Ubuntu, to get Java and flash player, add the following lines to your /etc/apt/sources.list file:
```
http://ppa.launchpad.net/webupd8team/java/ubuntu raring main
http://archive.canonical.com/ubuntu raring partner
```
then run:
```
sudo apt-get update && sudo apt-get install oracle-java7-installer adobe-flashplugin -y
```

You'll have to look up the installer commands for Red Hat, as I don't know what they are.

---

### Post by adityaismagic on 2013-06-21
Welcome to Ubuntu 13.04. It is possible to install a software which is not listed in Ubuntu Software Center. But it is really very painful and sometime it is harassing too, because first you have to download that specific software which is called a package with .deb extension and then you have to download it's supporting or supplementary software's. And it is possible that for a single software, you may have to download 100 supporting softwares. 

So THE best way to download any software is, to download it from Ubuntu Software Center ( icon is in left panel, if you didn't find icon then click on the first icon of panel and search there Ubuntu Software Center and you will have it). Now the most important thing is, YOU MUST HAVE TO CONNECTED WITH INTERNET. 

1> for Flash player - in Ubuntu Software Center, there is search box at upper right hand side, just wright "flash" and search. First name will be Adobe Flash Plugin. click on name then 2 buttons will appear, "more info" and "install". click on "more info". after some time its complete information will appear, then you can see its complete size and some "optional add-ons". You can install software without add-on but I suggest you must install with add-on because they are kind of supporting softwares. so check add-ons click on apply changes (which will appear after checking add-on) and then click on "install" button at upper right hand side.
2> for Java - in Ubuntu Software Center there are two compilers for Java. so it's your choice which one you want to install. 
                    when software center opens click on " Developer Tools "
                                   a> click on IDEs --  Eclipse
                                   b> click on java -- Open JDK
                    both are very good compilers. Read description or search on google about them and install wisely.

---

