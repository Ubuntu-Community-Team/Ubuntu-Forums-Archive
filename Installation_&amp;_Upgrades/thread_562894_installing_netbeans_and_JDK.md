---
title: "installing netbeans and JDK"
date: 2007-09-29
forum: Installation &amp; Upgrades
---

### Post by codeking on 2007-09-29
I've been trying to install NetBeans on ubuntu and it says I need JDK.  So I downloaded JDK, but after entering this:

```
cd ./Desktop
./jdk-6u2-linux-i586.bin
```

It installs into a folder on my desktop.  Needless to say, I don't want things to be installed on my desktop.   How can I install it where it's supposed to be installed?

---

### Post by radoe on 2007-09-29
> **codeking said:**
> I've been trying to install NetBeans on ubuntu and it says I need JDK.  So I downloaded JDK, but after entering this:

```
cd ./Desktop
./jdk-6u2-linux-i586.bin
```

It installs into a folder on my desktop.  Needless to say, I don't want things to be installed on my desktop.   How can I install it where it's supposed to be installed?

Simply copy it to the right place  after installation. Just keep  the structure below jdk1.6.0_02 like the installer created it.

---

### Post by codeking on 2007-09-29
Where should I move it to?

---

### Post by radoe on 2007-09-29
> **codeking said:**
> Where should I move it to?

Whereever you want. I keep copies of various JDK versions (1.4.x, 1.5.x, 1.6.x) in ~/java and symlink binaries of default versions to ~/bin.

Btw, why don't you use ubuntu packages for java (sun-java6-jdk et. al.)?

---

### Post by codeking on 2007-09-29
i did, but i got an error

i tried installing it on my desktop and moving it to the /usr/lib directory, but it says I don't have permission to write it, even though I'm a superuser.

---

### Post by radoe on 2007-09-29
> **codeking said:**
> i did, but i got an error

i tried installing it on my desktop and moving it to the /usr/lib directory, but it says I don't have permission to write it, even though I'm a superuser.

Please follow [https://help.ubuntu.com/community/Java]("https://help.ubuntu.com/community/Java") to install SUN Java packages from Ubuntu repository.

---

### Post by codeking on 2007-09-29
Did that, but when I try to install netbeans in the /usr/lib/ directory, it says it's read only.  How do I give myself privileges to that directory?

---

### Post by radoe on 2007-09-30
> **codeking said:**
> Did that, but when I try to install netbeans in the /usr/lib/ directory, it says it's read only.  How do I give myself privileges to that directory?

I'd suggest not installing it in /usr/lib. Install it to your homedirectory.

---

### Post by codeking on 2007-09-30
I don't want to have programs installed in my home directory because that's where I keep my files, not my programs.  Is there ANY way to get read/write access to /usr/ or even better, the entire filesystem?

---

### Post by franzb on 2007-10-07
Hello,

That's the way I was able to install netbeans successfully:

sudo sh netbeans-6.0beta1-ruby-linux.sh --javahome /usr/lib/jvm/java-6-sun

The package sun-java6-jdk has to be installed previously.

Franz

---

