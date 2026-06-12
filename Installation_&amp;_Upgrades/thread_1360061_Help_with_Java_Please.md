---
title: "Help with Java Please"
date: 2009-12-20
forum: Installation &amp; Upgrades
---

### Post by whitetimer on 2009-12-20
Hi All

This is my first step into using Linux having given up on Windows. I have just installled Ubuntu (and love it so far), but now i am having real difficulties installing Java JDK & JRE

I have searched the forum and online, tried a few things and it does not seem to want to work ... I would like to install jdk6 update 17 from Sun.

Would someone please be able to explain to me what i need to do to achieve this goal

Many Thanks

Whitetimer :(

---

### Post by Cheesemill on 2009-12-20
```
sudo apt-get install sun-java6-jre sun-java6-sdk
```

---

### Post by oldos2er on 2009-12-20
There are instructions here: [http://www.java.com/en/download/help/5000010500.xml](http://www.java.com/en/download/help/5000010500.xml)

The only thing you need to do differently is to run **sudo -i** instead of **su**. Because Ubuntu disables the root account, su won't work on Ubuntu.

Just FYI, you'll want to download the self-extracting binary.

I'm assuming you're aware that a slightly older version of Java is in the repositories.

---

### Post by whitetimer on 2009-12-20
> **oldos2er said:**
> There are instructions here: [http://www.java.com/en/download/help/5000010500.xml](http://www.java.com/en/download/help/5000010500.xml)

The only thing you need to do differently is to run **sudo -i** instead of **su**. Because Ubuntu disables the root account, su won't work on Ubuntu.

Just FYI, you'll want to download the self-extracting binary.

I'm assuming you're aware that a slightly older version of Java is in the repositories.

Hi oldos2er

Yes i did see the older version in the repositories, does it not matter then whether JDK/JRE are the latest release ?

I will try your suggestion, will that automatically configure the environment variable too ?

Many thanks for your help

Whitetimer

---

### Post by whitetimer on 2009-12-20
> **Cheesemill said:**
> ```
sudo apt-get install sun-java6-jre sun-java6-sdk
```

Hi Cheesemill

Many thanks, but i thought that was an outdated version. Will try the latest release first

Whitetimer

---

### Post by oldos2er on 2009-12-20
> **whitetimer said:**
>  does it not matter then whether JDK/JRE are the latest release ?


That depends on what Java programs you need to run.

---

### Post by whitetimer on 2009-12-20
> **oldos2er said:**
> That depends on what Java programs you need to run.

Well nothing specific really ... :P

---

### Post by oldos2er on 2009-12-20
If I were you, I'd install the Java packages in the repositories first, and see how they work for you. You can always manually install Sun's java later on, if you need to.

---

