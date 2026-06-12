---
title: "Java JRE 6.0 and Firefox 3.6 Apparently Incompatible?"
date: 2010-08-28
forum: Installation &amp; Upgrades
---

### Post by jimbo2907 on 2010-08-28
Hi Folks....thank you for taking the time and trouble to help us noobs.

I installed Ubuntu 5 days ago....looked great....seemed to offer everything I want.

Then I clicked on the firefox icon and it brought up Google ...Great!....Then I said ..this is easy..I'll have a look at my share-trading dynamic platform. Searched for Commsec and clicked 'launch Webiress'...and then it hiccupped!

I got a message saying I needed Java "Now downloading".....Okay I've had this happen in windows...no problemo.. Then I tried to follow the instructions contained on the download page from Java....thats what started my five days (30 hours now and counting) of misery.:sad:

Finally on one of the hundreds of Ubuntu pages I've read I found that there is a bug in java....that prevents it from working with the Firefox that Ubuntu provides.

So I cleverly removed firefox ....and went to Mozilla and downloaded a new version 3.6 of Firefox.....followed the instructions at Sourceforge.net (and other places I can't remember). Now I have Firefox in a folder in 'Documents' with libjavaplugin_oji.so linked to ///java/jre.6.0_21/plugin/i386/ns7...

  But when I try to fire up Webiress I still get the messsage "Java not installed ...now downloading". 

Can anyone tell me what I've done wrong please?   Cheers

---

### Post by mikewhatever on 2010-08-28
What version of Ubuntu do you have? As far as I know, all supported versions of Ubuntu (8.04 - 10.04) had Firefox upgraded to version 3.6. All you have to do to get it is install updates.
Sun's java is available from the partner repository, all nicely packaged and easy to install.
Browsing sites and manually downloading and installing software is the way it's done in Windows, but Ubuntu is not Windows.
[https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Canonical%20Partner%20Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Canonical%20Partner%20Repositories)

---

### Post by Oxwivi on 2010-08-28
I suggest you make a clean install to remove all the fudge you may've gotten while dealing with those crap you mentioned.

Add the partner repository like it's mentioned in this link: [https://help.ubuntu.com/community/Re...20Repositories]("https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Canonical%20Partner%20Repositories")

Then go to Terminal and run:

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

---

### Post by jimbo2907 on 2010-08-28
Thank you guys.
I did the clean instal and followed the link to get repositories ....then ran the code you suggested Oxwivi....
but the license agreement stopped at this window:
Package configuration

 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring sun-java6-jre &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           &#9474; 
 &#9474; Operating System Distributor License for Java v1.1 (DLJ)                  &#8593; 
 &#9474;                                                                           &#9646; 
 &#9474; Operating System Distributor License for Java version 1.1 (DLJ)           &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; SUN MICROSYSTEMS, INC. ("SUN") IS WILLING TO LICENSE THE JAVA PLATFORM    &#9618; 
 &#9474; STANDARD EDITION DEVELOPER KIT ("JDK" - THE "SOFTWARE") TO YOU ONLY UPON  &#9618; 
 &#9474; THE CONDITION THAT YOU ACCEPT ALL OF THE TERMS CONTAINED IN THIS LICENSE  &#9618; 
 &#9474; AGREEMENT (THE "AGREEMENT").  PLEASE READ THE AGREEMENT CAREFULLY.  BY    &#9618; 
 &#9474; INSTALLING, USING, OR DISTRIBUTING THIS SOFTWARE, YOU ACCEPT ALL OF THE   &#9618; 
 &#9474; TERMS OF THE AGREEMENT.                                                   &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; 1.  DEFINITIONS. "Software" means the code identified above in binary     &#9618; 
 &#9474;     form, any other machine readable materials including, but not         &#9618; 
 &#9474;     limited to, libraries, source files, header files, and data files),   &#8595; 
 &#9474;                                                                             
 &#9474;                                  <Ok>                                       

and it wouldn't let me click 'ok'          does that mean its ok or not?       oh well I'll try it...

---

### Post by jimbo2907 on 2010-08-28
Nope ...I can't close that window..it says it will kill the process......So I killed it..and tried to run the command line code again..and it says
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
jim@tkeubtu:~$

---

### Post by Cavsfan on 2010-08-28
Check out the links in my signature for future reference.
The one checks your Java version and the other provides instructions on how to update your Java.

You might be interested in the GRUB tutorial too.

---

### Post by jimbo2907 on 2010-08-28
Thank you Cavsan...shall do..:)

---

### Post by mikewhatever on 2010-08-29
There should be a text prompt letting you to agree to or decline the agreement by pressing y/n keys. Try scrolling to the bottom of the agreement.
The error you got says that another program is using the package manager. It could be Synaptic or the Update manager. In short, close all open windows and try the command again.

---

### Post by bjchip on 2010-08-29
Don't know why but no matter what is done with the plugin lib, it is ignored entirely.  The system insists on installing iced-tea.  I am not exactly pleased, but I am also not entirely sure this has anything to do with Ubuntu.   Issues with Java plugins are not exactly unknown, but the fact that I can't aim firefox at the plugin I want and tell it to use thing.... that doesn't seem to me to be a problem with ubuntu. 

Just saying.... I am going over to Mozilla now to see whether raising some hell with them makes any sense. 

BJ

---

### Post by jcolyn on 2010-08-29
If you do a clean install of Ubuntu wipe the drive first then install. After you reboot go to the terminal and type ```
sudo apt-get update
``` once done go to update manager and update your system.

Reboot then at the terminal enter ```
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6 plugin
``` During the install you will be prompted to agree to sun's EUL

Once done everything should work fine..

---

### Post by Innigo on 2010-09-01
There was a change in Firefox3.6 that broke jre6 but I did get Java version 6 update 2 to work for me. OpenJDK and IcedTea were in my new install of 10.04, apparently by default but they didn't give me a working java plugin in Firefox. I followed instructions at [http://ubuntuforums.org/showthread.php?t=1556276&highlight=firefox+java+plugin](http://ubuntuforums.org/showthread.php?t=1556276&highlight=firefox+java+plugin) which is marked [SOLVED] 

Although the advice from anieruddha is more in accordance with traditional Unix methods and presumably resembles what Synaptic (or apt-get) does for you in the background, it didn't work for me.  The Oracle/Sun site gives similar advice for Linux versions not using RPM. I downloaded jre-6u21-linux-i586.bin and tried extracting it in both my home and /opt but even after much sudo ln -s in various locations it still didn't work.

However, when I simply marked IcedTea plugin for removal in Synaptic and enabled the partner repo for lucid in the Other Software tab, Synaptic told me two other dependencies were also to be installed, namely sun-java6-bin and sun-java6-jre were to be installed. All three are v. 6.20dlj-1unbuntu3 ie. one version back from jre-6u21 but after restarting firefox, advice from lykeion seems to have worked whereas the more manual method has not and I seem to be running 6.20 with an inactive 6.21 still there.
I might remove it because the sun-java6-bin seems to have been put in /usr/lib rather than /opt so I'm thinking if I need the full JDK, I'll just get it from the partner repo and it'll go in there too.

---

### Post by Cavsfan on 2010-09-02
> **Innigo said:**
> There was a change in Firefox3.6 that broke jre6 but I did get Java version 6 update 2 to work for me. OpenJDK and IcedTea were in my new install of 10.04, apparently by default but they didn't give me a working java plugin in Firefox. I followed instructions at [http://ubuntuforums.org/showthread.php?t=1556276&highlight=firefox+java+plugin](http://ubuntuforums.org/showthread.php?t=1556276&highlight=firefox+java+plugin) which is marked [SOLVED] 

Although the advice from anieruddha is more in accordance with traditional Unix methods and presumably resembles what Synaptic (or apt-get) does for you in the background, it didn't work for me.  The Oracle/Sun site gives similar advice for Linux versions not using RPM. I downloaded jre-6u21-linux-i586.bin and tried extracting it in both my home and /opt but even after much sudo ln -s in various locations it still didn't work.

However, when I simply marked IcedTea plugin for removal in Synaptic and enabled the partner repo for lucid in the Other Software tab, Synaptic told me two other dependencies were also to be installed, namely sun-java6-bin and sun-java6-jre were to be installed. All three are v. 6.20dlj-1unbuntu3 ie. one version back from jre-6u21 but after restarting firefox, advice from lykeion seems to have worked whereas the more manual method has not and I seem to be running 6.20 with an inactive 6.21 still there.
I might remove it because the sun-java6-bin seems to have been put in /usr/lib rather than /opt so I'm thinking if I need the full JDK, I'll just get it from the partner repo and it'll go in there too.

I will guarantee the link in my signature will work. The 32 bit instructions are on the left and the 64 bit instructions are on the right.
It supplies every command you need; you just copy and paste. I did a clean install several days ago of 10.04.1 and I didn't have Java so,
The removal instructions did nothing, but everything else went flawlessly.
Sometimes you have to change the version to match the recent one, but they usually keep it up to date.

---

