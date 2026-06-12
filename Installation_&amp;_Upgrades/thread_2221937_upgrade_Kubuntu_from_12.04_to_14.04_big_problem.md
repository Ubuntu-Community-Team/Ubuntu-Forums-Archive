---
title: "upgrade Kubuntu from 12.04 to 14.04 big problem"
date: 2014-05-04
forum: Installation &amp; Upgrades
---

### Post by sgxnew54 on 2014-05-04
Hi guys,

I followed the wiki to upgrade (Kubuntu 12.04 LTS to 14.04 LTS Upgrade)  and after the step 2) "install update from Muon update manager" the  system asked me to restart to complte the update, I did but after reboot   I get many error and  at last I get the panel of the USER ID and  PASSWD. I Typed the credentials but the system starts to work but get  again the panel userr id and passwd, i.e. I didn't get the desktop. 

So I cannot complete the upgrade, as reported on the wiki, i.e. I didn't run the step 3 "Press **Alt-F2** and type **kubuntu-devel-release-upgrade**" and so on ....

Please do you have any idea to go on .
thanks in advance
Sandro

---

### Post by sgxnew54 on 2014-05-04
Hello, 
I don't get the desktop, I tried many times , the problem could be KDE?  and in this case what can be done  please ..??

regards

---

### Post by SeijiSensei on 2014-05-04
Connect the machine to your router with an Ethernet cable and boot into [recovery mode]("https://wiki.ubuntu.com/RecoveryMode"). Choose the "root shell" option when prompted and run the commands
```

mount -o remount,rw /
dhclient eth0
```
to have your machine join the network. You don't need sudo in recovery mode because you already have root privileges.  That means you can do all sorts of damage to your installation if you're not careful.

If the machine uses static addressing with entries in /etc/network/interfaces, you can start the network with the command "service networking start".

Now try running the updater from the command prompt by entering the command "do-release-upgrade -m desktop -f kde -d".  If this is a server, replace "desktop" with "server".

Everyone here is a volunteer so it can take time for someone knowledgeable (or allegedly knowledgeable like me!) to read and respond to your requests.  In general you should wait at least twenty-four hours before bumping a post.

---

### Post by sgxnew54 on 2014-05-04
Hello, thanks for your answer.
after boot in recovery mode and set up the network/ethernet  (ping works) I tried the cmd  "do-release-upgrade -m desktop -f kde -d", but i get the following messages like:

verify  new ubuntu release
no new release found.

   So I cannot go on .
 

 Other useful information to describe the situation :

 the cmd "uname -a" gives "Linux 3.2.0-61-generic", and on the terminal I see &#8220;Ubuntu 14.04 LTS&#8221; .
 After typed userid and passwd on the panel , I get now a little window, on the left corner of the video, like a terminal, where is possible type the comand  linux. That is very strange for me. but I cannot get the desktop.

regards .

---

### Post by monkeybrain20122 on 2014-05-04
There should be a big hand sticking out of the computer  to slap some senses into the user when he/she tries to "upgrade" with the upgrade manager. :) "upgrade" is easily the most problematic feature of Ububtu. It is unreliable, complex and takes hours to complete and likely to result in a broken system,--the degree of broken-ness is directly proportional the deviation from a vanilla install. 

Always do a fresh install, the small preparation you make is going to save you much troubles down the road. The corollary is that there is no point trouble shooting a blotched upgrade if it is not something trivial that you can fix in 5 minutes because you cannot be certain about how broken it is. It will be a lot faster to do a fresh install and you can be certain that the system is healthy (except for real bugs of course)

---

### Post by ibjsb4 on 2014-05-04
So you can get to terminal.  Have you tried the standard fixes?

```
sudo dpkg --configure -a
```

```
sudo apt-get -f install
```

---

### Post by sgxnew54 on 2014-05-05
Hi,
after the followings
sudo dpkg --configure -a
sudo apt-get -f install
I get these errors:
dpkg: errors processing package debtags (--configure): 
the sub-process post-installation returned the error status 139

error occured while processing : debtags

E: sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by beartham on 2014-11-06
I was doing fine with 12.04 on this HP Pavilion dv 6000 laptop, which I normally use with a Live USB containing TDE 3.5.13.2 instead of Kubuntu 12.04 which was previously upgraded from Kubuntu 9.04 successfully. I don't normally use the native installed 12.04 because I still hate KDE 4. But I thought I might as well see if it had been improved with 14.04. I clicked on a popup invitation to upgrade, assuming all would go well has it had before.

It did the upgrade taking about 2 hours. Then it requested that I restart to complete the upgrade. When it tried to reboot, I got this screen message:

   Intel(R) Boot FEP v4.1.18
   Copyright (C) 1997-2005, Intel Corporation

   CLIENT MAC ADDR: 00 16 36 EF 90 A1  GUID: 434E4637 3035 3456 4A57 001636EF90A1PXE-E53:
   No boot filename received

   PXE-M0F: Exiting Intel Boot Agent.
   Invalid partition table

Then the machine halted.

If anyone knows how to fix this situation from a Live USB. I can boot from it and try to fix the partition table you can tell me how. 

Otherwise, I guess I may be able to offload data from the hard drive, and try installing Kubuntu 14.04 from scratch.

Thanks in advance,

Joseph Thames,
beartham

---

