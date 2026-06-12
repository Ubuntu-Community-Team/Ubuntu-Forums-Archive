---
title: "NoMachine NX problems after today's updates"
date: 2009-04-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Jove on 2009-04-01
I use NoMachines NX suite to connect to remote boxes which works amazingly well - until today.

After today's updates on the server, the connection is successful, I see the desktop background, but there are no panels. I created a launcher on the desktop for gnome-terminal and can start this successfully. Any ideas as to what might have gone wrong? Happy to post any log extracts if you can point me in the right direction.

Incidentally, I attempted to upgrade to the latest NoMachines .debs to see if this fixed the issue, but it didn't. Currently on:

nxclient  3.3.0-6        NX Client
nxnode    3.3.0-17       NX Server Node
nxserver  3.3.0-22       NX Server

This issue has been replicated on two different NX servers.

Thanks,

Alan

---

### Post by Jove on 2009-04-01
It would appear that this issue is only with Gnome. Setting Desktop to UNIX / KDE on NX client configuration works fine.

---

### Post by Jove on 2009-04-01
Can anyone else confirm this issue? Or conversely, anyone still OK after today's updates?

---

### Post by rickbeton on 2009-04-02
I'm having difficulty with this too.  It worked fine until I installed the Ubuntu updates yesterday.

I'm connecting to a machine on a private LAN at 10.2.5.110. I can connect OK using SSH.

When I connect to the NX server on that machine, authentication succeeds but then I get the following error message in the 'detail' window:

```
NXPROXY - Version 3.3.0

Copyright (C) 2001, 2007 NoMachine.
See http://www.nomachine.com/ for more information.

Info: Proxy running in client mode with pid '6586'.
Session: Starting session at 'Thu Apr  2 10:10:53 2009'.
Error: Failed to resolve address of '::ffff:10.2.5.110'.
Error: Unknown remote host '::ffff:10.2.5.110'.
Session: Session terminated at 'Thu Apr  2 10:10:53 2009'.
```

It is no better whether I use Gnome or KDE. My colleagues who don't use Ubuntu are still able to connect to the server using NoMachine.

Is this a new IPv4/IPv6 problem perhaps (just my guess)?
Any suggestions how to diagnose and fix it?

Rick

---

### Post by Jove on 2009-04-02
Ahha - found this:

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/352716](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/352716)

Looks like a genuine bug.

---

### Post by paledread on 2009-04-02
fwiiw

Downgrading gnome-panel (assuming that is the missing panel) to the previous version seems to have worked for me.

---

### Post by schickb on 2009-04-03
> **paledread said:**
> Downgrading gnome-panel (assuming that is the missing panel) to the previous version seems to have worked for me.

Same issue here. Could you list the steps for downgrading?

---

### Post by paledread on 2009-04-03
Please don't hold my toes to the fire, but I think it went like :

sudo apt-get install gnome-panel-data_1%3a2.26.0-0ubuntu4_all.deb
sudo apt-get install gnome-panel_1%3a2.26.0-0ubuntu4_i386.deb

and then pin these versions, so that they don't get updated to version 5 again at the next update. This is easy to do in synaptic, and can also be done from a terminal, but I don't have the instructions to hand.

Restart the NX client and hopefully no smoke should come from your box, and gnome-panel should be operational again.

---

### Post by Jove on 2009-04-03
Good man - that's fixed it for me. Will pin:

gnome-panel 
gnome-panel-data 
gnome-panel-dbg 
libpanel-applet2-0

until there's a fix.

Cheers,

Alan

---

### Post by Jove on 2009-04-03
FYI, to do this from a terminal, sudo -s to get a root shell first then:

# echo gnome-panel hold | dpkg --set-selections
# echo gnome-panel-data hold | dpkg --set-selections
# echo gnome-panel-dbg hold | dpkg --set-selections
# echo libpanel-applet2-0 hold | dpkg --set-selections

Your next apt-get update will show these packages as held back.

To un-hold, replace the word "hold" in the above with "install" and re-run apt-get update / upgrade as usual.

More info here: [https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

---

### Post by rickbeton on 2009-04-04
> **paledread said:**
> Please don't hold my toes to the fire, but I think it went like :

sudo apt-get install gnome-panel-data_1%3a2.26.0-0ubuntu4_all.deb
sudo apt-get install gnome-panel_1%3a2.26.0-0ubuntu4_i386.deb


Can I ask a dumb newbie question?

In Synaptic, I can see how to select alternative versions and to pin them as needed. But I cannot see the version you mentioned (1:2.26.0-0ubuntu4_i386.deb, assuming '%3' ashould be ':')

Can Synaptic be persuaded to see older versions?
Rick

---

### Post by FPGA on 2009-04-04
I had installed Ubuntu 9.04 Beta on notebook HP 530, and... boots fast and etc...
BUT...
1) remote desktop VNC server (Ubuntu's default) does not work at all! I can see screen and send keys, but cant move mouse, it stuck at left upper part of screen! Any VNC client have troubles with Ubuntu 9.04 default VNC server! Because I can connect to other Ubuntu 8.10 computers and use mouse on them!..
2) XDMCP - it can send receive messages with XDMCP on the ethernet (as I can see from wireshark), but it DOES NOT WORK at all, cant connect, observe servers from other computers...
3) NX server, client from nomachine... in Gnome I cannot see panels, but can send keys and mouse moves...

Please! Help! I wanna kill somebody, I'm angry, I can't get working any of three possible ways of remote desktop in Ubuntu 9.04! Please, report BUG!..

---

### Post by paledread on 2009-04-05
> **rickbeton said:**
> Can I ask a dumb newbie question?

In Synaptic, I can see how to select alternative versions and to pin them as needed. But I cannot see the version you mentioned (1:2.26.0-0ubuntu4_i386.deb, assuming '%3' ashould be ':')

Can Synaptic be persuaded to see older versions?
Rick

The only suggestion that I can offer is that you have set synaptic to delete old packages after new package versions are installed. This setting is under Settings/Preferences/Files. My box was set this way (now changed), and I'm assuming that this is why gnome-panel '%4' was not freely available as an alternate after the problematic '%5' was installed as an update.

That is why the sudo apt-get install lines for '%4' were necessary.

---

### Post by paledread on 2009-04-05
> **rickbeton said:**
> Can I ask a dumb newbie question?

In Synaptic, I can see how to select alternative versions and to pin them as needed. But I cannot see the version you mentioned (1:2.26.0-0ubuntu4_i386.deb, assuming '%3' ashould be ':')

Can Synaptic be persuaded to see older versions?
Rick

But there gain I've just noticed that you seem to be using Ubuntu 7.10 which is pretty ancient. Maybe you should be upgrading to something newer.

Unless you are really using 9.04 (Jaunty Jackalope), which is where this particular problem occurs, you may be confusing yourself with unwanted (and misleading) stuff.

---

### Post by rickbeton on 2009-04-06
OK, I'm struggling with this and I'd be grateful for some advice. I have gnome-panel 1:2.24.1-0ubuntu2 installed. How can I go "back to" 1:2.26 (mentioned above)?

In the Software Sources tool, I've ticked intrepid-security and intrepid-updates.  I've also tried it with intrepid-propsed and intrepid-backports as well.

Suggestions please?

Rick

---

### Post by paledread on 2009-04-06
> **rickbeton said:**
> OK, I'm struggling with this and I'd be grateful for some advice. I have gnome-panel 1:2.24.1-0ubuntu2 installed. How can I go "back to" 1:2.26 (mentioned above)?

In the Software Sources tool, I've ticked intrepid-security and intrepid-updates.  I've also tried it with intrepid-propsed and intrepid-backports as well.

Suggestions please?

Rick

It seems to me unlikely that you should be involved in this thread.

This thread is for people running Ubuntu Jaunty Jackalope (version 9.04), and using nxclient to make connections to remote computers. Those people (me included) had a problem where there was an update of the gnome-panel package that resulted in gnome-panel failing to open after the nxclient connection was made. Downgrading the gnome-panel package to the previous version seems to have cured the problem, maybe temporarily.

Judging by your questions it looks likely that the above scenario doesn't apply in your case.

Are you running Ubuntu Jaunty Jackalope (9.04) or (perhaps) version 7.10 Gutsy Gibbon?

Are you using nxclient to connect to a remote computer?

Has gnome-panel (or panels) failed to open on your desktop?

Forget the gnome-panel version for the moment.

If you answer these 3 questions I'll try and assist.

---

### Post by swietowid on 2009-04-21
I have a question that is tangentially related.  Since I installed Jaunty I have been getting the warnings "Xlib:  extension "Generic Event Extension" missing on display ..." when I log in using NoMachine or FreeNX.  
This is new to me as it does not happened in Hardy or Intrepid.

Is this a bug?  Does it affect anything vital?

---

