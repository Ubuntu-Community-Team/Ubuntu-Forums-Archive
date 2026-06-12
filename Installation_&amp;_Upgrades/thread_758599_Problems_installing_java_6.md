---
title: "Problems installing java 6"
date: 2008-04-18
forum: Installation &amp; Upgrades
---

### Post by thor228 on 2008-04-18
hiya guys
I'm running a dual booting pc here with Win XP and ubuntu but recently a vital XP system file has become corrupted and I cannot be bothered to fix it (I could if I wanted to but really why bother fixing windoze piece of crap XP) so have now switched full-time to ubuntu, only one problem though- I am not the only person in this house to use this pc and my mum needs to use a particular Java applet for her work and i cannot get Java to work properly on Ubuntu.
I have been to the Java website and downloaded the Linux installer and followed the instructions and all seemed to be fine but when i tried to verify installation it said I had version 1.4.2 even though I had just installed version 6.5.
I have tried uninstalling and reinstalling many times using various different methods and same as before the installation seem to go fine but every time I try to verify installation the Java website tells me I have an outdated old version.
I have checked links in the firefox plugin directory and even redone the links just in case and I have turned on JavaScript and Java in firefox and i have tried removing all traces of 1.4 from my system but no matter what I try it keeps saying I have the wrong version.
I have tried using my mums Java applet for work myself and it misbehaves quite badly and is impossible to get any work done on it (unfortunately for legal and other reasons I cannot give out a link to this applet to see if any of you out there can get it to work)
if I cannot get this applet to work properly which I assume is due to the Java version then I will be forced to fix windblows XP and I don't want to do so as I love Linux)
PS. if any of you out there happen to have an AOL account then I may be able to give a link to the applet i am trying to get to work but obviously I won't be allowed to give out my mums password and such like for the applet itself (but if you can get to the applet and try typing some random letters and pressing enter then you will know if it's working or not (you'll have to contact me privately if you are willing to help and you have an AOL account))

---

### Post by ajgreeny on 2008-04-18
If you want the java runtime environment you can do that from the repositories.  Just make sure all the possible repositories are enabled in System>>Administration>>Software Sources and then search for **sun-java6-bin **and there it should be.  No need to download from the java website.

---

### Post by warp99 on 2008-04-18
Canonical, the sponsor of Ubuntu, has a business partnership with Sun Microsystems so all of the Java components including the build environment work properly and are readily available in the repositories so you don't need to go to any website and download Java. All of the packages for Sun Java are in the multiverse repository. 

Open the Synaptic package manager then go to Settings > Repositories > and tick the box marked multiverse, close then reload. Look for a file called sun-java6-bin and install that file. If it's already installed then reinstall it. After that open a terminal and issue the following command:

```
sudo update-alternatives --config java
```

and choose sun-java6 as your implementation. If you still have problems remove the older versions that you manually installed and repeat the steps.

---

### Post by thor228 on 2008-04-18
sorry guys, already solved my own problem by myself before i even got the chance to read any of your posts
took a lot of fiddling around.
basically there was something wrong with how the links were done so i just removed all java links from firefox plugins directory then redid then with sudu ln -s /blahblahblahwhatever/libjavaplugin_oji.so /usr/lib/firefox/plugins
thanks for the attempt to help anyway but too slow

---

