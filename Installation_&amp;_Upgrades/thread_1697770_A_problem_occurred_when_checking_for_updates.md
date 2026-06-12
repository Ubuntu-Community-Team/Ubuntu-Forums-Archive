---
title: "A problem occurred when checking for updates"
date: 2011-03-01
forum: Installation &amp; Upgrades
---

### Post by dartdog on 2011-03-01
On Ubuntu 10.10
I recently got a red circle on the top bar that displays the above message..
Per another thread:
I tried this command
sudo aptitude update && sudo aptitude safe-upgrade

And I got
sudo: aptitude: command not found

How can I fix?
I did have to change the default Python interpreter for other reasons to 2.7 a while prior to seeing this error, could they be related? if so how can I keep 2.7 as the default and still fix the issue?

---

### Post by Frogs Hair on 2011-03-01
You could try ```
sudo apt-get
``` Aptitude was no longer installed by default starting with 10.10 .

---

### Post by dartdog on 2011-03-01
Well I ran sudo apt-get update followed by sudo apt-get upgrade
And it seems I updated a group of packages,, 

The Update manager is still broken 

Same red ball on the title bar and same message (A problem occurred when checking for updates), when I attempt to run it it shows 6 packages to update but when I hit the install button it just rescans and discovers the same 6 packages and it will not install.. Any ideas??

---

### Post by Frogs Hair on 2011-03-01
The U.S. sever has been crap today for me I had run sudo apt-get update five times before all the sources connected.

---

### Post by dartdog on 2011-03-01
well the sudo apt-get upgrade gave me this:
The following packages have been kept back:
  linux-generic-pae linux-headers-generic-pae linux-image-generic-pae
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

But still I don't get why the main update manager is acting so flaky it just keeps rechecking and does not even seem to be attempting to download the packages it has selected. And it is picking 6 instead of the three that apt-get is refusing...

---

### Post by dartdog on 2011-03-01
Well I finally got the update manager to attempt to install the packages by right clicking on the red circle and telling it to install.. Got some errors that caused the package to "not install" but now at least the Update manager seems to think I am up to date.

But:: Now I cannot get a .deb package to install I tried clicking on it and I get some spinning circle for a while but then nothing.. but the red something is wrong with update manager symbol is on the title bar.. 

When I try to check to see if there are any settings on the update manager by clicking the "settings" button I get the sudo password alert then after filling it out the manager simply checks for updates again. What is going on??

---

### Post by towheedm on 2011-03-01
Just got the same problem, together with several other crashes, including but not limited to apport!!!!  Was upgrading via Synaptic when the crashes occurred.

---

### Post by dartdog on 2011-03-02
Well, in my case, I had switched the default version of python on the system... from 2.6 to 2.7,, I reverted that back and my installs seem to be back to something approaching normal

---

