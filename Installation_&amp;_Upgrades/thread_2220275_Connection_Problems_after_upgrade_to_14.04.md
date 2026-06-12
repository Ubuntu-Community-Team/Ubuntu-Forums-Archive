---
title: "Connection Problems after upgrade to 14.04"
date: 2014-04-27
forum: Installation &amp; Upgrades
---

### Post by alexcrowley6 on 2014-04-27
I've had some problems connecting remotely (within my home network) to a few services since upgrading from 13.10 to 14.04.

Apart from upgrading the OS from 13.10 to 14.04 I have not made any other changes.

I can still SSH into the machine but I can no longer connect via VNC, I have verified on the ubuntu box that remote desktop sharing is still enabled and all settings are the same however I get the following error when trying to connect via VNC;

Unknown authType 18

I'm also experiencing errors trying to connect via Transmission Remote GUI, although I was able to connect fine before I now receive the Connection Refused error all the time.

I have verified that the firewall is disable by running the following command.

```
sudo ufw disable
```

```
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
Firewall stopped and disabled on system startup
```


Any help would be much appreciated.

Thanks!

---

### Post by Richard_Brickley on 2014-04-27
I have the exact same problem.  I will not upgrade any more computer until it is fixed as I rely on vnc viewer to control those computers.

---

### Post by d.okuboyejo@gmail.com on 2014-04-29
> **Richard_Brickley said:**
> I have the exact same problem.  I will not upgrade any more computer until it is fixed as I rely on vnc viewer to control those computers.

The issue is caused by _*libpam-smbpass*_ module of **samba**.
Following the suggestion [here]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1257186")

The fix is by running

 ```
sudo pam-auth-update
``` and then unselect "SMB Password Synchronization

---

### Post by alexcrowley6 on 2014-04-29
Thank you for your reply.

I tried this and it removed the  '[COLOR=#000000][FONT=Ubuntu Mono]no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory' [/FONT][/COLOR]error.

But my original problem of not being able to connect via VNC or Transmission Remote GUI is still there, any other suggestions?

---

### Post by cbf305 on 2014-04-30
It looks like a setting is broken or on by default and it shouldn't be.  There is an open bug from the Alpha days ([https://bugs.launchpad.net/ubuntu/+source/vino/+bug/1290666](https://bugs.launchpad.net/ubuntu/+source/vino/+bug/1290666)).  There is a fix at the bottom using dconf-editor to disable encryption for remote-access.  I can confirm that it fixes this issue with a fresh install, but those that have upgraded YMMV.

---

### Post by alexcrowley6 on 2014-05-02
Thank you so much, the dconf-editor solution helped me gain access via vnc again.

I had to do this locally on the machine as trying to do this whilst SSH'd in did not work.

The problem with the transmission remote gui is still there however.

---

### Post by Richard_Brickley on 2014-05-09
I have 14.04 on two computers on my network.  I can remote view them from each other but I can not view them from any of my windows computers.  I tried pam-auth-update but there is no SMB Password Synchronization to unselect.  I also tried dconf-editor but do not know how to use it.  I have been using Ubuntu for many years and this is the first time I got this problem.

---

### Post by BarryD9545 on 2014-05-15
Same issue here, can't connect via VNC after the upgrade to 14.04.
Ran [COLOR=#000000][FONT=Ubuntu Mono]sudo pam-auth-update, [/FONT][/COLOR]but there was no option for [COLOR=#000000]SMB Password Synchronization.

Thanks for the upcoming help.[/COLOR]

---

### Post by dcharlespyle on 2015-04-11
I am seeing the same problem even now.  I found that VNC clients can connect when I use the GUFW GUI to turn off the firewall.  As soon as I do that I can see all my VNC connections and use them.  When I turn back on the firewall, I lose all VNC connections again.  I have tried creating default rules, advanced rules, etc.  Nothing works and I cannot access my VNC connections unless I completely turn the firewall off in Ubuntu 14.04.2.  If I find a solution, I'll let everybody know.

---

### Post by dcharlespyle on 2015-04-12
> **dcharlespyle said:**
> I am seeing the same problem even now.  I found that VNC clients can connect when I use the GUFW GUI to turn off the firewall.  As soon as I do that I can see all my VNC connections and use them.  When I turn back on the firewall, I lose all VNC connections again.  I have tried creating default rules, advanced rules, etc.  Nothing works and I cannot access my VNC connections unless I completely turn the firewall off in Ubuntu 14.04.2.  If I find a solution, I'll let everybody know.

There is a workaround but it isn't a fix.  Just change the "Incoming" setting at the top of the GUFW application window to Allow, run the VNC Client, and as soon as the connection is established you can switch it back to Deny or Reject.  It is just a 'quickie' workaround until I or somebody else figures out how to make rules for VNC actually work in GUFW while running in Ubuntu 14.04 LTS.

---

