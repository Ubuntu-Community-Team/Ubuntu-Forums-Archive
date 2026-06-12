---
title: "LD_LIBRARY_PATH in Ubuntu 10.04 Lucid."
date: 2010-06-01
forum: Installation &amp; Upgrades
---

### Post by jiapei100 on 2010-06-01
Hi, I changed my /etc/environment to

```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/lib/jvm/java-6-sun/bin"
LD_LIBRARY_PATH="/usr/lib/jni"
JAVA_HOME="/usr/lib/jvm/java-6-sun"
CLASSPATH="/usr/lib/jvm/java-6-sun/lib:."
```

I hope my Eclipse should be able to find java3d, because

```
jiapei@jiapei-laptop:/usr/lib/jni$ ls
libgluegen-rt.so                libjava-access-bridge-jni.so.0.0.0  libjogl.so              libswt-pi-gtk-3555.so
libj3dcore-ogl.so               libJavaEditline.so                  libswt-atk-gtk-3555.so
libjava-access-bridge-jni.so    libJavaReadline.so                  libswt-awt-gtk-3555.so
libjava-access-bridge-jni.so.0  libjogl_awt.so                      libswt-gtk-3555.so

```


According to some instructions on the internet, if I set LD_LIBRARY+PATH in /etc/environment, java should be able to search the native code when required.
But, this never works any longer in Ubuntu 10.04 Lucid.
This is absolutely strange.


And, even after a fresh rebooting, Ubuntu Lucid won't be able to find "$LD_LIBRARY_PATH" at all

```
jiapei@jiapei-laptop:/etc$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/lib/jvm/java-6-sun/bin
jiapei@jiapei-laptop:/etc$ echo $CLASSPATH
/usr/lib/jvm/java-6-sun/lib:.
jiapei@jiapei-laptop:/etc$ echo $JAVA_HOME
/usr/lib/jvm/java-6-sun
jiapei@jiapei-laptop:/etc$ echo $LD_LIBRARY_PATH

jiapei@jiapei-laptop:/etc$ 
```

As you may have noticed, there is an empty line after ```
echo $LD_LIBRARY_PATH
``` 

Did anybody else meet the same problem?
Does Ubuntu Lucid abandon the variable $LD_LIBRARY_PATH? 
But, there must be something else as a replacement, right?

Can anybody give me a hand??


Best Regards
JIA

---

### Post by Emanuele_Z on 2010-06-12
Hi, apparently (sadly) LD_LIBRARY_PATH doesn't work anymore in Lucid Lynx :(

Does anyone have more news about it?

Cheers,

---

### Post by derrekito on 2010-06-19
Bump!!

---

### Post by mwolfe on 2010-07-08
I'm having the same issue. I added a line to my .profile file, as I did with my path and a few other things.. All of them are set after logging in but the LD_LIBRARY_PATH is always empty.. If i manually source this file it will get set. It seems something that is sourced after .profile is clearing this variable. I double checked that my .profile is getting sourced by having it create a file, and when I logged out/back in the file was created, but my LD_LIBRARY_PATH was not set. I need this to be set because I've developed a QT application and its annoying to have to run it from within QT creator everytime or manually set the LD_LIBRARY_PATH in my terminal. Any ideas why this gets cleared and perhaps what the correct solution is for this?

---

### Post by davidmohammed on 2010-07-08
as far as I understand it, a global LD_LIBRARY_PATH value is no longer used by lucid due to perceived security issues.  If you do want to add new library paths you should now create your own .conf file in /etc/ld.so.conf.d
and add your folder to that file followed by

ldconfig -v

or you can add your folder to /etc/ld.so.conf

e.g.
echo "include /usr/local/lib" | sudo tee -a /etc/ld.so.conf
sudo ldconfig -v

---

### Post by msntrf on 2010-08-25
I understand how to use ld.so.conf.d/ to set linked libraries.  However, am I correct in thinking this is NOT how one can set Java's java.library.path?  That is, directories I add to ld.so.conf.d/*.conf do not show up in java.library.path.  Am I doing something wrong or is this the intended behavior?

If it is intended, what is the recommended way of setting java.library.path?  Do I have to do it by either exporting LD_LIBRARY_PATH right before running a Java program or by passing -Djava.library.path= to the JVM?  Is there a system-wide method?

Thanks in advance!

---

