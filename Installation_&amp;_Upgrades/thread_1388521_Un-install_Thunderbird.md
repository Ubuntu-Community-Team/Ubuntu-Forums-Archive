---
title: "Un-install Thunderbird"
date: 2010-01-23
forum: Installation &amp; Upgrades
---

### Post by Bananasdoom on 2010-01-23
I have installed the new Thunderbird 3 release for called shredder 3.0.2 now that I have installed it and found how buggy it is I don't really want it any more but I cannot uninstall it the normal way eg. sinaptic, ubuntu softwair centre. I installed it buy through the Terminal by following a guide on a blog so I am not to sure how I did it and how to un-do it. 

here is what I did 
[http://digitizor.com/2009/12/10/how-to-install-thunderbird-3-shredder-in-ubuntu-9-10/](http://digitizor.com/2009/12/10/how-to-install-thunderbird-3-shredder-in-ubuntu-9-10/) 

> 

[LIST]
[*]Add the Mozilla PPA in your source list using:
[/LIST]
[INDENT]sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa
[/INDENT]
[LIST]
[*]Update source list using:
[/LIST]
[INDENT]sudo apt-get update
[/INDENT]
[LIST]
[*]Install Thunderbird 3 using:
[/LIST]
[INDENT]sudo apt-get install thunderbird-3.0
[/INDENT]_It is advised that you  remove the repository from the source list after the installation. If  you do not know how to do it, here is how:_
 
[LIST]
[*]In Terminal, execute the command,
[/LIST]
[INDENT]sudo apt-get gedit /etc/apt/sources.list
[/INDENT]
[LIST]
[*]In the **source.list** file that is opened, find the  line which says &#8220;***[http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu)  karmic***&#8221; and remove it.
[*]Save and close the file. Done.
[/LIST]
I forgot to remove the source list dose this mater and should I do it ?? I am not able to use it it comes up with an error when I try 

[IMG]http://farm3.static.flickr.com/2746/4297764324_d984b587fc_b.jpg[/IMG]
Thanks

---

### Post by s.fox on 2010-01-23
Hello,

The correct command to edit your sourceslist file is:

```
sudo gedit /etc/apt/sources.list
```

-Silver Fox

---

