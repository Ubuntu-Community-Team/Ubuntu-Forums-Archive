---
title: "Failed to install 20.04.2 on HP DL360G5 with P400i controller"
date: 2021-04-10
forum: Installation &amp; Upgrades
---

### Post by pbucolo on 2021-04-10
Hi, 
I can't install ubuntu 20.04.2, the controller is detected correctly and the disk (Raid 1) is detected like /dev/sda, using vgscan and lgscan I can see the previous LVM volumes.
Wizard show me the new partitioning scheme (use entire disk with automatic partioning) but when I start the installation process I've got the error:  FAIL: removing previous storage devices  

I tried to add hpsa.hpsa_allow_any=1 at boot parameter too, but nothing change.


I note other issues:

1 - It's impossible to use virtual terminals (ALT+Fx), when I switch to the terminal I can see for a while the login request but immediatly the text disappear and remain visible only a dahs (or undescore).
Trying to switch to other virtual termninal (ALT+Fx) show the same issue.

2 - Due the previous issue I can start Install Wizard only connecting by ssh from remote PC logging with "installer" user and random password generated at boot time.

3 - In the wizard stage where is asked for a mirror site I've got an error and I need to continue without updating the installer altought the Server can surf to Internet.

any suggestion to overcome the installeation issue is welcome.

P.S. I run the installer using an USB drive with YUMI. Usually I use this USB drive without any issue to install OS to other servers.

- Pierluigi

---

