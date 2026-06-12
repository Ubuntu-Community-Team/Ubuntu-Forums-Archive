---
title: "setting up minecraft server---where's the java?"
date: 2012-09-08
forum: Installation &amp; Upgrades
---

### Post by jessepage1989 on 2012-09-08
been trying to set up a minecraft server on xubuntu. Originally tried on ubuntu server but i have one screen and keyboard so switching between compubters is a pain to look up. I can't seem to find a cut and try method of getting the appropriate java install. Every method I've seen and tried yeilds no java. Why is this so complicated? I feel like stealing movies is easier than installing the correct java the ubuntu has removed for its source list.

---

### Post by mikeyxote on 2012-09-08
When I put Hadoop on my Ubuntu install(11.4) the tutorial recommended pulling java from Ferramosca Roberto's repository.  I've been able to use this with minecraft client(ubuntu 11.4, xubuntu 11.4) and server(xubuntu 11.4).

Here are the command line instructions they posted:

# Add the Ferramosca Roberto's repository to your apt repositories
# See [https://launchpad.net/~ferramroberto/](https://launchpad.net/~ferramroberto/)
#
$ sudo apt-get install python-software-properties
$ sudo add-apt-repository ppa:ferramroberto/java

# Update the source list
$ sudo apt-get update

# Install Sun Java 6 JDK
$ sudo apt-get install sun-java6-jdk

# Select Sun's Java as the default on your machine.
# See 'sudo update-alternatives --config java' for more information.
#
$ sudo update-java-alternatives -s java-6-sun

Then you check version etc thus:

user@ubuntu:~# java -version
java version "1.6.0_20"
Java(TM) SE Runtime Environment (build 1.6.0_20-b02)
Java HotSpot(TM) Client VM (build 16.3-b01, mixed mode, sharing)

Hope that helps!

---

### Post by jessepage1989 on 2012-09-08
when i run sudo apt-get install sun-java6-jdk i get
```
apt-get install sun-java6-jdk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jdk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'sun-java6-jdk' has no installation candidate

```

---

### Post by mikeyxote on 2012-09-08
You can start by two things to make sure that the repository has been added:
-check /etc/apt/sources.list to see if it appears there with the correct release
-sudo apt-get update - to ensure that the repository will be checked with the install command.

I see on the minecraft wiki page the following instructions:

cd ~/
wget [https://raw.github.com/flexiondotorg/oab-java6/master/oab-java.sh](https://raw.github.com/flexiondotorg/oab-java6/master/oab-java.sh) -O oab-java.sh
chmod +x oab-java.sh
sudo ./oab-java.sh
If you want to watch progress, just run
tail -f ./oab-java.sh.log
Then, once the script has finished, run
sudo apt-get install sun-java6-jre

Are these the instructions you started with?  If not, you can give those a shot too.  

Good luck!

---

