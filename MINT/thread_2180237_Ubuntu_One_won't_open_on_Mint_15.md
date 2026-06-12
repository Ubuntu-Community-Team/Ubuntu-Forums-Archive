---
title: "Ubuntu One won't open on Mint 15"
date: 2013-10-12
forum: MINT
---

### Post by s1wood on 2013-10-12
I've just installed Linux Mint 15 (Mate) on my laptop. I have installed Ubuntu One from the Software manager but it doesn't show up anywhere in applications and isn't found on search. 
Any suggestions?

Susan

---

### Post by ajgreeny on 2013-10-12
Try the command **ubuntuone-installer** in terminal which should open the application for you.

---

### Post by s1wood on 2013-10-12
I got 
>The program 'ubuntuone-installer' is currently not installed. You can install it by typing:
sudo apt-get install ubuntuone-installer
susan@susan-ThinkPad-X61s ~ $ sudo apt-get install ubuntuone-installer
[sudo] password for susan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ubuntuone-installer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  ubuntuone-control-panel-qt ubuntuone-client-data<

I remembered having seen control-panel-qt in Synaptic so I went there and installed it and my UbuntuOne has now appeared.
So thanks for the advice - which sent me in the right direction but if anyone else has this problem** ubuntuone-controlpanel-qt in Synaptic** is the answer.

Thanks,

Susan

---

