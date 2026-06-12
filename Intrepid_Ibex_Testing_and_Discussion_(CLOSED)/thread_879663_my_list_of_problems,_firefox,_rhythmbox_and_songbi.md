---
title: "my list of problems, firefox, rhythmbox and songbird"
date: 2008-08-04
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by waspbr on 2008-08-04
k, here's my list of problems, fist the firefox problem,  not as much a problem than an annoyance.

Everytime I open a new firefox window, the title bar (windows headings) is hidden, I have to press F11 two times to make it go back to normal. And yes I am using compiz and emerald. here's a screenshot.
[[IMG]http://img530.imageshack.us/img530/3328/screenshotgu0.th.png[/IMG]](http://img530.imageshack.us/my.php?image=screenshotgu0.png)

the second problem I guess is sort of connected, I dunno why but all of a sudden rhythmbox started misbehaving, when launch it, it runs for a few seconds and then closes itself. In terminal I get a "segmentation fault" message. 

So then I tried using songbird, it won't play any songs, I click on the songs but it just won't play. I may have read something somewhere that suggested a java problem, but I am still puzzled. 

any help is more than welcome, it would be nice to see if someone else has got a similar problem.

---

### Post by tuxxy on 2008-08-04
What java version are you using,

```
sudo update-alternatives --config java
```

You could try updating if you feel its a java problem

---

### Post by waspbr on 2008-08-04
I gotta write down that command, keep forgetting it.

but 

here's the output

```

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*         1    /usr/lib/jvm/java-6-sun/jre/bin/java
 +        2    /usr/lib/jvm/java-6-openjdk/jre/bin/java


```

as it turns out I was running openjdk, so I have switched to sun's, so far there has been no difference, I have also run update manager but I haven't found anything related other then alsa-utils.  well, gonna reboot now...

---

### Post by tuxxy on 2008-08-04
Yes there may be no difference until you were to install the 1 /usr/lib/jvm/java-6-sun/jre/bin/java webplugin if you didnt already

---

### Post by waspbr on 2008-08-04
0.0

didn't realise sun had released webplugins for 64 bit systems, so far I have been relying on icedtea

---

### Post by waspbr on 2008-08-04
I must stop pouring vodka into my green tea, i can't really say for sure why(maybe the last update) but the annoying tittle bar thingy has stopped, hurray one less annoyance.

and update on the java thing.I ran that command again and I got another option

```
  Selection    Alternative
-----------------------------------------------
*         1    /usr/lib/jvm/java-6-sun/jre/bin/java
 +        2    /usr/lib/jvm/java-6-openjdk/jre/bin/java
          3    /usr/bin/cacao

```

cacao? 

Although the problems with rhythmbox and songbird still persist, banshee seems to work fine so far...

---

### Post by tuxxy on 2008-08-04
ahh yes I meant 32bit plugin, I use GCJ and the 32bit plugin with great results.

Heres a link to setting it up in 64bit Hardy

[http://ubuntuforums.org/showthread.php?t=774956](http://ubuntuforums.org/showthread.php?t=774956)

---

### Post by mattduckman on 2008-08-04
i got a segfault in rhythmbox once because it had trouble with a cd that was in the drive. you might want to try removing all cds, dvds, and usb devices and try again.

if that doesn't work, you can try using the debug option to see what's going on at the time of the segfault. if you don't pipe the output to a file, it'll take like 20x longer to start up. i think this is how you do it:
```
rhythmbox -d 2> rhythmbox.debug
```

---

