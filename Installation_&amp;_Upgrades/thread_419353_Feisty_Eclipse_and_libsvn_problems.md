---
title: "Feisty Eclipse and libsvn problems"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by hunkybill on 2007-04-22
Hi,

Installed the latest Eclipse from Feisty repository, 3.2.2. Installed libsvn-javahl so I can use Subclipse plugin. Installed Subclipse, blows out and bombs when clicking Team->SVN. No JavaHL Library could be found. 

I fixed this in Edgy using a very painful process of rebuilidng libapr0. Feisty does not use this library so I am most confused about how to debug and fix this issue. Eclipse is useless to me without Subversion, and Subversion means Subclipse has to work, with JavaHL. 

Is there some way to get this fixed???

Thanks!!

Dave

---

### Post by mike.thorton on 2007-04-23
Hello,

I haven't managed to get this sw working (Eclipse+Subclipse) on Ubuntu Feisty Fawn 7.04 too.:( 

Anybody did?

---

### Post by mike.thorton on 2007-04-24
Ok, here you are the screenshot. I hope somebody will help.

---

### Post by patjoh on 2007-04-25
Hey guys!

I had the exact same problem and after some testing this fix worked for me:

[LIST=1]
[*]Install sun-java6-bin, sun-java6-jdk, sun-java6-jre
[*]install libsvn-javahl.
[*]If needed, install eclipse...
[*]Open /usr/lib/eclipse/eclipse.ini and add this line at the botton of the file:"-Djava.library.path=/usr/lib/jni/".
[*]Open /etc/eclipse/java_home and add the line "/usr/lib/jvm/java-6-sun" to the top of list of java-versions.
[*]Start eclipse and install subclipse.
[/LIST]

Hopefully that should do it...

---

### Post by mike.thorton on 2007-04-25
Thank you!!!!

It works for me as well. You've saved me from searching the Internet next time:KS

---

### Post by abatcher on 2007-06-25
I had problems getting subclipse running too, so i followed these instructions

Starting eclipse from the command line gave me this error:
> 
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xacf61acb, pid=3924, tid=3084760752
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_08-b03 mixed mode, sharing)
# Problematic frame:
# C  [libsvnjavahl-1.so.0.0.0+0xdacb]  _ZN7JNIUtil18setExceptionThrownEv+0x2b
#


I did *sudo apt-get remove libsvn-javahl *, started eclipse again, and subclipse was suddenly working.

So my advise, if the above instructions wouldnt work, would be:
**apt-get remove libsvn-javahl** and try again :D

---

### Post by igorilla on 2007-08-01
I worked just these 2 steps, as I already had Sun Java 5.

2. libsvn-javahl
4. Open /usr/lib/eclipse/eclipse.ini and add this line at the botton of the file:"-Djava.library.path=/usr/lib/jni/"

Thanks a lot for a great tip.

---

### Post by charlieg on 2007-08-20
> **patjoh said:**
> Open /usr/lib/eclipse/eclipse.ini and add this line at the botton of the file:"-Djava.library.path=/usr/lib/jni/".
Awesome tip!  Solved a subversive issue for me with it not finding javahl despite it being installed.

---

### Post by WhosRodney on 2007-08-23
patjoh, thanks for the help.  It worked for me :)

---

### Post by legalizemeth on 2007-10-23
> **abatcher said:**
> I had problems getting subclipse running too, so i followed these instructions

Starting eclipse from the command line gave me this error:


I did *sudo apt-get remove libsvn-javahl *, started eclipse again, and subclipse was suddenly working.

So my advise, if the above instructions wouldnt work, would be:
**apt-get remove libsvn-javahl** and try again :D
This is indeed an option.  But what happened here is that Subclipse fell back on SVNKit, or whatever the pure-Java SVN adapter is called.  That's fine, but be advised you will lose the ability to work with projects checked out via Subclipse with the command-line SVN tools.

---

### Post by legalizemeth on 2007-10-23
> **igorilla said:**
> 
4. Open /usr/lib/eclipse/eclipse.ini and add this line at the botton of the file:"-Djava.library.path=/usr/lib/jni/"

Thanks a lot for a great tip.
Yes, thank you very much.  This was exactly what I needed.  However, there was one more thing, in case anyone else has a similar issue.  I had worked around this problem previously by adding a symlink in $JAVA_HOME/jre/lib/i386 pointing to the real javahl shared lib.  In addition to adding /usr/lib/jni to my java.library.path, I had to remove my old symlink for Eclipse to stop crashing.

Thanks again patjoh!

---

### Post by jimmyxx on 2008-04-10
> **patjoh said:**
> Open /usr/lib/eclipse/eclipse.ini and add this line at the botton of the file:"-Djava.library.path=/usr/lib/jni/"

Worked for me too, thanks

---

