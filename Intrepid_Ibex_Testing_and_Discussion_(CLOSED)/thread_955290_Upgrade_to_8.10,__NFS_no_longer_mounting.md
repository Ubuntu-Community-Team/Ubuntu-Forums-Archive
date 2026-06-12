---
title: "Upgrade to 8.10,  NFS no longer mounting"
date: 2008-10-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by expatCM on 2008-10-22
I have just upgraded four clients from 8.04 to 8.10.  No issues apart from one machine.

That client can no longer mount NFS shares from the fstab.

If I issue the command 
sudo mount -a 
the mounts are loaded as usual.

Any suggestions where to look to fix this?

---

### Post by Eredeath on 2008-10-23
Sounds like you need to load the hal daemon.

---

### Post by expatCM on 2008-10-24
> Sounds like you need to load the hal daemon.

Could you please tell me why and how?

---

### Post by expatCM on 2008-10-24
I am trying to find a workaround for this.

I know that "sudo mount -a" solves this problem so is there any way of putting that command into the startup programs (System / Preferences / Sessions)?

---

### Post by Archmage on 2008-10-24
For me this sounds like a firewall problem.

---

### Post by wgrant on 2008-10-24
It could be that Network Manager isn't bringing up the interfaces early enough. I've heard that a reinstall fixes it, but I've not looked into how it should be fixed properly on existing systems.

---

### Post by expatCM on 2008-10-24
What makes you think this?   It was working with 8.04.  The system was upgraded.  It then no longer works until sudo mount -a is issued and then it is fine.  How does the firewall get involved?

---

### Post by expatCM on 2008-10-24
wgrant .... we both posted at the same moment so I did not see your comment.

If the Network Manager is not bringing up the interfaces early enough then I imagine that when the fstab line is run then there is nothing there to mount.

So there has to be a work around until this gets fixed.  My wife is not coping well with entering sudo mount -a ....  not that sort of user.   Can the gnome-scheduler be used for this type of command?  That being the case the scheduler can no doubt be started from the Sessions / Startup Programs.

The use of sudo seems to be the challenge since it is hard to see how to automate the password ....

---

### Post by Archmage on 2008-10-24
> **expatCM said:**
> What makes you think this?   It was working with 8.04.  The system was upgraded.  It then no longer works until sudo mount -a is issued and then it is fine.  How does the firewall get involved?

Because after the upgrade the exception/binding in portmap got delete. At least for me I need to enter it again. After that it worked flawless and did mount at booting without mount -a.

---

### Post by expatCM on 2008-10-24
> the exception/binding in portmap got delete.

Well that sounds good but sadly I have no idea what it means.  So there is a file called portmap and that has some settings called exception/binding that got trashed.  Where is this file normally found, I just took a look in /etc and did not see it .... ?

---

### Post by expatCM on 2008-10-25
I guess there is no file called portmap and it is hosts.allow and hosts.deny which are the control files here.  However since the content of both files is commented out there should be no reason for traffic to be blocked.

Is there any way to set a scheduled task to run on boot that issues "sudo mount -a" since that is all that I need to do?

---

### Post by FuturePilot on 2008-10-25
Put
```
mount -a
```
in /etc/rc.local
That is the last script that gets run at bootup before the graphical login.

---

### Post by wgrant on 2008-10-25
What happens when you run sudo /etc/network/if-up.d/mountnfs.sh on affected systems (before you mount the NFS exports manually)?

---

### Post by expatCM on 2008-10-26
Hi William,

it gives an error

sudo: /etc/network/if-up.d/mountnfs.sh: command not found

---

### Post by wgrant on 2008-10-26
> **expatCM said:**
> Hi William,

it gives an error

sudo: /etc/network/if-up.d/mountnfs.sh: command not found

Try dropping the .sh from the end.

---

### Post by jongkind on 2008-10-26
I had the same problem. What worked for me is using an ip address in fstab instead of a server name.

So:
server_ip:/dir /mntpoint nfs rw,hard,intr 0 0
(server_ip=e.g. 192.168.2.1, etc.)

instead of:
servername:/dir /mntpoint nfs rw,hard,intr 0 0

---

### Post by expatCM on 2008-10-26
* if-up.d/mountnfs[]: waiting for interface eth0 before doing NFS mounts

Interesting ..... but the problem here is that eth0 is integrated into the motherboard and not working.   Another card is in use which happens to have ended up as eth2.

---

### Post by expatCM on 2008-10-26
jongkind - nice idea but sadly I use the server IP in fstab already ...

---

### Post by wgrant on 2008-10-26
> **expatCM said:**
> * if-up.d/mountnfs[]: waiting for interface eth0 before doing NFS mounts

Interesting ..... but the problem here is that eth0 is integrated into the motherboard and not working.   Another card is in use which happens to have ended up as eth2.

That's what I thought. I had this on one of my clients, and removing old interfaces from /etc/network/interfaces fixed it.

---

### Post by expatCM on 2008-10-26
Spot on William ....  I commented out eth0 from the /etc/network/interfaces file and the mount was there on reboot ....

Just one remaining problem which has appeared at some recent point that apt-get update will now not run ....  none of the repositories at all are found.  All other Internet connectivity is working though ... 

I went to System / Administration / Network Tools and looked at the Devices tab.  eth2 is there with all the settings.  Fine.  But there is also eth1.  I guess apt-get update is looking to this interface but it does not exist and so cannot run.

Since eth1 is not in the interfaces file I cannot comment it out.

Do you happen to know where to look for that setting?

---

### Post by wgrant on 2008-10-26
What is the precise text of the error message that apt-get update gives you? It knows nothing about specific interfaces, so eth1 is unlikely to be causing trouble. Can you access the Internet normally?

---

### Post by expatCM on 2008-10-26
Normal access to the Internet is no problem (browser / email / skype)

sudo apt-get update gives an error on every line similar to this 

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg
  Could not resolve 'us.archive.ubuntu.com'

If I change the source to Main the same thing happens.

---

### Post by expatCM on 2008-10-26
I just went to another computer on the network and ran sudo apt-get update and there was no issue at all ....   The machine also is upgraded from 8.04 to 8.10.

---

### Post by expatCM on 2008-10-27
something a bit strange is happening ....

If I ping ubuntu.com it instantly dies - no host.  If I ping google.com ... same thing.  If I browse, no problems.  Ping on other client machines works.

Clearly something has changed since it had to work during the upgrade but I cannot see what ....

---

