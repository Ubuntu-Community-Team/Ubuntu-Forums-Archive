---
title: "Install CD wont load live session"
date: 2008-01-14
forum: Installation &amp; Upgrades
---

### Post by mic159 on 2008-01-14
I just recently made a new PC, and i wish to install ubuntu on it. iv installed ubuntu on various other computers and it worked.

My system is:
Asus P5E
XFX 8800GT (x2, Not SLI)
Intel Core2 Quad 6600
4GB OCZ 6400 ram

I am using the 64bit version of ubuntu 7.10.

When i booted the CD without the quiet and splash options, i managed to find that it says "No screens found" when its trying to start X.

When booting normally (with quiet and splash), it just goes from the menu to a black screen (the monitor says no siginal).

What can i do? even the safe graphics mode does the same :confused:

---

### Post by PmDematagoda on 2008-01-14
I suggest you try the Alternate CD, the Alternate CD can be obtained from [here]("http://www.ubuntu.com/getubuntu/download"), just check the checkbox near the end of the page that will allow you to download the Alternate CD ISO.
 
In case you were wondering, the Alternate CD is the text-based installer for Ubuntu.

After you have successfully installed Ubuntu you can follow this [thread]("http://ubuntuforums.org/showthread.php?t=665018") on getting your Nvidia 8800GT card to work on Ubuntu.

---

### Post by mic159 on 2008-01-14
I cant get it to work. I installed the NVIDIA driver from the site and it still boots in safe graphics mode.

I tried the dpkg-reconfigure thing and the nvidia-xcofig but no success..
i did manage to get it to start once, but it locked up as soon as i entered my username and password.

what do i need to do next?

---

### Post by PmDematagoda on 2008-01-14
Did you add the nv and nv_new modules to the disabled modules list as given in the last page?

---

### Post by BooNality on 2008-04-02
I am about to go forth with Ubuntu and an 8800GTS so I'm bookmarking this thread

---

### Post by mic159 on 2008-04-26
I managed to get it working by installing ubuntu via the alternate CD (not the live CD) and then using the new version of envy (it now supports 8800GT)

---

