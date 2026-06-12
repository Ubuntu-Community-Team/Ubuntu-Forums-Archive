---
title: "jdk 6 installation problem"
date: 2010-03-05
forum: Installation &amp; Upgrades
---

### Post by rosy Jovita on 2010-03-05
Hi,

I'm having problem with the jdk installation in my pc.
previously i've successfully installed jdk in ubuntu 9.04 but unfortunately 
my pc crash and i need to reformat the pc.
And now even i've reinstall ubuntu 7.04 and try to install the jdk.
tried out this command many times: sudo apt-get install sun-java6-jdk
but only got this error:
E: Couldn't find package sun-java6-jdk

please help..
looking forward for replies.

---

### Post by honey toast on 2010-03-05
i think you don't have the ubuntu universe or one of those enabled. Go into your System > Admin > Software Sources then check on the 'other software' tab. Depending on what you have in there, you may or may not be allowed to install certain apps. 


here is the link that I used to enable more repositories:

```

http://www.psychocats.net/ubuntu/sources

```

hope i was of help to you. :)

---

### Post by rosy Jovita on 2010-03-10
hi,

i've reformat my pc and reinstall ubuntu 9.04.
someone told me that i need to install the openjdk(in the add/remove program).
I've tried to install but there are problem with the update.
what should i do?
i tried this command: sudo apt-get install sun-java6-jdk 
but it gave me this error: couldn't find the package.
what is going on?
i have run sudo apt-get autoclean before doing all this.

---

### Post by slakkie on 2010-03-10
Could you post your sources.list?

Alternativly you could use the sources.list as shown in the code tags.

```

### Jaunty 9.04
# Required
deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ jaunty main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ jaunty-security main restricted universe multiverse
#deb-src http://security.ubuntu.com/ubuntu/ jaunty-security main restricted universe multiverse
# Recommended
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted universe multiverse
# Optional
deb http://packages.medibuntu.org/ jaunty free non-free
#deb-src http://packages.medibuntu.org/ jaunty free non-free
deb http://archive.canonical.com/ubuntu/ jaunty partner
#deb-src http://archive.canonical.com/ubuntu/ jaunty partner
#deb http://archive.ubuntu.com/ubuntu/ jaunty-proposed main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ jaunty-proposed main restricted universe multiverse
#deb http://archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

```

---

