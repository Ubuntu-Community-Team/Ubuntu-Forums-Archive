---
title: "Partial Upgrade"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by Vyizis on 2010-10-10
I upgraded my server to 10.10 from 10.04 today using do-release-upgrade, it seemed to complete fine and I rebooted the system to be greeted by the following on login:

```
Linux itseybox 2.6.35-22-generic-pae #33-Ubuntu SMP Sun Sep 19 22:14:14 UTC 2010 i686 GNU/Linux
Ubuntu 10.10

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

  System information as of Sun Oct 10 17:50:01 BST 2010

  System load:     0.47               IP address for wlan0: 192.168.0.100
  Usage of /:      1.7% of 143.67GB   IP address for as0t1: 5.5.4.1
  Memory usage:    26%                IP address for as0t0: 5.5.0.1
  Swap usage:      0%                 IP address for as0t2: 5.5.8.1
  Processes:       124                IP address for as0t3: 5.5.12.1
  Users logged in: 0

  Graph this data and manage this system at https://landscape.canonical.com/

Ubuntu 10.10

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

 System information disabled due to load higher than 1

[B]474 packages can be updated.
0 updates are security updates.

*** System restart required ***[/B]
Last login: Sun Oct 10 17:37:57 2010 from
dan@itseybox:~$

```

The bit in bold confuses me, apt-get upgrade and do-release-upgrade show everything as being up to date, is there any way to confirm if the upgrade has worked or not?

---

### Post by mörgæs on 2010-10-10
Did you notice the 'system restart required?'-message? :-)

---

### Post by Vyizis on 2010-10-10
I did, i have restarted it several times! The message stays.

---

### Post by mörgæs on 2010-10-10
How does it work when booted from a live CD?

---

### Post by Rob_Quads on 2010-10-11
I've also seen the same problem. Not packages to be installed by the updater but the login screen says there is and keeps saying a reboot is required.

---

### Post by Vyizis on 2010-10-11
The system does not have a cd drive, monitor, kb or mouse its not so easy to test the system in a live environment. I don't think the issue has anything to do with a hardware incompatibility. I think the issue stems from me performing the upgrade using ssh and dropping the connection half way though. Unfortunately I didn't use screen the first time round so I had to start the process again.

---

### Post by mörgæs on 2010-10-11
After all the failed attempts it is maybe best just to go for a clean install, if you can find a spare screen and the like.

---

### Post by VanDaMe on 2010-10-11
I have the same issue

```
Welcome to the Ubuntu Server!
 * Documentation:  http://www.ubuntu.com/server/doc

  System information as of Tue Oct 12 10:13:41 WIT 2010

  System load:  0.14               Processes:           193
  Usage of /:   1.6% of 135.62GB   Users logged in:     0
  Memory usage: 2%                 IP address for eth1: 172.16.0.15
  Swap usage:   0%

  Graph this data and manage this system at https://landscape.canonical.com/

Ubuntu 10.04.1 LTS

Welcome to the Ubuntu Server!
 * Documentation:  http://www.ubuntu.com/server/doc

 System information disabled due to load higher than 1

1 package can be updated.
0 updates are security updates.

*** System restart required ***
```

I already restart the server for 5 times. But still have the same :mad:

---

### Post by Vchat20 on 2010-10-12
> **VanDaMe said:**
> I have the same issue

```
Welcome to the Ubuntu Server!
 * Documentation:  http://www.ubuntu.com/server/doc

  System information as of Tue Oct 12 10:13:41 WIT 2010

  System load:  0.14               Processes:           193
  Usage of /:   1.6% of 135.62GB   Users logged in:     0
  Memory usage: 2%                 IP address for eth1: 172.16.0.15
  Swap usage:   0%

  Graph this data and manage this system at https://landscape.canonical.com/

Ubuntu 10.04.1 LTS

Welcome to the Ubuntu Server!
 * Documentation:  http://www.ubuntu.com/server/doc

 System information disabled due to load higher than 1

1 package can be updated.
0 updates are security updates.

*** System restart required ***
```

I already restart the server for 5 times. But still have the same :mad:

I'm getting the same thing even though my update manager list is clean and have rebooted a few times since then. This and vino not working are both really annoying.

No offense to the dev's, but it could have waited rather than wanting to hit 10-10-10 10:10 which nobody but the super obsessed would care about.

---

### Post by mörgæs on 2010-10-12
The problem is not the release date. It was like this with every release I remember. 

An online upgrade is probably the most complicated of all operations one can do on a computer. The more the installation is tweaked, the more can fail. The developers have no chance to test all kinds of setup, so basically it is a shot in the dark.

The real problem is that people are encouraged to upgrade online without being properly warned of the risk. My guess is that most of them waste more time troubleshooting their upgrade than it would have taken to back up the data and do a fresh install.

---

### Post by Vchat20 on 2010-10-12
> **mörgæs said:**
> The problem is not the release date. It was like this with every release I remember. 

An online upgrade is probably the most complicated of all operations one can do on a computer. The more the installation is tweaked, the more can fail. The developers have no chance to test all kinds of setup, so basically it is a shot in the dark.

The real problem is that people are encouraged to upgrade online without being properly warned of the risk. My guess is that most of them waste more time troubleshooting their upgrade than it would have taken to back up the data and do a fresh install.

Honestly never had any problems doing online upgrades on other distros. Even so, it further exacerbates the issue if they don't at least bother to test the upgrade mechanism from a clean stock install of the OS. This is my case where I am sitting save for my own personal data which has absolutely 0 modifications on ubuntu's own code. Stock 10.04 ubuntu-desktop lamp-server.

And I really do not want to do a clean install as I just did it 2 weeks ago on this machine and any extended downtime, expected or otherwise, isn't in the cards considering how long it's been down already.

My comment about the release date is more to the idea that these few and fairly minor (but still terribly annoying) bugs should not even logically be affected by these in-place upgrades and I'm sure with a little more testing rather than rushing the release out the door just to hit the specific date they wouldn't even be an issue right now.

*shrug* May just have to jump in and do some hand massaging on this and do some investigating to fix these issues on my own.

---

### Post by VanDaMe on 2010-10-12
as I remember, this never happended before in Ubuntu upgrade :)

---

### Post by Kitagua on 2010-10-14
Same issue here. Upgrade has been performed via ssh and screen session. The welcome message is splitted into two sections, the first part (Ubuntu 10.10) is fine 0 updates and nothing about "System restart required" while the second section still welcomes me to Ubuntu 10.04 pretending that there is one update and a system restart required. Where is this "welcome" message being generated?

---

### Post by roganjosh on 2010-10-14
I have a similar issue. I upgraded to 10.10 using the Update Manager (via a VNC connection) but now when I log in via SSH I get this (these?) welcome message(s)...

```

Linux HTPC 2.6.35-22-generic #34-Ubuntu SMP Sun Oct 10 09:26:05 UTC 2010 x86_64 GNU/Linux
Ubuntu 10.10

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

0 packages can be updated.
0 updates are security updates.

Ubuntu 10.10

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

684 packages can be updated.
0 updates are security updates.

*** System restart required ***
Last login: Thu Oct 14 20:32:49 2010 from router

```

---

### Post by Xpistos on 2010-10-15
I have not done any upgrade on my system and I am getting the same error message on my 10.04.1 LTS server:


"System information disabled due to load higher than 1"

---

### Post by jason.craven on 2010-10-15
Here's the fix: [http://ubuntuforums.org/showthread.php?t=1593161](http://ubuntuforums.org/showthread.php?t=1593161)

---

### Post by Thaskalas on 2010-11-10
Thanks for the link, it fixed my issue!

---

### Post by alecz20 on 2011-10-21
> **Vyizis said:**
> The system does not have a cd drive, monitor, kb or mouse its not so easy to test the system in a live environment. I don't think the issue has anything to do with a hardware incompatibility. I think the issue stems from me performing the upgrade using ssh and dropping the connection half way though. Unfortunately I didn't use screen the first time round so I had to start the process again.

I do all my upgrades over SSH using screen, otherwise it's too risky.

Also, if I have a heavily customized system, that I don't want to lose, I take an image with Clonezilla before the upgrade. It is true that I need to attach keyboard, and monitor, but I think it's worth the trouble.

---

