---
title: "Trouble with JAVA_HOME"
date: 2010-01-08
forum: Installation &amp; Upgrades
---

### Post by whitetimer on 2010-01-08
Hi All

I have just done a minimal install ;) and i have just installed java 6 update 17 form the sun website, but i am having trouble settings the JAVA_HOME stuff

When i type java -version i get 

> The program 'java' can be found in the following packages:
 * gcj-4.4-jre-headless
 * openjdk-6-jre-headless
 * cacao
 * gij-4.3
 * jamvm
 * kaffe
Try: sudo apt-get install <selected package>
java: command not found

I have done this in ~/.profile

> export JAVA_HOME=$HOME/usr/lib/jvm/jdk1.6.0_17
export PATH=$PATH:$JAVA_HOME/bin

What else am i supposed to do ?

Many Thanks

Whitetimer

---

### Post by Mighty_Joe on 2010-01-08
> **whitetimer said:**
> $HOME/usr/lib/jvm/jdk1.6.0_17

Did you really install Java to your home directory?  *Interesting* choice.  
Does the directory really exist?  Does the bin subdirectory really exist?
Perhaps starting fresh would be a good idea.  Have a look at [this tutorial]("http://sites.google.com/site/easylinuxtipsproject/java").

---

### Post by whitetimer on 2010-01-08
> **Mighty_Joe said:**
> Did you really install Java to your home directory?  *Interesting* choice.  
Does the directory really exist?  Does the bin subdirectory really exist?
Perhaps starting fresh would be a good idea.  Have a look at [this tutorial]("http://sites.google.com/site/easylinuxtipsproject/java").

Hi Mighty Joe

No i have not installed Java to my home directory its in

> /usr/lib/jvm folder

Where the synaptic version is installed, i was just trying to install the latest version 
:(

---

### Post by whitetimer on 2010-01-08
Sorted it :)

---

### Post by SecretCode on 2010-01-08
I presume you sorted it by removing $HOME from the JAVA_HOME line?

Post the details for everyone's benefit :)
and mark the thread SOLVED (under thread tools)! :wink:

---

### Post by whitetimer on 2010-01-15
Hi ... Ok this is how i resolved the issue with java

1) First i installed 
sudo install sun-java6-jre sun-java6-jdk sun-java6-plugin sun-java6-fonts

2) Then i installed the latest sun-jdk jdk-6-update-17
chmod +x {JAVA-VERSION}
then
sudo sh ./{JAVA-VERSION}
sudo cp {extracted JAVA-VERSION} to /usr/lib/jvm/

3) Make the new JRE the default
sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm/{JAVA VERSION}/jre/bin/java" 1

4) sudo update-alternatives --set java /usr/lib/jvm/{JAVA VERSION}/jre/bin/java

Thats all i did and everything is working great

Hope it helps other noobs like me ...

---

