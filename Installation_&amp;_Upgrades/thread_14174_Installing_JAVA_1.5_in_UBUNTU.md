---
title: "Installing JAVA 1.5 in UBUNTU"
date: 2005-02-05
forum: Installation &amp; Upgrades
---

### Post by buttonpusher on 2005-02-05
I've downloaded the proper version of JAVA for Linux and have been following the instructions in the UBUNTU Guide.  My hang up is when I use the command to expand the package I get the following statement:

dirname: too many arguments
Try `dirname --help' for more information.
dirname: too few arguments
Try `dirname --help' for more information.

and the expansion stops.  From what it looks like it doesn't fully expand the file and if I try the MV command it will not find the directory.  Is there another way to get this done or what am I doing wrong - again?

thanking all in advance,

Buttonpusher :?:

---

### Post by macewan on 2005-02-05
[http://www.ubuntulinux.org/wiki/Java15](http://www.ubuntulinux.org/wiki/Java15)

---

### Post by buttonpusher on 2005-02-05
=D> 

macewan

I followed the instructions in the link you provided and after trying it twice it finally installed.  Thanks for the link.  I'll start to check them before posting again.

---

### Post by keyshawn on 2005-02-09
[QUOTE=macewan][http://www.ubuntulinux.org/wiki/Java15](http://www.ubuntulinux.org/wiki/Java15)[/QUOTE]

Thanks for the link ! 

I installed it flawlessly, though I can't get java to work in firefox [1.0 - backport] :(
Any help on this one ?

---

### Post by kiddo on 2005-02-13
Same thing here, is there a way to make firefox just work on this one >_<? Followed instructions *à la lettre*, yet I can't get java to work (didn't even try making multimedia support work)
 
 However, I'm sure java is properly installed, since java --version gives me a proper output. And what's funny is that when I visit my webmin page with some java in it, firefox will give me the nice "click here to see what missing plugins need to be installed blah blah blah" and then next, it then shows "available plugins:" and java is there... but it won't do anything about it  >_<
 
 Other things I'd like to have answers on the linux version of firefox:
 how to disable that "use my domain for anything you can't find" ? If I try to use the lucky search with only one word, it will always come back to my server. Not a problem with the windows version.
 
 Also, why do the form buttons look so ugly? Why don't they blend with gnome?

---

### Post by JayCnrs on 2005-02-14
You will need to put the plugin from the java folder into the Firefox plugin directory, create a symbolic link to  /where/java/is/plugins/browser(not sure writing this from Windows machine)/ns7/libjavaplugin_oji(again not sure of this ) use the following command
**ln -s /where/java/is/plugins/browser(not sure writing this from Windows machine)/ns7/libjavaplugin_oji(again not sure of this ) /directory/firefox/plugins**. 

Sorry that I can't give you the right paths but my Firefox is installed from the download found at the Firefox website.

---

### Post by kiddo on 2005-02-14
Does the fact I'm using a backported Firefox change anything?
 The ln was done everytime, it's there.. but it won't work!

---

### Post by JayCnrs on 2005-02-15
Did you try linking to the other plugin located under ns7-gcc29, the backported Firefox may have been compiled using gcc-29.

---

### Post by tkiesel on 2005-02-15
I finally got it to work. The trick was reading up in about: plugins in Firefox, which led to [Mozilla plugindoc](http://plugindoc.mozdev.org/).

Firefox looks for plugins in /home/username/.mozilla/plugins , not in /home/username/.mozilla/firefox/plugins

Putting the  link to libjavaplugin_oji.so into the former rather than the latter made it work for me.

---

### Post by danip on 2005-02-17
I followed the ubuntu guide did everthing thig it says and java still will not work on firefox.  I followed that last instruction listed here

```
steve@blackbetty ~/Desktop $ sudo ln -s /usr/java/jre1.5.0_01/plugin/i686/ns7/libjavaplugin_oji.so /home/steve/.mozilla/plugins

```

I still cannot get java to work in firefox.  Any help?

---

### Post by cyberchills on 2005-02-17
Ok, here's the deal.  If you put it in your personal profile it will be good only for your userid.  The best solution is to make it global by putting the symlink in /usr/lib/mozilla-firefox/plugins .  

Secondly make sure you go into your firefox preferences and turn java on

Please note it is best to download the Java directly from [www.java.com](www.java.com) or Sun.


**RESPECT**

---

### Post by danip on 2005-02-19
```
steve@blackbetty ~ $ sudo ln -s /usr/java/jre1.5.0_01/plugin/i686/ns7/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins
Password:
ln: `/usr/lib/mozilla-firefox/plugins/libjavaplugin_oji.so': File exists

```

Java still doesnt work.

---

### Post by kassetra on 2005-02-19
Here is the information I had to follow in order to make my java work:
 
 [http://www.ubuntulinux.org/wiki/JavaPackageBuild15001]("http://www.ubuntulinux.org/wiki/JavaPackageBuild15001")
 
 I did make one minor change to the instructions at the end because I'm using warty:
 
 Where it says:
  >   First install the sun-j2re1.5debian or sun-j2sdk1.5debian package with sudo apt-get install.  

   The Debian/Ubuntu package has been created in the current directory. You can install the package as root (e.g. sudo dpkg -i sun-j2re1.5_1.5.0+r01_i386.deb). 

 
 
 I did this instead:
  ```
sudo dpkg -i sun-j2re1.5*
```
 
 because I kept getting an unmet dependency error on both packages no matter which I tried to install first, so with the line above, it figured out how to install them both together.
 
 I hope this helps.

---

### Post by piedamaro on 2005-02-19
[QUOTE=danip]```
steve@blackbetty ~ $ sudo ln -s /usr/java/jre1.5.0_01/plugin/i686/ns7/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins
Password:
ln: `/usr/lib/mozilla-firefox/plugins/libjavaplugin_oji.so': File exists

```

Java still doesnt work.[/QUOTE]
Easy, the link exists already (/usr/lib/mozilla-firefox/plugins/libjavaplugin_oji.so': File exists) and it's obviously broken, so remove the old link and relink.

---

### Post by cyberchills on 2005-02-19
Which vesion of firefox are you using? 

and rm the old link and create a new one.

---

### Post by danip on 2005-02-19
nm i had to restart for something and java started working.

---

