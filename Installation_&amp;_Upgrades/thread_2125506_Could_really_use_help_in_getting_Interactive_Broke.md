---
title: "Could really use help in getting Interactive Brokers TWS software to work!"
date: 2013-03-14
forum: Installation &amp; Upgrades
---

### Post by PacoDeGato on 2013-03-14
I'm quite new to Ubuntu, and although I've searched and tried to follow the instructions on how to get TWS to work (either the web based OR the stand-alone version), I just cannot get it to open.

I originally installed the newest java from the Software Center, and, at least for the web based launch, I could get the log in applet to open up. However, it gave me an error about not being able to find certain .jar files in the classpath after I entered my credentials.

As far as the stand-alone version of TWS, I didn't even get that far.

All of the instructions I found from people who had these problems earlier were from at least a few years ago, so maybe something has changed.

If someone can help me to get this to work (I usually just use the web-launched version of TWS on my Windows machine), I'd appreciate it, as I'd like to move completely to Ubuntu.

If it helps, I have installed the 64 Bit version of the 12.10.

Thanks,

PDG

---

### Post by sdnian on 2013-03-14
Check the page - [http://www.interactivebrokers.com.hk/en/index.php?f=674&os=unix](http://www.interactivebrokers.com.hk/en/index.php?f=674&os=unix)
Download TWS standalone and follow the 4 step.. This's all you need.

---

### Post by chexxer42 on 2013-08-11
> **sdnian said:**
> Check the page - [http://www.interactivebrokers.com.hk/en/index.php?f=674&os=unix](http://www.interactivebrokers.com.hk/en/index.php?f=674&os=unix)
Download TWS standalone and follow the 4 step.. This's all you need.


Didn't work for me? for beginners I think it needs a bit more info.

In (1) download file into "Home" directory or move in to "Home" if it automatically downloads to "Downloads". Also note the file name, as you may find it's "unixmacosx_latest.jar"

In (2) run Terminal (Ctrl-Alt-T), create directory "mkdir IBJts",  then type "ls" to check the file is in the current directory/folder, if it is then run "jar xf unixmacosx.jar" or "jar xf unixmacosx_latest.jar " as appropriate. You might need to install "OpenJDK Java & Runtime" before this will work. I installed it but I still needed to run "sudo apt-get install fastjar" before it ran without errors

Then (3) and (4) should run OK.


To create a short cut I used something posted by mitsugiri on August 19th 2010 and disentropy on April 28th 2011 with slight modifications using "gedit" and saved it to the desktop

#!/bin/bash
#Run IB TWS
#Created 2010-08-19

cd /home/yourusername/IBJts/
java -cp jts.jar:hsqldb.jar:jcommon-1.0.12.jar:jfreechart-1.0.9.jar:jhall.jar:eek:ther.jar:rss.jar -Xmx512M jclient.LoginFrame .


Haven't been able to get "Launcher' working, but giving the saved file "Execute" permissions in properties, allows me to double click the desktop icon and then select "Run in Terminal" on the Pop-Up to work.

---

