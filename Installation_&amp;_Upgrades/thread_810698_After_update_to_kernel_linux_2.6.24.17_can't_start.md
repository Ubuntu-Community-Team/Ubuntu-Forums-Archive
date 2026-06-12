---
title: "After update to kernel linux 2.6.24.17 can't start administrative applications and..."
date: 2008-05-28
forum: Installation &amp; Upgrades
---

### Post by Paulo M. on 2008-05-28
Hello!
Please, I need some help... since I've made today's updates - one of them kernel linux 2.6.24.17 - in my grub dual boot appears (beside Windows XP Pro, of course) two different ubuntu OS - the old 2.6.24.16 and the new one 2.6.24.17 (and the recovery modes of each one, too).
But the worst of this is that in the new kernel I'm not able to start any administrative process (synaptic, update manager or anyone else...) and lost all my configuration settings as nvidia settings (witch driver I can't enable because that issue concerning administrative processes), compiz, and so on...
When I try to start any of those applications, appears in the lower panel an indication of a window "starting administrative..." for a while and then it's gone again and nothing happens...
Can anyone tell me what is wrong with this?

Thanks in advance!

---

### Post by dstew on 2008-05-28
Does everything work OK with your older kernel?

---

### Post by Paulo M. on 2008-05-28
Thanks...
Yes it did work, but not anymore....
Now, in grub the old kernel don't show anymore..... and in this new one, I still can't use synaptic or other administrative application!
I really don't now what to do....

Thanks again (and help me please... I did decided to move towards ubuntu because was tired of M$ bugs... :()

All my best!

---

### Post by Paulo M. on 2008-05-28
Hello again.
I got some news, but don't know if are they helpless...
I could run synaptic and update manager in terminal, but there were two strange messages in terminal:
"sudo: unable to resolve host Speeduntu" (Speeduntu is my pc name) and "current dist not found in meta-release file".
Besides, when I try to start synaptic or update manager in System>Administration menu, in system monitor starts a sleeping gksu process...
As I told before, don't know if this is helpful... but I really need some help!

Thanks in advance one more time

---

### Post by Paulo M. on 2008-05-28
I really don't know how, but my hosts file was changed...
Editing it with the correct pc name, it became fine...
I think all my problems are solved for now.
Thanks again!

---

### Post by ScottyP on 2008-05-28
Paulo-

Can you explain what you did to fix the problem? It sounds like I have the same problem and I'm very new to Ubuntu and Linux.

Thanks!

---

### Post by dstew on 2008-05-28
Boot into Recovery Mode, and choose Root Command Line. On the command line, enter this command to edit your /etc/hosts file:```
nano /etc/hosts
```Look for the line near the top that has your system name with an extension (like .HOME). Put a # at the front to "comment it out". Then, hit ctrl-X (nano's menu at the bottom lists it as ^X) to exit, and type Y to save the file. Then, reboot. You can enter reboot on the command line to reboot.

---

### Post by ScottyP on 2008-05-28
Found the fix off of this thread: [http://ubuntuforums.org/showthread.php?t=723361]("http://ubuntuforums.org/showthread.php?t=723361")

Followed the directions given by PmDematagoda

dstew - I think it's basically the same direction you were going. Thanks!

---

### Post by Xirowei on 2008-05-28
I also facing same problem after a fresh install of Ubuntu follow by an update of total 101 items. Here is the solution that works for me.

run Terminal type in command: **sudo gedit /etc/hosts**
the output of the Terminal should look like this:
127.0.0.1 localhost
127.0.1.1 **xirowei.WORKGROUP**

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

[I]xirowei = username
WORRKGROUP = domain name[/I]

Change to below output by delete away ".WORKGROUP":
127.0.0.1 localhost
127.0.1.1 **xirowei**

Save the file. Now try run any administrative applications, the window that prompt you to enter password will appear now.

---

### Post by Paulo M. on 2008-05-28
Yes. that's it...
editing /etc/hosts just like told up here, solved my problem.
Thank you all, and sorry for not getting in here in time to help you too!

All my best!

---

