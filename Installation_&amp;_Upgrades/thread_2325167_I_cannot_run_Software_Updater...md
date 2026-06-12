---
title: "I cannot run Software Updater.."
date: 2016-05-19
forum: Installation &amp; Upgrades
---

### Post by Robert_Cline on 2016-05-19
Greetings.

I am running Ubuntu 16.04 on an HP 2000-2b09WM, specs as follows:


Product Name
2000-2b09WM


Product Number
C2N25UA


Microprocessor
1.3GHz AMD E-300 Accelerated Processor


Microprocessor Cache
1MB L2 Cache


Memory
2GB DDR3 SDRAM DIMM (I have upgraded this to 4gb)


Video Graphics
AMD Radeon HD 6310 Discrete-Class graphics


Display
15.6-inch diagonal HD BrightView LED-backlit display (1366x768)


Hard Drive
320GB 5400RPM hard drive


Network Card
10/100BASE-T Ethernet LAN (RJ-45 connector)


My problem is that when I run the Software Updater, or try to update via Terminal or Synaptic, whichever one I use hangs... forever. 

HTOP says that one of my 2 processors is stuck on 100 percent, and the process is:  'appstreamcli refresh', PID is 2233.

I Googled this and the result was over my head. LOL.

Can anyone explain this to me?

Thanks.

---

### Post by Brandon_MacEachern on 2016-05-19
I think the server is down.  I'm having this same issue on a brand new installation.  If I try to install with updates, that hangs too.

---

### Post by bearlake on 2016-05-19
Have you tried a different server?

Were any errors reported? If so please post.

or

Post the output of these if there any errors and please use code tags.

```
sudo apt update && sudo apt upgrade
```

---

### Post by Brandon_MacEachern on 2016-05-19
Yea that won't work.  Sage found out that disabling backports fixes this issue.  It really is something wrong with the metadata on backports causing appstreamcli to max out 100% usage.

No logs, no errors.  It just freezes on update, so upgrade is never ran.

---

### Post by Robert_Cline on 2016-05-19
I have not received any error messages, just hangs and CPU goes to 100 percent.. I also have a new installation, also, this is happening on my other computer, an Acer HTPC, with Ubuntu 16.04 and a new installation. Good to know it probably is not just me. Thanks for the information, I appreciate you guys.

OK, I disabled the backports, and ran it again, and it works. Thanks again, Brandon.

---

### Post by bearlake on 2016-05-19
It seems some people are having the same troubles as you.

I'm sure they will have it fixed shortly.

Not sure why I was able to update with no issues.

---

### Post by Mishrito on 2016-05-20
There's been another thread about this. This is the relevant bug report.
[https://bugs.launchpad.net/ubuntu/+source/appstream/+bug/1583845](https://bugs.launchpad.net/ubuntu/+source/appstream/+bug/1583845)

 It seems simply removing the appstream package will solve the issue and allow you to update normally. However this will also remove gnome-software (the fancy GUI application that comes with ubuntu for dealing with apps). If you want to keep that, you will have to install the fixed appstream package which is linked to somewhere in the comments for that bug report, But if you don't care about "Gnome Software", then simply remove appstream.

---

### Post by geovino on 2016-05-20
Same here, no updates. Will use another OS until they fix the problem.

---

### Post by vanadium on 2016-05-20
It will be solved pretty soon, and if you do not want to wait, [it is easily fixed with some commands](https://bugs.launchpad.net/ubuntu/+source/appstream/+bug/1579712):
```

sudo mv /etc/apt/apt.conf.d/50appstream /etc/apt/apt.conf.d/50appstream.disabled
cd /tmp && mkdir asfix
cd asfix
wget https://launchpad.net/ubuntu/+archive/primary/+files/appstream_0.9.4-1ubuntu1_amd64.deb
wget https://launchpad.net/ubuntu/+archive/primary/+files/libappstream3_0.9.4-1ubuntu1_amd64.deb
sudo dpkg -i *.deb
sudo mv /etc/apt/apt.conf.d/50appstream.disabled /etc/apt/apt.conf.d/50appstream

```
I agree with you that it is a pity that such very visible bugs sometimes do pop up, but that's life, I guess.

---

### Post by Robert_Cline on 2016-05-20
True dat, LOL.. thank you all for the help & info.

---

### Post by TerryDixon on 2016-05-22
I have the same problem.

---

### Post by geovino on 2016-05-23
Repos are working now...

---

