---
title: "broken apt-get update due to cups"
date: 2011-01-09
forum: Installation &amp; Upgrades
---

### Post by skela on 2011-01-09
I am struggling to upgrade packages (even install packages) using apt-get, aptitude or synaptic.
It keeps getting stuck on the cups package.

Doing a:
sudo apt-get install -f

Results in 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
warning, in file '/var/lib/dpkg/status' near line 60331 package 'virtualbox-3.1':
 error in Version string '3.1.6-59338_Ubuntu_hardy': invalid character in revision number
warning, in file '/var/lib/dpkg/status' near line 60332 package 'virtualbox-3.1':
 error in Config-Version string '3.1.6-59338_Ubuntu_hardy': invalid character in revision number
warning, in file '/var/lib/dpkg/status' near line 62533 package 'virtualbox-2.2':
 error in Version string '2.2.4-47978_Ubuntu_hardy': invalid character in revision number
warning, in file '/var/lib/dpkg/status' near line 62534 package 'virtualbox-2.2':
 error in Config-Version string '2.2.4-47978_Ubuntu_hardy': invalid character in revision number
warning, in file '/var/lib/dpkg/status' near line 62671 package 'virtualbox-2.1':
 error in Version string '2.1.4-42893_Ubuntu_hardy': invalid character in revision number
warning, in file '/var/lib/dpkg/status' near line 62672 package 'virtualbox-2.1':
 error in Config-Version string '2.1.4-42893_Ubuntu_hardy': invalid character in revision number
warning, in file '/var/lib/dpkg/available' near line 63765 package 'virtualbox-3.1':
 error in Version string '3.1.6-59338_Ubuntu_hardy': invalid character in revision number
warning, in file '/var/lib/dpkg/available' near line 66113 package 'virtualbox-2.2':
 error in Version string '2.2.4-47978_Ubuntu_hardy': invalid character in revision number
warning, in file '/var/lib/dpkg/available' near line 66245 package 'virtualbox-2.1':
 error in Version string '2.1.4-42893_Ubuntu_hardy': invalid character in revision number
Setting up cups (1.4.4-6ubuntu2.3) ...

Where it stops.
Anyone have a fix for this?

---

### Post by dino99 on 2011-01-09
you might clean the room :(

note: hardy is no more maintained (outdated)

into synaptic: check you only use genuine ubuntu repo (third parties) and use the same release.

why all these old virtualbox: remove them (with synaptic) and install 4.0 from oracle

sudo rm /var/cache/apt/archives/*

then update, upgrade again

---

### Post by funkydunky on 2011-04-26
I am having a similar problem whn trying to upgrade from 10.10 to 11.04 using apt-get. Everything was fine until it tried to upgrade CUPS. At this point the upgrade hangs with:

Preparing to replace cups 1.4.4-6ubuntu2.3 (using .../cups_1.4.6-5ubuntu1_i386.deb) ...

The only way to get out is to kill the process. After this I ran 'dpkg --configure -a' as the upgrade had crashed and got the following message:

dpkg: error processing cups (--configure):
 Package is in a very bad inconsistent state - you should reinstall it before attempting configuration.
Errors were encountered while processing:
 cups

I have tried reinstalling CUPS but again the process hangs at the first message. I have also tried to completely remove CUPS but get a message saying I should reinstall it before removing it.

I tried to do the rest of the upgrade while ignoring CUPS but cannot. I tried using synaptic and CUPS is automatically checked for upgrade and I cannot uncheck it. This now hangs whenever I try to do something as it gets stuck with CUPS. 

I have had a look around various forums and tried suggested solutions for similar problems but nothing has worked. Now I am completely stuck with a half upgraded laptop and no idea how to proceed. Any suggestions?

---

### Post by funkydunky on 2011-04-26
Ok, I managed to get the upgrade to finish. I ran the command:

dpkg -i /var/cache/apt/archives/cups_1.4.6-5ubuntu1_i386.deb 

This hung but I was able to force it to go on using 'Ctrl-C' when it did so. I had to do this a couple of times in the process. I got some error messages but it seemed to work. After that I just ran:

apt-get upgrade

apt-get dist-upgrade

and so on and was able to finish upgrading my system. When This was finished I reinstalled CUPS with synaptic and then reinstalled the other CUPS packages I'd removed earlier.

Things seem to be fine now.

---

