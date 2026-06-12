---
title: "Unintstall Ubuntu"
date: 2008-11-10
forum: Installation &amp; Upgrades
---

### Post by Kanakha on 2008-11-10
A while ago I installed Ubuntu 8.04 on my laptop alongside Windows. Long story short I'm getting tired of the start up propts (having to select windows when I want it to start) and I'd like to take Ubuntu off of my computer. But I don't know how......a little help please?

---

### Post by phillik747 on 2008-11-10
You could always edit the grub menu to default to windows; this wouldn't uninstall Ubuntu but keep you from having to select windows at bootup. But to answer your questions its a matter of reclaiming the ubuntu partition under windows. 

1. Boot up in Windows xp.

2. Start>>control panel>>administrative tools>>computer management

3. Go to disk management under &#8220;storage&#8221;

4. Select your hard disk and then the Linux partition.

5. Delete the Linux partition this will delete Linux and grub.

6. Now reboot your laptop with the windows xp install disk and select the repair option. In the command prompt type &#8220;fixmbr".

7. Above command will repair your boot loader and rewrite ntldr which will replace corrupted grub.

8.Thats it done now boot your laptop or desktop normally it will be booted by default in windows xp.

After you boot back into windows just format that old Linux partition to NTFS. You will need a 3rd party app to 'expand' the windows partition over the old Linux partition.

---

### Post by oilchangeguy on 2008-11-10
"After you boot back into windows just format that old Linux partition to NTFS. You will need a 3rd party app to 'expand' the windows partition over the old Linux partition."

no need for a third party app, when the partiton manager on the live ubuntu cd will perform this function. no need to format the space. just use the partition manager to increase the windows partition so that it uses all of the available space.

---

### Post by Kanakha on 2008-11-10
Ah, this sounds like a project for the weekend, since the week will be too busy to do this. But thanks so much for the help! This can be closed mow :)

---

