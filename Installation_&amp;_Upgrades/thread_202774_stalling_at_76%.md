---
title: "stalling at 76%"
date: 2006-06-24
forum: Installation &amp; Upgrades
---

### Post by irutgers on 2006-06-24
I downloaded the single CD install of the latest desktop version of Ubuntu (6.06) and am having trouble installing.

The CD and the non-installed version of Ubuntu loads fine but when I install (after answering the 6 questions) the system stalls at 76% of copying files (every time the same place).

I did check the integrity of the CD image and it checks out.  I have tried the safe? mode install and have tried the install with the F6 switch to no avail.

I previously ran debian (latest version) and recall I had to use a special switch to get around a ATA hard drive issue (don't know if this is a factor with ubuntu).

So my question is ... is this an issue with the server my pc is trying to access or is there a special switch I need to use to get around the ATA stuff?

Thx in advance for your help!

---

### Post by mibadt on 2006-06-24
Since you are after a server, I guess your problem might stem from the fact that the installation can't access the repositories during install.

You can verify this as follows:
1. Once you are almost there (say at about 70%) open a non graphical terminal by pressing ALT+CTRL+F1 (Beware-you'll be root there).
2. From that terminal try to ping (say ping [www.yahoo.com)](www.yahoo.com)).
3. If you can't ping you'll have to fix your Internet connecivity before proceeding. Issues to look at:
a. is your Ethernet (say eth0) up: run ipconfig, if necessary allocate a static IP (say 10.0.0.111) or run dhclient.
b. After that check the DNS issue and if necessary edit (using nano) /etc/resolv.conf and replace the addresses there with the DNS addrseses of your ISP.
c. Once you can ping you'll have to wait 2-3 minutes and instllation should proceed.

Note: at any stage you can switch back to the graphical install process by: ALT+CTRL+F

[QUOTE=irutgers]I downloaded the single CD install of the latest desktop version of Ubuntu (6.06) and am having trouble installing.

The CD and the non-installed version of Ubuntu loads fine but when I install (after answering the 6 questions) the system stalls at 76% of copying files (every time the same place).

I did check the integrity of the CD image and it checks out.  I have tried the safe? mode install and have tried the install with the F6 switch to no avail.

I previously ran debian (latest version) and recall I had to use a special switch to get around a ATA hard drive issue (don't know if this is a factor with ubuntu).

So my question is ... is this an issue with the server my pc is trying to access or is there a special switch I need to use to get around the ATA stuff?

Thx in advance for your help![/QUOTE]

---

### Post by irutgers on 2006-06-24
I successfully pinged Yahoo as suggested before the 76% mark ... once I get to the 76% mark ATL + CTRL + F1 doesn't work. 

[QUOTE=mibadt]Since you are after a server, I guess your problem might stem from the fact that the installation can't access the repositories during install.

You can verify this as follows:
1. Once you are almost there (say at about 70%) open a non graphical terminal by pressing ALT+CTRL+F1 (Beware-you'll be root there).
2. From that terminal try to ping (say ping [www.yahoo.com)](www.yahoo.com)).
3. If you can't ping you'll have to fix your Internet connecivity before proceeding. Issues to look at:
a. is your Ethernet (say eth0) up: run ipconfig, if necessary allocate a static IP (say 10.0.0.111) or run dhclient.
b. After that check the DNS issue and if necessary edit (using nano) /etc/resolv.conf and replace the addresses there with the DNS addrseses of your ISP.
c. Once you can ping you'll have to wait 2-3 minutes and instllation should proceed.

Note: at any stage you can switch back to the graphical install process by: ALT+CTRL+F[/QUOTE]

---

