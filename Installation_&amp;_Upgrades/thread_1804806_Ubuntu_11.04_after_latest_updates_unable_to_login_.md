---
title: "Ubuntu 11.04 after latest updates unable to login to the system"
date: 2011-07-15
forum: Installation &amp; Upgrades
---

### Post by j.gohel on 2011-07-15
I have installed Ubuntu 11.04 32-bit on my new desktop.
After installation all gone well.

The initial upgrades after fresh installation also ran well and I was able to reboot and use the system successfully.This was before three-days.Yesterday night I ran again the Update Manager and installed the available (4-5) updates and then I installed Sun-Java-JDK using Synaptic Package Manager using the packages from the canonical partners.

After installation was done I shut down the system and in the morning when
I restarted the system the login screen is coming up but on entering the login credentials a black screen with some text(unable to see the text) flashes and returns me back to login screen.I tried logging in with both normal and admin type users.But admin type user too encounters the same problem.

Can anybody help me pointing out what might have happened and how can I resolve it.I have partitioned my 500GB into 5 partitions and there is sufficient data on each partition.

I assume fresh installation would fix it and the data on logical partitions would be intact but doing this re-installation would require me to install the updates again 
and do all the settings I did till now again.

If there is any option to avoid this re-installation and resolve the problem, please let me know.Also is there any possibility of Live Ubuntu running directly from 
CD helping in getting rid of the problem?

Thanks,
Jignesh

---

### Post by raja.genupula on 2011-07-15
hey man ! 
first feed with this .i will try to send the remaining data later.  first login in shell and then move to GUI with (ctrl+alt+f7 i think ).after this goto System Settings -login window chooser .make a look at that window , for any  mistake .

---

### Post by j.gohel on 2011-07-15
Hey Raja, 
Thanks for you reply.

> first login in shell and then move to GUI with (ctrl+alt+f7 i think  ).after this goto System Settings -login window chooser .make a look at  that window , for any  mistake.I am newbie to Linux so can you please provide detailed steps.

How to login to shell? When system is started and login screen appears is there any option on login screen to do this? As I said I am unable to login to the system.
Entering the credentials and pressing OK flashes out a screen and within a second returns me back to the login screen.

Thanks,
Jignesh

---

### Post by raja.genupula on 2011-07-15
when booting press tab then write text at last
after login press ctrl+alt+f7

---

### Post by j.gohel on 2011-07-15
> when booting press tab then write text at last
after login press ctrl+alt+f7

Hey Raja, Sorry but I am unable to do what you have mentioned.
When booting I constantly pressed "TAB" key but nothing came up to enter "text".
Also I tried keeping pressing the "TAB" key and writing "text".This may look silly.But I have no option to try out.

Doing above steps does nothing but to take me to the Login Screen showing the users created by me on my system.

Also I tried selecting each of the follwing options 
"Recovery Console", 
"Ubuntu Classic", 
"Ubuntu Classic(No effect)", 
"Ubuntu(Safe Mode)"

 from taskbar dropdown at the bottom of the screen which appears when selecting a user for entering his/her password.

But no success.

Thanks,
Jignesh

---

### Post by j.gohel on 2011-07-19
Hi All,

I have got this resolved.Thanks to Raja for his inputs on directing me to login to shell when system is starting up.I followed below mentioned steps to get my problem resolved:


1) After startup, Login Screen appears
2) Press CTL+ATL+F1**

3) Shell appears
4) Login with credentials
5) Press CTL+ATL+F7**
6) There I found a message on console:
        stopping automatic crash report generation [fail]***

7) Tried the last solution by Nuc72 in thread at link [http://ubuntuforums.org/showthread.php?t=1745793&page=2](http://ubuntuforums.org/showthread.php?t=1745793&page=2)

Other Helpful Links I referenced:

**
a) [http://www.computing.net/answers/linux/linux-in-plain-text-mode/14938.html](http://www.computing.net/answers/linux/linux-in-plain-text-mode/14938.html)
b) [http://ubuntuforums.org/showthread.php?p=11050207](http://ubuntuforums.org/showthread.php?p=11050207)

***
[http://ubuntuforums.org/showthread.php?t=1745793&page=2](http://ubuntuforums.org/showthread.php?t=1745793&page=2)


Hope this helps somebody else in case anybody encounters the problem I faced.

Thanks,
Jignesh

---

