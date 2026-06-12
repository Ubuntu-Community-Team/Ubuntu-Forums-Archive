---
title: "JDK manual install"
date: 2010-06-03
forum: Installation &amp; Upgrades
---

### Post by ubun2warrior on 2010-06-03
I have downloaded the jdk-6u20-linux-i586.bin from their website. I also read the instruction given to install jdk manually but i was not able to run a single program. Can someone give a step by step instruction to install jdk and also tell me how to set the path so i can easily execute the programs.

---

### Post by derekeverett on 2010-06-03
How come you don't want to just install java from the repos? It's a lot easier...

Or if your interested in an IDE Eclipse is in the repos and is easy to use.

---

### Post by wojox on 2010-06-03
Try this [http://wojox.homelinux.org/?p=78](http://wojox.homelinux.org/?p=78)

---

### Post by abhishek.malhotra35 on 2010-06-03
For installation, chmod 777 jdk-6u20-linux-i586.bin. Then do ./jdk-6u20-linux-i586.bin.

This will start the installation. Select the location where you want to install.

For Path and classpath do:
export PATH=$PATH:<installation_dir>/bin;
export CLASSPATH=$CLASSPATH:/<installation_dir>/lib;

---

### Post by ubun2warrior on 2010-06-03
Hi abhishek

I did as you said. Then i tried to compile a program and the following error shows:

The program 'javac' can be found in the following packages:
 * openjdk-6-jdk
 * ecj
 * gcj-4.4-jdk
 * gcj-4.3
Try: sudo apt-get install <selected package>

Regards

---

### Post by abhishek.malhotra35 on 2010-06-03
I am assuming that your installation went well. Can you please post the results of following commands:
echo $PATH
echo $CLASSPATH

Also, can you please post the path where java got installed.

---

### Post by lykeion on 2010-06-03
Do you get a line starting with 'java-6-sun' if you try this command:```
update-java-alternatives --list
```If so you can set it to that like this:```
sudo update-java-alternatives --set java-6-sun
```

---

### Post by ubun2warrior on 2010-06-05
echo $PATH:
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
echo $CLASSPATH

in echo classpath it does not display anything

---

### Post by ubun2warrior on 2010-06-05
this is the path where java got installed


/home/comp1/jdk1.6.0_20

---

### Post by ubun2warrior on 2010-06-05
I also wanted to know , how can i uninstall jdk and do a fresh install i can try that as well. But i am unable to uninstall jdk
please help??

---

