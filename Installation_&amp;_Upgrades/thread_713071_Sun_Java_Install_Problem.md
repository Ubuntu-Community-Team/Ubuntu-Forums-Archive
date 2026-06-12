---
title: "Sun Java Install Problem"
date: 2008-03-02
forum: Installation &amp; Upgrades
---

### Post by npc100 on 2008-03-02
Hi all,

I'm running 7.10 and trying to install the Sun jdk. I've tried installing it via Synaptic and that returned various dependency errors. I've tried

```
sudo apt-get install  sun-java6-bin sun-java6-plugin sun-java6-fonts sun-java6-jre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  binfmt-support
The following NEW packages will be installed
  sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/32.7MB of archives.
After unpacking 93.8MB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package sun-java6-bin.
(Reading database ... 91966 files and directories currently installed.)
Unpacking sun-java6-bin (from .../sun-java6-bin_6-03-0ubuntu2_i386.deb) ...
sun-dlj-v1-1 license has already been accepted
Selecting previously deselected package sun-java6-jre.
Unpacking sun-java6-jre (from .../sun-java6-jre_6-03-0ubuntu2_all.deb) ...
sun-dlj-v1-1 license has already been accepted
Selecting previously deselected package sun-java6-fonts.
Unpacking sun-java6-fonts (from .../sun-java6-fonts_6-03-0ubuntu2_all.deb) ...
Selecting previously deselected package sun-java6-plugin.
Unpacking sun-java6-plugin (from .../sun-java6-plugin_6-03-0ubuntu2_i386.deb) ...
Setting up sun-java6-bin (6-03-0ubuntu2) ...
/var/lib/dpkg/info/sun-java6-bin.postinst: 84: /usr/lib/jvm/java-6-sun-1.6.0.03/bin/java: not found
dpkg: error processing sun-java6-bin (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of sun-java6-plugin:
 sun-java6-plugin depends on sun-java6-bin (= 6-03-0ubuntu2); however:
  Package sun-java6-bin is not configured yet.
dpkg: error processing sun-java6-plugin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-jre:
 sun-java6-jre depends on sun-java6-bin (= 6-03-0ubuntu2) | ia32-sun-java6-bin (= 6-03-0ubuntu2); however:
  Package sun-java6-bin is not configured yet.
  Package ia32-sun-java6-bin is not installed.
dpkg: error processing sun-java6-jre (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-fonts:
 sun-java6-fonts depends on sun-java6-jre (>= 6-03-0ubuntu2); however:
  Package sun-java6-jre is not configured yet.
dpkg: error processing sun-java6-fonts (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java6-bin
 sun-java6-plugin
 sun-java6-jre
 sun-java6-fonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
 
```

 if I do 

```
sudo dpkg --configure -a
Setting up sun-java6-bin (6-03-0ubuntu2) ...
/var/lib/dpkg/info/sun-java6-bin.postinst: 84: /usr/lib/jvm/java-6-sun-1.6.0.03/bin/java: not found
dpkg: error processing sun-java6-bin (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of sun-java6-plugin:
 sun-java6-plugin depends on sun-java6-bin (= 6-03-0ubuntu2); however:
  Package sun-java6-bin is not configured yet.
dpkg: error processing sun-java6-plugin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java6-bin
 sun-java6-plugin

```

Giving up on 6, I tried 5 with the same results.

I then tried downloading:
jdk-6u4-linux-i586.bin and
jre-6u2-linux-i586.bin
from Sun's website, chmoded them and tried to run and with both files get:

```

<snip several page license agreement>
Do you agree to the above license terms? [yes or no]
yes
Unpacking...
Checksumming...
The download file appears to be corrupted.  Please refer
to the Troubleshooting section of the Installation
Instructions on the download page for more information.
Please do not attempt to install this archive file.

```

Any idea's?

---

### Post by Pumalite on 2008-03-02
Post the output of:
sudo apt-get install -f

---

### Post by npc100 on 2008-03-02
```
sudo apt-get install -f
[sudo] password for neil:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up sun-java6-bin (6-03-0ubuntu2) ...
/var/lib/dpkg/info/sun-java6-bin.postinst: 84: /usr/lib/jvm/java-6-sun-1.6.0.03/bin/java: not found
dpkg: error processing sun-java6-bin (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of sun-java6-plugin:
 sun-java6-plugin depends on sun-java6-bin (= 6-03-0ubuntu2); however:
  Package sun-java6-bin is not configured yet.
dpkg: error processing sun-java6-plugin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-jre:
 sun-java6-jre depends on sun-java6-bin (= 6-03-0ubuntu2) | ia32-sun-java6-bin (= 6-03-0ubuntu2); however:
  Package sun-java6-bin is not configured yet.
  Package ia32-sun-java6-bin is not installed.
dpkg: error processing sun-java6-jre (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-fonts:
 sun-java6-fonts depends on sun-java6-jre (>= 6-03-0ubuntu2); however:
  Package sun-java6-jre is not configured yet.
dpkg: error processing sun-java6-fonts (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java6-bin
 sun-java6-plugin
 sun-java6-jre
 sun-java6-fonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Pumalite on 2008-03-02
You have to remove those packages and then reinstall:
sudo dpkg --remove --force-remove-reinstreq <packagename>

---

### Post by npc100 on 2008-03-02
thanks for the help, but unfortunately that didn't work:

```
neil@Lister:~$ sudo dpkg --remove --force-remove-reinstreq sun-java6-bin sun-java6-plugin sun-java6-jre sun-java6-fonts
(Reading database ... 92613 files and directories currently installed.)
Removing sun-java6-bin ...
Removing sun-java6-plugin ...
Removing sun-java6-jre ...
Removing sun-java6-fonts ...
neil@Lister:~$ sudo apt-get install  sun-java6-bin sun-java6-plugin sun-java6-fonts sun-java6-jre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  binfmt-support
The following NEW packages will be installed
  sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/32.7MB of archives.
After unpacking 93.8MB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package sun-java6-bin.
(Reading database ... 91966 files and directories currently installed.)
Unpacking sun-java6-bin (from .../sun-java6-bin_6-03-0ubuntu2_i386.deb) ...
sun-dlj-v1-1 license has already been accepted
Selecting previously deselected package sun-java6-jre.
Unpacking sun-java6-jre (from .../sun-java6-jre_6-03-0ubuntu2_all.deb) ...
sun-dlj-v1-1 license has already been accepted
Selecting previously deselected package sun-java6-fonts.
Unpacking sun-java6-fonts (from .../sun-java6-fonts_6-03-0ubuntu2_all.deb) ...
Selecting previously deselected package sun-java6-plugin.
Unpacking sun-java6-plugin (from .../sun-java6-plugin_6-03-0ubuntu2_i386.deb) ...
Setting up sun-java6-bin (6-03-0ubuntu2) ...
/var/lib/dpkg/info/sun-java6-bin.postinst: 84: /usr/lib/jvm/java-6-sun-1.6.0.03/bin/java: not found
dpkg: error processing sun-java6-bin (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of sun-java6-plugin:
 sun-java6-plugin depends on sun-java6-bin (= 6-03-0ubuntu2); however:
  Package sun-java6-bin is not configured yet.
dpkg: error processing sun-java6-plugin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-jre:
 sun-java6-jre depends on sun-java6-bin (= 6-03-0ubuntu2) | ia32-sun-java6-bin (= 6-03-0ubuntu2); however:
  Package sun-java6-bin is not configured yet.
  Package ia32-sun-java6-bin is not installed.
dpkg: error processing sun-java6-jre (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-fonts:
 sun-java6-fonts depends on sun-java6-jre (>= 6-03-0ubuntu2); however:
  Package sun-java6-jre is not configured yet.
dpkg: error processing sun-java6-fonts (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java6-bin
 sun-java6-plugin
 sun-java6-jre
 sun-java6-fonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Pumalite on 2008-03-02
why don't you install:
sudo aptitude install build-essential
(it comes with java)
(remove the others first)

---

### Post by Pumalite on 2008-03-02
Also Synaptic>Search>java>install

---

### Post by npc100 on 2008-03-02
Already done that, but I want to use netbeans and that requires sun-java5-bin etc.

Had it all working perfectly prior to a disc failure (and subsequent reinstall of Ubuntu) 

Luckily I had backups of my source code....just wish I'd backed up the entire drive!!

---

### Post by Pumalite on 2008-03-02
Sorry to hear that. Good luck.

---

### Post by aysiu on 2008-03-02
> **Pumalite said:**
> why don't you install:
sudo aptitude install build-essential
(it comes with java)
(remove the others first)
I don't see Java in [the list of *build-essential*'s dependencies](http://packages.ubuntu.com/gutsy/build-essential).

Dependency errors like the OP's usually stem from conflicting repositories.

**Step 1**:
[Get a fresh set of repositories](http://www.psychocats.net/ubuntu/sources#key)

**Step 2**: ```
sudo apt-get update
sudo apt-get -f install
```

---

### Post by Pumalite on 2008-03-02
Sorry, I meant ubuntu-restricted-extras

---

### Post by npc100 on 2008-03-02
Thanks to both of you - I've finally got it working :)

In the hope it might help someone else in this situation, this is what I did

Removed all copies of sun-java6-bin etc, then did  the same for sun-java5-bin etc as per Pumalite's suggestion
Changed the repositories as per Aysiu's suggestion
Went into /var/cache/apt/archives and removed all the .debs there
Rebooted
Used Synaptic to download sun-java5-bin (it all installed correctly this time!)
Used Synaptic to download netbeans

...and the problems started again :(

Running netbeans as anything other than root gave me a host of Java.Io.Exceptions. This was because the netbeans.conf file was missing, so it didn't know to put files into my $HOME directory.

Copied the netbeans.conf.orig to netbeans.conf and this problem was resolved.

netbeans then started to load correctly, but gave me 140+ warnings about missing modules.

Had enough at this point, so used Synaptic to remove netbeans, went to the netbeans site and downloaded the installer from there...and it all now works :)

Again, many thanks for your help....now best back up the entire drive ;)

---

