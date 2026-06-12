---
title: "What is the system requirement to run Ubuntu 11.04?"
date: 2011-04-22
forum: Installation &amp; Upgrades
---

### Post by fred_gavin on 2011-04-22
Dear All, 

I just upgraded to Ubuntu 11.04 Beta from 10.10. As I am running Ubuntu in VirtualBox on Windows 7 host, so when I restart Ubuntu, the message about "Unity" appears, and says the system does not meet the requirements to run "Unity". 

Currently, I signed 2CPU, 1.5G RAM and 64MB video memory to Ubuntu, and it works perfectly on 10.10. 

So is it the video memory too small to run 11.04? 

After "unity" fails, the classical desktop is still working. But the desktop screen again become small on the monitor. 

This is the problem when I upgraded 10 from 9. Although I solved it at that time, kind forgot how. 

Could anyone please give me some suggestions, again?

Thank you very much

---

### Post by coffeecat on 2011-04-22
The problem is graphics in VirtualBox. You need 3d acceleration for Unity because Unity is a compiz plugin. 

I believe that if you install the very latest version of VirtualBox and install the guest additions into the guest Natty system, then you will be able to enable 3d and get Unity, but I haven't tried this for myself.

---

### Post by fred_gavin on 2011-04-22
Thanks for the reply. 

I am using VirtualBox 4.0.4, the latest one 4.0.6 was just released on 21/04/2011. 

I did install the guest addition and enable the 3d acceleration when I set up VirtualBox and Ubuntu 10.10. 

I increased video memory to the maximum allowed 128 just now. But as "unity" seemed disabled at first place, so still the classical desktop screen. And the desktop still fairly small. 

Any further suggestion?

Thank you.

---

### Post by coffeecat on 2011-04-22
If the Natty virtual window is small and you can't resize it, it sounds as though guest additions are not installed properly. If you installed them in Maverick, they might need re-installing.

There are a couple of threads about VirtualBox and Natty in the Natty subforum:

[http://ubuntuforums.org/forumdisplay.php?f=394](http://ubuntuforums.org/forumdisplay.php?f=394)

You might get more replies in that forum. If you want to have your thread moved there, simply click on the [IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG] button in one of your own posts and ask a mod to move it. Don't worry about it being called "Report abuse" - it can be used to request a simple move of thread.

---

### Post by Hedgehog1 on 2011-04-23
> **fred_gavin said:**
> Thanks for the reply. 

I am using VirtualBox 4.0.4, the latest one 4.0.6 was just released on 21/04/2011. 

I did install the guest addition and enable the 3d acceleration when I set up VirtualBox and Ubuntu 10.10. 

I increased video memory to the maximum allowed 128 just now. But as "unity" seemed disabled at first place, so still the classical desktop screen. And the desktop still fairly small. 

Any further suggestion?

Thank you.

I you wish to run Unity, you will need to install the 4.0.6 version of Vbox and then re-load the updated guest additions.

I just loaded 4.0.6 today, and installed Natty and had Unity running after installing the new guest additions and rebooting the virtual machine.

***The Hedge***

:KS

p.s. It is possible to run Unity in 4.0.4, but it requires and long list of painful steps and fussing about.  It was really nice to have Unity up and running so easily with 4.0.6

---

