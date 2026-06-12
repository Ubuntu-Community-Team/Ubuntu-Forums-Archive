---
title: "ModemMgr(573) Fails preventing Shutdown"
date: 2015-07-24
forum: Installation &amp; Upgrades
---

### Post by Rick St. George on 2015-07-24
New install of Xubuntu v14.04 on 64bit Laptop. 

Upon Shutdown, it will not shutdown all the way. Notice on the screen;

* Speech-dispatcher disabled: edit etc/default/speech-dispatcher
* Modemmanager(573) caught signal, (warn) could not acquire the 'org.freedesktop.modemmanager1' service name. [FAIL] 
*deactivating swap       [OK]
mount: / is busy
* wil now halt

---------------------

But does not fully shutdown. Have to Power Off , and upon reboot .. bunch of gobbledegook shows on screen before boot-up.

Any suggestions appreciated.
Rick

---

### Post by Rick St. George on 2015-07-29
Wonder why it hasn't upgraded to v15.04? 

Should problem above be fixed prior to upgrading Xubuntu LTS?

Thanks for any reply!
Rick

---

### Post by Rick St. George on 2015-07-29
Noticed more info - on Shutdown. Screen reads;

* Could not get the system bus. Make sure the message bus daemon is running! Message: did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken. 

But fails to completely shutdown. Any ideas or suggestions?
Thanks for any help.
Rick

---

### Post by Rick St. George on 2015-08-20
See this Thread ... Both Problems Solved.

[http://ubuntuforums.org/showthread.php?t=2291483](http://ubuntuforums.org/showthread.php?t=2291483)

---

