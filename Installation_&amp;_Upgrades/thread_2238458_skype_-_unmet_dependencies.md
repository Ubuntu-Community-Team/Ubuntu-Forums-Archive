---
title: "skype - unmet dependencies"
date: 2014-08-08
forum: Installation &amp; Upgrades
---

### Post by baol2 on 2014-08-08
Hello, I have Ubuntu 12.04

I recently had some strange problems with skype, so i needed to install it again. As the one I got from the Software Center was not working properly, I downloaded skype from here:
[http://download.cnet.com/Skype-for-Ubuntu/3000-2349_4-75300362.html](http://download.cnet.com/Skype-for-Ubuntu/3000-2349_4-75300362.html)

Skype is working, but a red dot is oon top-left screen, saying that:
Red dot: Error : Broken Count > 0. That usually means that your installed packages have unmet dependencies

I am not good at programming. I did this and the answert is:
baol@baol-AOD270:~$ apt-get check 
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied) 
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Now my Ubuntu Software Center is blocked:
Items cannot be installed or removed until the package catalogue isn't repaired

And it cannot repair ....
Package operation failed. Details:
InstallArchives() failed: dpkg: dependency problems prevent configuration of skype: 
 skype-bin (4.3.0.37-0ubuntu0.12.04.1) breaks skype (<< 4.1.0.20.0-0ubuntu0.12.04.1) and is installed. 
  Version of skype to be configured is 2.2.0.35-1. 
dpkg: error processing skype (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already 
Errors were encountered while processing: 
 skype 
Error in function:  
dpkg: dependency problems prevent configuration of skype: 
 skype-bin (4.3.0.37-0ubuntu0.12.04.1) breaks skype (<< 4.1.0.20.0-0ubuntu0.12.04.1) and is installed. 
  Version of skype to be configured is 2.2.0.35-1. 
dpkg: error processing skype (--configure): 
 dependency problems - leaving unconfigured

What should I do?
Thank you in advance
Baol

---

### Post by ajgreeny on 2014-08-08
That is such an old version of skype that you got from cnet that I am not surprised that it failed (2.2.0.35-1) so I think you might do better to stick with the repos, or even get the version direct from skype [http://www.skype.com/en/download-skype/skype-for-computer/](http://www.skype.com/en/download-skype/skype-for-computer/) ignoring the ubuntu version, 12.04, it is for; it does install fine and I have just added it to my VirtualBox VM of Xubuntu 14.04 64bit and it works fine even in the VM.

You may get better results, judging by your problems, from totally removing your current skype with terminal, though it sounds as if you were trying to use apt terminal commands while the USC was still open; that will always fail.  Only use one method of package management at a time, but I can't help with any details of the USC as I never use it; it's always synaptic for me as it tells me so much more about what is happening.

Before you make any other attempts to install packages, by whatever means, it may be worth running ```
sudo apt-get install -f
``` to see if there are any packages that need fixing.

---

### Post by baol2 on 2014-08-08
Dear friend
As i was saying before, I am kinda dummy with computers.
First of all, I am not able to remove skype. I cannot find its filles, and the only way i know to remove a program is through the USC, which is not responding. Maybe you can tell me what i have to write in order to remove it through the terminal commands  

This is the result of install -f : 

Get:1 [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner skype i386 4.3.0.37-0ubuntu0.12.04.1 [16.1 kB]
Fetched 16.1 kB in 1s (16.0 kB/s)
dpkg: dependency problems prevent configuration of skype:
 skype-bin (4.3.0.37-0ubuntu0.12.04.1) breaks skype (<< 4.1.0.20.0-0ubuntu0.12.04.1) and is installed.
  Version of skype to be configured is 2.2.0.35-1.
dpkg: error processing skype (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 skype
E: Sub-process /usr/bin/dpkg returned an error code (1)

One more "small" problem. I am in China right now, and the chinese web page of skype doesnt offer any Linux version. I cannot get to the english one, this is why i downloaded that version from cnet.
Is installing Ubuntu from the beginning a good soluton?

---

### Post by ajgreeny on 2014-08-08
OK, so try ```
sudo apt-get remove --purge skype*
```

---

### Post by baol2 on 2014-08-08
and everything is working! thanks a lot!

---

### Post by ajgreeny on 2014-08-08
Brilliant!!

Please go to Thread Tools at the top of the thread and mark this as SOLVED.

---

