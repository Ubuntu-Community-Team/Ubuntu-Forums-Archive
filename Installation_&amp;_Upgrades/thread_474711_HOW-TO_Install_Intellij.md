---
title: "HOW-TO Install Intellij"
date: 2007-06-15
forum: Installation &amp; Upgrades
---

### Post by htaylor on 2007-06-15
These are the few steps that I took to initially get 
IntelliJ up and running.

If you have not downloaded a JDK, then do the following:
In your browser, google for 'jdk 6 download'
You should see one of more links for Download - Center
I chose the one for jdk-6.
Once you've downloaded it to your desktop, move the file 
to where you want it to live.  

For example (from your home directory):
> cd Desktop
> mv jdk-6-linux-i586.bin /usr/java
> cd /usr/java
> chmod +x jdk-6-linux-i586.bin
> ./jdk-6-linux-i586.bin

It should create the directory, jdk1.6.0

Once you've downloaded intelliJ, 
move it from the desktop to the
directory where you want it to live and
do the following steps below:

To unpack IDEA into current directory.
% tar -xzvf idea-6.0.5.tar.gz

To set environment variable IDEA_JDK, you can
do it in IDEA_HOME/bin/idea.sh script, like:

IDEA_JDK=/usr/java/jdk1.6.0

Now you should be able to run IDEA using idea.sh script.
cd to your idea/bin directory and type ./idea.sh

---

### Post by brampintelon on 2008-05-05
I have installed IntelliJ and it is working, but now I have to choose wich JDK I have installed, but where is it located? I know it's a n00bisch question, but I'm an absolute beginner in Linux.

I'm using the latest (Hardy Heron) Kubuntu. For what it's worth, I have also installed BlueJ and that's working fine.

Best regards,

Bram Pintelon

---

