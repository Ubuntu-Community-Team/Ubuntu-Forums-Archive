---
title: "&quot;apt-get&quot; trouble.... help"
date: 2007-07-17
forum: Installation &amp; Upgrades
---

### Post by retroP on 2007-07-17
ok well I was trying to install limewire and whatnot and now after a bunch of b.s I got it installed but now when ever I try to "sudo apt-get" anything it give me this:

```
~$ sudo apt-get install clamav
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  clamav-base clamav-freshclam libclamav2 libgmp3c2
Suggested packages:
  unrar lha clamav-docs
Recommended packages:
  arj unzoo
The following NEW packages will be installed:
  clamav clamav-base clamav-freshclam libclamav2 libgmp3c20 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 11.6MB of archives.
After unpacking 13.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libgmp3c2 libclamav2 clamav-base clamav-freshclam clamav
Install these packages without verification [y/N]? y
Err http://us.archive.ubuntu.com feisty/main libgmp3c2 2:4.2.1+dfsg-4build1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com feisty-security/universe libclamav2 0.90.2-0ubuntu1.3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com feisty-security/universe clamav-base 0.90.2-0ubuntu1.3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com feisty-security/universe clamav-freshclam 0.90.2-0ubuntu1.3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com feisty-security/universe clamav 0.90.2-0ubuntu1.3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gmp/libgmp3c2_4.2.1+dfsg-4build1_i386.deb  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/pool/universe/c/clamav/libclamav2_0.90.2-0ubuntu1.3_i386.deb  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/pool/universe/c/clamav/clamav-base_0.90.2-0ubuntu1.3_all.deb  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/pool/universe/c/clamav/clamav-freshclam_0.90.2-0ubuntu1.3_i386.deb  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/pool/universe/c/clamav/clamav_0.90.2-0ubuntu1.3_i386.deb  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

and then when I try all the update I get this:


```
~$ sudo apt-get update
Password:
Err http://medibuntu.sos-sts.com feisty Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://medibuntu.sos-sts.com feisty/free Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://medibuntu.sos-sts.com feisty/non-free Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com feisty-security Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com feisty-security/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com feisty-security/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com feisty-security/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com feisty-security/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com feisty Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com feisty/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com feisty/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com feisty/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com feisty/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com feisty-updates Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com feisty-updates/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com feisty-updates/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/Release.gpg  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/free/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
retrop@retrop-desktop:~$ sudo apt-get install clamav
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  clamav-base clamav-freshclam libclamav2 libgmp3c2
Suggested packages:
  unrar lha clamav-docs
Recommended packages:
  arj unzoo
The following NEW packages will be installed:
  clamav clamav-base clamav-freshclam libclamav2 libgmp3c2
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 11.6MB of archives.
After unpacking 13.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libgmp3c2 libclamav2 clamav-base clamav-freshclam clamav
Install these packages without verification [y/N]? y
Err http://security.ubuntu.com feisty-security/universe libclamav2 0.90.2-0ubuntu1.3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com feisty-security/universe clamav-base 0.90.2-0ubuntu1.3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com feisty-security/universe clamav-freshclam 0.90.2-0ubuntu1.3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com feisty-security/universe clamav 0.90.2-0ubuntu1.3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com feisty/main libgmp3c2 2:4.2.1+dfsg-4build1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gmp/libgmp3c2_4.2.1+dfsg-4build1_i386.deb  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/pool/universe/c/clamav/libclamav2_0.90.2-0ubuntu1.3_i386.deb  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/pool/universe/c/clamav/clamav-base_0.90.2-0ubuntu1.3_all.deb  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/pool/universe/c/clamav/clamav-freshclam_0.90.2-0ubuntu1.3_i386.deb  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/pool/universe/c/clamav/clamav_0.90.2-0ubuntu1.3_i386.deb  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
retrop@retrop-desktop:~$ 
```

I"ve tried all kinds of stuff to try and get it on my own, but phailed horribly.... can some one please help out here?

---

### Post by az on 2007-07-17
"Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)"

Are you using a proxy and is it properly configured?

---

### Post by retroP on 2007-07-17
> **az said:**
> "Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)"

Are you using a proxy and is it properly configured?

might be it, I was messing with one,  and a firewall. firehol and a firefox add on called PhProxy. If thats it how could I restore defaults to my system?

---

### Post by retroP on 2007-07-17
also all this happend after installing the limewire java stuff..... think that might have messed me up.

---

### Post by az on 2007-07-18
> **retroP said:**
> might be it, I was messing with one,  and a firewall. firehol and a firefox add on called PhProxy. If thats it how could I restore defaults to my system?

See here:
[https://help.ubuntu.com/community/AptGetHowto?highlight=%28proxy%29](https://help.ubuntu.com/community/AptGetHowto?highlight=%28proxy%29)

Quote:

"Setting up apt-get to use a http-proxy
These are three methods of using apt-get with a http-proxy. 

Method 1. 

This is a temporary method that you can manually use each time you want to use apt-get through a http-proxy. This method is useful if you only want to temporarily use a http-proxy. 

Enter this line in the terminal prior to using apt-get (substitute your details for yourproxyaddress and proxyport). 

export http_proxy=http://yourproxyaddress:proxyportMethod 2. 

This method uses the apt.conf file which is found in your /etc/apt/ directory. This method is useful if you only want apt-get (and not other applications) to use a http-proxy permanently. 

Note:- On some installations there will be no apt-conf file set up. This procedure will either edit an existing apt-conf file or create a new apt-conf file. 

gksudo gedit /etc/apt/apt.confAdd this line to your apt.conf file (substitute your details for yourproxyaddress and proxyport). 

Acquire::http::Proxy "http://yourproxyaddress:proxyport";Save the apt.conf file. 

Method 3. 

This method adds a two lines to your .bashrc file in your $HOME directory. This method is useful if you would like apt-get and other applications for instance wget, to use a http-proxy. 

gedit ~/.bashrcadd these lines to the bottom of your .bashrc file (substitute your details for yourproxyaddress and proxyport) 

http_proxy=http://yourproxyaddress:proxyport
export http_proxySave the file. Close your terminal window and then open another terminal window 

Test proxy with sudo apt-get update and whatever networking tool you desire. I use firestarter to see active connections. 

If you make a mistake and go back to edit the file again, remember to close the terminal and reopen it. It will not function with the new settings until you do. "

---

