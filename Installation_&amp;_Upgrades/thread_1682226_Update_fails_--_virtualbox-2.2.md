---
title: "Update fails -- virtualbox-2.2"
date: 2011-02-05
forum: Installation &amp; Upgrades
---

### Post by juny20 on 2011-02-05
I searched and tried multiple things with no luck. I am getting the following error when I tried to do a system udpate (below). It points to errors on the virtualbox-2.2 package, which was for Intrepid. I now have Maverick, but the system will not let me uninstall the package. How can I correct this? Any suggestion?

```
installArchives() failed: 
Extracting templates from packages: 24%
Extracting templates from packages: 48%
Extracting templates from packages: 72%
Extracting templates from packages: 96%
Extracting templates from packages: 100%
Preconfiguring packages ...

Extracting templates from packages: 24%
Extracting templates from packages: 48%
Extracting templates from packages: 72%
Extracting templates from packages: 96%
Extracting templates from packages: 100%
Preconfiguring packages ...
warning, in file '/var/lib/dpkg/status' near line 53665 package 'virtualbox-2.2':
 error in Version string '2.2.4-47978_Ubuntu_intrepid': invalid character in revision number
warning, in file '/var/lib/dpkg/status' near line 53666 package 'virtualbox-2.2':
 error in Config-Version string '2.2.4-47978_Ubuntu_intrepid': invalid character in revision number
warning, in file '/var/lib/dpkg/available' near line 56201 package 'virtualbox-2.2':
 error in Version string '2.2.4-47978_Ubuntu_intrepid': invalid character in revision number
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 325852 files and directories currently installed.)
Preparing to replace libc-dev-bin 2.12.1-0ubuntu10.1 (using .../libc-dev-bin_2.12.1-0ubuntu10.2_i386.deb) ...
Unpacking replacement libc-dev-bin ...
Preparing to replace libc6-dev 2.12.1-0ubuntu10.1 (using .../libc6-dev_2.12.1-0ubuntu10.2_i386.deb) ...
Unpacking replacement libc6-dev ...
Preparing to replace libc-bin 2.12.1-0ubuntu10.1 (using .../libc-bin_2.12.1-0ubuntu10.2_i386.deb) ...
Unpacking replacement libc-bin ...
Processing triggers for man-db ...
warning, in file '/var/lib/dpkg/status' near line 53668 package 'virtualbox-2.2':
 error in Version string '2.2.4-47978_Ubuntu_intrepid': invalid character in revision number
warning, in file '/var/lib/dpkg/status' near line 53669 package 'virtualbox-2.2':
 error in Config-Version string '2.2.4-47978_Ubuntu_intrepid': invalid character in revision number
warning, in file '/var/lib/dpkg/available' near line 56201 package 'virtualbox-2.2':
 error in Version string '2.2.4-47978_Ubuntu_intrepid': invalid character in revision number
Setting up libc-bin (2.12.1-0ubuntu10.2) ...
warning, in file '/var/lib/dpkg/status' near line 53667 package 'virtualbox-2.2':
 error in Version string '2.2.4-47978_Ubuntu_intrepid': invalid character in revision number
warning, in file '/var/lib/dpkg/status' near line 53668 package 'virtualbox-2.2':
 error in Config-Version string '2.2.4-47978_Ubuntu_intrepid': invalid character in revision number
warning, in file '/var/lib/dpkg/available' near line 56201 package 'virtualbox-2.2':
 error in Version string '2.2.4-47978_Ubuntu_intrepid': invalid character in revision number
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 325852 files and directories currently installed.)
Preparing to replace libc6 2.12.1-0ubuntu10.1 (using .../libc6_2.12.1-0ubuntu10.2_i386.deb) ...
Unpacking replacement libc6 ...
warning, in file '/var/lib/dpkg/status' near line 53668 package 'virtualbox-2.2':
 error in Version string '2.2.4-47978_Ubuntu_intrepid': invalid character in revision number
warning, in file '/var/lib/dpkg/status' near line 53669 package 'virtualbox-2.2':
 error in Config-Version string '2.2.4-47978_Ubuntu_intrepid': invalid character in revision number
warning, in file '/var/lib/dpkg/available' near line 56201 package 'virtualbox-2.2':
 error in Version string '2.2.4-47978_Ubuntu_intrepid': invalid character in revision number
Setting up libc6 (2.12.1-0ubuntu10.2) ...
Generating locales...
  en_AG.UTF-8... done
  en_AU.UTF-8... done
  en_BW.UTF-8... done
  en_CA.UTF-8... done
  en_DK.UTF-8... done
  en_GB.UTF-8... done
  en_HK.UTF-8... done
  en_IE.UTF-8... done
  en_IN.UTF-8... done
  en_NG.UTF-8... done
  en_NZ.UTF-8... done
  en_PH.UTF-8... done
  en_SG.UTF-8... done
  en_US.UTF-8... done
  en_ZA.UTF-8... done
  en_ZW.UTF-8... done
Generation complete.
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
warning, in file '/var/lib/dpkg/status' near line 53667 package 'virtualbox-2.2':
 error in Version string '2.2.4-47978_Ubuntu_intrepid': invalid character in revision number
warning, in file '/var/lib/dpkg/status' near line 53668 package 'virtualbox-2.2':
 error in Config-Version string '2.2.4-47978_Ubuntu_intrepid': invalid character in revision number
warning, in file '/var/lib/dpkg/available' near line 56201 package 'virtualbox-2.2':
 error in Version string '2.2.4-47978_Ubuntu_intrepid': invalid character in revision number
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 325852 files and directories currently installed.)
Preparing to replace linux-libc-dev 2.6.35-1024.42 (using .../linux-libc-dev_2.6.35-1025.44_i386.deb) ...
Unpacking replacement linux-libc-dev ...
warning, in file '/var/lib/dpkg/status' near line 53668 package 'virtualbox-2.2':
 error in Version string '2.2.4-47978_Ubuntu_intrepid': invalid character in revision number
warning, in file '/var/lib/dpkg/status' near line 53669 package 'virtualbox-2.2':
 error in Config-Version string '2.2.4-47978_Ubuntu_intrepid': invalid character in revision number
warning, in file '/var/lib/dpkg/available' near line 56201 package 'virtualbox-2.2':
 error in Version string '2.2.4-47978_Ubuntu_intrepid': invalid character in revision number
Setting up install-info (4.13a.dfsg.1-5ubuntu1) ...
/etc/environment: line 2: /proc/asound/card0/pcm0p/oss: No such file or directory
dpkg: error processing install-info (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 install-info
warning, in file '/var/lib/dpkg/status' near line 53668 package 'virtualbox-2.2':
 error in Version string '2.2.4-47978_Ubuntu_intrepid': invalid character in revision number
warning, in file '/var/lib/dpkg/status' near line 53669 package 'virtualbox-2.2':
 error in Config-Version string '2.2.4-47978_Ubuntu_intrepid': invalid character in revision number
warning, in file '/var/lib/dpkg/available' near line 56201 package 'virtualbox-2.2':
 error in Version string '2.2.4-47978_Ubuntu_intrepid': invalid character in revision number
Setting up install-info (4.13a.dfsg.1-5ubuntu1) ...
/etc/environment: line 2: /proc/asound/card0/pcm0p/oss: No such file or directory
dpkg: error processing install-info (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up libc-dev-bin (2.12.1-0ubuntu10.2) ...
Setting up linux-libc-dev (2.6.35-1025.44) ...
Setting up libc6-dev (2.12.1-0ubuntu10.2) ...

```

---

