---
title: "Help installing apache FOP.."
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by Enissay on 2007-11-14
Hello every Body,
I tried to install apache FOP...
I don't know witch repositorie do I have to add...
Please help

---

### Post by tehet on 2007-11-14
It's not packaged in any official repository. You have to build it yourself.
[https://bugs.launchpad.net/ubuntu/+bug/121600](https://bugs.launchpad.net/ubuntu/+bug/121600)

---

### Post by jjalocha on 2007-11-27
Luckily, you don't have to build it, you can download the binary distribution (fop-0.94-bin-jdk1.4.tar.gz). In order to use it, you might have to install Java (sun-java6-jre) via aptitude.

Once downloaded, you can unpack it, and run it directly from the command line inside the newly created directory (fop-0.94). Something like:

```

$ cd fop-0.94
$ ./fop example.fo output.pdf

```


If you wish to use FOP system-wide, you have to do a more serious installation. Something like:

```

$ sudo cp fop-0.94-bin-jdk1.4.tar.gz /usr/local/share/
$ cd /usr/local/share/
$ sudo tar -xvzf fop-0.94-bin-jdk1.4.tar.gz
$ sudo cp fop-0.94/fop /usr/local/bin/

```

Then you have to edit this new '/usr/local/bin/fop' file, and add the following line somewhere near the start:

```

FOP_HOME=/usr/local/share/fop-0.94/

```

Just don't touch the first line, called "sha-bang" (#! /bin/sh). This must stay there for  your script to work.

Now, you can run FOP from your command line like any other application:

```

$ fop example.fo output.pdf

```

---

### Post by Enissay on 2007-12-02
thks for your answer....
/usr/local/bin/ doesnt exist... so i created it....:KS

---

