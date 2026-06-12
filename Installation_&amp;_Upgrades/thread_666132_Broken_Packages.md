---
title: "Broken Packages"
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by K-Mode on 2008-01-13
Hey, so i use this guide ([http://ubuntuforums.org/showthread.php?t=148075](http://ubuntuforums.org/showthread.php?t=148075)) to install JRE, but instead i used the jre-6u4-linux-i586.bin file. after following what it said, everything seemed like it went fine. in the end it seemed like it was installed, but when i did "java -version" it didnt show anything about JRE.

Now im trying to install it in different ways and it says i have broken packages. i just switched to ubuntu to see how it is, so  i dont know anything btw. I probably havent given enough info, but how can i go about fixing the problem?

---

### Post by ForumTroll on 2008-01-13
Try opening up synaptic package manager...i.e. goto the menu or type
> sudo synaptic into a terminal.

Click on edit i think and then "fix broken packages" do this agian and again until the message dissapears. Usually twice depending on your repos.

Also make sure that you do not have any terminals open as this can interfere.

After that i am out and would need to have a think...let me know how you get on.

---

### Post by PmDematagoda on 2008-01-13
You can also execute:-
```
sudo apt-get install -f
```
which will handle the broken packages automatically.

---

### Post by K-Mode on 2008-01-13
> **ForumTroll said:**
> Try opening up synaptic package manager...i.e. goto the menu or type
 into a terminal.

Click on edit i think and then "fix broken packages" do this agian and again until the message dissapears. Usually twice depending on your repos.

Also make sure that you do not have any terminals open as this can interfere.

After that i am out and would need to have a think...let me know how you get on.

So i tried what both of you said to do, and when i tried "sudo apt-get install sun-java6-jre sun-java6-plugin" i got this:
```
K-Mode@K-Mode-Laptop:~$ sudo apt-get install sun-java6-jre sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sun-java6-jre: Depends: java-common (>= 0.24) but it is not installable
                 Depends: sun-java6-bin (= 6-03-0ubuntu2) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-03-0ubuntu2) but it is not installable
  sun-java6-plugin: Depends: sun-java6-bin (= 6-03-0ubuntu2) but it is not going to be installed
E: Broken packages

```


**Edit: i fixed it. i removed the files and folders i installed before, check marked "oficcially supported" and "restricted copyright" along w/ universe and multiverse. Tried "sudo apt-get install sun-java6-jre sun-java6-plugin" again and it worked. Thanks.**

---

