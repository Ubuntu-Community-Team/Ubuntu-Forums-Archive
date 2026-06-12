---
title: "Installed Ubuntu alongside Windows Vista but cannot boot into Vista"
date: 2012-01-16
forum: Installation &amp; Upgrades
---

### Post by fathobbit14113 on 2012-01-16
I installed Ubuntu into my C drive with the option "install alongside windows" while windows was running and manually created a partition for Ubuntu.  Now I have tried restarting my computer several times but cannot find the option to choose which OS to boot up.  I need to get back to Windows to see all my files, please help?

---

### Post by oldfred on 2012-01-16
I am confused on how you installed. There is no along side from inside Windows. If in Windows you can install wubi which is just a file inside Window's NTFS partition. Or you install to a separate partition.

To see exactly what is where, post the link to the results.txt that the boot info script creates from boot repair.:

Yanni has created a easy way to download boot repair & run script:
HOWTO : easily create a Boot-Info summary
[http://ubuntuforums.org/showthread.php?p=11164270](http://ubuntuforums.org/showthread.php?p=11164270)
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by fathobbit14113 on 2012-01-16
I guess what I meant was that the computer was on and running when I put the Ubuntu disk in and installed it. Then I chose the install alongside option.

---

### Post by fathobbit14113 on 2012-01-16
[http://paste.ubuntu.com/806688/](http://paste.ubuntu.com/806688/)       after following instructions this is what i was told (by the computer) to post to a forum.

---

### Post by darkod on 2012-01-16
What exactly happens when you start the computer?
Do you get the grub boot menu first or nothing at all, black screen?

Did you try running the cd in live mode to see if it works first? Black screen can mean video issue.

Otherwise the results don't show anything wrong. Nothing I can spot anyway.

---

### Post by fathobbit14113 on 2012-01-16
When the computer starts up it goes straight to Ubuntu.  When I installed it, it said it would give me the option to choose either Windows or Ubuntu whenever the computer turned on.  I'm having trouble getting to Windows.

---

### Post by darkod on 2012-01-16
Hmmm, according to the results it located Vista correctly and it should show you a boot menu.
Also, are you aware you have a wubi install inside windows? Most people deinstall wubi before installing a dual boot.

Boot ubuntu and post the result of:
df -h

---

### Post by oldfred on 2012-01-16
Your sda1 looks larger than the normal 100MB boot/recovery partition, but it has wubi and does not have this file:
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition, but may all in one partition)
/bootmgr /Boot/BCD [COLOR=DarkRed]/Windows/System32/winload.exe 
[/COLOR]

Sometime script does not find winload.exe, do you have it in your sda1? or somewhere else on system. It is normally the c: drive.

---

### Post by fathobbit14113 on 2012-01-16
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             138G   11G  120G   9% /
none                  3.4G  688K  3.4G   1% /dev
none                  3.4G  124K  3.4G   1% /dev/shm
none                  3.4G   92K  3.4G   1% /var/run
none                  3.4G     0  3.4G   0% /var/lock

---

### Post by fathobbit14113 on 2012-01-16
Oldfred, I'm afraid I don't understand what you mean.. I don't know how to look for that file.

---

### Post by oldfred on 2012-01-16
From Ubuntu file browser Nautilus, can you click on sda1. It may just show as 400GB or whatever size it is. Then you can browse it and see if it has all your normal Windows files & folders.

---

