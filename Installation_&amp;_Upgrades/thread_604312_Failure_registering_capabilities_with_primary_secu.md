---
title: "Failure registering capabilities with primary security module"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by sendxp on 2007-11-06
When I upgrade the system from 7.04 server to 7.10. I just get a error message as "[COLOR="Red"]Failure registering capabilities with primary security module[/COLOR]"

I try on reload the kernel module but not working with "modprobe capability" command. the error is as the below: 
**FATAL: Error inserting capability (/lib/modules/2.6.22-14-server/kernel/security/capability.ko): Invalid argument**

I had search with Google and someone but no any best answer. Is is right or ..., and how to fix this problem? if you can please give me a hand. thank you very much.

---

### Post by Nehvrook on 2007-11-06
I'm having the same problem now. I managed to get into Ubuntu again using the old Kernel but it's put me in "Low Graphics Mode" for some reason. Not a clue what to do right now. Any help would be great.

---

### Post by Handssolow on 2007-11-07
I've found this message too in my /var/log/messages on my  Gutsy system.

My Gutsy OS is showing some signs of instability unlike Feisty before. Boot up is slower partly I suspect because Xserver resets as I'm not using the default screen resolution. Sometimes it doesn't boot properly and then  I have to press my reset button and sometimes it hasn't shut down properly without error messages popping up.

I've spotted three error massages so far.

ACPI: looking for DSDT in intramfs ....error, file /DSDT not found
Probably not that important but I'm not certain.

Failure registering capabilities with primary security module

Repeated lines of  Network Manager, perhaps trying to work my wireless card which I've removed and now use a wired connection.

---

### Post by sendxp on 2007-11-07
Maybe upgrade isn't a good solution for any system.
I will try to install a new normal Ubuntu 7.10 sever and to lookup it.

---

### Post by smurphy_it on 2007-11-09
I don't think that is it.  I have done a clean install of Gutsy 7.10 but I have that same error message when I do a dmesg.

---

### Post by bastubis on 2007-11-26
Firefox won't load, says it can't initialise browser's security component. I've followed the instructions here: [http://forums.mozillazine.org/viewtopic.php?t=272556&sid=5dfaf5ed5be5d448883d892d8528db09](http://forums.mozillazine.org/viewtopic.php?t=272556&sid=5dfaf5ed5be5d448883d892d8528db09) -- creating a new profile worked temporarily but soon got the error msg again with firefox refusing to load. 

I've got this in dmesg:

[   25.436000] Failure registering capabilities with primary security module.

I thought it might be a corrupt partition so I ran fsck and it fixed some errors but I'm still getting the firefox message and 'failure registering capabilities' message from dmesg -- don't know what to do next?

---

### Post by sylecn on 2007-12-04
I have the same error repeat in my /var/log/message.
This error message is not harmful. See [http://www.nsa.gov/selinux/list-archive/0308/4961.cfm](http://www.nsa.gov/selinux/list-archive/0308/4961.cfm)

Firefox is working fine.

I also get repeat error:

 ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.

It's nothing with upgrade. I install gutsy clean.

---

### Post by joehack on 2007-12-05
My Ubuntu Server 7.10 reports the same message. It was a installation from scratch.
Strange!

Regards,
Jochen

---

### Post by Handssolow on 2007-12-05
> **sylecn said:**
> I have the same error repeat in my /var/log/message.
This error message is not harmful. See [http://www.nsa.gov/selinux/list-archive/0308/4961.cfm](http://www.nsa.gov/selinux/list-archive/0308/4961.cfm)

Firefox is working fine.

I also get repeat error:

 ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.

It's nothing with upgrade. I install gutsy clean.

My  /var/log/messages has "SELinux: Disabled at boot" which doesn't fit with the nsa.gov advice.

---

### Post by dclausen on 2007-12-06
> **sendxp said:**
> When I upgrade the system from 7.04 server to 7.10. I just get a error message as "[COLOR="Red"]Failure registering capabilities with primary security module[/COLOR]"
.

This error means a program is attempting to use a port that is already in use.  I found this out after attempting to start bind9 via: /etc/init.d/bind9 start while it was already running.

So, short answer is: something is trying to start that's already started.

---

### Post by pmilano1 on 2007-12-31
This is not the case. 

I have the same issue with Bind9, and there is nothing but p22 in use.

---

### Post by starscalling on 2008-01-18
ok lets see if we can solve this over the weekend here:
Jan 15 14:41:30 masterloki kernel: [  321.848003] Security Framework v1.0.0 initialized
Jan 15 14:41:30 masterloki kernel: [  321.848067] SELinux:  Disabled at boot.

 is first part and

Jan 15 14:41:30 masterloki kernel: [  323.780346] AppArmor: AppArmor initialized<5>audit(1200436869.636:2):  type=1505 info="AppArmor initialized" pid=1178
Jan 15 14:41:30 masterloki kernel: [  323.787771] fuse init (API version 7.8)
Jan 15 14:41:30 masterloki kernel: [  323.793564] Failure registering capabilities with primary security module.

being the second bit
so whats inside the security framework? sorry but i'm on the way out - i'll check back later ^^

---

### Post by bastubis on 2008-01-26
I uninstalled the Allpeers extension from Firefox and now it loads fine. Allpeers worked fine on feisty but seems to cause an error when starting Firefox from a profile with Allpeers installed. :confused:

---

### Post by cbonar on 2008-01-26
Hi, I've same error in dmesg, but I dont see any apparent error : Firefox is working fine and I'm not using Allpeers. Can you check if it didn't uninstall some dependency or something ?

By the way, I've problems with my network card (Intel 2200BG) disconnecting regularly, and I had to disable hardware encryption to get rid of other error messages (this is why I was searching for some answers about this message).

My dmesg :

```
[   16.991945] AppArmor: AppArmor initialized<5>audit(1201367763.932:2):  type=1505 info="AppArmor initialized" pid=1198
[   16.999100] fuse init (API version 7.8)
[   17.003623] Failure registering capabilities with primary security module.
```

---

### Post by cracker on 2008-04-12
I get this message every time I start bind. Is there something I should be concerned about here?

---

### Post by DjCoke on 2008-04-13
I get this messag too when i start bind9.
What's happening here?

---

### Post by ikt on 2008-05-01
I get this message too when i start bind9.
What's happening here?

---

### Post by plumcreek on 2008-05-08
Check /var/log/syslog and see if it is reporting any typos in your /etc/bind/named.conf file.

---

### Post by shof2k on 2008-06-08
I get the same message during boot, even after a vanilla install of Hardy.  Googling, I found [http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/899006039831]("http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/899006039831") suggesting a conflict between SELinux and Capabilities.


Bug 163616 at [https://bugs.launchpad.net/ubuntu/+bug/163616]("https://bugs.launchpad.net/ubuntu/+bug/163616") also confirms this.

I'd sugggest it isn't a major problem unless you also get the message running your own programs.

Peace

---

### Post by Nullack on 2008-06-20
I get this, and the strange thing is I dont use the capabilities module? lsmod doesnt show it.

Its reported under bug [https://bugs.launchpad.net/ubuntu/+bug/163616](https://bugs.launchpad.net/ubuntu/+bug/163616)

Jun 20 19:25:23 ppp kernel: [   28.636543] Security Framework initialized
Jun 20 19:25:23 ppp kernel: [   28.636551] SELinux:  Disabled at boot.
Jun 20 19:25:23 ppp kernel: [   28.636566] AppArmor: AppArmor initialized
Jun 20 19:25:23 ppp kernel: [   28.636570] Failure registering capabilities with primary security module.

---

