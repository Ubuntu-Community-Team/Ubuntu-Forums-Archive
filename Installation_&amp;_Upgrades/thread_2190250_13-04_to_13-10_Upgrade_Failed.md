---
title: "13-04 to 13-10 Upgrade Failed"
date: 2013-11-26
forum: Installation &amp; Upgrades
---

### Post by SpikeLS6 on 2013-11-26
I first clicked on the Upgrade button on the Automatic Software Updater. After the Authentication screen it simply disappeared and returned the the Desktop. Sometimes the Authentication screen did not come up, even after rebooting the laptop.

I next went to Terminal and used the following commands:
"sudo apt-get update", then "sudo apt-get dist-upgrade". Terminal details showed it reviewing files at each command, but ended up back at my original prompt. 13-10 did not install.

In the Forums I read that others tried the following commands in Terminal:
    "do-release-upgrade" & "sudo apt-get upgrade".

What should I try next?

Spike

---

### Post by jdeca57 on 2013-11-26
Well I did that in a virtual machine. First of all I'd go to the latest version of the actual release:
sudo apt-get update
sudo apt-get upgrade
Afterwards, the GUI prompted me for a distribution upgrade but I guess that the manual way must also work?
sudo apt-get dist-upgrade
I found - like you probably did - [http://askubuntu.com/questions/215267/apt-get-dist-upgrade](http://askubuntu.com/questions/215267/apt-get-dist-upgrade)
But that's not really helpful...

---

### Post by ian-weisser on 2013-11-26
"It didn't work" is not enough information. Exact error messages are more helpful.

What (*exactly*) happened when you did **do-release-upgrade** ?
Can you show us that terminal session?
If not, can you do it again and show us? Paste the entire terminal session here (use [code] tags).

FYI : A dist-upgrade will update your kernel, but not change your release. A do-release-upgrade will upgrade you to the next release of Ubuntu.

---

### Post by SpikeLS6 on 2013-11-26
I went through all the previous commands, then tried "sudo do-release-upgrade". After Authentication, it began to download the "Saucy.tar" ball. I worked through the Q&A's, and it continued through the downloads and installations. When I checked System Settings, Ubuntu 13-10 was indeed working. I have tried several programs opening and closing and so far everything functions normally.

Apparently for this release the "do-release-upgrade" is the command to use.

Thank you for your help. I was a bit long in replying becuase it took over two hours to install 13-10.

Spike

---

### Post by craig10x on 2013-11-26
If you just run one version of ubuntu, the next time you upgrade, you might want to burn the iso of the new version, run it live and the installer should (in addition to wipe out and replace with) give you the option to UPGRADE (that is the way i do my upgrades for each new version)...so instead of taking 2 hours it will take around 25 minutes (like a clean install)...that is because it gets the files directly from the iso and not from the internet...

---

### Post by ian-weisser on 2013-11-26
Happy to see your system working for you.

---

### Post by SpikeLS6 on 2013-11-26
I run only one version of Ubuntu on both the laptop and the desktop. I will save your ISO instructions and try it on the desktop in a week or two. Thank you the suggestion.

Spike

---

### Post by craig10x on 2013-11-26
You're welcome, Spike...and don't forget to turn off your ppas (if you have any) in the software sources on your install before you run the live session iso... ;)
When you do it on the desktop, let us know how it went...i would certainly be interested in hearing about it...that method seems to be very under-used around here...most use the software updater method...
It even looks like a clean install, you will get the slide show and everything :)

You can read about my experience with it here:
[http://ubuntuforums.org/showthread.php?t=2181643&highlight=wow+great+upgrade](http://ubuntuforums.org/showthread.php?t=2181643&highlight=wow+great+upgrade)

---

