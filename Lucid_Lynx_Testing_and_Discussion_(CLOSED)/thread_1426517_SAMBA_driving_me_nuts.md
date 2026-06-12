---
title: "SAMBA driving me nuts"
date: 2010-03-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by theozzlives on 2010-03-10
I upgraded Karmic to Lucid (I was having probs in Karmic) ans everytime I'd bring up the network all I would see is "Windows Network". I'd click on it and it'd say it can't receive the share list from the server. Well it did that after the upgrade, so I did a fresh install. Now I can get to my workgroup, but get the same message when I click on it. My laptop don't show on the network. I filed a bug report, but was wondering is it just my system or is it affecting others?

---

### Post by emarkay on 2010-03-10
Yea, join the club!

[http://ubuntuforums.org/showthread.php?t=1420657](http://ubuntuforums.org/showthread.php?t=1420657)

Pretty pathetic (IMHO) if you ask me...

---

### Post by timosha on 2010-03-10
It worked fine in Lucid up to 3 weeks ago. Now I have this problem on 3 Thinkpads, 1 HP Pavilion and 1 HP dx2400.

Samba works as long as I don't use password protected shares. When I try to access a password protected share I get that "Mounting" message, CPU load goes up to 100%, CPU is heating up and fans go crazy and after 15 minutes I get a dbus error message.

But, it works fine in Karmic.

---

### Post by whoop on 2010-03-10
Do you get high cpu usage from gvfsd-smb-brows while experiencing this?
I reported a bug on this:
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/532024](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/532024)

But ubuntu won't be fixing it so I upstreamed it:
[https://bugzilla.gnome.org/show_bug.cgi?id=612202](https://bugzilla.gnome.org/show_bug.cgi?id=612202)

---

### Post by timosha on 2010-03-10
Yes, this is exactly the bug I am experiencing.

---

### Post by theozzlives on 2010-03-15
Apparently this is a SAMBA problem. This weekend I installed Jaunty (which I've NEVER had a problem with) on a customer's computer. I plugged it into the network and the same thing happened. Fortunately he don't run a network. Anyhow we must've got a bad update down the tubes or something, hope SAMBA fixes it soon. It's making Ubuntu look bad.

---

### Post by tad1073 on 2010-03-15
similar problem here, samba takes forever to open the shares, then I get pop-ups about opening the shares and then the dbus errors. Even moving the network icon freezes my system for a bit.

---

### Post by theozzlives on 2010-03-17
Well Beta 1 is tomorrow, something needs to be done. I'd hate to see a broken LTS get released.

---

### Post by whoop on 2010-03-17
> **theozzlives said:**
> Well Beta 1 is tomorrow, something needs to be done. I'd hate to see a broken LTS get released.

Well, my bug report is starting to get quite active ([https://bugs.launchpad.net/ubuntu/+s...fs/+bug/532024](https://bugs.launchpad.net/ubuntu/+s...fs/+bug/532024)), so things are being done. Join in if you want.

---

### Post by theozzlives on 2010-03-23
I keep getting updates to SAMBA, but no fix! I need my networking to work so I can setup my server to be a domain controller.

---

### Post by pbpersson on 2010-03-23
I use SMB4K with the IP addresses for the remote machines and then bookmark the connection so I don't have to remember it when I want to connect to the data server.

A poor solution but it works......

---

### Post by theozzlives on 2010-03-23
> **pbpersson said:**
> I use SMB4K with the IP addresses for the remote machines and then bookmark the connection so I don't have to remember it when I want to connect to the data server.

A poor solution but it works......

I've got my IPs bookmarked, but I need the name resolution in Nautilus. Windows 7 doesn't have a problem seeing the network by host name.

---

### Post by Ron F. on 2010-04-12
This is bad and has to be fixed before the final release at the end of the month.

Ubuntu 10.04: To get around the problem, I am using Gigolo and then I bookmarked the Windows server shares I need directly against their various 192.168.*.* IP addresses. Name resolution is still not working.

Ubuntu 9.10: Name resolution works fine.

---

### Post by theozzlives on 2010-04-16
Release  is 13 days away, are they gonna fix SAMBA or are they gonna have another broken release? LTS is important that it works!

---

