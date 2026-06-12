---
title: "Unsupported Work install"
date: 2005-03-19
forum: Installation &amp; Upgrades
---

### Post by viniosity on 2005-03-19
My wife recently took a new job at a large organization.  The job comes with a standard dell desktop loaded with Windows 2000.  It's constantly crashing and causing her problems so she's asked me to put linux on it for her.  As far as I know there are no special apps she needs to run except that she has to connect to an exchange server.  I'm looking for the easiest way to go about it:

1. should I use a 2nd disk loaded w/ Ubuntu and put it into the computer? Else, what's the easiest way to reduce the win2000 partition size (w/out forking over $$ for partition magic) and install Ubuntu?

2. what do I need to connect her to the exchange server besides plain 'ol evolution?

3. any other pitfalls I should be aware of?

---

### Post by gungaden on 2005-03-21
How familiar are you with Linux? If you are not well-versed in Linux program installation and maintenance, perhaps your best bet is to repair your wife's Windows installation. Windows products are well known for problems caused by installs/uninstalls of software, interrupted boots and shutdowns, etc. A copy of Norton Systemworks sometimes is well worth the money to repair such problems. If there are not many files personal files on the laptop, I recommend that you back them up on floppy or CD and then re-install your Windows and other software...you will be amazed at the results. I am not against using Ubuntu or other Linux operating systems on a personal PC, but if you are not really knowledeable about Linux, you may have a lot of learning to do to install, configure, and maintain the various Linux programs.

---

### Post by bored2k on 2005-03-21
[QUOTE=gungaden]How familiar are you with Linux? If you are not well-versed in Linux program installation and maintenance, perhaps your best bet is to repair your wife's Windows installation. Windows products are well known for problems caused by installs/uninstalls of software, interrupted boots and shutdowns, etc. A copy of Norton Systemworks sometimes is well worth the money to repair such problems. If there are not many files personal files on the laptop, I recommend that you back them up on floppy or CD and then re-install your Windows and other software...you will be amazed at the results. I am not against using Ubuntu or other Linux operating systems on a personal PC, but if you are not really knowledeable about Linux, you may have a lot of learning to do to install, configure, and maintain the various Linux programs.[/QUOTE]
 Or he can install Linux, and install vmware on top of it with Windows just in case she/he ever needs a Windows specific application ;) .

---

### Post by gungaden on 2005-03-21
Yes.

My suggestions were based upon his statement that the current Windows installation is constantly crashing and that perhaps he may have a steep learning curve with Linux. I believe that WE ALL wish to become Linux gurus and move to the Linux environment, but sometimes the time necessary to get something installed and running successfully in Linux is not possible if we have work that has to be done today.

---

### Post by Buffalo Soldier on 2005-03-21
[QUOTE=viniosity]1. should I use a 2nd disk loaded w/ Ubuntu and put it into the computer? Else, what's the easiest way to reduce the win2000 partition size (w/out forking over $ for partition magic) and install Ubuntu?[/QUOTE]
[list]
[*]I would choose the route of 2nd disk. Even by being careful, there is still risk in changing partition size.   
[*]Not easiest but at least cheaper way of resizing is booting with Ubuntu LiveCD and then resizing using **parted** or **Qparted**. 
[/list]   > 
2. what do I need to connect her to the exchange server besides plain 'ol evolution?I think evolution can handle it quite well with its [evolution-exchange]("http://higgs.djpig.de/ubuntu/www/hoary/gnome/evolution-exchange") plugin.

 >  3. any other pitfalls I should be aware of?I don't think the main hurdle is technical problems but with the company your wife is working with. I think most companies have IT policies regarding adding new hardware / software to their computers.

---

### Post by viniosity on 2005-03-21
[QUOTE=Buffalo Soldier][list]
[*]I would choose the route of 2nd disk. Even by being careful, there is still risk in changing partition size.   
.[/QUOTE]

Just so that I'm sure.. if I use the 2nd disk method I would pop a second hard disk in, make sure it's set up as a slave disk, then insert the ubuntu cd and, when asked for where to install, choose HDB (and let it auto-partition).  Where would I install grub? MBR?

---

