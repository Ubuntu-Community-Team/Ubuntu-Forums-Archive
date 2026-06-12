---
title: "Problem during installing J2EE"
date: 2006-07-12
forum: Installation &amp; Upgrades
---

### Post by forlog on 2006-07-12
Hi,

I've downloaded java_ee_sdk-5-linux.bin from sun site, created /usr/local/java directory, run ./java_ee_sdk-5-linux.bin (everything with sudo) and got:

Checking available disk space...
Checking Java(TM) 2 Runtime Environment...
Extracting Java(TM) 2 Runtime Environment files...
Deleting temporary files...

Here program hungs up. Does anyone know what is wrong?

Thanks in advance.

---

### Post by Jagot on 2006-07-13
Can't answer the specific problem, but are you aware that you can get the jdk in the multiverse repo?

```
sudo aptitude update
sudo aptitude install sun-java5-jdk
```

---

### Post by challengerlks on 2007-05-03
I also faced with the same problem when I installed this with Ubuntu 7.04. However, if U install it with your own user account ( i.e. not with sudo command ), U can install it without any problems. 

I also do not have this problem when I used Ubuntu 6.10. I have no idea about that.

---

### Post by zvacet on 2007-05-03
It is in synaptic.That is easyest way I know.

---

### Post by randal on 2007-05-31
I'm having the same problem... installation stalls at: deleting temporary files...

I've already installed the sun-java-1.600 and it's already my default...
Anyone has anything on this...?

---

### Post by randal on 2007-06-01
I managed to solve the problem on Feisty. Here's what I did:

1. I setup the JAVA_HOME environment variable to /usr/lib/jvm/java-6-sun-1.6.0.00 through /etc/profile. I added this code to the end of the file:

```
export JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.00

PATH="${PATH}":"${JAVA_HOME}":"${JAVA_HOME}"/bin
```

I'm not very sure with the last entry with the /bin though. I rebooted after this.

2. I forgot to setup the JDK so I installed it through:

```

sudo apt-get install sun-java6-jdk
```

3. Since I've already downloaded the SDK, I just went to the directory where I saved it and then ran it.

```
sudo chmod +x java_ee_sdk-5_02-linux-nojdk.bin
sudo ./java_ee_sdk-5_02-linux-nojdk.bin
```

then I followed through the wizard.

I hope this helps.

---

### Post by randal on 2007-06-01
Please comment on how I set the environment variables...

---

