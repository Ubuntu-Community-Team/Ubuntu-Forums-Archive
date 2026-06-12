---
title: "Fetching from update servers fail when when using update managers."
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by efrens on 2010-01-11
I'd appreciate guidance on his matter.
I have Ubuntu Karmic 64-bit installed.

Update manager tells me there are updates available, but when i try to install them, downloading the updates fail and throws this error:

```
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6-i386_2.10.1-0ubuntu16_amd64.deb

```

Consequently, a similar error occurs when I try installing Sun Java 6 Runtime.

```
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-jre_6-15-1_all.deb Connection failed [IP: 91.189.88.31 80]
```

And of course Ubuntu Restricted Extras stalls when it's time to download the Java package :(

I tried synaptic, update manager, aptitude, apt-get, and they all throw similar errors.

Then I also tried connecting to different servers, to no avail.

So to check if it's my connection to the net that has problems somehow, I tried downloading the file directly through my web browser, and it works. (But it's not recommended, and it won't let me!, install the updates manually, right?)

I tried searching for the errors on the net and in the forums, and they're all somehow related to proxy servers. I then checked if I'm using some inappropriate proxy settings, and everywhere it's all set up to connect to the net directly, which is, well, my setup.

Take note though, that I am able to install other softwares normally, i.e, using synaptic, apt-get etc. The ones I tried include Pidgin and Mplayer.

It's just these updates and Java:

```
jeanne@jeanne-desktop:~$ sudo sudo aptitude upgrade
W: The "upgrade" command is deprecated; use "safe-upgrade" instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be upgraded:
  libc-bin libc-dev-bin libc6 libc6-dev libc6-i386 
5 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 7,878kB/11.5MB of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Err http://security.ubuntu.com karmic-proposed/main libc6-i386 2.10.1-0ubuntu16
  Connection failed
Err http://archive.ubuntu.com karmic-updates/main libc6-i386 2.10.1-0ubuntu16   
  Connection failed [IP: 91.189.88.30 80]
Err http://archive.ubuntu.com karmic-updates/main libc6 2.10.1-0ubuntu16
  Connection failed [IP: 91.189.88.40 80]
E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6-i386_2.10.1-0ubuntu16_amd64.deb: Connection failed [IP: 91.189.88.30 80]
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

jeanne@jeanne-desktop:~$
```

I don't know what else I could do to fix this.
Any suggestions?

Thanks.

ps. This is my sources.list, maybe this will help.
```
#
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com KEY



# Ubuntu supported packages
deb http://security.ubuntu.com/ubuntu karmic-proposed main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-proposed main restricted universe multiverse


deb http://archive.ubuntu.com/ubuntu/ karmic main universe restricted multiverse
deb http://security.ubuntu.com/ubuntu/ karmic-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ karmic-updates universe main multiverse restricted

#medibuntu
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2EBC26B60C5A2783
deb http://packages.medibuntu.org/ karmic free non-free
deb-src http://packages.medibuntu.org/ karmic free non-free

#MPlayer Core Libraries
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0DA7581859566E92
deb http://ppa.launchpad.net/rvm/libs/ubuntu karmic main

#vlc 1
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com D739676F7613768D
deb http://ppa.launchpad.net/c-korn/vlc/ubuntu karmic main

#GIMP (Testing Version)
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 43BB102C405A15CB
deb http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu karmic main

# Ubuntu tweak
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6AF0E1940624A220
deb http://ppa.launchpad.net/tualatrix/ubuntu karmic main
deb-src http://ppa.launchpad.net/tualatrix/ubuntu karmic main

#compiz-fusion
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2ED6BB6042C24D89
deb http://ppa.launchpad.net/compiz/ubuntu karmic main

#firefox
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 632D16BB0C713DA6
deb http://ppa.launchpad.net/fta/ppa/ubuntu karmic main

#Ubuntu Mozilla Security Team
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com A6DCF7707EBC211F
deb http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu karmic main


#chromium-browser
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 5A9BF3BB4E5E17B5
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu karmic main

#google
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com A040830F7FAC5991
deb http://dl.google.com/linux/deb/ stable non-free

#empathy
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com FA3A1271
deb http://ppa.launchpad.net/telepathy/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/telepathy/ppa/ubuntu karmic main

#pidgin
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7FB8BEE0A1F196A8
deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu karmic main
```

---

### Post by llawwehttam on 2010-01-11
Are you using a proxy?

That could cause errors.

---

### Post by slakkie on 2010-01-11
Doesn't look like a proxy. Maybe try it a bit later, sometimes these problems occur and 5 minutes later it is gone.

---

### Post by chrisinspace on 2010-01-15
I'm having a similar issue.  I have an Ubuntu Server running as a VM in VirtualBox.  I'm getting several errors like this when I apt-get update:
```

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg  Connection failed [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2  Connection failed [IP: 91.189.88.30 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_US.bz2  Connection failed [IP: 91.189.88.40 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg  Connection failed

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

I get a whole series of hits before that...it's just a few servers giving me problems.  I can ping addresses both inside and outside of my network from this box.  I can ssh into it from a remote location and I can even ping the addresses that are returning the errors, so I can't see how this is a simple connection problem.  I am not using a proxy and I am using a straight bridge between the VM's emulated network adapter and a dedicated port on a physical NIC.

---

### Post by chrisinspace on 2010-01-15
After a couple of hours of looking online and through the forums, I finally came across this:

[http://ubuntuforums.org/showthread.php?t=1315182&highlight=apt-get+update+connection+failed](http://ubuntuforums.org/showthread.php?t=1315182&highlight=apt-get+update+connection+failed)

I took the suggestion in the last post, but only partially implemented it.  I changed all references to us.archive.ubuntu.com from http:// to ftp:// and it worked.  Don't ask me why, but it worked.

---

