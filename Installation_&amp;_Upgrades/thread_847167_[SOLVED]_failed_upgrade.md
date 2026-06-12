---
title: "[SOLVED] failed upgrade??"
date: 2008-07-02
forum: Installation &amp; Upgrades
---

### Post by mahela007 on 2008-07-02
I used the alternate CD to try to upgrade ubuntu. Nothing was happening after a few minutes so a took out the CD. Now when I try to upgrade using the internet connection it says that some files cannon be updated and that this could be caused by an incomplete update. What can I do to fix this?

---

### Post by Pumalite on 2008-07-02
Post the output of:
sudo apt-get -f install

---

### Post by mahela007 on 2008-07-02
mahela007@mahela007-desktop:~$ sudo apt-get -f install
[sudo] password for mahela007:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libavutil1d libnfsidmap2 libdc1394-13 libgtk1.2 libglib1.2 libevent1
  libdv-bin libavformat1d libgssapi2 librpcsecgss3 libsynfig0 libxml++2.6c2a
  libswscale1d ffmpeg libgsm1 libgtk1.2-common libavcodec1d libimlib2 portmap
  erlang-base libungif4g
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 829 not upgraded.
mahela007@mahela007-desktop:~$

---

### Post by Pumalite on 2008-07-02
sudo apt-get autoremove
sudo apt-get update
sudo apt-get dist-upgrade
Then try again.

---

### Post by mahela007 on 2008-07-02
thanks. I'll check back with the result in a little while

---

### Post by mahela007 on 2008-07-02
are you sure that wont harm my computer? I just typed the first line and it deleted a bunch of files. what do the second and third lines do?

---

### Post by Pumalite on 2008-07-02
I need to see the output.

---

### Post by mahela007 on 2008-07-02
oops.. I closed the terminal window a while ago. I didnt enter the 3rd comman yet. should I do that now?

---

### Post by Pumalite on 2008-07-02
Try to upgrade again. I insist is better a clean install.

---

### Post by mahela007 on 2008-07-02
what do you mean by a clean install?

---

### Post by Pumalite on 2008-07-02
You save your data and /home: install Ubuntu 8.04 and then restore your data and settings (/home).

---

### Post by mahela007 on 2008-07-02
the update menu had an option called "upgrade to 8.04". will that do insta=ead of a full installation.
???

---

### Post by tech0007 on 2008-07-02
You dont need to do a clean install if an upgrade will work fine.

What version are you on now? Try 'lsb_release -a'.
On the terminal, do this:
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

3rd command will upgrade your version of ubuntu

---

### Post by mahela007 on 2008-07-02
Im using gutsy.. 7.10. Will getting the uprade solve the issue about updates?

---

### Post by Pumalite on 2008-07-02
Right now you are just updated. To upgrade is to go from one version to the next: i.e 7.10 to 8.04
To do that you can upgrade or do a clean install. Having a separate /home helps with a clean install because you can keep your settings:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

