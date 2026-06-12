---
title: "Eclipse Start Up problem"
date: 2008-10-21
forum: Installation &amp; Upgrades
---

### Post by raedbenz on 2008-10-21
Hi,

 i installed Eclipse using CLI on my Ubuntu8.04

```
sudo apt-get install eclipse
```

when i start up i get [ATTACH]89147[/ATTACH]
any hints??
thanks

---

### Post by xphlo on 2008-10-21
Im not a pro when it comes to java, but I recall similar problems some time ago.

Right now you are pointed to /usr/lib/jvm/java-gcj/bin/java. Type...
```

ls /usr/lib/jvm

```
Check out which jre's you have installed, and instead of java-gcj, try java-1.5.0-sun or similar (1.5 is recommended). So now you will want to point to "/usr/lib/jvm/java-of-choice/bin/java".

You can either add your new jre to PATH before you run eclipse, or you can dig up eclipse.ini (couldn't tell you where apt puts that) and change the default java jre within. 
One way to set PATH (non eclipse.ini) is to make a small shell script that sets PATH to your destination, and then executes eclipse for you. And then, to get eclipse going, you just point your menus/desktop_icons/symbolic_links to your script. If you go with the script method, it also makes it easy(ier?) to pass arguments to eclipse (ram usage, others...)

Once upon a time, I was an IDE whore, and it was quite easy to bloat eclipse(it can do a lot). I found that downloading base eclipse installs ([http://www.eclipse.org/downloads/index_project.php](http://www.eclipse.org/downloads/index_project.php)) and unpacking in your home directory was much easier to manage.
Instead of having one eclipse install with a thousand addons, taylor several separate eclipse instances to your different work enviroments.

Good luck

---

