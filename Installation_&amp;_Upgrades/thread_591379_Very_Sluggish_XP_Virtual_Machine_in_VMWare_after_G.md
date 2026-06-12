---
title: "Very Sluggish XP Virtual Machine in VMWare after Gutsy and VMWare update"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by Mavtech on 2007-10-25
I updated to Gutsy which as we all know breaks VMWare.  I uninstalled VMWare Server 1.0.3 and installed 1.0.4.  When I loaded my XP Virtual Machine into VMWare Server, it is incredibly slow.  It takes 5 minutes to load to the desktop and takes a long time to open up Outlook.  Did I miss anything when I updated?  I'm pretty sure I installed the linux headers.  When I updated VM Tools, it got worse.  Any ideas?  Thanks for any help.

---

### Post by Steve1961 on 2007-10-25
Afraid I haven't got any answers for VMware, but why not try Virtualbox - seems to be working fine, although I don't know how easy it is to import VMware images

---

### Post by Mavtech on 2007-10-25
I could try virtual box.  It's just a pain to have to go through the stupid activation again.  :lol:

My XP machine was working great in the previous version of VMWare and Ubuntu.

---

### Post by Steve1961 on 2007-10-25
> **Mavtech said:**
> I could try virtual box.  It's just a pain to have to go through the stupid activation again.  :lol:

My XP machine was working great in the previous version of VMWare and Ubuntu.

Would you need to reactivate?  The latest version of Virtualbox can import VMDK images, although I suppose teh change in virtual hardware could trigger a reactivation

---

### Post by jrasmussen0 on 2007-10-25
Did you upgrade the vmware tools for the XP machine?  I also had some problems running vmware in gutsy but that was because I used Cannonical's commercial repository which wasn't updated for gutsy.

The other issue I have had is time synch.  My Duo-Core 2 used a speed stepping technology and vmware server chokes when it tries to automatically detect my processor speed.

I had to edit /etc/vmware/config and add 
[INDENT]host.cpukHz = 2670000
host.noTSC = TRUE
ptsc.noTSC = TRUE[/INDENT]

And every time I upgrade the vmware module with vmware-config.pl, I have to readd the same lines.  I guess vmware-config.pl overwrites the file every time.

---

### Post by Mavtech on 2007-10-25
Yeah, I updated VMWare Tools.  It made it worse than it was before I installed the tools.  I will give the edits a shot.  Thanks!

---

### Post by Somatik on 2007-10-25
any of you know how to enable remote login?

---

### Post by Mavtech on 2007-10-26
> **Steve1961 said:**
> Would you need to reactivate?  The latest version of Virtualbox can import VMDK images, although I suppose teh change in virtual hardware could trigger a reactivation

VirtualBox rocks!  Thanks!  It's tons faster than VMWare has been for me.

---

### Post by Steve1961 on 2007-10-26
Glad you sorted it out.  Were you able to import the VMware image?

---

### Post by Mavtech on 2007-10-26
> **Steve1961 said:**
> Glad you sorted it out.  Were you able to import the VMware image?

No, I did a fresh install of Vista Enterprise.  I wanted to see how that works in VirtualBox.  So far, it works great.  I downloaded both files for the Office 2007 trial at the same time_ in the virtual machine_ at 1.9 MBps  (Yeah, we have a ridiculous connection here at work). The connection to our Service Center software and the Exchange server are nice and fast as well.  

Of course, at the same time, I may have figured out my issue with VMWare.  Looks like it could have been my error.  I could have sworn I had reboot since I installed VMWare 1.0.4.  After I reboot yesterday, I noticed that Ubuntu informed me that there was a new restricted driver loaded.  It was the VMWare kernel driver.  I don't think that was loaded before which could have been what was slowing down my guest OS.  Duh!

Either way, I am happy.  If I hadn't asked for this help, you would never have been able to show me VirtualBox.  I much prefer this over VMware!  Thanks!

---

### Post by Steve1961 on 2007-10-26
> Either way, I am happy. If I hadn't asked for this help, you would never have been able to show me VirtualBox. I much prefer this over VMware! Thanks!

Me too.  By the way, if you have problems accesing the usb subsystem just add this line to /etc/fstab

none /proc/bus/usb usbfs devgid=1002,devmode=664 0 0

the devgid entry is the group id of vboxusers

---

### Post by g_dwarf on 2008-03-23
> **Mavtech said:**
> I may have figured out my issue with VMWare.  Looks like it could have been my error.  I could have sworn I had reboot since I installed VMWare 1.0.4.  After I reboot yesterday, I noticed that Ubuntu informed me that there was a new restricted driver loaded.  It was the VMWare kernel driver.  I don't think that was loaded before which could have been what was slowing down my guest OS.  Duh!

I'm not so sure it was your fault. For days now I have been trying to run my native Windows XP installation in VMware Player (downloaded from VMware, I'm running Gutsy and I don't think it's in the repositories). I definitely rebooted my system a great number of times since installing VMware. In the end I decided to give Virtualbox a try. I just rebooted after installing Virtualbox, and I get the same message about the VMware kernel driver, which made me doubt my sanity for a second ("I just installed Virtualbox, right, not VMware?" "Yes I'm sure." "I did reboot after installing VMware before, right?" "Well, certainly, a million times, trying to dualboot XP").

So apparently it's Virtualbox that causes the VMware kernel driver to show up in Restricted Drivers? Does anyone know?

(I had a slight hope that XP would start now in VMware but alas)

---

