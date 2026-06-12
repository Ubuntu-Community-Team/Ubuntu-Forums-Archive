---
title: "Help a Xubuntu newb install java"
date: 2008-01-01
forum: Installation &amp; Upgrades
---

### Post by I_Love_Cheese on 2008-01-01
Good evening.

Can someone please give me step-by-step instructions in layman's terms how to download and install java?

I just installed Xubuntu 7.10 on a laptop with no OS.

I'm brand new to this, so any help with the actual download of the file, where to save, what to do, etc., would be greatly appreciated.

Thanks!

---

### Post by Partyboi2 on 2008-01-02
Open up "Software Sources" (Applications->System->Software Sources)
On the first tab make sure all are ticked except "Source Code"
close that.
Then open a terminal(applications>accessories>terminal)
then type
```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```(when you type your password you will not see it on screen)
It will start to install. It will ask for you to agree to license terms. Select Yes, and hit Enter.
After it has installed type in the terminal
```
java -version
```the output should look like this
> java version “1.6.0&#8243;
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)To check if it is enabled in firefox, open firefox and in the address bar type
```
about:plugins
```and check.
[http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html)
Or you can look through add/remove (Applications->System->Add/Remove)
Do a search for Java

---

### Post by I_Love_Cheese on 2008-01-02
Thanks Partyboi, I'll give it a shot.

---

### Post by I_Love_Cheese on 2008-01-02
After the first step (sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts) I get the following:

"Some package information could not be insstalled.  This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming."

"The following packages have unmet dependencies:
sun-java6-jre: Depends: java-common (.= 0.24) but it is not installable
                        Depends: sun-java6-bin (= 6-03-0ubuntu2) but it is not going to be installed 

Holy craps! Now what?

---

### Post by Partyboi2 on 2008-01-02
In "Software Sources" try changing the download server to a different one and see what happens. 
If that does not work, what is the output for this terminal command
```
sudo apt-get update
```

---

