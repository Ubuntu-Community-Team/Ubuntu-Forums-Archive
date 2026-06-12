---
title: "Virtual Box Problem"
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by Ceiber Boy on 2010-01-18
Hi

I'm running Ubuntu 9.10 - the Karmic Koala (64-bit)- released in October 2009. in every way it works perfectly, from the repository using the synaptic package manager i installed virtual box (VB) to run windows XP (32-bit). 

when i installed everything went well and i was able to install and run without problem XP in VB, however upon rebooting the computer i opened VB and then tried to start XP, then i was confronted with the following Error messages:

  p, li { white-space: pre-wrap; }  *Failed to open a session for the virtual machine WinXP.*
 *Virtual machine 'WinXP' has terminated unexpectedly during startup.*
 

  p, li { white-space: pre-wrap; }  [I]Kernel driver not installed (rc=-1908)

Please install the virtualbox-ose-source package[/I]
 i followed the instructions and reinstalled 'virtualbox-ose-source package' again using the synaptic package manager. again it worked immediately but upon rebooting my machine it constantly returns to the same problem. I have also tried downloading VB direct from sunmicro systems but still have the same problem.


[U]Questions
[/U]How do i fix this problem?
Is VB from the repositories 64-bit?

Any help would be greatly appreciated as i am a Linux convert and now loath using windows but an forced to due to software used by my employer that will not run on wine!

Regards

---

### Post by lorsen on 2010-01-18
If you got the same error when downloading  the 64 bit variant directly from sunmicro systems it seems that it is not a problem with the package in the repos.

Did you install the guest additions inside WinXP? I don't really believe it will solve the problem but it is worth a try.
(Sorry, don't have a link at hand.)

---

### Post by Ceiber Boy on 2010-01-18
yes i did install the guest additions and the problem still remains!

---

### Post by lorsen on 2010-01-18
Did you run the vbox the first time as root or as "normal user"[I]?
[/I]I just stumbled about this guide [http://ubuntuguide.net/installi-windows-xp-inside-ubuntu-using-virtualbox](http://ubuntuguide.net/installi-windows-xp-inside-ubuntu-using-virtualbox) where they add the user to the group *vboxusers*.
However I don't know if this is necessary (my vbox runs under mac os).

Since I have no real idea I just keep asking, maybe we slowly approach the problem ;-):
What happens when u close winxp and vbox and restart winxp, without restarting the computer/ubuntu?

---

### Post by SirBismuth on 2010-01-18
I sometimes have issues with VB after a kernel update, it tells me to run a command... which I cannot remember, and my troubleshooting file is at home.  

Does it only tell to to reinstall that package, nothing about running a command?.

Just checked Google, and my issue was solved when the command "modprobe vboxdrv" is run.

B

---

### Post by Ceiber Boy on 2010-01-18
Once XP is runing i can start and stop it as many times as i like and it will still reload, however when i reboot Ubuntu it requires me to run the following command:

[FONT=monospace]sudo /etc/init.d/vboxdrv setup
[/FONT]
form what i understand this recompiles the kernel!! yes/no? however when i do run this command things seem to work!

how do i therefore get around running this command every time i reboot?

---

### Post by Ceiber Boy on 2010-01-19
/dev/vboxdrv and vboxnetctl disappear on reboot

how can i stop this from happening?

---

### Post by banerjeerupak on 2010-04-06
I'm running 32 bit xp in my vbox over my karmic koala. 
Now i'm planning to upgrade to the Ubuntu 10.04. Would it affect the vbox and the xp within it. Also, there is an upgrade of vbox ready to install, should i do it. I have set up xp after a lot of trouble, and don't want to go through it again.

---

