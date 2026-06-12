---
title: "I cannot install eclipse"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by gasull on 2007-04-25
Hi.

When I try to mark eclipse for installation within Synaptic I get this message:

```

eclipse:
 Depends: eclipse-jdt but it is not going to be installed
 Depends: eclipse-pde but it is not going to be installed
 Depends: eclipse-source but it is not going to be installed

```

If I try to mark eclipse-jdt for installation I get this:

```

eclipse-jdt:
 Depends: eclipse-platform but it is not going to be installed
 Depends: junit (>=3.8) but it is not installable
 Depends: ant-optional (>=1.6.5-3) but it is not installable

```

If I try eclipse-platform I get:

```

eclipse-platform:
 Depends: java-common (>=0.23) but it is not installable
 Depends: eclipse-rcp but it is not going to be installed
 Depends: libjsch-java (>=0.1.28) but it is not installable
 Depends: libtomcat5.5-java but it is not going to be installed

```

And so on.

How can I install eclipse?

TIA.

---

### Post by jsym on 2007-04-25
The issue seems to be with the java packages.  Do you currently have java installed? (I'll assume "Yes")  What happens if you try to reinstall java directly?  What about Sun's Java package?

What happens if you simply try to use apt-get?  (Likely the same thing, but worth a try)

I suppose it could be a repository problem (i.e. the files are not available in the repositories that you have active currently), but that's just a shot in the dark.  If all else fails you could try changing them and then try again.

---

### Post by gasull on 2007-04-25
No, I don't have Java installed.  But I have similar problems when I try to install sun-java5-jdk:

```

sun-java5-jdk:
 Depends: sun-java5-jre but it is not going to be installed
 Depends: sun-java5-demo but it is not going to be installed

```

If I try sun-java5-jre:

```

sun-java5-jre:
 Depends: java-common  but it is not installable
 Depends: sun-java5-bin but it is not going to be installed or
 	ia32-sun-java5-bin (=1.5.0-11-1ubuntu2) but it is not installable

```

If I search for java-common in Synaptic I don't find any packages!

And yes, I get the same problems if I try with apt-get.

Please help.

---

### Post by Browser_ice on 2007-04-25
Isn't Ubuntu 7.04 already Java enabled ?

But wait, maybe you don't have 7.04 ?

---

### Post by gasull on 2007-04-25
> **Browser_ice said:**
> Isn't Ubuntu 7.04 already Java enabled ?

But wait, maybe you don't have 7.04 ?

Yes, I have Ubuntu Feisty.

---

### Post by jsym on 2007-04-25
Perhaps you do not have *all* the repositories installed.  I looked around the web a bit and this seems to be a common error for people with similar complaints.

For example: [http://www.google.ca/search?q=synaptic+depends+not+installable&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a]("http://www.google.ca/search?q=synaptic+depends+not+installable&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a")

Are all of Universe, Multiverse, etc. checked?

If so, did you try switching to different repositories?

---

### Post by gasull on 2007-04-26
> **jsym said:**
> Perhaps you do not have *all* the repositories installed.  I looked around the web a bit and this seems to be a common error for people with similar complaints.

For example: [http://www.google.ca/search?q=synaptic+depends+not+installable&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a]("http://www.google.ca/search?q=synaptic+depends+not+installable&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a")


Maybe I should try sudo apt-get -f install as the first link in the google search suggest.  Won't it break anything?

> **jsym said:**
> 
Are all of Universe, Multiverse, etc. checked?


Yes.  Even backports.

> **jsym said:**
> 
If so, did you try switching to different repositories?

I don't understand what you mean with different repositories.  Different mirrors or repositories of other Ubuntu versions?

Here is my /etc/apt/sources.list

```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

```

---

### Post by jsym on 2007-04-27
The suggestion for the repositories was simply to try a different mirror.  It's a long shot in the dark.  Since you're already running 7.04 it's likely not an issue with the necessary files being part of a different upgrade.  I get similar dependency complaints when I'm not connected to the Net and the files are not on the install CD, but this is likely not your problem either.

Sorry I couldn't be more help.

---

### Post by eapache on 2007-04-27
What happens if you use the graphical add/remove program to install "Ubuntu restricted extras"?

---

### Post by gasull on 2007-04-29
I solved it!

The solution is to add the [Medibuntu repositories]("http://medibuntu.sos-sts.com/repository.php").

The idea about the Ubuntu restricted extras gave me a clue of what to do.  Thank you so much.

---

