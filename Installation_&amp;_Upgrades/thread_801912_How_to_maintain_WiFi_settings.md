---
title: "How to maintain WiFi settings?"
date: 2008-05-21
forum: Installation &amp; Upgrades
---

### Post by Flashfox on 2008-05-21
I am new to Linux. I installed Ubuntu 8.04 on a second partition of my XP Homw SP3 machine and all seems to be working fine.

However, whenever I shutdown and restart the computer, I need to reenter the WPA2 key and restart the WiFi service.

Question 1 --> How can I configure Ubuntu so that the WiFi WPA2 key stays memorized?

Question 2 --> How can I ensure that the WiFi connection automatically relinks when the system is started?

Next, regarding installations...

Question 3 --> How do I install applications? Drivers? I downloaded a .gz file (for Ubuntu) but double clicking on it fails. I tried several methods but never got the driver to install. I am certain that I am missing something.

I was trying to install a printer driver: 20070725084555687_UnifiedLinuxDriver.tar.gz

Suggestions?

Thanks in advance :confused:

---

### Post by lisati on 2008-05-21
> **Flashfox said:**
> 
Question 1 --> How can I configure Ubuntu so that the WiFi WPA2 key stays memorized?



One way is to use the Keyring Manager which, if installed properly, can be found on the System->Administration menu. Give that a try, and if you need any more help, don't be afraid to ask.

---

### Post by lisati on 2008-05-21
> **Flashfox said:**
> 
Question 3 --> How do I install applications? Drivers? I downloaded a .gz file (for Ubuntu) but double clicking on it fails. I tried several methods but never got the driver to install. I am certain that I am missing something.

 A common way of adding applications is through the "Applications"->"Add/Remove" menu, which will download and install programs for you automatically.

---

### Post by iaculallad on 2008-05-21
Questions 1 and 2 can be answered by browsing this [sticky]("http://ubuntuforums.org/showthread.php?t=318539").
For question 3: To install a .gz files, you need to extract the file first. Can be done by right-clicking on the file and selecting "Extract to". Normally file is extracted on the user's Desktop. Change directory on the Folder where the file is extracted and issue ./install (done while in the terminal).

---

### Post by Flashfox on 2008-05-21
I checked in System | Admionistration and did not fins Keyring Manager. However, there "Authorizations" folder. When I check there, I can't find any references to the Keyring Manager.

---

### Post by iaculallad on 2008-05-21
Try [this]("http://ubuntuforums.org/showthread.php?t=318539"), it gives you the idea on how to setup WiFi settings without the use of GUI. A neat workaround.

---

