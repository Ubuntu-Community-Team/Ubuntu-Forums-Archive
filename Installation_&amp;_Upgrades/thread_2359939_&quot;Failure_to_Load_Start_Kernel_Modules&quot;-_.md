---
title: "&quot;Failure to Load Start Kernel Modules&quot;- Ubuntu 16.10 with Windows 10"
date: 2017-04-29
forum: Installation &amp; Upgrades
---

### Post by Caleb012 on 2017-04-29
I received the above message and now my Wi-Fi no longer works. I tried to run UKUU but have been unable to make any progress. I have Windows 10 along with Ubuntu 16.10 dual boot. I think I messed up somehow trying to update the Kernel.......Thanks very much!

---

### Post by Frogs Hair on 2017-04-29
Did you manually update the kernel from an external source or did it update through the update manager.

---

### Post by Caleb012 on 2017-04-29
I ran UKUU and picked a kernel. I re-ran UKUU and picked an older version when the version I chose did not solve problem. I know little about Ubuntu.......I hope to learn though......

---

### Post by Frogs Hair on 2017-04-29
Is this it below ? If so you can boot from system supplied kernel by selecting it in grub.

[http://www.omgubuntu.co.uk/2017/02/ukuu-easy-way-to-install-mainline-kernel-ubuntu](http://www.omgubuntu.co.uk/2017/02/ukuu-easy-way-to-install-mainline-kernel-ubuntu)

---

### Post by Caleb012 on 2017-04-29
Yes...that is it. How would I boot from grub with the system supplied one?
I just read the following on that page..........
"Upgrading to a mainline Linux kernel is generally *not* a good idea. If in doubt, don’t mess about."

I probably should not venture where I lack knowledge........

---

### Post by Frogs Hair on 2017-04-29
If it's not listed use advanced options.

---

### Post by Caleb012 on 2017-04-30
Thank you are your assistance!

When I boot, my options are "Ubuntu"....and Ubuntu with Advanced Options. Under Advance Options....I currently have 17 choices......there are different versions......such as-

4.8.0-22 Generic

4.8.0-22 (Upstart)

4.8.0-22 (Recovery Mode)

I am unsure which to pick.......

---

### Post by Caleb012 on 2017-04-30
I found the correct version (4.8.0-46) through a process of elimination. How do I get it to boot from that particular one? Also, how do I clean up all those other versions? 

I now boot cleanly, with no error messages stating "failure to load start kernel modules" plus my wi-fi is working again!

Hurrah!!!!!!!!

---

### Post by Frogs Hair on 2017-04-30
As the post stated you can use  [COLOR=#000000]UKUU to clean the main line versions. I use the snyaptic package manager to clean old kernel versions.   They may show up in the status section as autoremovable or Installed(local or obsolete) ```
sudo apt install synaptic
```[/COLOR] I've never used UKUU so you may want wait for input from someone who has or do more research on the application.

---

### Post by Caleb012 on 2017-04-30
Frogs Hair......Thank you very much for your knowledgeable assistance.......it is very much appreciated!

---

### Post by Frogs Hair on 2017-04-30
You're welcome !

---

