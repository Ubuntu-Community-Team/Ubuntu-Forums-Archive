---
title: "Migrating Mail Server VM, Requesting Help on Postfix and Dovecot Files to Move/Update"
date: 2018-07-21
forum: Installation &amp; Upgrades
---

### Post by Robert_Boutin on 2018-07-21
Hi, I have a mail server running on a VirtualBox 5.2 VM.  Built a a couple years ago using Perfect Server instructions, Ubuntu 16.04 Server, Apache, MySql, PHP7, Postfix, Dovecot (pop only, not imap), roundcube, ispconfig.

It's been 100% rock solid, but when I first installed Virtualbox, I didn't realize installing my mail server on a dynamic disk would cause it to explode over time to 300GB due to dozens of snapshots taken and deleted when I was setting it up.  It's only using about 10GB of of actual data so backing it up has been a painfully slow.  

I want to migrate it to a new 30GB fixed size disk to make it easier to do backups.  I started by rebuilding the same base server by installing the same versions of all the packages on my current VM.

I've moved dumps of my roundcube, ispconfig, phpmyadmin, and mysql databases to the new machine.  I've also rsync'ed my entire vmail folder and dovecot folder, and postfix main.cf and master.cf files.  I believe overwriting the main.cf and master.cf files is all I need to do for postfix.  But for dovecot, are there other files I need to be looking at besides just dovecot.conf?  I simply don't remember if I had to modify other dovecot files when I set this up previously.

Any suggestions on important things to consider as I proceed?

Thanks as always

---

### Post by TheFu on 2018-07-21
vboxmanage has a clone option or a sparse to preallocated method.  No need to rebuild anything.   The virtualbox.org site has lots of instructions. [https://www.virtualbox.org/manual/ch08.html](https://www.virtualbox.org/manual/ch08.html)
Isn't there a File-->Copy option in the GUI?  I've seen that suggested for cloning to a new virtual disk as well.

But really, virtualbox is not a good solution for running a server. Take a look at KVM which is what all the major players use for the full virtualization solution.  There's a tool - qemu-img which will convert a .vdi into whatever you want.

I tend to use snapshots that are part of LVM, since those are necessary to have zero downtime with backups.  Having a snapshot doesn't replace backups, as you know. We still have to get the OS/Data onto different physical media, without any corruption.

Putting so many high-risk services onto a single machine isn't really following best practices, BTW.  IMHO.

---

### Post by Robert_Boutin on 2018-07-21
Thanks, if I can do it without rebuilding, that will make life much easier.  I'll check out KVM too.  Virtualbox has worked well for what I need, but I don't know what I don't know so once I get this mail server situated, I'll spend some time with KVM.  I have some questions about your last two comments.

1 - Regarding backups, I was planning to shut the VM down for 15-20 minutes (around 3:00 a.m.) while the entire VM folder is copied to backup media.  A little downtime won't kill me since legit incoming mail will be resent.  To avoid the downtime completely, are you suggesting I can take a snapshot and then back up that static file?  Can I restore a VM from a single snapshot?

2 - *"Putting so many high-risk services onto a single machine isn't really following best practices, BTW.  IMHO."* - I have separate VMs for mail, cloud storage, and web server specifically because I learned the hard way a few years back that running several services on a single machine was a very bad idea (but I did learn a lot...).  Are you saying that my mail server may have too many services?  Do you mean like Roundcube and ispconfig (and I guess Apache if you mean stripping it down to just handle mail)?

Thanks again, I always appreciate the experience coming from this forum.

---

### Post by TheFu on 2018-07-21
If you want to know what is possible with vbox snapshots, read those docs. Vbox snapshots aren't usable in the same ways as other snapshot technologies. 

[https://www.howtoforge.com/linux_lvm_snapshots](https://www.howtoforge.com/linux_lvm_snapshots)
[http://tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html](http://tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html)
ZFS also supports snapshots.

We split email systems into gateways and servers.  The gateways are connected to the internet to filter inbound and outbound email traffic.  Running only the bare minimum to support that effort; postfix and filters. Nothing else. Real email system(s) are inside the server LAN, not connected to the internet.

We take lots of other security architecture steps too, following the same basic ideas from the 1980s. Only that access which is required is possible. That gets applied to network architecture, server architecture, webapp arch, DBMS and desktops.

---

### Post by Robert_Boutin on 2018-07-24
Well, for the moment, I'll say thanks on the vbox backup.  I was indeed able to shrink my vdi from 280GB to about 35GB so now my VMs are at least more manageable when backing up.  Everything I had previously found online suggested I couldn't shrink a fixed vdi but it seems I can.

I'll have to take some time and put some thought into your other comments.  I'm always wanting to learn new things and make my system more robust, but I have to balance that with the realities of my skill level (not terribly great) and my available time (also not terribly great).  I'll definitely check out KVM though.  Thanks again for your guidance!

---

### Post by TheFu on 2018-07-25
If you feel the issue has been solved, please mark this thread as solved to help the community. Thread Tools near the top allows that.

Being cautious is smart!  Your production systems are your responsibility and only you can know what is best. 

The other items definitely shouldn't be hopped onto without lots of thought and probably at least a few months of testing on non-production systems first.  I spent 6 months using KVM before switching from vbox and slowly migrated systems over once the decision was made.

---

### Post by Robert_Boutin on 2018-07-25
I'm marking this thread as solved, not because my original question (thread title) was answered but because the ability to compact my virtualbox vdi was a suitable workaround.  For the record, I referred to this post:

[https://superuser.com/questions/529149/how-to-compact-virtualboxs-vdi-file-size](https://superuser.com/questions/529149/how-to-compact-virtualboxs-vdi-file-size)

Thanks again for the assistance, advice, and patience

---

