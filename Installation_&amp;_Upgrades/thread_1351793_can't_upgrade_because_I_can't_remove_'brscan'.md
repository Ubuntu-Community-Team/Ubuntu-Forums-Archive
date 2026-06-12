---
title: "can't upgrade because I can't remove 'brscan'"
date: 2009-12-10
forum: Installation &amp; Upgrades
---

### Post by cetandi on 2009-12-10
Hi I am reasonably new and i can't figure out how to paste here so can someone read this attachment and help me because I can't upgrade to the next version (i have 8.04)
Thanks!!

---

### Post by gspat on 2009-12-11
> I've been trying to upgrade from 8.04 to the next version ...

AND I get message  “partial upgrade only”, so I  try the partial upgrade and nothing happens, for example the screen that says it's performing the partial upgrade, disappears.
I can't remember the process I went through, but through searching forums and trying things out in the terminal, I found out that the problem is a file called brscan (brother printer drivers I believe) and when I tried to get rid of the little devil in package manager I get “  E: brscan: subprocess post-removal script returned error exit status 1”

Upon further reading I tried this command    sudo apt-get purge brscan

and here's the latest:

 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
The following packages were automatically installed and are no longer required: 
  libswfdec-0.6-90 libmono-peapi2.0-cil libncursesw5-dev 
  libboost-date-time1.34.1 libnss3-dev libnspr4-dev libestools1.2 
Use 'apt-get autoremove' to remove them. 
The following packages will be REMOVED: 
  brscan 
0 upgraded, 0 newly installed, 1 to remove and 82 not upgraded. 
1 not fully installed or removed. 
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable) 
E: Unable to lock the download directory 

I at a loss...could someone help....Thank you

P.S. I'd also like to know if I have to upgrade to the latest version by upgrading all the upgrades chronologically, or if I can skip something, and get there easier

hi.. I pasted your file in so it's easier to get at...

the error you showed simply means you have more than 1 package manager running (either through the terminal or in seperate windows) you can only have 1 open, period. the package removal should work then.

---

### Post by cetandi on 2009-12-18
Hey thanks...I have no idea how I had two running but I just tried again out of synaptic package manager, and after marking for complete removal, I get:


E: brscan: subprocess post-removal script returned error exit status 1

therefore I am still stumped....:confused:

---

### Post by cetandi on 2009-12-24
Btw I just recieved a message from Brother support, and this is what happened when I tried to un install brscan
 cetandi@cetandi-desktop:~$  dpkg  -P brscan
dpkg: requested operation requires superuser privilege
cetandi@cetandi-desktop:~$ sudo dpkg -P brscan
[sudo] password for cetandi: 
(Reading database ... 187266 files and directories currently installed.)
Removing brscan ...
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHL': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHL2': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHL2FB': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHLFB': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHMFB': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHminiFB': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/YL4': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/YL4FB': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/ZL2': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/ZL2FB': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/ZLe': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/ZLeFB': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane': No such file or directory
dpkg: error processing brscan (--purge):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 brscan


signed:
still stumped

---

### Post by davel1232 on 2010-05-01
I had the same issue. I found that the file path being used for removal did not match the actual location of th Brother files. They were in: /usr/Brother/... 
I moved the entire "Brother" file to /usr/local/Brother and then I was able to remove the brscan files and upgrade. 

dave@dave-laptop:~$ sudo mv /usr/Brother /usr/local/Brother
dave@dave-laptop:~$ sudo apt-get install -f

this removed brscan.
I was able to complete the upgrade. 
hope this helps.

---

### Post by thomasw81 on 2010-05-27
Good fix. I had the same problem with brscan, but no files whatsoever in /usr/local. So synaptic could not remove the package. I created the /usr/local/Brother and /usr/local/Brother/sane directory and was able to remove brscan with synaptic.

---

### Post by violin.yanev on 2010-11-30
Sounds like a poorly written Brother driver for linux to me...

---

