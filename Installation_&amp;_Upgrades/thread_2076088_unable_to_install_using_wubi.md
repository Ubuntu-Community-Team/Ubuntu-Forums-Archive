---
title: "unable to install using wubi"
date: 2012-10-25
forum: Installation &amp; Upgrades
---

### Post by soearl6375 on 2012-10-25
When using WUBI to install Unbunto I get the following error: 

Error  executing command
>>command=C:\Windows\sysnative\bcdedit.exe /create /d
Ubunto /application bootsector
>>retval=1
>>stderr=the boot configuration data store could not be opened.
The system cannot find the file specified.

>>stdout=

---

### Post by Rubi1200 on 2012-10-26
Hi and welcome to the forums :-)

Please post some more information so we can help you.

Computer make and model, operating systems, if you have RAID etc.

The more you tell us, the better advice we can provide.

If there were other errors when attempting to install there should be a log file.

Windows side installation logs are in your user temp folder (%temp%)

Post the contents here please.

---

### Post by Karlchen on 2012-10-26
Hello, soearl6375.

Have you launched wubi.exe in elevated mode? I.e. have you right-clicked wubi.exe and selected "Run as administrator"?
Wubi needs to be run with full administrative privileges.

Apart from that please answer Rubi1200's questions and follow Rubi1200's advice.

Kind regards,
Karl

---

### Post by bcbc on 2012-10-26
Check this out: [http://askubuntu.com/q/73585/14916](http://askubuntu.com/q/73585/14916)

---

