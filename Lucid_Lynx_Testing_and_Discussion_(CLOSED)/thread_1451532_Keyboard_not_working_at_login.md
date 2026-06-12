---
title: "Keyboard not working at login"
date: 2010-04-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by vDub2000 on 2010-04-10
I installed Ubuntu 10.04 Beta 2 using VMware Player. After it has finished installing and I'm at the login screen, it will not accept any input whatsoever from the keyboard. I've tested it on two different machines and it's the same result on each one.

Before someone suggests there's something wrong with VMware Player, there isn't. I can install and use Ubuntu 9.10 on it without any problems.

---

### Post by taylorkh on 2010-04-10
This happened somewhere in the updates after beta 1.  It has been discussed although I do not recall seeing a solution.

Ken

---

### Post by vDub2000 on 2010-04-17
I found a solution here:

[http://communities.vmware.com/thread/263410](http://communities.vmware.com/thread/263410)

Once the edits are made to the console-setup, all becomes well again.

---

### Post by allCuExpMa on 2010-04-19
found 2 things which obviously worked for a few people:
1. mouseemu caused the problem for a few people, they removed it....
2. sudo dpkg-reconfigure console-setup do that in recovery mode or
   do it in tty1-6. to do it in tty1: press ctrl+alt+F1 then login.
   stop "gdm" > type in > "sudo services gdm stop" press ENTER.
   then type in the above command: "sudo dpkg-reconfigure console-setup"
   use USA as the default setup and follow the steps.

unfortunately non of the above worked for me... here's what I did:

1. go to >System>Administration>Language Support<  (when I went there it told me to install the "Language Support" which I did.
2. after the install go to >System>Preferences>Keyboard and there
use the "Accessibility" tab and disable "Only accept long keypresses"

that did the job for me....good luck
T[m]

---

