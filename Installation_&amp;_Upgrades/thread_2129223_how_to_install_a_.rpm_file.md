---
title: "how to install a .rpm file"
date: 2013-03-25
forum: Installation &amp; Upgrades
---

### Post by amitshree on 2013-03-25
i dont know how to install a file. I have downloaded [ jdk-6u43-linux-i586-rpm.bin    ]("http://download.oracle.com/otn-pub/java/jdk/6u43-b01/jdk-6u43-linux-i586-rpm.bin")from oracle.com.Please guide me how to install it using terminal.

---

### Post by Cheesemill on 2013-03-25
First of all delete that file. RPM files are for Red Hat or Fedora machines, not for Ubuntu.

Then install Java by typing the following commands into a terminal...
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```

---

### Post by amitshree on 2013-03-25
but i want to install java6. Is there any way to install it.

---

### Post by Cheesemill on 2013-03-25
You can replace oracle-java7-installer with oracle-java6-installer in the above command.

Is there any particular reason you need version 6, it reached end-of-life in February and won't be getting any more updates.
From a security point of view it's much safer to be using 7.

---

### Post by amitshree on 2013-03-25
yes, i am following moziila wiki to build a platform for android development where it is recommended. [https://wiki.mozilla.org/Mobile/Fennec/Android#Building_Fennec](https://wiki.mozilla.org/Mobile/Fennec/Android#Building_Fennec)

---

### Post by amitshree on 2013-03-25
i have also installed** oracle-java6-installer**
but why this command is not working
sudo apt-get install sun-java6-jdk mercurial ccache

---

### Post by Cheesemill on 2013-03-25
Try this instead...
```
sudo apt-get install mercurial ccache
```

The sun-java6-jdk package isn't in the repositories anymore due to licensing issues. But you don't need it anyway as you have already install Java with the commands I gave you earlier.

---

