---
title: "Lubuntu 16.04 w/nVidia, no drivers after update."
date: 2018-04-18
forum: Installation &amp; Upgrades
---

### Post by zelon88 on 2018-04-18
Hi there,


I'm running an ASUS Strix 970 GTX on Lubuntu 16.04.


I updated my system this past Saturday and my graphics drivers have not worked since. I cannot provide a nvidia-bug-report.sh log for the problem because "*sh nvidia-bug-report.sh*" fails with the error..... 

```
user@computer:~$ sudo su
root@computer:/home/user# sh nvidia-bug-report.sh
sh: 0: Can't open nvidia-bug-report.sh
```

After I failed to generate a logfile I tried running "*startx -- -logverbose 6*" and "*sh nvidia-bug-report.sh*" again with the following output.....

```
root@computer:/home/user# startx -- -logverbose 6
xauth: (stdin):2:  unknown command "fbd921459934c63b0e7493124c71e685"


X.Org X Server 1.18.4
Release Date: 2016-07-19
X Protocol Version 11, Revision 0
Build Operating System: Linux 4.4.0-97-generic x86_64 Ubuntu
Current Operating System: Linux computer 4.4.0-116-generic #140-Ubuntu SMP Mon Feb 12 21:23:04 UTC 2018 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-116-generic.efi.signed root=UUID=e4c05f82-c3e5-440b-8ec3-8f44557550c0 ro quiet splash vt.handoff=7
Build Date: 13 October 2017  01:57:05PM
xorg-server 2:1.18.4-0ubuntu0.7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.33.6
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Wed Apr 18 18:20:23 2018
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
xinit: connection to X server lost

waiting for X server to shut down (II) Server terminated successfully (0). Closing log file.

root@computer:/home/user# sh nvidia-bug-report.sh
sh: 0: Can't open nvidia-bug-report.sh
```

For the first couple days I was unable to switch from the open-source Nouveau drivers because doing so in the "Software & Updates" window would immediately result in the driver switching back to Nouveau. I have since passed that problem but now no drivers, from 384 to 396 will recognize a GPU and my resolution is very low. I have tried using every Linux kernel from  "4.4.0-116-generic"  through  "4.4.0-121-generic" and enabled development builds with no change in this issue. I've also purged and reinstalled "nvidia-current" to no avail. I am getting ready to reinstall the entire OS but I'm not confident that will solve the problem either. 

I also sent this info to nVidia hoping they had some ideas. Not really sure what to do. I'd appreciate any input.

---

### Post by monkeybrain20122 on 2018-04-18
How did you install your driver before?

---

### Post by zelon88 on 2018-04-18
I honestly don't know how long it's been since I installed the driver to be honest. I imagine I used something like "*sudo apt install nvidia-current*".

It just worked for a long time until last Saturday when it... well... didn't.

---

### Post by zelon88 on 2018-04-19
So nVidia got back to me and filled me in that I wasn't running nvidia-bug-report.sh correctly, lol! Then it crashed anyway. 

They instructed me to look into some articles relating to an outdated version of gcc that was being used to build retpoline versions of 4.4.0-116. I verified this myself by installing the 4.4.0-112 kernel and booting into it with perfectly functional drivers. 

I'm now rebuilding the 116 kernel with the latest gcc-5 and I'm going to try booting it in a minute. Fingers crossed that I can get it working! 

[https://askubuntu.com/questions/1009725/login-loop-after-upgrading-to-4-4-0-116-kernel-graphical-login-screen-black?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa](https://askubuntu.com/questions/1009725/login-loop-after-upgrading-to-4-4-0-116-kernel-graphical-login-screen-black?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa)

---

