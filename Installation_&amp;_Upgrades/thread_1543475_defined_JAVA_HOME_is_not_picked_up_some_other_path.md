---
title: "defined JAVA_HOME is not picked up some other path taken"
date: 2010-08-01
forum: Installation &amp; Upgrades
---

### Post by tapas_mishra on 2010-08-01
Ubuntu 9.04 
I have in /etc/profile.d/jdk.sh
```

export JAVA_HOME=/usr/lib/jvm/java-6-sun
export PATH=$JAVA_HOME/bin:$PATH

```but when I am typing ```
which java
``` I see 
```
root@tapas-laptop:/usr/lib/jvm/java-6-sun# which java
/usr/lib/jvm/java-6-sun/bin/java

```which is not set in PATH.
So why is this happening and how can I avoid this ?

---

### Post by lykeion on 2010-08-01
It _is_ set in PATH or maybe I don't understand your question.

You add JAVA_HOME/bin to PATH and that is where java is, just like `which java` shows.

(EDIT)
Just saw that this was related to **_[another]("http://ubuntuforums.org/showthread.php?t=1543461")_** thread you posted, which you tagged SOLVED.
Please do not double post like that. This is not a chat.

---

### Post by tapas_mishra on 2010-08-01
> **lykeion said:**
> This is not a chat.

This is a different problem.

The   JAVA_HOME in PATH is 
```

/usr/lib/jvm/**java-6-sun**/bin

```but instead of that it is taking java from 
```

/usr/lib/jvm/**java-6-sun-1.6.0.13**/bin

```both of the JAVA_HOME/bin are different directories

when I type ```
ant 
```I got 
```

 ant
Unable to locate tools.jar. Expected to find it in /usr/lib/jvm/**java-6-sun-1.6.0.13**/lib/tools.jar
Buildfile: build.xml does not exist!
Build failed

```The above java it picked is not the one I defined in JAVA_HOME.

---

### Post by lykeion on 2010-08-01
ok, sorry then ;)

if you browse to /usr/lib/jvm you will notice that java-6-sun is a symlink to folder java-6-sun-#

this is what it should be and and lets you have several java folders in /usr/lib/jvm

to list and switch installed java versions you use update-java-alternatives, see
```
man update-java-alternatives
```

---

### Post by tapas_mishra on 2010-08-01
Oh yes you pointed the right thing.Thanks.

---

### Post by lykeion on 2010-08-01
sun-java6-jdk is in the partner repository

there are hundreds of post in this forum explaining how to enable it and install jdk (and I have written it before as well)

---

### Post by tapas_mishra on 2010-08-01
I just installed 
apt-get install sun-java6-jdk
but it was not in /usr/lib/jvm 
Also I did a find / -name jdk 
but there was no result where did it installed jdk.
Also ```

root@tapas-laptop:/usr/lib# find / -name sun-java6-jdk*
/usr/share/doc/sun-java6-jdk
/usr/share/doc-base/sun-java6-jdk-readme
/usr/share/lintian/overrides/sun-java6-jdk
/usr/share/menu/sun-java6-jdk
/var/lib/dpkg/info/sun-java6-jdk.postrm
/var/lib/dpkg/info/sun-java6-jdk.config
/var/lib/dpkg/info/sun-java6-jdk.postinst
/var/lib/dpkg/info/sun-java6-jdk.templates
/var/lib/dpkg/info/sun-java6-jdk.preinst
/var/lib/dpkg/info/sun-java6-jdk.prerm
/var/lib/dpkg/info/sun-java6-jdk.list
/var/lib/dpkg/info/sun-java6-jdk.md5sums
/var/lib/doc-base/documents/sun-java6-jdk-readme
/var/lib/doc-base/omf/sun-java6-jdk-readme
/var/lib/doc-base/omf/sun-java6-jdk-readme/sun-java6-jdk-readme-C.omf
/var/cache/apt/archives/sun-java6-jdk_6-13-1_i386.deb
```

---

### Post by lykeion on 2010-08-01
I don't think you understood my previous post about the symlink

package sun-java6-jdk installs to /usr/lib/jvm/java-6-sun-#/
(where # is the version number)

/usr/lib/jvm/java-6-sun 
(is a symlink - like a shortcut in Windows - which points to the currently used java)

update-java-alternatives
(is a command with which you set the java version to use)

---

### Post by tapas_mishra on 2010-08-01
Hi I got my problem resolved.I checked /usr/lib/jvm/java-6-sun
and I found this time the number of directories had increased also the files were more then when I had not done
```
apt-get install sun-java6-jdk
```
So when I am typing ant the error which I reported is not coming.

I did not understood your reply completely for the sake of my understaning and if some one comes across this thread I will say please explain following
> **lykeion said:**
> 
package sun-java6-jdk installs to /usr/lib/jvm/java-6-sun-#/
(where # is the version number)

/usr/lib/jvm/java-6-sun 
update-java-alternatives
(is a command with which you set the java version to use)

---

### Post by lykeion on 2010-08-01
Well, I think it's very clear. What exactly is unclear?
First I explain the differences between **java-6-sun-1.6.0.13** (or whatever your version number is) and **java-6-sun** in the directory /usr/lib/jvm

Then I explain the command **update-java-alternatives**, with which you can switch between java versions (type **man update-java-alternatives** in a terminal to read more)

Glad your problems were resolved, also:
> **tapas_mishra said:**
> Mark the threads as solved when you get answers.

---

### Post by tapas_mishra on 2010-08-01
> **lykeion said:**
> 

package sun-java6-jdk installs to /usr/lib/jvm/java-6-sun-#/
(where # is the version number)


I am not clear with the above statement.As when it was jre there also it was in the same place.
Also when I installed jdk new files are there and old also existed.
I expected jdk to create a separate directory.
So I asked.

---

### Post by lykeion on 2010-08-01
JDK and JRE are installed into same top directory, JRE is installed in a sub-folder

File listing comparisons:
**_[sun-java6-jre]("http://packages.ubuntu.com/karmic/all/sun-java6-jre/filelist")_**
**_[sun-java6-jdk]("http://packages.ubuntu.com/karmic/i386/sun-java6-jdk/filelist")_**

> **tapas_mishra said:**
> Mark the threads as solved when you get answers

---

### Post by tapas_mishra on 2010-08-01
Okay.

---

