---
title: "K3b will not start segmentation fault"
date: 2010-02-17
forum: Installation &amp; Upgrades
---

### Post by gwoodruff on 2010-02-17
Howdy, I did a clean install of Karmic keeping my home partition intact. I had to reinstall some apps but everything seems to work fine except for K3b. When I launch from the terminal I get: 
gary@Ath64-W:~$ k3b
Segmentation fault
I have uninstalled and reinstalled with the same results. Everything worked fine in 9.04.
Can anyone give me any direction as how to proceed?

Thanks, Gary

---

### Post by dearingj on 2010-02-17
When you uninstalled k3b, did you also delete its configuration file? On my computer, k3b stores its configuration in the file 'k3brc' in the folder "/home/username/.kde/share/config". Note that .kde is a hidden folder.

I'm guessing that your config file got corrupted somehow; deleting it will cause k3b to create a new one.

---

### Post by gwoodruff on 2010-02-17
Tried getting rid of the config file, reinstalled k3b and get same error. If I look at my log files the only thing I see is "Ath64-W kernel: [  364.213702] k3b[2817]: segfault at 8 ip 00007f4aaf9615a3 sp 00007fff782df9c0 error 4 in ld-2.10.1.so[7f4aaf956000+1f000]" every time I have tried to launch it.

---

### Post by gwoodruff on 2010-02-18
bump - pls help?

---

### Post by cybrsaylr on 2010-02-18
I'm having problems with K3b also. It doesn't work for me anymore while it worked fine in the past.

When I go to add song files for burning I get this error message now:

> Unable to handle the following files due to an unsupported format:
You may manually convert these audio files to wave using another application supporting the audio format and then add the wave files to the K3b project.

I can't figure out what to do.

---

### Post by SuperSonic4 on 2010-02-18
What version are you using? I had an audio error when trying to rip CDs so I rolled back to the previous version. I'm on version 1.70 and all works as expected

---

### Post by cybrsaylr on 2010-02-18
I'm using this version:

K3b
Version 1.68.0
Using KDE 4.3.2 (KDE 4.3.2)

---

### Post by gwoodruff on 2010-02-20
Cyb, try ```
sudo apt-get install libk3b6-extracodecs
```In the future please try to stay on topic in posts. My problem with k3b is not related or similar to the problem you encountered. A simple search of the forum for your error message provides the solution.

Thanks, Gary

---

### Post by cybrsaylr on 2010-02-20
gwoodruff,
Thanks that code worked like a charm.
Wasn't really certain if that problem was related or not to your problem. That was why I asked it.

In the past K3b worked issue free and Brasero gave me problems. Now with Karmic the reverse happened, Brasero works great and K3b was acting up.

---

### Post by gwoodruff on 2010-02-23
bump - anyone have any suggestions or solutions?

Gary

---

### Post by gwoodruff on 2010-02-28
bump, last attempt before I try and reload the os.

---

