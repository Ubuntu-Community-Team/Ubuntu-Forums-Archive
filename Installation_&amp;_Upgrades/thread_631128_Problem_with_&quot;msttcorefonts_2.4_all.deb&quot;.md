---
title: "Problem with &quot;msttcorefonts_2.4_all.deb&quot; installation"
date: 2007-12-04
forum: Installation &amp; Upgrades
---

### Post by olsoveasna on 2007-12-04
Dear everyone,

I am newbie to Ubuntu. Recently, I downloaded Ubuntu 7.04 Christian Edition and installed successfully in my desktop computer. I am really loving it as it has parental control and many useful softwares integrated with. I am learning how to use it with my wife. Now, I would like you to help me solve a problem that I may say it was my mistake or a bug. I wanted to have some Microsoft fonts in Ubuntu, so I downloaded "msttcorefonts_2.4_all.deb". After it was downloaded, I made double click on it, then I clicked on "Install Package" button. Due to my slow dial up internet connection, I clicked "Cancel" button. After a few clicks, it came back to main installation panel; and then bad thing started. Everytime I made double click on ".deb" package, it showed a pop up asked me to close another installation. But I did not install anything. I restared my computer many times and it was still there. I am sorry for no screenshot. However, PLEASE HELP ME! I want to add more stuffs to my Ubuntu.

Many thanks for your help.

---

### Post by erginemr on 2007-12-04
Hello and Welcome to Ubuntu Forums,

You are probably having a problem similar to the given screenshots. If that is the case, I have found the following site that relates to the same issue:

[http://www.ubuntux.org/synaptic-sudden-reboot-exclusive-lock-problem](http://www.ubuntux.org/synaptic-sudden-reboot-exclusive-lock-problem)

Normally, when you run any installer, be it GDebi (double-clicking deb files), Synaptic, aptitude ot apt-get, the Debian packaging system protects itself from concurrent runs by using empty lock files and checking them to see if currently another installation is active or not. 

Probably, your forcing the "msttcorefonts" package to close itself has left some residual lock files thet are reported open. If I were you, I would try the following from the console:

```
sudo rm /var/lib/dpkg/lock  -> Deletes the lock file
sudo rm -r /tmp/*  -> Deletes what is inside the /tmp directory, but be careful to use /tmp/* not /tmp
```

and then,

```
sudo dpkg --configure -a   -> Tries to fix the dpkg system
sudo apt-get install -f  -> Tries to fix the apt-get system
```

Good Luck...

[P.S. Be very careful with the "sudo rm" command! You may end up deleting all your files, if you are not careful enough.]

---

### Post by olsoveasna on 2007-12-04
Hi Erginemr,

Your first image tell what happened to my desktop. I will follow you and hope to get rid of this problem. Anyway, if you don't mind, please see images captured on my desktop computer. Those will help you find out exact problem in my Ubuntu.

Thanks.

---

### Post by olsoveasna on 2007-12-05
:) So happy. Thank you very much for support. I can install new packages now.

---

### Post by erginemr on 2007-12-06
:biggrin: Take care and have fun!

---

