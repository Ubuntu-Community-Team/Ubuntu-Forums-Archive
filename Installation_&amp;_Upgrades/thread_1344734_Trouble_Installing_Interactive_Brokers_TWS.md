---
title: "Trouble Installing Interactive Brokers TWS"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by pablosanchez on 2009-12-03
Hi all,

First I'll state that I'm a complete noob and just trying out ubuntu as I've had about enough of Windows, and trying to move my daytrading items across to ubuntu. 

I'm trying to run the software below in the standalone version. 

[http://www.interactivebrokers.com/en/p.php?f=tws](http://www.interactivebrokers.com/en/p.php?f=tws)

I've got all the jave reqs. (i think...), but can't seem to install as per the IB instructions

Could anyone point me in the right direction, any help would be much appreciated.

cheers,

pablo

---

### Post by marbss on 2009-12-26
I'm still looking for a solution myself.  

Trying to figure out how to install the stand alone version - the web version works fine in ubuntu 9.10.

going to search the forums at elitetrader.com....  pls let me know if you find a solution.

....
google "TWS linux"  or "TWS ubuntu site:elitetrader.com"  no time left to check for today.

---

### Post by marbss on 2009-12-28
first make sure java is installed...  other than that the only thing I can get running is TWS Web.  

[http://squidoptions.com/2007/03/26/installing-ib-tws-on-linux/](http://squidoptions.com/2007/03/26/installing-ib-tws-on-linux/)



here's the IB forums. [https://www.interactivebrokers.com/smf/index.php?action=search2](https://www.interactivebrokers.com/smf/index.php?action=search2)


If anyone has the installation instructions for the standalone Unix TWS for Ubuntu.  Please post.

---

### Post by mitsugiri on 2010-08-03
I know this is very belated but did you figure out the solution? If not I recently went through this and I can post the solution if you want to get the standalone TWS app working on Ubuntu.

---

### Post by TraderLars on 2010-08-18
Mitsugiri, would you mind posting that TWS + Ubunu solution please.

Thanks

---

### Post by mitsugiri on 2010-08-18
Here's a step by step:

1. Make sure that you have a recent version of Java Runtime Environment installed.  
2. Go to [http://www.interactivebrokers.com/en/control/systemstandalone.php?os=unix&ib_entity=llc](http://www.interactivebrokers.com/en/control/systemstandalone.php?os=unix&ib_entity=llc) and download the standalone app for unix.
3. Create a folder called "TWS" or "IB" or whatever you want in your home directory.
4. Find and right click the downlaoded file called "unixmacosx.jar" and select "Open with Archive Manager"
5. Select the two folders "IBJts" and "META-INF" and select extract
6. Navigate to the folder you just created in step 3 and extract the folders there.
7. Open up a terminal window and change directory to the folder where your IB files reside. e.g. "cd TWS" or "cd IB"
8. Change directory to the IBJts folder, "cd IBJts"
9 Then type ```
java -cp jts.jar:hsqldb.jar:jcommon-1.0.12.jar:jfreechart-1.0.9.jar:jhall.jar::KSother.jar:rss.jar -Xmx512M jclient.LoginFrame .
``` including the period at the end and you should get the login page.
10. Henceforth to launch TWS you have to follow steps 7-9.

---

### Post by TraderLars on 2010-08-18
Hey Thanks, that works really well. I wondering if you could point me to a text that describes how to create a graphic shortcut with that startup code. I have been using Ubuntu 10 for a total of 1 day and I must say.... it's amazing! I've permanently switched over!

Best Regards,

Lars

---

### Post by mitsugiri on 2010-08-19
1. First right click on your desktop and create a new file.
3. Rename the file to anything you like.
2. Enter the following code to that file and save it.
```
#!/bin/bash
#Run IB TWS
#Created 2010-08-19

cd IB
cd IBJts
java -cp jts.jar:hsqldb.jar:jcommon-1.0.12.jar:jfreechart-1.0.9.jar:jhall.jar:other.jar:rss.jar -Xmx512M jclient.LoginFrame .

```
4. Right click on the file and go to properties. Under Permissions, click the checkbox that says Allow executing file as a program
5. Close the properties box
6. Right click on the desktop and select Create Launcher
7. Select Application as Type. Enter "TWS" as Name and under Command, browse to the file you just created on the desktop, select it and hit OK.
8. This will create a launcher on the desktop.  Now you can just double click it to launch TWS.

To know more about bash script, just do a search here for it.

---

### Post by nauru on 2011-02-15
Hi thanks for these instructions.  First set works great for me.  However for creating the launcher, I've followed all those steps and the launcher does nothing when I double click it.  Both the launcher and the file I created are allowed to run as executable as per instructions.  Any idea how this might be fixed?  thx

---

### Post by nauru on 2011-04-01
Can anyone please help?

---

### Post by disentropy on 2011-04-28
try this in your launcher command:

```
sh /home/yourusername/IBJts/IBJts/IBlauncher.sh
```

then create IBlauncher.sh to look something like this and save it in the dir /home/yourusername/IBJts/IBJts/ + give it execute permission.

```
#!/bin/bash
#Run IB TWS
#Created 2010-08-19

cd /home/yourusername/IBJts/IBJts/
java -cp jts.jar:hsqldb.jar:jcommon-1.0.12.jar:jfreechart-1.0.9.jar:jhall.jar:other.jar:rss.jar -Xmx512M jclient.LoginFrame .
```

---

### Post by captainbodhi on 2012-03-10
> **nauru said:**
> Can anyone please help?

It did not work with me too, until I changed the Type (step 7 of the instruction) from Application to Application in terminal. This creates a launcher icon named TWS on your desktop. Double-click it and the terminal will open and the TWS Log-in screen appears after a few seconds.

---

### Post by deeperinits on 2013-01-29
Followed all the instructions and I'm able to open TWS, but for some reason the charts are not displaying! 

Has anyone experienced this problem?

Thanks

---

### Post by oldos2er on 2013-01-29
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

