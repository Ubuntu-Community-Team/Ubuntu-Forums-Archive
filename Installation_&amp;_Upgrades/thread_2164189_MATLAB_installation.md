---
title: "MATLAB installation"
date: 2013-07-30
forum: Installation &amp; Upgrades
---

### Post by CkDGTAT on 2013-07-30
Hi,

I am utterly unable to find where the mistake come from, any idea?

```


% ./install -glnxa64 -v | sed 's/jan/jan/g'

Preparing installation files ...
->  DVD                 = /home/jan/Downloads/mat4
->  ARCH                = glnxa64
->  DISPLAY             = :0
->  TESTONLY            = 0
->  JRE_LOC             = /tmp/mathworks_3336/sys/java/jre/glnxa64/jre
->  LD_LIBRARY_PATH     = /tmp/mathworks_3336/bin/glnxa64
 
Command to run:
/tmp/mathworks_3336/sys/java/jre/glnxa64/jre/bin/java -Xmx512m  -splash:"/home/jan/Downloads/mat4/java/splash.png" -Djava.ext.dirs=/tmp/mathworks_3336/sys/java/jre/glnxa64/jre/lib/ext:/tmp/mathworks_3336/java/jar:/tmp/mathworks_3336/java/jar/ja_JP/:/tmp/mathworks_3336/java/jar/zh_CN/:/tmp/mathworks_3336/java/jarext:/tmp/mathworks_3336/java/jarext/axis2/:/tmp/mathworks_3336/java/jarext/guice/:/tmp/mathworks_3336/java/jarext/webservices/ com/mathworks/professionalinstaller/Launcher -root "/home/jan/Downloads/mat4" -tmpdir "/tmp/mathworks_3336" 
 
Installing ...
/tmp/mathworks_3336/sys/java/jre/glnxa64/jre/bin/java: 1: /tmp/mathworks_3336/sys/java/jre/glnxa64/jre/bin/java: Syntax error: "(" unexpected
Finished

```

Any help would be greatful thank you!

---

### Post by Topsiho on 2013-07-31
Hi,

The question how to install Matlab has been asked quite often on this forum. Maybe you can find an answer to your question by searching for matlab install.

Another useful idea might be to try the matlab clone Octave, which is in the repositories, and is very easy to install.

Topsiho

---

### Post by gordintoronto on 2013-07-31
Also here: [https://help.ubuntu.com/community/MATLAB](https://help.ubuntu.com/community/MATLAB)

---

### Post by Topsiho on 2013-08-01
In the link of gordintoronto (thanks for this link) I read:
"MATLAB R2012a users are strongly encouraged to install R2012a on Ubuntu 10.04 LTS or Ubuntu 10.10 for best results."

At this point of time this is not a good advice, as these versions of Ubuntu are not supported anymore. Ubuntu users are strongly discouraged to use these versions of Ubuntu for security reasons :)

Topsiho

---

