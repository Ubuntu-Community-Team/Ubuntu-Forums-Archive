---
title: "Total Upgrade Failure (Dapper--&gt;Feisty)"
date: 2007-07-14
forum: Installation &amp; Upgrades
---

### Post by Trurl on 2007-07-14
Hi everyone, 

   A friend just tried to upgrade from dapper to feisty (going through edgy) and followed the sources.list upgrade method. Unfortunately, the result of all this is that X11 has completely crashed, along with the network card. We now get a number of error messages, such as a "fail_delay" when logging in with the console and all sorts of language error messages, a locale error, and some perl script errors. These errors are contingent on what commands are tried, but all seem to point back to a xorg.conf configuration problem.

A message that always appears is: locale: Cannot set LC_All to default locale: no such file or directory
 
Here is what I have tried to fix the problem

I've attempted to reconfigure Xorg.conf using the sudo dpkg-reconfigure xserver-xorg. This failed and is what put me on to the network card failure

In an attempt to fix the ethernet, I tried the suggestion in the main stickied upgrade thread: sudo ifup eth0 .
This results in the following errors:

There is already a PID file /var/run/dhclinet.eth0.pid with pid 134993416

SIOCSIFADDR: Permission Denied
eth0: Error while getting interface flags: No such device
<repeat of the previous line>
Bind socket to interface: No such device
Failed to bring up eth0

At this point, I'm really flummoxed as to how to fix this since I can't even reach the web to reconfigure xorg, or even restart the upgrade process. 

Any help would be greatly appreciated!

Thanks for your time!

---

### Post by Pumalite on 2007-07-14
See if you can save your /home partition and do a fresh install of Feisty.

---

### Post by Trurl on 2007-07-14
Good suggestion. The only concern is that we don't lose anything during the reinstall. The current partition situation is as follows:

Windows (60 GB): Home (120 GB) : Root (50 GB) : Swap (1 GB)

Is it possible to install Feisty into Root without altering Home, or must Home be backed up? The problem with backing up Home is that whenever I go into Windows to try to move files from Linux to Windows, I'm running into permission errors, such as "access denied" on certain files, and I've no way to actually do a full backup.

I suppose the main question is: can I take a Feisty live CD and install Feisty over the corrupted version of Dapper in Root, -without- changing the nature of Home?

Thanks for any suggestions...

---

### Post by tgalati4 on 2007-07-14
Of course you tried the Feisty Live CD first to make sure that the network and X worked properly.

---

### Post by Trurl on 2007-07-15
Haha. 

Back to the question: Is there any way to either re-install Dapper or Feisty over Root without altering what's currently in Home?

---

### Post by merlinus on 2007-07-15
I have reinstalled feisty three times without anything in my /home partition being affected. 

Just be sure NOT to check the format box for that partition whilst installing.

Good luck!

-merlin

---

