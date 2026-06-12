---
title: "Wine not working after recent updates."
date: 2015-07-28
forum: Installation &amp; Upgrades
---

### Post by pfakaprolly on 2015-07-28
Hi. 

After recent updates on my laptop recently wine is unable to launch. Even config and so on is completely unable to launch after reinstall.

I can launch the linux version of Steam tho, but I have some errors there aswell. Where the games are not avalible anymore and the program tells me that I got no space on HD. That is something I suspect is related. 

Thanks for any attempts for aiding me.

---

### Post by SwedO on 2015-07-28
Same problem here.

---

### Post by yellerKat on 2015-07-28
Me too, after a kernel update from 3.13.0-58 to -59.

Everything works fine if I hold down shift on boot and load the -58 kernel.

---

### Post by pfakaprolly on 2015-07-28
Thank you. 

The update contained an error then.

---

### Post by oldfred on 2015-07-28
Please add to bug report, they tend to only work on ones with many users complaining.
[https://bugs.launchpad.net/ubuntu/+source/wine1.6/+bug/1479040](https://bugs.launchpad.net/ubuntu/+source/wine1.6/+bug/1479040)

This worked for me, but still gave error as it started my Picasa.
I opened terminal and started wine server.

wineserver -p

Then clicked on my Picasa Icon to load it. Error flashed but Picasa loaded.

---

### Post by cmcanulty on 2015-07-28
same here even after purging and reinstalling everything, your command got it to open but now my library software won't install it comes up with an error that never happened before I am totally ************* as I really need that
and now ultra vnc fails too!

---

### Post by riaan3 on 2015-07-29
> **yellerKat said:**
> Me too, after a kernel update from 3.13.0-58 to -59.

Everything works fine if I hold down shift on boot and load the -58 kernel.
Thanks for this - was a lifesaver last night !

I hope they sort this out - it is bloody irritating to say the least.

---

### Post by RobotOfBarr on 2015-07-29
I updated Ubuntu 14.04 LTS via the Software Updater at about 2330 UTC yesterday 2015-07-28 and when I rebooted (as required), WINE immediately stopped working. It worked properly up to the update and reboot.

From the Terminal, Wine returns nothing at all:

r@r-X550CL:~$ env WINEPREFIX="/home/r/.wine" wine C:\\Program\ Files\ \(x86\)\\FireTrust\\MailWasher\ Free\\MailWasher.exe 
r@r-X550CL:~$

Nothing---------^

My suspicion is the kernel update has broken WINE.

---

### Post by howefield on 2015-07-29
> **RobotOfBarr said:**
> My suspicion is the kernel update has broken WINE.

Have you tried booting via the previous working kernel?

---

### Post by cmcanulty on 2015-07-29
kernel fix opened for me after I also ran
```
wineserver -p
``` I saw on a forum last night forget where, big hassle reinstalling everything in wine
now I am afraid to run updates

---

### Post by RobotOfBarr on 2015-07-29
I didn't know I could (!), but I have, and yes, that works as before. So is my suspicion confirmed?

---

### Post by mark235 on 2015-07-29
> **yellerKat said:**
> Me too, after a kernel update from 3.13.0-58 to -59.

Everything works fine if I hold down shift on boot and load the -58 kernel.

I specially renewed my Ubuntu forum account to write this message... :-)
(the more report the better)

It took me a long time before I figured out why my Netlinx studio would not run, when it
worked perfectly! yesterday, even reinstalling to Wine 1.7.44 did not help...

The above message did help, rolling back to -58 and everything is working fine, 
so there is a problem with Kernel 3.13.0-59 and Wine.
I can remember I that there was a notice in Dmesg about a segmentation fault.

Grtzz  Mark

---

### Post by howefield on 2015-07-29
> **RobotOfBarr said:**
> I didn't know I could (!), but I have, and yes, that works as before. So is my suspicion confirmed?

Well, that is good in as much as you at least have a working system, which will buy you some time whilst you get a solution for the newer kernel, not sure if what cmcanulty is offering above is a fix.

In case you hadn't found it, here is a thread with the same issue..

[http://ubuntuforums.org/showthread.php?t=2288589](http://ubuntuforums.org/showthread.php?t=2288589)

---

### Post by RobotOfBarr on 2015-07-29
Same here - rolled back to -58 and all works as before. I didn't need "wineserver -p".
 
(Sorry Moderators: I didn't find this thread, please delete the other if you wish - "Update 2015-07-28 has broken WINE")

---

### Post by landennick on 2015-07-29
> **howefield said:**
> Have you tried booting via the previous working kernel?

I was having this problem and I rolled back the Kernel on reboot :-

> To choose which kernel you want to use, at boot, hold down < Shift>  to see the Grub menu, scroll down with the arrow keys to "Advanced  options for Ubuntu", and you will see a menu where you can select a  kernel. You want one of the ones that *doesn't* say "(Recovery mode)".

This worked for me.

---

### Post by oldfred on 2015-07-29
Threads merged.

---

### Post by SwedO on 2015-07-29
New kernel! Wine is working again! :p

---

### Post by RobotOfBarr on 2015-07-29
Latest update ( -61) seems to have solved the problem for me too. Thanks to all who helped.

---

