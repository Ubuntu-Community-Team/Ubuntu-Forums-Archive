---
title: "Upgrading your JDK"
date: 2008-06-17
forum: Installation &amp; Upgrades
---

### Post by sh!ft on 2008-06-17
Eh, I'm sure there's better ways... But this is just my solution, comment/correct as you feel necessary. I'm sure theres several ways to reach the same end.



It seems the repository is a fair bit out of date, and if you're a java junkie like myself, this bothers you... Especially because of all the new functionality in the beta releases lately.

The main bonus in the new JVM's is the fix for the heapspace. In the repository version, you can't go above a 768mb heapspace without getting bugs on some systems for no apparent reason... Supposedly this has been resolved. At least, upgrading fixes it for me :) (yay).

So, after I looked at the deb install file I came up with this solution and decided to share it.

**Prerequisite**
You need to install the java development kit from repository... 
```
sudo apt-get install sun-java6-jdk
```

**Step1:**
Visit [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp), click download on the "Update x beta" or whatever version you want, and navigate through your system information until you get your bin file... Not the RPM remember we're a Debian distribution, we WILL NOT use red hat package managers.

**Step2:**
Once it's downloaded, navigate to the directory in a terminal and extract it by doing:
```
sh jdk-VERS-beta-linux-ARCH.bin
```
Of course replacing VERS and ARCH accordingly. (ie. "sh jdk-6u10-beta-linux-x64.bin")

Navigate through the license... You should probably read that but in case you just don't care, type "yes" and hit enter to skip it.

**Step3:**
If you've done everything right to here, you should now have a folder in the downloaded directory that's "jdkVERSION" or in my example case "jdk1.6.0_10"

We need to move this to a globally accepted place. (/usr/lib/jvm/)
```
sudo mv jdkVERSION /usr/lib/jvm/
```

Navigate to the jvm folder...
```
cd /usr/lib/jvm/
```

Delete the old symbolic link...
```
sudo rm java-6-sun
```

Add the new link to our fresh java:
```
sudo ln -s jdkVERSION java-6-sun
```

**COMPLETE**

To verify the installation: 
```
java -version
```

It should now say whatever version you installed.

---

