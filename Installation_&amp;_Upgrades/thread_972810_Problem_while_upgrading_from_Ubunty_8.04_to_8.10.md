---
title: "Problem while upgrading from Ubunty 8.04 to 8.10"
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by aslamsha on 2008-11-06
Hi, 
I am new to Linux and and relatively new to this forum. I was using Ubuntu Hardy 8.04 and tried upgrading to 8.10 and ran into problems. The upgradation stopped showing this error message:

dpkg: error processing /var/cache/apt/archives/libelf1_0.131-4_i386.deb (--unpack):
 files list file for package `liblcms1' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/libelf1_0.131-4_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

I was wondering in the forum to find whether anybody had the same problem and stumbled upon this post [here]("http://ubuntuforums.org/showthread.php?t=949436&highlight=dpkg%3A+error+processing+(--unpack)%3A+files+list+file+package+%60liblcms1%27+missing+final+newline")

I tried following the solution given in there but without success:
Opened /var/lib/dpkg/info/liblcms1.list file and appended a newline and saved. Then I tried again but it showed the same error.

I am unable to understand the problem and need help. Is this a bug?

---

### Post by Partyboi2 on 2008-11-06
Open a terminal and backup liblcms1.list file
```
 sudo mv /var/lib/dpkg/info/liblcms1.list /var/lib/dpkg/info/liblcms1.list.old
```
then reinstall the package

```
sudo apt-get --reinstall install liblcms1
```

---

### Post by aslamsha on 2008-11-06
Thanks for reply, but there were problems again:

syed@syed-laptop:/$ sudo apt-get --reinstall install liblcms1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  bug-buddy: Depends: libelf1 (>= 0.131-1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

So, I did:
syed@syed-laptop:/$ sudo apt-get -f install 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libelf1
The following NEW packages will be installed:
  libelf1
0 upgraded, 1 newly installed, 0 to remove and 363 not upgraded.
30 not fully installed or removed.
Need to get 0B/45.9kB of archives.
After this operation, 143kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 
dpkg: serious warning: files list file for package `liblcms1' missing, assuming package has no files currently installed.
194814 files and directories currently installed.)
Unpacking libelf1 (from .../libelf1_0.131-4_i386.deb) ...
Setting up liblcms1 (1.16-10) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing liblcms1 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of openjdk-6-jre-headless:
 openjdk-6-jre-headless depends on liblcms1; however:
  Package liblcms1 is not configured yet.
dpkg: error processing openjdk-6-jre-headless (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openjdk-6-jre-lib:
 openjdk-6-jre-lib depends on openjdk-6-jre-headless (>= 6b11); however:
  Package openjdk-6-jre-headless is not configured yet.
dpkg: error processing openjdk-6-jre-lib (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openjdk-6-jre:
 openjdk-6-jre depends on openjdk-6-jre-headless (>= 6b12-0ubuntu6); however:
  Package openjdk-6-jre-headless is not configured yet.
dpkg: error processing openjdk-6-jre (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openjdk-6-jdk:
 openjdk-6-jdk depends on openjdk-6-jre (>= 6b12-0ubuntu6); however:
 No apport report written because the error message indicates its a followup error from a previous failure.
                           No apport report written because the error message indicates its a followup error from a previous failure.
                                                     No apport report written because MaxReports is reached already
                                   No apport report written because MaxReports is reached already
                  Package openjdk-6-jre is not configured yet.
dpkg: error processing openjdk-6-jdk (--configure):
 dependency problems - leaving unconfigured
Setting up libgd2-xpm (2.0.36~rc1~dfsg-3ubuntu1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing libgd2-xpm (--configure):
 subprocess post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libgraphviz4:
 libgraphviz4 depends on libgd2-noxpm (>= 2.0.36~rc1~dfsg) | libgd2-xpm (>= 2.0.36~rc1~dfsg); however:
  Package libgd2-noxpm is not installed.
  Package libgd2-xpm is not configured yet.
dpkg: error processing libgraphviz4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmagick10:
 libmagick10 depends on libgraphviz4 (>= 2.18); however:
  Package libgraphviz4 is not configured yet.
 libmagick10 depends on liblcms1 (>= 1.15-1); however:
  Package liblcms1 is not configured yet.
dpkg: error processing libmagick10 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxine1-misc-plugins:
 libxine1-misc-plugins depends on libmagick10; however:
  Package libmagick10 is not configured yet.
dpkg: error processing libxine1-misc-plugins (--configure):
 dependency problems - leaving unconfigured
Setting up libmad0 (0.15.1b-3) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            No apport report written because MaxReports is reached already
                          dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing libmad0 (--configure):
 subprocess post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libxine1-ffmpeg:
 libxine1-ffmpeg depends on libmad0 (>= 0.15.1b-3); however:
  Package libmad0 is not configured yet.
dpkg: error processing libxine1-ffmpeg (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libxine1-plugins:
 libxine1-plugins depends on libxine1-ffmpeg (>= 1.1.15-0ubuntu3); however:
  Package libxine1-ffmpeg is not configured yet.
 libxine1-plugins depends on libxine1-misc-plugins (>= 1.1.15-0ubuntu3); however:
  Package libxine1-misc-plugins is not configured yet.
dpkg: error processing libxine1-plugins (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxine1-misc-plugins (= 1.1.15-0ubuntu3) | libxine1-plugins (= 1.1.15-0ubuntu3); however:
  Package libxine1-misc-plugins is not configured yet.
  Package libxine1-plugins is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of gxine:
 gxine depends on libxine1 (>= 1.1.8); however:
  Package libxine1 is not configured yet.
dpkg: error processing gxine (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of amarok-engine-xine:
 amarok-engine-xine depends on libxine1 (>= 1.1.8); however:
  Package libxine1 is not configured yet.
dpkg: error processing amarok-engine-xine (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of amarok:
 amarok depends on amarok-engine-xine (= 2:1.4.10-0ubuntu3) | amarok-engine-yauap (= 2:1.4.10-0ubuntu3); however:
  Package amarok-engine-xine is not configured yet.
  Package amarok-engine-yauap is not installed.
dpkg: error processing amarok (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up libelf1 (0.131-4) ...

Setting up bug-buddy (2.24.1dfsg-0ubuntu1) ...

dpkg: dependency problems prevent configuration of default-jre-headless:
 default-jre-headless depends on openjdk-6-jre-headless (>= 6b11); however:
  Package openjdk-6-jre-headless is not configured yet.
dpkg: error processing default-jre-headless (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of default-jre:
 default-jre depends on default-jre-headless (= 1.6-30ubuntu3); however:
  Package default-jre-headless is not configured yet.
 default-jre depends on openjdk-6-jre (>= 6b11); however:
  Package openjdk-6-jre is not configured yet.
dpkg: error processing default-jre (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of default-jdk:
 default-jdk depends on default-jre (= 1.6-30ubuntu3); however:
  Package default-jre is not configured yet.
 default-jdk depends on openjdk-6-jdk (>= 6b11); however:
  Package openjdk-6-jdk is not configured yet.
dpkg: error processing default-No apport report written because MaxReports is reached already
             No apport report written because MaxReports is reached already
                                                                           No apport report written because MaxReports is reached already
                                                         No apport report written because MaxReports is reached already
                                       No apport report written because MaxReports is reached already
                     No apport report written because MaxReports is reached already
   No apport report written because MaxReports is reached already
                                                                 No apport report written because MaxReports is reached already
                                               No apport report written because MaxReports is reached already
                             No apport report written because MaxReports is reached already
           No apport report written because MaxReports is reached already
                                                                         No apport report written because MaxReports is reached already
                                                       jdk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of eog:
 eog depends on liblcms1 (>= 1.15-1); however:
  Package liblcms1 is not configured yet.
dpkg: error processing eog (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gimp:
 gimp depends on liblcms1 (>= 1.15-1); however:
  Package liblcms1 is not configured yet.
dpkg: error processing gimp (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of imagemagick:
 imagemagick depends on liblcms1 (>= 1.15-1); however:
  Package liblcms1 is not configured yet.
 imagemagick depends on libmagick10; however:
  Package libmagick10 is not configured yet.
dpkg: error processing imagemagick (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libnb-java2-java:
 libnb-java2-java depends on default-jdk | sun-java6-jdk; however:
  Package default-jdk is not configured yet.
  Package sun-java6-jdk is not installed.
dpkg: error processing libnb-java2-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libnb-apisupport1-java:
 libnb-apisupport1-java depends on libnb-java2-java (= 6.1-0ubuntu1); however:
  Package libnb-java2-java is not configured yet.
dpkg: error processing libnb-apisupport1-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of miro:
 miro depends on libxine1 (>= 1.1.8); however:
  Package libxine1 is not configured yet.
 miro depends on imagemagick; however:
  Package imagemagick is not configured yet.
 miro depends on libxine1-plugins (>= 1.1.12); however:
  Package libxine1-plugins is not configured yet.
dpkg: error processing miro (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php5-gd:
 php5-gd depends on libgd2-xpm (>= 2.0.36~rc1~dfsg); however:
  Package libgd2-xpm is not configured yet.
dpkg: error processing php5-gd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rss-glx:
 rss-glx depends on libmagick10; however:
  Package libmagick10 is not configured yet.
dpkg: error processing rss-glx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on eog; however:
  Package eog is not configured yet.
 ubuntu-desktop depends on rss-glx; however:
  Package rss-glx is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ca-certificates-java:
 ca-certificates-java depends on openjdk-6-jre-headless | cacao-oj6-jre-headless | sun-java6-jre-headless; however:
  Package openjdk-6-jre-headless is not configured yet.
  Package cacao-oj6-jre-headless is not installed.
  Package sun-java6-jre-headless is not installed.
dpkg: error processing ca-certificates-java (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc6 ...
No apport report written because MaxReports is reached already
                                                              ldconfig deferred processing now taking place
Errors were encountered while processing:
 liblcms1
 openjdk-6-jre-headless
 openjdk-6-jre-lib
 openjdk-6-jre
 openjdk-6-jdk
 libgd2-xpm
 libgraphviz4
 libmagick10
 libxine1-misc-plugins
 libmad0
 libxine1-ffmpeg
 libxine1-plugins
 libxine1
 gxine
 amarok-engine-xine
 amarok
 default-jre-headless
 default-jre
 default-jdk
 eog
 gimp
 imagemagick
 libnb-java2-java
 libnb-apisupport1-java
 miro
 php5-gd
 rss-glx
 ubuntu-desktop
 ca-certificates-java
E: Sub-process /usr/bin/dpkg returned an error code (1)

Unable to figure out where I am going wrong?

---

