---
title: "Non-interactive install of sun-java6-jre"
date: 2008-07-23
forum: Installation &amp; Upgrades
---

### Post by ehammond on 2008-07-23
I am automating the install of various software for virtual machines and would like to effect the following in a non-interactive manner:

  apt-get install -y sun-java6-jre

I have already read and accepted the license agreement and I don't wish to be forced to agree to it manually during every automated install.

I have already tried
  export DEBIAN_FRONTEND=noninteractive
but this has no effect.

Ideas?

---

### Post by thesheff17 on 2010-10-12
I still have this problem.  Also I cannot switch to open jdk.  Is there anyway to bypass this license.

---

### Post by smoser on 2010-10-12
From bug 634487 [1]

export DEBIAN_FRONTEND=noninteractive
add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner"
apt-get update
echo 'sun-java6-bin   shared/accepted-sun-dlj-v1-1    boolean true
sun-java6-jdk   shared/accepted-sun-dlj-v1-1    boolean true
sun-java6-jre   shared/accepted-sun-dlj-v1-1    boolean true
sun-java6-jre   sun-java6-jre/stopthread        boolean true
sun-java6-jre   sun-java6-jre/jcepolicy note
sun-java6-bin   shared/present-sun-dlj-v1-1     note
sun-java6-jdk   shared/present-sun-dlj-v1-1     note
sun-java6-jre   shared/present-sun-dlj-v1-1     note
'|debconf-set-selections
apt-get -y install sun-java6-jdk

Generically if debconf is asking you questions, you can answer them once, and then see what answers were recorded and seed them the next time.

You can view debconf answers via 'debconf-get-selections' in debconf-utils.
- apt-get install debconf-utils
- sudo debconf-get-selections > pre
- sudo apt-get install foo
- sudo debconf-get-selections > post
- diff -u pre post

The changes can be seeded with debconf-set-selections as show above.

--
[1] [https://bugs.launchpad.net/ubuntu/+source/linux-ec2/+bug/634487](https://bugs.launchpad.net/ubuntu/+source/linux-ec2/+bug/634487)

---

### Post by zzzz8 on 2011-10-01
Hi Scott,

I'm using the Ubuntu Cloud guest images and the cloud init package to install certain packages at startup.  I would like to install the Sun Java 6 JDK using cloud-init and cloud-config in a noninteractive manner.

The instructions you have above apply when one is running a script.  I would like to avoid putting the commands above into the runcmd portion of the cloud-config script (it will be quite long and ugly to maintain).  Moreover, the commands in the runcmd portion of cloud-config are run near the end of startup - and I have some dependencies where I want to execute the install of the Sun Java 6 JDK package earlier.

What's the best way of specifying the install of the Sun Java 6 JDK package in cloud-config?

---

### Post by thesheff17 on 2011-10-01
You can disable the prompt by using the below commands. I run these as root.  Let me know if this works out:

echo 'sun-java6-plugin shared/accepted-sun-dlj-v1-1 boolean true' | /usr/bin/debconf-set-selections

echo 'sun-java6-bin shared/accepted-sun-dlj-v1-1 boolean true' | /usr/bin/debconf-set-selections

echo 'sun-java6-jre shared/accepted-sun-dlj-v1-1 boolean true' | /usr/bin/debconf-set-selections

---

### Post by zzzz8 on 2011-10-01
Hi,

Thanks for the info.  Your commands work - as well as Scott's.  There's a caveat because I'm trying to do this on Amazon EC2 during startup.  However, I would have to run these commands in the runcmd section of cloud-config or perhaps pass it in directly in the user-data as a script.  Either method is just a bit too late in the startup sequence.

If you know of a way to execute these scripts earlier in the startup sequence, please let me know.  Thanks!

---

### Post by thesheff17 on 2011-10-02
I see what you mean about being able to execute the commands pre cloud-init. I admit I'm not using the cloud init script and have custom python scripts configuring my ec2 images.  I would suggest emailing/joining the ubuntu ec2 google group and sending the group an email.  [http://groups.google.com/group/ec2ubuntu?pli=1](http://groups.google.com/group/ec2ubuntu?pli=1)  Unfortunately the ubuntu forums seem a little stale for server ubuntu community support. Smoser is prob the guy you want for help on cloud init and prob watches that ec2 group more closely.

---

