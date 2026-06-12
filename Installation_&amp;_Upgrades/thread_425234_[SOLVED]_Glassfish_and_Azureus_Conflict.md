---
title: "[SOLVED] Glassfish and Azureus Conflict"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by jpietari on 2007-04-27
I installed Azureus on Feisty and it worked great.  I then installed Glassfish and again, Glassfish worked great.  I then rebooted my machine and Azureus crashes on startup.  When I execute the program in a shell, it states that a log "hs_err_pid8843.log" was created.  I don't where to find log.   

When I open a browser and type [http://localhost:4848](http://localhost:4848), it redirects me to [http://localhost:4848/asadmin/admingui/TopFrameset](http://localhost:4848/asadmin/admingui/TopFrameset), but the "Problem loading Page" screen is displayed.  Glassfish doesn't seem to be working either....

I'm guessing the version of Java is conflicting and there might be a port issue....

I looked into the services running and I do not see Glassfish.  Is this normal???

Java Version:
-----------------
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_11-b03)
Java HotSpot(TM) Client VM (build 1.5.0_11-b03, mixed mode, sharing)

---

### Post by LuisGMarine on 2007-04-27
I might not be able to help you with your glassfish problem, but I have had the problem with Azureus in the past.  Forgive me, but its been a while and I don't exactly remember what I did, but I will try to do my best to recollect those memories and help you out.

Firs thing first, upgrade your java to 1.6.  To do so , please follow this easy to follow guide located [here]("http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html")

After you have done that download the latest Azureus from their official website.  Should be version 2.5.0.4, and it should come in a tar.bz2.

untar the file to w/e you would like and simply just run the script from the azureus folder.  Not this does not add it to your menu, you can do that manually.  I just added an icon to my desktop.

For that all I did was:

1. Right-Click anywhere on the desktop, select ' Create Launcher '
2. Once the ' Create Launcher ' app has pulled up fill in the information.  For command you are going to navigate to the script that is in your azureus folder,  For example mine resides in /home/username/azureus/azureus.  Its as simple as that.
3. For the icon was a bit tricky.  The good azureus icon resides in the azureus folder and its labeled 'azureus.png'.  For some unknown reason the ' Create Launcher' application doesn't seem to allow you to put .png's from their icon selection menu.  So just pick an ordinary icon from the folder it opens up when you hit the ' icon ' button, and pick any random ugly icon.  Once the application and weird icon are on your desktop, right click on it, select properties, and then click the icon and this time it will recognize the .png and you should be able to select it.

Hope this helps out a bit, post any questions if you are lost.

-LuisGMarine

---

### Post by jamesstansell on 2007-05-02
Your problems may be related, by virtue that these are both Java applications, but I don't think it's a direct conflict between the two.

First, as Luis said, the Azureus problem is well known.  You'll find it in the launchpad bug reports for Azureus.  I've heard that someone was submitting a fix for the feisty-proposed repository but I haven't confirmed that.  As listed in comments in the bug a fairly simple work-around is to replace the Azureus2.jar file.  It works fine with the java5 jre on Edgy so you may not need java6.

Regarding glassfish, it must be running if that redirect is happening.  The log files may be in a directory called domain1/logs.

As for the process name I would try finding it with this command: ```
 sudo fuser 4848/tcp
```
I wouldn't be at all surprised if the name was java or asadmin or something else that didn't sound like glassfish.

I checked launchpad for bugs for glassfish but I guess none have been reported yet.

Regards,

-james.

---

### Post by jpietari on 2007-05-12
Thanks for all the help with Glassfish and Azureus.

Please bare with me as I'm relatively new to Linux and do not have a solid understanding of where to look to figure out errors.

Azureus Problem: 
I ended up uninstalling Azureus and now use Bittorrent and Bittornado.  I'm sure the workarounds work but I don't want to change things outside the Ubuntu repositories.  I did that on a previous install and ran into problems when I upgraded to Feisty.

Glassfish Problem:
I shouldn't of even posted this.  I used Tomcat previously, which by default, started upon start-up.  Glassfish needs to be started manually  by using the command 'asadmin start-domain domain1'.

Thanks for the help!!!!

---

