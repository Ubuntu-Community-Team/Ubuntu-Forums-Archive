---
title: "problem with software updater"
date: 2018-08-18
forum: Installation &amp; Upgrades
---

### Post by idkwhatimdoing1.0 on 2018-08-18
Good day, I have Ubuntu 18.04 and every time I check to see if there are any upgrades to do for ubuntu I click on the software updater icon and it scans. The problem is that at around 3 quarters in the scan it stops and gives me a window that says. > Failed to download repository information. Check your internet connection now obviously my internet is fine and has no problems... I am always connected to it and this error will also happen if I'm connected through Ethernet. Now theres three button available its Settings... or Try Again or ok. If i press setings I just get into some randoma page that says its all good. If I press Try Again it just does the same thing and if I press ok it just tells me what the update are and then I can install it. So basically the warning is kinda useless as it seems to work fine but is quite annoying. Can anyone help or know what to do?

---

### Post by TheFu on 2018-08-18
Open a terminal.
Run **sudo apt update**
If that works, 
run **sudo apt upgrade**

Be happy. Forget the GUI.

If it fails, post the exact command and relevant messages back here inside "code tags" - adv reply (#) - so they are easily readable.

---

### Post by idkwhatimdoing1.0 on 2018-08-18
I ran the sudo apt update and i recieved these messages ```
Ign:1 cdrom://Ubuntu 18.04 LTS _Bionic Beaver_ - Release amd64 (20180426) bionic InRelease
Err:2 cdrom://Ubuntu 18.04 LTS _Bionic Beaver_ - Release amd64 (20180426) bionic Release
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit:3 http://archive.canonical.com/ubuntu bionic InRelease
Hit:4 http://ca.archive.ubuntu.com/ubuntu bionic InRelease                     
Hit:5 http://archive.ubuntu.com/ubuntu bionic InRelease                        
Hit:6 http://ppa.launchpad.net/git-core/ppa/ubuntu bionic InRelease            
Get:7 http://security.ubuntu.com/ubuntu bionic-security InRelease [83.2 kB]    
Get:8 http://ca.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]   
Ign:9 http://ppa.launchpad.net/paolorotolo/android-studio/ubuntu bionic InRelease
Hit:10 http://ppa.launchpad.net/webupd8team/java/ubuntu bionic InRelease       
Get:11 http://ca.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB]
Err:12 http://ppa.launchpad.net/paolorotolo/android-studio/ubuntu bionic Release
  404  Not Found [IP: 91.189.95.83 80]
Get:13 http://ca.archive.ubuntu.com/ubuntu bionic-proposed InRelease [242 kB]
Reading package lists... Done                                   
E: The repository 'cdrom://Ubuntu 18.04 LTS _Bionic Beaver_ - Release amd64 (20180426) bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/paolorotolo/android-studio/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
 
```

is this normal?

Then when I entered the command sudo apt upgrade and I got an error message. ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  antlr3 aspectj bnd default-jdk-doc java-wrappers javahelp2 junit4-doc
  libantlr-java libantlr3-runtime-java libaopalliance-java libargs4j-java
  libasm-java libasm4-java libaspectj-java libatinject-jsr330-api-java
  libbeansbinding-java libbindex-java libbsh-java libbytelist-java
  libcdi-api-java libcglib-java libcodemodel-java libcommons-beanutils-java
  libcommons-cli-java libcommons-codec-java libcommons-collections3-java
  libcommons-compress-java libcommons-digester-java libcommons-io-java
  libcommons-lang-java libcommons-lang3-java libdom4j-java libdtd-parser-java
  libeclipselink-java libequinox-osgi-java libfastinfoset-java
  libfelix-framework-java libfelix-gogo-runtime-java libfelix-main-java
  libfelix-osgi-obr-java libfelix-resolver-java libfreemarker-java
  libgeronimo-annotation-1.3-spec-java libgeronimo-interceptor-3.0-spec-java
  libgeronimo-j2ee-connector-1.5-spec-java libgeronimo-jta-1.1-spec-java
  libgeronimo-validation-1.1-spec-java libguava-java libguice-java
  libhamcrest-java-doc libhawtjni-runtime-java libhtml5parser-java
  libhttpclient-java libhttpcore-java libicu4j-4.4-java libini4j-java
  libisorelax-java libistack-commons-java libjansi-java libjansi-native-java
  libjavaewah-java libjaxb-api-java libjaxb-java libjaxen-java
  libjcodings-java libjcommander-java libjemmy2-java libjgit-java libjna-java
  libjna-jni libjna-platform-java libjnlp-servlet-java libjoda-time-java
  libjpa-2.1-spec-java libjsch-agent-proxy-java libjson-simple-java
  libjsonp-java libjsr305-java libjsr311-api-java libjvyamlb-java
  libkxml2-java liblucene3-contrib-java liblucene3-java
  libmaven-file-management-java libmaven-parent-java libmaven-resolver-java
  libmaven-shared-io-java libmaven-shared-utils-java libmaven3-core-java
  libmsv-java libmysql-java libnb-absolutelayout-java libnb-javaparser-java
  libnb-org-openide-util-java libnb-org-openide-util-lookup-java
  libosgi-annotation-java libosgi-compendium-java libosgi-core-java
  libplexus-archiver-java libplexus-cipher-java libplexus-classworlds-java
  libplexus-component-annotations-java libplexus-interpolation-java
  libplexus-io-java libplexus-sec-dispatcher-java libplexus-utils-java
  libplexus-utils2-java libpostgresql-jdbc-java librelaxng-datatype-java
  librngom-java libsdo-api-java libsequence-library-java libservlet3.1-java
  libsimple-validation-java libsisu-guice-java libsisu-inject-java
  libsisu-ioc-java libsisu-plexus-java libslf4j-java libsnappy-java
  libsnappy-jni libsqljet-java libstax-ex-java libstreambuffer-java
  libstringtemplate-java libstringtemplate4-java libsvn-java
  libsvnclientadapter-java libsvnkit-java libswing-layout-java libswingx-java
  libtrilead-ssh2-java libtxw2-java libwagon-provider-api-java
  libws-commons-util-java libxsom-java libyaml-snake-java
  linux-headers-4.15.0-31 linux-headers-4.15.0-31-generic
  linux-image-4.15.0-31-generic linux-modules-4.15.0-31-generic openjdk-11-doc
  testng
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up sympa (6.2.24~dfsg-1) ...
head: cannot open '/etc/mailname' for reading: No such file or directory
hostname: invalid option -- 'q'
dpkg: error processing package sympa (--configure):
 installed sympa package post-installation script subprocess returned error exit status 128
Errors were encountered while processing:
 sympa
E: Sub-process /usr/bin/dpkg returned an error code (1)
 
```

please help with this sympa error as it is really getting annoying as it won't back up anything

---

### Post by TheFu on 2018-08-18
Remove all extra PPAs.  These are not core and can cause dependency issues.  I'd just rename all the files to xyz.save in /etc/apt/sources.list.d/

Run the update/upgrade again. Errors? 

What's with all the java stuff? I specifically avoid anything built with java, mono,  or php.

No clue what sympa is. Sorry. Google says it is a mailing list manager.  If you don't run this on purpose, then your box is likely hacked and being used to spam the world.  If that is the case, time to nuke it from orbit and start over. That's the only way to be certain.

---

### Post by idkwhatimdoing1.0 on 2018-08-18
So the Sympa thing has been removed. I do not remember ever installing this and it's not like it would be helpeful for me as I don't send mass emails. By removing the Sympa thing everything works fine now and there's no issues. However I do have a question is there a way to find out if you've been hacked? It is either a completely weird coincidence or not but recently I've been dealing with some coding ideas with companies and I've been told it could have potential but they didn't want to patent things right now... To be honest t's kinda sketchy that my computer is acting up now...

---

### Post by TheFu on 2018-08-18
Dude.  If you didn't install sympa, then someone else did. You've been hacked.  Something like that doesn't get automatically installed accidentally.  Nuke it from orbit.   Seriously. Nuke the box. Anything less means if they left something behind, and they almost certainly did, that it, or something worse, will come back.

If you are careless and may have installed sympa ... that is different.  Pay more attention. Keep track of what you install. You don't need to track every dependency, but you should keep up with anything you manually say to install.
  In the olden days (1995), I had a separate notebook for each server I ran. Inside I'd put notes about every change I made to the system(s).  Paper.  There's something different about paper notes that just works.

That's a bunch of java stuff.  If you aren't a java programmer, it is way too much.

Don't mix desktop stuff with server stuff if the server stuff is available over the internet.  Basic security.  If anyone from the outside can access anything on the machine, it shouldn't be a desktop machine.  Lots of added risks and attacks are possible on desktops when compared to a minimal, only what is needed, server install.

---

### Post by idkwhatimdoing1.0 on 2018-08-18
Um I was downloading a lot of plug-ins in Android Studio so the java was probably from there... And I've been trying to install Netbeans but nothing is working cause of the Java things so maybe from that too... And I checked the Sympa files thing and they were empty of any emails, list etc... so maybe not. Either way I removed all programs from my laptop and changed all passwords so hopefully that helps.

---

### Post by TheFu on 2018-08-18
So you are doing java.  Then all those java things make sense.

But sympa is a server-sort of program.  It doesn't get magically installed if you didn't install it. It is your machine.

---

