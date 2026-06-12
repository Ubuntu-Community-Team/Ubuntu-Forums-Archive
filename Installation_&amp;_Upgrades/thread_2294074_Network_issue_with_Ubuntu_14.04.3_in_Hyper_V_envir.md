---
title: "Network issue with Ubuntu 14.04.3 in Hyper V environment / not running stable"
date: 2015-09-09
forum: Installation &amp; Upgrades
---

### Post by Rainer78 on 2015-09-09
Hi @ all,

  I think I have problems with my network connection on my 14.04.3 x64 servers.

  What happened up to now: A few month ago, I installed Ubuntu server 14.04.1 on a physical PC. I  installed Samba, LAMP (for subversion access), Firebird-SQL-Server and  that's it. Everything works fine. We planed to change the physical PC to  a virtual machine and I installed everything on a Hyper-VM system  (running on a Windows Server 2008 R2 host). Everything here works fine,  too. 

  
I updated both servers everytime with "apt-get dist-upgrade" and so I  have Ubuntu 14.04.3 on them now. But since I updated to 14.04.3, I got  problems with my network connections.

  The issue is the same on both machines (physical an VM). When I try to access the Samba shares from my Windows notebook (or  accessing subversion repositories), it works several minutes, and then  the system crashes.

  On the physical PC, I can't access via PuTTY (ssh) and I can't login  at the PC itselfs. When I press the Numlock key on the keyboard, the LED  doesn't changed the state.

  
On the VM, I can't access via PuTTY, but when I use the console, I still can controll the VM. I found an article ([https://technet.microsoft.com/de-de/library/Dn531029.aspx](https://technet.microsoft.com/de-de/library/Dn531029.aspx))  and I installed the packages they mentioned. But I still have the  problem. While I was restoring archive files (created on the physical PC) on the  VM (I had access via PuTTY), the system crashes, too (but only the  network device). Accessing via console still works.

  
To keep my daily business alive, I reinstalled my physical PC with 14.04.2, and I don't have any problems any more (up to now).

  Is there anything I can do to get the 14.04.3 version running  (primary on the VM)? Otherwise I think I have to reinstall 14.04.2 on  the VM, too. Or do you now any command / service I have to call /  restart to get the network running again? 


  Regards,

  Rainer

---

### Post by TheFu on 2015-09-09
Not the answer you want, but .... Use KVM as the hypervisor. Haven't ever seen these sorts of issues with it. Can't remember the last time it crashed .... because it has NEVER crashed in 5+ yrs of running 20 VMs.

What do they say - mixing vendors just ends up with 1 vendor blaming the other?

Might be important to move this thread to virtualization too, but hardly anyone there uses hyper-v.

---

### Post by Rainer78 on 2015-09-10
Hi TheFu,  > **TheFu said:**
> Not the answer you want, but .... Use KVM as the hypervisor.   Yes, that's true :-)  If I could decide it, I would do it. :-(    My IT department prefers Windows-Servers (including as Guest / VMs) and I am the only one who wanted an Ubuntu VM.  I guess I will set up the machine with 14.04.2 and don't make an dist-upgrade any more.   Regards,    Rainer

---

### Post by Rainer78 on 2015-09-10
Yesterday evening I installed 14.04.2 on the physical PC and updated all packages with apt-get upgrade. I didn't run apt-get dist-upgrade. This morning everything works fine. The login screen shows 14.0.4.3, but the kernel is still 3.16.0-30.  So I made the same procedure on my VM and up to now th VM works fine, too.  So I think the problem is part of the kernel. For me, I won't run a dist-upgrade for the next time.

---

### Post by TheFu on 2015-09-10
> **Rainer78 said:**
> Hi TheFu,    Yes, that's true :-)  If I could decide it, I would do it. :-(    My IT department prefers Windows-Servers (including as Guest / VMs) and I am the only one who wanted an Ubuntu VM.  I guess I will set up the machine with 14.04.2 and don't make an dist-upgrade any more.   Regards,    Rainer

Please note the EOL dates: [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) before decided what to load.

---

