---
title: "I can't get Java to work on 12.04"
date: 2012-04-21
forum: Installation &amp; Upgrades
---

### Post by More or Less on 2012-04-21
I have already tried the download center.  The firefox browser doesn't seem to recognize java being installed.  I tried running it and then firefox, but still nothing.

7 is the most recent version, correct?  If so, how can I get it? The java.com site has something about RPM files but I don't know if I can install that or how to.

---

### Post by darkod on 2012-04-21
You can simply unpack the java7 .tar.gz and that's it.

If you want it to be used as main java, you can select it using something like:
sudo update-alternatives --config java

---

### Post by More or Less on 2012-04-21
> You can simply unpack the java7 .tar.gz and that's it.I am not sure how to unpack with .tar.gz files.  Maybe you can explain.

However, I did find a solution when I read [http://ubuntuforums.org/showthread.php?t=1952134](http://ubuntuforums.org/showthread.php?t=1952134)

In there it said "icedtea".  It's not the top installation.  I had downloaded 7 and it didn't work.  So, while downloading 6, I read this thread, and I saw the "tea" part.  

I think you guys need to set up a better system of informing users what they need to upgrade/download.  I downloaded 7 thinking it was the solution.  However, third and fourth on the list shows me "Java IcedTea".  Bingo!!! Java is now shown in Firefox plugins.

I don't know how a new user to Ubuntu is supposed to know "IcedTea" will work but the first result "7" won't.  I simply went down the list because I was desperate.  Perhaps, you can place more emphasis on what will work, not what is MORE popular or MORE downloaded.

Then, the new user will get the files they need.  I am not saying this to complain, but to show a sore spot in the whole linux distribution process.  With Windows, I install and after 30 minutes, it's done.  I am up and running.  I admit Ubuntu now is superior, but it's like training a dog 1 trick at a time vs. putting dough in the oven waiting for the goods to bake.

The problem I have is resolved, but any new user will face the same issue.  Still worth looking into.  List IcedTea first and second in your download area, not third and fourth.

Whatever formula you have now places them third and fourth on my list.

---

### Post by c2tarun on 2012-04-21
You should try this:
[http://www.tricksfind.in/2012/04/how-to-install-sun-java-on-ubuntu.html](http://www.tricksfind.in/2012/04/how-to-install-sun-java-on-ubuntu.html)

---

### Post by darkod on 2012-04-21
For future reference, unpacking compressed files is as simple as right-click, Extract...

---

### Post by More or Less on 2012-04-22
> For future reference, unpacking compressed files is as simple as right-click, Extract... 	

Yea, I know that.  But where do I extract them, and what happens after that?  I have extracted what I assumed were program files for a program in the programs folder.  However, how do you get them to run?  In Windows there is an obvious .exe file which launches the program.  I don't see that in Ubuntu.  When I go to click the files either I get the files opening in text editor or it just hangs.

---

### Post by darkod on 2012-04-22
Actually, we were talking about different things. It is now clear that you were talking only about a java plugin for a browser, while I thought you were after the java JDK to use for programming java.
How it works is that you don't have to specifically install it. You only unpack it where ever you want, and with the update-alternatives you tell the system to use it when you are programming java.

Also, in linux the executable program doesn't necessarily need to be .exe. Depending on the software and its installation instructions you run the file that starts the install and usually that's it. Sometimes it is a .bin file, or .sh, etc...

---

### Post by More or Less on 2012-04-22
> **darkod said:**
> Actually, we were talking about different things. It is now clear that you were talking only about a java plugin for a browser, while I thought you were after the java JDK to use for programming java.
How it works is that you don't have to specifically install it. You only unpack it where ever you want, and with the update-alternatives you tell the system to use it when you are programming java.

Also, in linux the executable program doesn't necessarily need to be .exe. Depending on the software and its installation instructions you run the file that starts the install and usually that's it. Sometimes it is a .bin file, or .sh, etc...

That's all well in good, but that still doesn't tell me where to extract it.  If you are saying I can extract it anywhere and then click the "X", what do I do next?  I still can't find the program to launch.  If I search for it in the search area, it doesn't come up.  It's as if it is not on my computer or just being stored like it is on a USB stick.

The only thing that has worked for me is running a .deb file.  After running a .deb file, I can then search for the program, add it as a shortcut to the desktop, and then I always have easy access to that program in the future.  I don't have to search for it.

.bin, .zip, .gz files don't seem to do anything or give me any indication what to do next.  I am sorry, I am not a programmer, so I don't know how to launch these programs without an easy 1 click of the mouse and search for the name of the program.  

Please walk me through it step by step.  This is not only with Java, it is with ANY program I download.  Only .deb programs load.

Perhaps you can explain, STEP BY STEP how I install this .gz at [http://im.qq.com/qq/linux/download.shtml](http://im.qq.com/qq/linux/download.shtml) 

There is also an RPM.  I can't get the .deb to install because it says there is a non-digit in the name.  I think it has to do with "v" for version number being next to the version number.  A simple renaming of the file doesn't work.

So, any help you can give regarding this would be appreciated.  I think the programmers of the .deb just need to re-update it so it doesn't have the "v".  However, maybe I can get he .gz file or the RPM one to install QQ properly.

---

### Post by jerome1232 on 2012-04-22
First try OpenJDK and Icedtea

```
sudo apt-get install icedtea-plugin
```

If that doesn't work for you then remove it, and install java 6, using the self-extracting binary (like a .exe) from here, simply mark it as executable (right click, permissions, allow executing as a program) and run it.

[http://www.java.com/en/download/linux_manual.jsp?locale=en](http://www.java.com/en/download/linux_manual.jsp?locale=en)

---

### Post by darkod on 2012-04-22
I was talking about the Java JDK, not about any program.

For a particular program you will have to check the installation instructions. They usually tell you which file to run to install. In most cases there is a Readme in the extracted files.

I can't understand the link you sent in Chinese, and in the English download page there is no version for linux shown. So, I have no idea how they developed it, you will have to look for installation instructions on their website, or contact them, or google about the procedure to install that program in ubuntu.

Arguing about the difference in installing programs in windows and linux is pointless, they work in different ways. If you prefer the windows way so much, no one is stopping you to use it. Not all companies make an effort to publish installation instructions for the linux version but that is up to them, we can not be responsible for that.

---

### Post by More or Less on 2012-04-22
> **jerome1232 said:**
> First try OpenJDK and Icedtea

```
sudo apt-get install icedtea-plugin
```If that doesn't work for you then remove it, and install java 6, using the self-extracting binary (like a .exe) from here, simply mark it as executable (right click, permissions, allow executing as a program) and run it.

[http://www.java.com/en/download/linux_manual.jsp?locale=en](http://www.java.com/en/download/linux_manual.jsp?locale=en)

Yea, I already found icedtea in the download center, but it wasn't the first result.  There is no way to know icedtea or 7 (or the 6) which were listed before icedtea would not do what I was looking for.

I am suggesting they categorize user programs and developer programs.  This way if you are a user, you don't download unnecessary programs.

---

### Post by jerome1232 on 2012-04-23
> **More or Less said:**
> Yea, I already found icedtea in the download center, but it wasn't the first result.  There is no way to know icedtea or 7 (or the 6) which were listed before icedtea would not do what I was looking for.

I am suggesting they categorize user programs and developer programs.  This way if you are a user, you don't download unnecessary programs.

hmmm, well on mine they do this exactly. 11.10

Also when I read the descriptions of the packages, it gives a brief overview of what it does. You have to hit "more info" to see the detailed descriptions.

---

### Post by Curtis6767 on 2012-04-23
Installed IcedTea plugin and all the other IcedTeas were installed, as well.

Java up and running.

Thanks

---

### Post by techsupport on 2012-04-23
> **More or Less said:**
> I have already tried the download center.  The firefox browser doesn't seem to recognize java being installed.  I tried running it and then firefox, but still nothing.

7 is the most recent version, correct?  If so, how can I get it? The java.com site has something about RPM files but I don't know if I can install that or how to.

Try using a guide to get everything installed like Java 7.. etc etc:

[http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)

---

### Post by Ericj1186 on 2012-04-28
Maybe someone can help me.

I followed this guide to install Java 7: [http://www.unixmen.com/201204-top-things-to-do-after-installing-ubuntu-2/](http://www.unixmen.com/201204-top-things-to-do-after-installing-ubuntu-2/)

It said to do this first:

```
sudo apt-get purge openjdk*
```

Then:
```
sudo add-apt-repository ppa:eugenesan/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```

After doing that, I cannot install anything that requires Java because it says there is an issue with oracle Java7 installer. I cannot even add Faenza because of this. I also, somehow, have OpenJDK activated in the Software Center, but I cannot remove it at all. Every time I remove it, I get a "cannot remove package" message, and it removes anyway.

I need to find a way to purge all attempts at Java, so I can follow the new guides.

UPDATE:
I ran 
```
sudo apt-get purge openjdk*
```

It said one package not fully installed or removed. Here is the last error message I got:

```

Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by darkod on 2012-04-28
Look at my post #2. If we are talking about Java JDK, you don't need any special installs. At least I think so.

Remove that repository that you added. Go to the Oracle website and download the Java 7 JDK .tar.gz linux version. Extract in any folder on the computer, in your Home/java7jdk for example.

Use the update-alternatives command to tell the system to use that java as main. That should be it.

It worked for me for Netbeans, haven't tried it much for other things.

---

### Post by Ericj1186 on 2012-04-28
I admit, and this was stupid, I probably added a few repos. Is there anyway I can see which one was associated with this?

After following post #2, I tried to add Faenza icons. Here is what happens:

```

me@me:~$ sudo apt-get install faenza-icon-theme
Reading package lists... Done
Building dependency tree       
Reading state information... Done
faenza-icon-theme is already the newest version.
The following packages were automatically installed and are no longer required:
  libunistring0:i386 libgomp1:i386 libcroco3:i386 libgettextpo0:i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up oracle-java7-installer (7u3-0~eugenesan~precise4) ...
Downloading...
--2012-04-28 17:32:41--  http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz
Resolving download.oracle.com (download.oracle.com)... 184.84.252.224, 184.84.252.223
Connecting to download.oracle.com (download.oracle.com)|184.84.252.224|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz [following]
--2012-04-28 17:32:41--  https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz
Resolving edelivery.oracle.com (edelivery.oracle.com)... 184.87.134.174
Connecting to edelivery.oracle.com (edelivery.oracle.com)|184.87.134.174|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://download.oracle.com/errors/download-fail-1505220.html [following]
--2012-04-28 17:32:42--  http://download.oracle.com/errors/download-fail-1505220.html
Connecting to download.oracle.com (download.oracle.com)|184.84.252.224|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5307 (5.2K) [text/html]
Saving to: `./jdk-7u3-linux-x64.tar.gz'

     0K .....                                                 100%  526M=0s

2012-04-28 17:32:42 (526 MB/s) - `./jdk-7u3-linux-x64.tar.gz' saved [5307/5307]

Download done.
sha256sum mismatch jdk-7u3-linux-x64.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

According to that Faenza is installed, and I was able to add the icons, but I want to make sure everything is working correctly.

---

### Post by darkod on 2012-04-28
Well, the repo would be listed as eugenesan or similar. It should be easy to spot in Software Sources.

With the repo there it still tried to download and install the jdk. And fails at the hash mismatch.

---

### Post by Ericj1186 on 2012-04-28
I removed it, then tried this site: [http://www.tricksfind.in/2012/04/how-to-install-sun-java-on-ubuntu.html](http://www.tricksfind.in/2012/04/how-to-install-sun-java-on-ubuntu.html)

I still have the error when I hit Oracle-Java7-installer. I also still have that 1 not fully installed or removed item.

java-version shows

```
java version "1.7.0_03"
Java(TM) SE Runtime Environment (build 1.7.0_03-b04)
Java HotSpot(TM) 64-Bit Server VM (build 22.1-b02, mixed mode)

```

Then, I run:

```
me@me:~$ sudo apt-get purge openjdk-7-jre icedtea-7-plugin
[sudo] password for me:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package icedtea-7-plugin is not installed, so not removed
Package openjdk-7-jre is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libunistring0:i386 libgomp1:i386 libcroco3:i386 libgettextpo0:i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up oracle-java7-installer (7u3-0~eugenesan~precise4) ...
Downloading...
--2012-04-28 17:55:58--  http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz
Resolving download.oracle.com (download.oracle.com)... 65.125.72.33, 65.125.72.59
Connecting to download.oracle.com (download.oracle.com)|65.125.72.33|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz [following]
--2012-04-28 17:55:58--  https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz
Resolving edelivery.oracle.com (edelivery.oracle.com)... 184.86.86.174
Connecting to edelivery.oracle.com (edelivery.oracle.com)|184.86.86.174|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://download.oracle.com/errors/download-fail-1505220.html [following]
--2012-04-28 17:55:59--  http://download.oracle.com/errors/download-fail-1505220.html
Connecting to download.oracle.com (download.oracle.com)|65.125.72.33|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5307 (5.2K) [text/html]
Saving to: `./jdk-7u3-linux-x64.tar.gz'

     0K .....                                                 100% 8.07M=0.001s

2012-04-28 17:55:59 (8.07 MB/s) - `./jdk-7u3-linux-x64.tar.gz' saved [5307/5307]

Download done.
sha256sum mismatch jdk-7u3-linux-x64.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

From the first, it sounds like Sun Java is working. I guess I'll take it.

UPDATE: Nevermind. I tried to do a Java Verification on their site, and it doesn't recognize Java...

---

### Post by darkod on 2012-04-28
Java verification is for the plugin, whether you can run java in the browser. The latest commands you posted clearly say you don't have the icedtea plugin installed. Install it and the verification should pass.

But that is not a development environment (JDK) verification.

Are you after a JDK or just the plugin so java can work in a browser?

---

### Post by Ericj1186 on 2012-04-28
> **darkod said:**
> Java verification is for the plugin, whether you can run java in the browser. The latest commands you posted clearly say you don't have the icedtea plugin installed. Install it and the verification should pass.

But that is not a development environment (JDK) verification.

Are you after a JDK or just the plugin so java can work in a browser?

Wow. That just made a whole lot of sense.

I just want Java for my browser. So, I just need to install icetea? I feel really dumb now.

But that doesn't really explain why the java errors keep coming up.

---

### Post by darkod on 2012-04-28
Yeah, you only need the icedtea-7-plugin.

Those errors are for installing the oracle-7-jdk that you tried from that link. But that is not directly from oracle, it's from some repo which might not be packaged good, or who knows what's wrong.

---

### Post by Ericj1186 on 2012-04-28
How can I remove all instances of Java that I have installed and just install the icedtea plugin? I removed that errant repo.

---

### Post by darkod on 2012-04-28
For the plugin:
sudo apt-get install icedtea-7-plugin

You can try:
sudo apt-get remove --purge <package name>

for what you installed, but it's not always necessary. If you insist removing something, you can try like that.

---

### Post by Ericj1186 on 2012-04-28
> **darkod said:**
> For the plugin:


sudo apt-get install icedtea-7-plugin

You can try:
sudo apt-get remove --purge <package name>

for what you installed, but it's not always necessary. If you insist removing something, you can try like that.

Both had errors. I'll post them in order:

Purging Java:

```
me@me-Aspire-5552:~$ sudo apt-get remove ---purge oracle-java7-installer
[sudo] password for me: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libunistring0:i386 libgomp1:i386 libcroco3:i386 libgettextpo0:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  default-jre default-jre-headless icedtea-netx icedtea-netx-common
  openjdk-6-jre
Suggested packages:
  icedtea-plugin
The following packages will be REMOVED:
  oracle-java7-installer*
The following NEW packages will be installed:
  default-jre default-jre-headless icedtea-netx icedtea-netx-common
  openjdk-6-jre
0 upgraded, 5 newly installed, 1 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 4,218 B/844 kB of archives.
After this operation, 1,587 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise/main default-jre-headless amd64 1:1.6-43ubuntu2 [3,336 B]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise/main default-jre amd64 1:1.6-43ubuntu2 [882 B]
Fetched 4,218 B in 0s (5,334 B/s)    
Selecting previously unselected package default-jre-headless.
(Reading database ... 219567 files and directories currently installed.)
Unpacking default-jre-headless (from .../default-jre-headless_1%3a1.6-43ubuntu2_amd64.deb) ...
Selecting previously unselected package openjdk-6-jre.
Unpacking openjdk-6-jre (from .../openjdk-6-jre_6b24-1.11.1-4ubuntu2_amd64.deb) ...
Selecting previously unselected package default-jre.
Unpacking default-jre (from .../default-jre_1%3a1.6-43ubuntu2_amd64.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Setting up default-jre-headless (1:1.6-43ubuntu2) ...
Setting up openjdk-6-jre (6b24-1.11.1-4ubuntu2) ...
update-alternatives: using /usr/lib/jvm/java-6-openjdk-amd64/jre/bin/policytool to provide /usr/bin/policytool (policytool) in auto mode.
Setting up default-jre (1:1.6-43ubuntu2) ...
(Reading database ... 219599 files and directories currently installed.)
Removing oracle-java7-installer ...
update-alternatives: error: unknown argument `cdrom'
dpkg: error processing oracle-java7-installer (--purge):
 subprocess installed pre-removal script returned error exit status 2
Downloading...
--2012-04-28 19:19:24--  http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz
Resolving download.oracle.com (download.oracle.com)... 205.247.221.136, 205.247.221.154
Connecting to download.oracle.com (download.oracle.com)|205.247.221.136|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz [following]
--2012-04-28 19:19:29--  https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz
Resolving edelivery.oracle.com (edelivery.oracle.com)... 23.61.2.174
Connecting to edelivery.oracle.com (edelivery.oracle.com)|23.61.2.174|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://download.oracle.com/errors/download-fail-1505220.html [following]
--2012-04-28 19:19:30--  http://download.oracle.com/errors/download-fail-1505220.html
Connecting to download.oracle.com (download.oracle.com)|205.247.221.136|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5307 (5.2K) [text/html]
Saving to: `./jdk-7u3-linux-x64.tar.gz'

     0K .....                                                 100% 6.52M=0.001s

2012-04-28 19:19:30 (6.52 MB/s) - `./jdk-7u3-linux-x64.tar.gz' saved [5307/5307]

Download done.
sha256sum mismatch jdk-7u3-linux-x64.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Installing Icedtea

```
me@me-Aspire-5552:~$ sudo apt-get install icedtea-7-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libunistring0:i386 libgomp1:i386 libcroco3:i386 libgettextpo0:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  icedtea-netx icedtea-netx-common openjdk-7-jre
Suggested packages:
  icedtea6-plugin
The following NEW packages will be installed:
  icedtea-7-plugin icedtea-netx icedtea-netx-common openjdk-7-jre
0 upgraded, 4 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
Need to get 87.6 kB/930 kB of archives.
After this operation, 1,886 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise/universe icedtea-7-plugin amd64 1.2-2ubuntu1 [87.6 kB]
Fetched 87.6 kB in 0s (130 kB/s)          
Selecting previously unselected package openjdk-7-jre.
(Reading database ... 219600 files and directories currently installed.)
Unpacking openjdk-7-jre (from .../openjdk-7-jre_7~u3-2.1.1~pre1-1ubuntu2_amd64.deb) ...
Selecting previously unselected package icedtea-netx-common.
Unpacking icedtea-netx-common (from .../icedtea-netx-common_1.2-2ubuntu1_all.deb) ...
Selecting previously unselected package icedtea-netx.
Unpacking icedtea-netx (from .../icedtea-netx_1.2-2ubuntu1_amd64.deb) ...
Selecting previously unselected package icedtea-7-plugin.
Unpacking icedtea-7-plugin (from .../icedtea-7-plugin_1.2-2ubuntu1_amd64.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Setting up oracle-java7-installer (7u3-0~eugenesan~precise4) ...
Downloading...
--2012-04-28 19:20:24--  http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz
Resolving download.oracle.com (download.oracle.com)... 184.84.252.223, 184.84.252.224
Connecting to download.oracle.com (download.oracle.com)|184.84.252.223|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz [following]
--2012-04-28 19:20:24--  https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz
Resolving edelivery.oracle.com (edelivery.oracle.com)... 184.87.134.174
Connecting to edelivery.oracle.com (edelivery.oracle.com)|184.87.134.174|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://download.oracle.com/errors/download-fail-1505220.html [following]
--2012-04-28 19:20:25--  http://download.oracle.com/errors/download-fail-1505220.html
Connecting to download.oracle.com (download.oracle.com)|184.84.252.223|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5307 (5.2K) [text/html]
Saving to: `./jdk-7u3-linux-x64.tar.gz'

     0K .....                                                 100%  520M=0s

2012-04-28 19:20:25 (520 MB/s) - `./jdk-7u3-linux-x64.tar.gz' saved [5307/5307]

Download done.
sha256sum mismatch jdk-7u3-linux-x64.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up openjdk-7-jre (7~u3-2.1.1~pre1-1ubuntu2) ...
Setting up icedtea-netx-common (1.2-2ubuntu1) ...
Setting up icedtea-netx (1.2-2ubuntu1) ...
update-alternatives: using /usr/lib/jvm/java-6-openjdk-amd64/jre/bin/javaws to provide /usr/bin/javaws (javaws) in auto mode.
Setting up icedtea-7-plugin (1.2-2ubuntu1) ...
Errors were encountered while processing:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by darkod on 2012-04-28
It's the same error. The installation of oracle-java7-installer is somehow broken, and until it finishes it gives the error. But I don't know enough to suggest a solution.

Maybe someone else will jump in. And try googling about "error installing package in ubuntu" or similar, maybe you will find a way to remove this.

---

### Post by Ericj1186 on 2012-04-29
Here's how I fixed it:

I ran all these commands:
```

sudo rm /var/lib/dpkg/info/oracle-java7-installer*
sudo apt-get purge oracle-java7-installer*
sudo rm /etc/apt/sources.list.d/*java*
sudo apt-get update
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer

```

Then, I tested it with these:
```

sudo apt-get update
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove

```

Finally, I uninstalled a program and reinstalled it. All was well. Before I did this fix, I was running into "Package operation fail" errors when I tried to install or remove an item, but it'd install or remove fine. I also passed the Java verify applet.

[Source 1]("http://askubuntu.com/questions/126372/sha256sum-mismatch-jdk-7u3-linux-x64-tar-gz-error-when-trying-to-install-orac"), [Source 2]("http://askubuntu.com/questions/54851/package-operation-failed-when-installing-software")

---

### Post by astrand on 2012-04-29
I was having exactly the same problem.  I followed the previous post's approach and it solved the problem for me as well.  I'm now up and running with Java.
Thanks

---

### Post by datenhalde on 2012-06-18
> **jerome1232 said:**
> First try OpenJDK and Icedtea

```
sudo apt-get install icedtea-plugin
```


Doesn't work for me. FF13 on Precise doesn't seem to recognize the plugin. 
A symlink in /usr/lib/mozilla/plugins/ points to /etc/alternatives: 

libjavaplugin.so -> /etc/alternatives/mozilla-javaplugin.so

Which points to: 

/etc/alternatives/mozilla-javaplugin.so -> /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so

Does this work for anyone?

---

