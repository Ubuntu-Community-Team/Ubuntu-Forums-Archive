---
title: "Delay on shutdown (Mint LMDE)"
date: 2015-07-10
forum: MINT
---

### Post by ogp on 2015-07-10
Chaps, 

I have downloaded and installed LMDE2 on two laptops. And both of them are exhibiting the same problem - they delay on shutdown. If you tell the machine to shutdown then the Mint logo appears and disappears and a list of closing processes is given, on a black background. However when it gets to "Hardware Clock Updated To <Date> , <Time>", it hangs for around three minutes. 

This happens to two machines (A Dell Inspiron 6400 and a samsung NC10 netbook), although both of them were fine before I set them up to connect to Samba shares (in fstab), and if I manually disconnect from the Samba shares before shutting down (using # sudo umount -a) then they shut down nicely. I am therefore suspecting that the delay in shutdown is something to do with disconnecting the samba shares. 

An option would be to call a script on shutdown that disconnects the samba shares before doing anything else, but this would feel like it's not addressing the problem. 

Does anyone have any ideas what could be causing this and how it could be solved? I'm happy to provide more information if you can tell me how to find it. I doh't know whether this problem is specific to LMDE or whether it applies to other forms of Mint as well. 

All help welcomed, thank you. 


Oli.

---

### Post by howefield on 2015-07-10
Thread moved to the "*MINT*" forum.

---

### Post by v3.xx on 2015-07-10
I have seen talk about this at the Mate forum.  The slow shutdown is thought to be the new systemd causing the hangup.  

Systemd can be replaced with the old Upstart to see if this is your problem.

[https://wiki.ubuntu.com/SystemdForUpstartUsers#Permanent_switch_back_to_upstart](https://wiki.ubuntu.com/SystemdForUpstartUsers#Permanent_switch_back_to_upstart)

---

### Post by d-cosner on 2015-07-10
LMDE 2 does not use systemd by default. Have you ran these commands one at a time in the terminal? You do not need root privileges to do this.

```
[COLOR=#333333][FONT=Lucida Grande]gsettingsset org.cinnamon.desktop.session settings-daemon-uses-logind true[/FONT][/COLOR]
```

```
[COLOR=#333333][FONT=Lucida Grande]gsettingsset org.cinnamon.desktop.session session-manager-uses-logind true[/FONT][/COLOR]
```

```
[COLOR=#333333][FONT=Lucida Grande]gsettingsset org.cinnamon.desktop.session screensaver-uses-logind false[/FONT][/COLOR]
```

---

### Post by ogp on 2015-07-19
Guys,

Thank you for your answers. I appreciate your help. 

As it is, I'm not getting on with LMDE in several ways (the fact that you can't add PPA's to it is a big problem) and I have, as of this evening, abandoned it in favour of going back to regular Linux Mint. So this issue is no longer a problem for me. 

Thanks all the same. 


Oli.

---

