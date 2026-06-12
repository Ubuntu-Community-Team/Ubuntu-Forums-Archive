---
title: "frostwire closes, java 1.5.0_06 as default"
date: 2007-04-13
forum: Installation &amp; Upgrades
---

### Post by Franscisco on 2007-04-13
Does anyone know what is wrong with Frostwire, it closes and the terminal says something went wrong because I might be using a wrong version of java.
the default java is java 1.5.0_06 on my box. any help!

---

### Post by phossal on 2007-04-13
Edited.

---

### Post by Franscisco on 2007-04-14
I put java 5 as default, so Frostwire can run, but when I type in the terminal Frostwire, the program opens, and then closes, and the below massage appears. what is wrong? I appreciate any help I can get. 

******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)

omar@freekbox:~$

---

### Post by phossal on 2007-04-14
You want to download this: [frostwire-4.13.1.7.noarch.tar.gz]("http://frostwire.com/download-file.php?fileid=tarball"). Download it to your desktop. Right-click and extract it. Open the folder, and inside is a script called runFrost.sh or something similar. Double click it. Click "run in terminal" at the prompt. Post any errors. (There shouldn't be any) For the record, if I were going to use such a thing, I probably would use Limewire - which downloads in a similar way - rather than Frostwire.

---

### Post by Timbo78 on 2007-04-15
> **phossal said:**
>  if I were going to use such a thing, I probably would use Limewire - which downloads in a similar way - rather than Frostwire.

FrostWire and LimeWire are the same thing, you need to do some research. FrostWire is open source and functions the same as a LimeWire Pro installation, i.e. turbo charged connections. 

I have intermittent problems with FrostWire, it will sometimes crash on startup or it will churn away using up 100% of CPU time... Not as solid as the Windows version i have to say. 

T

---

### Post by phossal on 2007-04-15
They're not the same thing. But I'm a practical person. For the sake of entertaining each other, let's assume they *are*. In that case, use Limewire. Not Frostwire. You'll have no problem with my suggestion. They're the same thing.

The CPU problems are likely a result of the JDK you're using. You're using a packaged version of Frostwire? And JDK 1.4 or something? Worse, running beryl?

I recommend JDK 6, and LimewireOther.zip. I've installed them both hundreds of times now. And LimewireOther as recently as a day ago. JDK 6 and LimewireOther play well together.

---

### Post by Timbo78 on 2007-04-15
> **phossal said:**
> They're not the same thing. But I'm a practical person. For the sake of entertaining each other, let's assume they *are*. In that case, use Limewire. Not Frostwire. You'll have no problem with my suggestion. They're the same thing.

The CPU problems are likely a result of the JDK you're using. You're using a packaged version of Frostwire? And JDK 1.4 or something? Worse, running beryl?

I recommend JDK 6, and LimewireOther.zip. I've installed them both hundreds of times now. And LimewireOther as recently as a day ago. JDK 6 and LimewireOther play well together.

Yeah cool, i have LimeWire installed on Linux and it crashes out too. Lucky i don't generally do much in the way of P2P file sharing. At the end of the day if i really, really need to use LimeWire i'll use the WinXP version, again as i said it is a rare that i use it.  

I am running a vanilla 6.10 install with GNOME, using a theme i picked up from gnome.org or somewhere. 

T

---

### Post by geezerone on 2007-04-15
I downloaded 4.13.1.7 which closes when opened? was ok before (4.13.1.?):(

---

### Post by phossal on 2007-04-15
Try to launch it from the command line. Then post your errors.

---

### Post by geezerone on 2007-04-16
Thanks for the response.

Here is the error from command line which points to JAVA issue but worked with previous version ok?

```
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:585)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb0e08ef6, pid=6009, tid=2965101488
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_06-b05 mixed mode, sharing)
# Problematic frame:
# C  [libfontmanager.so+0x31ef6]
#
# An error report file with more information is saved as hs_err_pid6009.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
/usr/lib/frostwire/runFrostwire.sh: line 122:  6009 Aborted                 ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar $ARGUMENTS

******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)

```

I installed jre 6 to no avail.

---

### Post by geezerone on 2007-04-16
I uninstalled and reinstalled from synaptic but when frostwire starts it goes to chat configuration but says to use a unique username and when typed in closes. I restart frostwire but same again so never get to use it! :(

---

### Post by phossal on 2007-04-16
Are you using Beryl?

---

### Post by geezerone on 2007-04-16
Not using Beryl (have heard of it - what is it?) - I had used Automatix previously and Frostwire working. I saw another thread [here ]("http://ubuntuforums.org/showthread.php?t=305337&page=5") with other users having same nickname problem but no answer?

---

### Post by phossal on 2007-04-16
I have a working Frostwire example on my desktop. It opens. I don't use it, except to test its installation. Here is my suggestion: update your Java to at least JDK6u1, and then update Frostwire from their site, and avoid the packages.

---

### Post by whistlerspa on 2007-04-20
I found i had a problem when I had j2re v 1.4.2 installed along wth java 1.5.0 . Once I completely removed the former frostwire worked straight away.

---

### Post by phossal on 2007-04-21
Is there a chance you didn't configure update-alternatives, so that your applications were still trying to use the older one? I have had two or three different JDK's installed on my machine at a time, with no problems.

---

### Post by edantes on 2007-06-02
I bumped into this problem today and corrected it after reading this post and others.  Just to make a record nof the solutions in case anyone cames back here.

The packaged frostwire requires java 1.5 or higher.  You should install the sun-java packages and make it the defaut with this command:

[INDENT]sudo update-alternatives --config java[/INDENT]

---

### Post by Tuomas on 2008-06-24
Thanks, edantes!

---

