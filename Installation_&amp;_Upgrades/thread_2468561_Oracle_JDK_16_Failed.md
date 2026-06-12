---
title: "Oracle JDK 16 Failed"
date: 2021-11-03
forum: Installation &amp; Upgrades
---

### Post by starfox101 on 2021-11-03
For sometime I've had minecraft bedrock running on Ubuntu 20.04.3 LTS. I wanted to try java version. After many failed attempts I figured out the problem. JDK 16 has been removed! Requires JDK 17.  I now have minecraft java version 17.* running. The problem is  Apt Get is trying to install JDK 16 for about 3 weeks now. I have searched, came up with different thing. None have fixed this..
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289419&stc=1[/IMG]

thanks
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289419&d=1635943992&thumb=1&stc=1[/IMG]

---

### Post by ActionParsnip on 2021-11-03
Manually download the file.

---

### Post by starfox101 on 2021-11-03
The file does not exist, That's why I downloaded 17

---

### Post by MAFoElffen on 2021-11-04
Sounds like a support request to Oracle, to at least inform them that there is a problem... Squeaky wheels do get grease, They can't fix it if they are not aware of it.

---

### Post by monkeybrain20122 on 2021-11-04
IS Java 17 working for you? If yes what do you try to fix? apt trying to upgrade openjdk 16 has no effect on your oracle-java. I assume you have already set up update-altermatives to default java to Oracle Java (else you won't be able to run your game, or if it runs, that means openjdk already works, you don't need Oacle)

What is the output of 
```

java -version
```

---

### Post by starfox101 on 2021-11-04
openjdk version "17.0.1" 2021-10-19
OpenJDK Runtime Environment (build 17.0.1+12-39)
OpenJDK 64-Bit Server VM (build 17.0.1+12-39, mixed mode, sharing)

---

### Post by monkeybrain20122 on 2021-11-04
So openjdk 17 is working for you. What is it that need fixing?

---

### Post by starfox101 on 2021-11-05
The problem is  Apt Get is trying to install JDK 16 for about 3 weeks now.

---

### Post by monkeybrain20122 on 2021-11-05
> **starfox101 said:**
> The problem is  Apt Get is trying to install JDK 16 for about 3 weeks now.

It won't affect JDK17, multiple versions of java can coexist. It won't change the default (which is java17 now from what you posted above)

How to switch between different javas with update-alternatives (you don't need to worry since your default is working, just provide this for extra info) [https://dev.to/thegroo/install-and-manage-multiple-java-versions-on-linux-using-alternatives-5e93](https://dev.to/thegroo/install-and-manage-multiple-java-versions-on-linux-using-alternatives-5e93)

---

### Post by starfox101 on 2021-11-07
I guess, It's a nag Screen! Every time I SSH in, or use webmin it tells me it can't locate java 16. I just want to fix it!

---

### Post by ActionParsnip on 2021-11-07
Eugh @ webmin

---

### Post by Tadaen_Sylvermane on 2021-11-07
We were discussing Minecraft java version the other day in another thread. For the record the java version on my Windows desktop opens using the OpenJDK, not Oracle (as evidenced by it's asking for permission through the firewall). As such you can most likely eliminate the Oracle version altogether and just move to the OpenJDK. I'm assuming Bedrock is the same? I haven't tried Bedrock yet but my Docker which uses version 17 works perfectly. If it can't see the repo then it should shut up once and for all.

---

