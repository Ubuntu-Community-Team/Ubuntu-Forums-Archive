---
title: "Can Not Calculate the Upgrade"
date: 2010-12-06
forum: Installation &amp; Upgrades
---

### Post by Onael on 2010-12-06
I keep getting this message while I try to run updates. The Update Manager says I have 35MB to install but it doesn't do it. Can anyone tell me what the problem is and how to maybe fix it? Also, how do I 'report this bug against the update-manager package'? Thank you.

[IMG]http://ubuntuforums.org/picture.php?albumid=2132&pictureid=7104[/IMG]

Onael

---

### Post by mörgæs on 2010-12-06
Before reporting the bug (if it is), you could try to reboot the computer and run

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```and see if the error message from this (if any) sheds some light on the problem. 

Remember to close all windows which might open automatically during the process.

---

### Post by mörgæs on 2010-12-06
By the way, here is the list of bugs against Update Manager:
[https://bugs.launchpad.net/ubuntu/+source/update-manager](https://bugs.launchpad.net/ubuntu/+source/update-manager)

Again, just use the command line. After trying it a few times you will probably forget that you have ever used Update Manager :-)

---

### Post by Onael on 2010-12-07
Okay. I tried but it didn't work. Thanks anyway. Luckily, I had just installed the system last night so I haven't really tweaked anything to my liking. I ended up just re-installing Lucid.

---

