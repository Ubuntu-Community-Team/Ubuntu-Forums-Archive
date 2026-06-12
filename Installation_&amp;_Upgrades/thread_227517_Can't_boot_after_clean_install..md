---
title: "Can't boot after clean install."
date: 2006-08-01
forum: Installation &amp; Upgrades
---

### Post by leetwanker on 2006-08-01
I booted up the Desktop CD with no problem other than it was very slow "mounting root filesystem". I fooled around a bit and decided that Ubuntu worked very nicely and wanted to get much more familiar with it. I start installing it and deleted my SuSE 10.1 partitions in the process to let Ubuntu install in its place. The install went fine without any error and asked me to reboot.

When it rebooted it pretty much hung at "waiting for root filesystem..."

after about 5-10 minutes it finally dropped to a shell and said /dev/hdd1 does not exist.

If i had to guess I'd say that Ubuntu isn't using the raid drivers for my mobo and that is causing it to be unable to read the partitions that it had just created when I booted from the live CD.

I'm currently waiting for someone to give me some guidance on this so that I can start playing around with configuring it, etc.


My System Info:
Asus P5AD2 Premium Mobo
1GB DDR2
GeForce 6600GT PCI Express
20gb linux hard drive
(I am also Dual-Booting Windows XP on a seperate 20gb and have a third 100gb data drive) *dual booting is 100% functional in my case other than the linux half not booting*


I have the hard drives plugged into the board's on-board IDE raid controller but not operating as a raid just for the fact that there is only one 'normal' IDE connection on my board which is being used for my CD-ROMs.

Hopefully someone has seen this and can give me some advice on fixing it quickly.

Thanks!
wanker

---

### Post by bwayman on 2006-08-01
Looks like you have a bad MBR.

---

### Post by leetwanker on 2006-08-01
How do I go about fixing (or clearing) my MBR, either to enable me to boot properly, or reinstall Ubuntu?

Thanks

---

### Post by leetwanker on 2006-08-02
I believe I've ruled out an MBR problem. I booted from the WinXP CD and went into recoverymode and used their FIXMBR tool to reinstall the NTLDR boot manager just incase there was some sort of corruption. After I did that, XP booted up just fine and I rebooted to the Ubuntu CD and did another clean install and I'm still getting the same issue.

Is there something wrong with the latest Ubuntu Desktop CD?

---

### Post by leetwanker on 2006-08-02
Does Dapper support IT8212 IDE/RAID controllers? I think this may be my problem. Any suggestions on how to get it to boot?

Thanks.
wanker

---

### Post by leetwanker on 2006-08-02
I'm sure nobody gives a shit but Ubuntu's officially lost a user. Put me on the mailing list for when the distro actually works? kthx

PS. that whole deal where you can't log in as root and you have to sudo every root command is mighty annoying.

---

### Post by GreenHawkIA on 2006-08-02
Sorry to hear you left.  I don't know about RAID controllers myself - so I can't help you there.  But if the sudo vs. root issue bugs you so much you can create a root password and login there.  Just terminal and then "sudo passwd root" & specify a root password.  If you want to login to GDM with root just "sudo gedit /etc/gdm/gdm.conf" and change AllowRoot to =true.

---

