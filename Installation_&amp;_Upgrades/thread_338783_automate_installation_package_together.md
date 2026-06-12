---
title: "automate installation package together"
date: 2007-01-14
forum: Installation &amp; Upgrades
---

### Post by voltage on 2007-01-14
Hi,

Currently I need to install apache tomcat5, but before i doing the sudo apt-get install the tomcat5, I have to install the JDK or JRE.

Normally, I have to install those package 1 by 1. But I found that is take too much of time to wait for 1 package complete then install another package.

So, do somebody know how to doing the package installation at the sametime by automate ? then i noneed to take too much of time.. 

Please Advice.
Thanks And Good Day.
Rg,
Frank Ong

---

### Post by aysiu on 2007-01-15
You can combine commands with *&&* so that one runs right after the other: ```
sudo apt-get update && sudo apt-get install sun-java5-bin -y && sudo apt-get install tomcat5 -y
``` I'm assuming Java is a dependency of *tomcat5*? If not, you can install the two together with one command: ```
sudo apt-get update && sudo apt-get install sun-java5-bin  tomcat5 -y
```

---

### Post by voltage on 2007-01-15
> **aysiu said:**
> You can combine commands with *&&* so that one runs right after the other: ```
sudo apt-get update && sudo apt-get install sun-java5-bin -y && sudo apt-get install tomcat5 -y
``` I'm assuming Java is a dependency of *tomcat5*? If not, you can install the two together with one command: ```
sudo apt-get update && sudo apt-get install sun-java5-bin  tomcat5 -y
```

Thanks. I will try ..

---

### Post by voltage on 2007-01-15
> **aysiu said:**
> You can combine commands with *&&* so that one runs right after the other: ```
sudo apt-get update && sudo apt-get install sun-java5-bin -y && sudo apt-get install tomcat5 -y
``` I'm assuming Java is a dependency of *tomcat5*? If not, you can install the two together with one command: ```
sudo apt-get update && sudo apt-get install sun-java5-bin  tomcat5 -y
```


From the previous command which have to type into the command line, so can it posible type every command into one text file then run those installation by using text file.

Thanks.

---

### Post by aysiu on 2007-01-15
> **voltage said:**
> From the previous command which have to type into the command line, so can it posible type every command into one text file then run those installation by using text file.

Thanks.
Yes. It's called a shell script. You can find an example of one here:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

The instructions for using it are on that site. When you download the script, don't follow the instructions, though. Open the script with a text editor, and you'll see how it works. Basically, the first line tells Ubuntu you're using a shell script. After that, everything is just a terminal command.

---

