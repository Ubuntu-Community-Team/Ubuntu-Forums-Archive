---
title: "java troubles since upgrade to 12.04 and trying to install some software"
date: 2012-05-05
forum: Installation &amp; Upgrades
---

### Post by gnowledge on 2012-05-05
disclaimer:
I am on a different computer from what I was using in the earlier posts of this account (that install never went through, dunno why i'm telling you all this, I'm using the wrong ubuntuforums account atm, but whatever)

I recently upgraded from 11.10 to 12.04, and now after I try to do pretty much anything from installing new software to disabling third-party repositories I get messages complaining about Oracle JDK 7 Installer and so on. It seems this may have occurred after I installed some software, openrocket, I believe.

running sudo apt-get install -f (which I was recommended to try by the computer after the more straight forward sudo apt-get install oracle-java7-installer didn't work) I get this:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  python-central
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  oracle-java7-installer
Suggested packages:
  ttf-kochi-gothic ttf-sazanami-gothic ttf-kochi-mincho ttf-sazanami-mincho
  ttf-arphic-uming
The following packages will be upgraded:
  oracle-java7-installer
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/14.5 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up oracle-java7-installer (7u3-0~eugenesan~precise4) ...
Downloading...
--2012-05-05 02:12:09--  http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz
Resolving download.oracle.com (download.oracle.com)... 64.71.251.171, 64.71.251.160
Connecting to download.oracle.com (download.oracle.com)|64.71.251.171|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz [following]
--2012-05-05 02:12:09--  https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz
Resolving edelivery.oracle.com (edelivery.oracle.com)... 23.61.6.174
Connecting to edelivery.oracle.com (edelivery.oracle.com)|23.61.6.174|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://download.oracle.com/errors/download-fail-1505220.html [following]
--2012-05-05 02:12:10--  http://download.oracle.com/errors/download-fail-1505220.html
Connecting to download.oracle.com (download.oracle.com)|64.71.251.171|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5307 (5.2K) [text/html]
Saving to: `./jdk-7u3-linux-i586.tar.gz'

     0K .....                                                 100%  490K=0.01s

2012-05-05 02:12:10 (490 KB/s) - `./jdk-7u3-linux-i586.tar.gz' saved [5307/5307]

Download done.
sha256sum mismatch jdk-7u3-linux-i586.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of oracle-jdk7-installer:
 oracle-jdk7-installer depends on oracle-java7-installer; however:
  Package oracle-java7-installer is not configured yet.
dpkg: error processing oracle-jdk7-installer (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                 Errors were encountered while processing:
 oracle-java7-installer
 oracle-jdk7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

And when I try to remove either Open JDK 6 or 7 Runtime, I get an alert in Ubuntu Software Centre stating "Items cannot be installed or removed until the package catalogue is repaired. Do you want to repair it now? Once Update Manager has finished the repairs you can close it and return to the store. So then I click Repair.. I authenticate and then it says Package operation failed The installation or removal of a software package failed. I go to check out the details of it all and I get this:
```
installArchives() failed: Setting up oracle-java7-installer (7u3-0~eugenesan~precise4) ...
Downloading...
--2012-05-05 02:26:40--  http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz
Resolving download.oracle.com (download.oracle.com)... 64.71.251.171, 64.71.251.160
Connecting to download.oracle.com (download.oracle.com)|64.71.251.171|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz [following]
--2012-05-05 02:26:40--  https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz
Resolving edelivery.oracle.com (edelivery.oracle.com)... 23.11.250.174
Connecting to edelivery.oracle.com (edelivery.oracle.com)|23.11.250.174|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://download.oracle.com/errors/download-fail-1505220.html [following]
--2012-05-05 02:26:41--  http://download.oracle.com/errors/download-fail-1505220.html
Connecting to download.oracle.com (download.oracle.com)|64.71.251.171|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5307 (5.2K) [text/html]
Saving to: `./jdk-7u3-linux-i586.tar.gz'

     0K .....                                                 100% 2.35M=0.002s

2012-05-05 02:26:41 (2.35 MB/s) - `./jdk-7u3-linux-i586.tar.gz' saved [5307/5307]

Download done.
sha256sum mismatch jdk-7u3-linux-i586.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of oracle-jdk7-installer:
 oracle-jdk7-installer depends on oracle-java7-installer; however:
  Package oracle-java7-installer is not configured yet.
dpkg: error processing oracle-jdk7-installer (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 oracle-java7-installer
 oracle-jdk7-installer
Error in function: 
Setting up oracle-java7-installer (7u3-0~eugenesan~precise4) ...
Downloading...
--2012-05-05 02:26:41--  http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz
Resolving download.oracle.com (download.oracle.com)... 64.71.251.171, 64.71.251.160
Connecting to download.oracle.com (download.oracle.com)|64.71.251.171|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz [following]
--2012-05-05 02:26:42--  https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz
Resolving edelivery.oracle.com (edelivery.oracle.com)... 23.11.250.174
Connecting to edelivery.oracle.com (edelivery.oracle.com)|23.11.250.174|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://download.oracle.com/errors/download-fail-1505220.html [following]
--2012-05-05 02:26:42--  http://download.oracle.com/errors/download-fail-1505220.html
Connecting to download.oracle.com (download.oracle.com)|64.71.251.171|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5307 (5.2K) [text/html]
Saving to: `./jdk-7u3-linux-i586.tar.gz'

     0K .....                                                 100% 2.63M=0.002s

2012-05-05 02:26:42 (2.63 MB/s) - `./jdk-7u3-linux-i586.tar.gz' saved [5307/5307]

Download done.
sha256sum mismatch jdk-7u3-linux-i586.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of oracle-jdk7-installer:
 oracle-jdk7-installer depends on oracle-java7-installer; however:
  Package oracle-java7-installer is not configured yet.
dpkg: error processing oracle-jdk7-installer (--configure):
 dependency problems - leaving unconfigured
```

So I can't remove the software I need to remove in order to remove or install any software. Or update Java on my computer at all. If it helps anything at all, here's an lspci readout:
```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
03:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```

---

### Post by sourchier on 2012-05-05
What happens if you try sudo apt-get clean then sudo apt-get autoclean. Can it download the package then?

---

### Post by gnowledge on 2012-05-05
Those commands run just fine. So I try to install the package after that but.. It then says

"The package system is broken
Check if you are you are using third-party repositories. If so, disable them, because they are a common source of problems. Furthermore, run the following command in a Terminal: apt-get install -f"

with the Details listed as "The following packages have unmet dependencies:

oracle-java7-installer: "

So then I run sudo apt-get install -f as it recommends, and then blam. Back to square one.

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  python-central
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  oracle-java7-installer
Suggested packages:
  ttf-kochi-gothic ttf-sazanami-gothic ttf-kochi-mincho ttf-sazanami-mincho
  ttf-arphic-uming
The following packages will be upgraded:
  oracle-java7-installer
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 14.5 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ppa.launchpad.net/webupd8team/java/ubuntu/ precise/main oracle-java7-installer all 7u4-0~webupd8~0 [14.5 kB]
Fetched 14.5 kB in 0s (27.6 kB/s)                 
Setting up oracle-java7-installer (7u3-0~eugenesan~precise4) ...
Downloading...
--2012-05-05 04:42:53--  http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz
Resolving download.oracle.com (download.oracle.com)... 66.185.85.137, 66.185.85.139
Connecting to download.oracle.com (download.oracle.com)|66.185.85.137|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz [following]
--2012-05-05 04:42:53--  https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz
Resolving edelivery.oracle.com (edelivery.oracle.com)... 23.60.146.174
Connecting to edelivery.oracle.com (edelivery.oracle.com)|23.60.146.174|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://download.oracle.com/errors/download-fail-1505220.html [following]
--2012-05-05 04:42:54--  http://download.oracle.com/errors/download-fail-1505220.html
Connecting to download.oracle.com (download.oracle.com)|66.185.85.137|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5307 (5.2K) [text/html]
Saving to: `./jdk-7u3-linux-i586.tar.gz'

     0K .....                                                 100% 7.22M=0.001s

2012-05-05 04:42:54 (7.22 MB/s) - `./jdk-7u3-linux-i586.tar.gz' saved [5307/5307]

Download done.
sha256sum mismatch jdk-7u3-linux-i586.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of oracle-jdk7-installer:
 oracle-jdk7-installer depends on oracle-java7-installer; however:
  Package oracle-java7-installer is not configured yet.
dpkg: error processing oracle-jdk7-installer (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            Errors were encountered while processing:
 oracle-java7-installer
 oracle-jdk7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by gnowledge on 2012-05-05
running sudo apt-get install oracle-jdk7-installer in the terminal after autoclean gets me this:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
oracle-jdk7-installer is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 oracle-java7-installer : Conflicts: oracle-jdk7-installer
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
mdavis@lobstermeat94:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
mdavis@lobstermeat94:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  python-central
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  oracle-java7-installer
Suggested packages:
  ttf-kochi-gothic ttf-sazanami-gothic ttf-kochi-mincho ttf-sazanami-mincho
  ttf-arphic-uming
The following packages will be upgraded:
  oracle-java7-installer
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 14.5 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ppa.launchpad.net/webupd8team/java/ubuntu/ precise/main oracle-java7-installer all 7u4-0~webupd8~0 [14.5 kB]
Fetched 14.5 kB in 0s (27.3 kB/s)                 
Setting up oracle-java7-installer (7u3-0~eugenesan~precise4) ...
Downloading...
--2012-05-05 04:50:15--  http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz
Resolving download.oracle.com (download.oracle.com)... 66.185.85.137, 66.185.85.139
Connecting to download.oracle.com (download.oracle.com)|66.185.85.137|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz [following]
--2012-05-05 04:50:15--  https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz
Resolving edelivery.oracle.com (edelivery.oracle.com)... 23.60.146.174
Connecting to edelivery.oracle.com (edelivery.oracle.com)|23.60.146.174|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://download.oracle.com/errors/download-fail-1505220.html [following]
--2012-05-05 04:50:15--  http://download.oracle.com/errors/download-fail-1505220.html
Connecting to download.oracle.com (download.oracle.com)|66.185.85.137|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5307 (5.2K) [text/html]
Saving to: `./jdk-7u3-linux-i586.tar.gz'

     0K .....                                                 100% 1.67M=0.003s

2012-05-05 04:50:15 (1.67 MB/s) - `./jdk-7u3-linux-i586.tar.gz' saved [5307/5307]

Download done.
sha256sum mismatch jdk-7u3-linux-i586.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of oracle-jdk7-installer:
 oracle-jdk7-installer depends on oracle-java7-installer; however:
  Package oracle-java7-installer is not configured yet.
dpkg: error processing oracle-jdk7-installer (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 oracle-java7-installer
 oracle-jdk7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
and then the software update centre pops up with its message again about being unable to add or remove software.

---

### Post by sourchier on 2012-05-05
Can you try the fix procedure included here:

[http://www.liberiangeek.net/2012/04/fix-duplicate-sources-list-entry-errors-in-ubuntu-12-04-precise-pangolin/]("http://www.liberiangeek.net/2012/04/fix-duplicate-sources-list-entry-errors-in-ubuntu-12-04-precise-pangolin/")

Or the fix described here:

[http://rootzwiki.com/topic/23008-howto-install-java-7-on-ubuntu-1204/]("http://rootzwiki.com/topic/23008-howto-install-java-7-on-ubuntu-1204/")

---

### Post by Tanker Bob on 2012-05-05
Try running "sudo dpkg-reconfigure -a" in a terminal without the quotes. That will rebuild the pacakge system. I had to do that after GIMP 2.8 broke my package system yesterday. It takes a while to run, so be patient. It worked fine for me.

---

### Post by trent1799 on 2012-07-05
I had this problem and the link

[http://rootzwiki.com/topic/23008-howto-install-java-7-on-ubuntu-1204/](http://rootzwiki.com/topic/23008-howto-install-java-7-on-ubuntu-1204/)

worked for me.

---

### Post by QIII on 2012-07-05
Although this is a somewhat old post and the OP is surely long gone, the following may provide some edification for those who happen on the thread:

At this time, the eugenesan/java PPA is broken.  

The solution above, although functional, will not leave the user with an automatic update of Oracle Java as updates are released.  webupd8.org has a PPA that is updated as Oracle releases Java updates and the user does not need to reinstall from the Oracle website each time.

For a suggested method to fix this issue, please see the Java wiki link in my signature.  In the table of contents, find "Command Line Methods" under "Oracle Java 7".

Near the end of the Oracle Java 7 section, I have added a note about this issue and a remedy.

---

