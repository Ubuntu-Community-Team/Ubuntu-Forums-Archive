---
title: "Installing Eclipse Ganymede"
date: 2008-07-30
forum: Installation &amp; Upgrades
---

### Post by yeuker on 2008-07-30
I am trying to install eclipse Ganymede on Ubuntu 8.04 but it doesnt seem to work.  Here is what I did:

- I downloaded the eclipse.tar.gz from the eclipse website into /home/cory/eclipse
# tar xzvf eclipse.tar.gz
# sudo mv eclipse /opt
# cd /opt/eclipse
# eclipse

Output: 

The program 'eclipse' is not installed.  You can install eclipse by typing sudo apt-get install eclipse.

Also, I have sun java installed and java -version works great (Java 1.6).  

# echo $JAVA_HOME
/usr/lib/jvm/java-6-sun

I dont want to install eclipse from the repository because I want Ganymede.  Can someone please help?  What am I missing?  Thanks so much,

Cory

---

### Post by yeuker on 2008-07-30
I figured it out.  I cant start eclipse from the command line.  If I navigate there from the desktop and double click on the eclipse icon, it works.  Anyone know why I cant start it from the command line?

---

### Post by fifth on 2008-07-30
you want to use ./eclipse on the command line to launch the app in your current folder. Just typing eclipse will attempt to launch an app from the system environment paths.

ie in this situation;

1. 'eclipse' will not work
2. '/home/user/some_folder/eclipse' will work
3. cd '/home/user/some_folder' followed by './eclipse' will work

---

