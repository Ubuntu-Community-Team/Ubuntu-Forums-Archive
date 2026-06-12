---
title: "Ubuntu 10.4 Beta 1 won't start anymore on my Thinkpad T400 and with cryptdisks"
date: 2010-03-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by anidel on 2010-03-22
Hi,
 
I have an issue with Ubuntu 10.4 beta 1 (updated yesterday from 8.04).
The update had an issue with flashplugin-nonfree but I solved that. Just reporting.
 
The update went fine, I was able to boot correctly.
It disabled fglrx and was using ATI open source drivers fine and even working with two monitors.
 
Then I had the idea to try fglrx so I went on and installed it (apt-get install fglrx).
It downloaded, installed, compiled, updated initram and so on...
I didn't reboot.
I did an apt-get update -f install and an apt-get autoremove as it was saying I should do it.
Weird enough this removed Thunderbird for no particular reason and it also removed gdm.
So I reinstalled (apt-get install thunderbird and apt-get install gdm) them.
 
One think I noticed is that the boot was in plain text. Ubuntu 10.04 was written in ASCII and it asked me the cryptdisks password in that "splash" screen in text mode.
 
Of course I didn't like it. Thus, still without rebooting, I went and typed:
 
apt-get install usplash
 
and it removed GDM again. I thought it was fine as it should be an alternative to GDM.
 
After that I rebooted.
And now it won't start.
From the logs I see that cryptdisks is being killed with a SIGTERM and the boot process simply remain stuck there.
Tried to go to the recovery alternative in GRUB, and I see it detects few things than several warnings about udevd and SYSFS{}= that will be removed in the future and then last thing is the
 
cryptdisks-udev (/dec/sda2) main process killed by TERM signal
 
and 
 
cryptdisks-enable mail process killed by TERM signal
 
(both errors refer to the same process ID (pid) being killed)
 
The kernel it's trying to use is 2.6.32-16-generic
 
The previous one available in GRUB is 2.6.24-27-generic and if I try that one (recovery) is errors about not being able to find
 
/dev/disk/by-uuid/<uui> and drops me into a shell (BusyBox) .
 
I have several years of expertise in Linux, but not in Ubuntu and it's tools.
Any ideas of what I can do to fix this and get to the previous working kernel?
 
Thanks!!
Aniello

---

### Post by anidel on 2010-03-22
Up, no ideas ? :/

---

### Post by anidel on 2010-03-22
Actually I think plymouth crashed earlier.. issue is I can't boot from  a USB or a CD Rom, so I have no idea how the heck I can fix this :(

---

### Post by Mark Phelps on 2010-03-23
Yeah -- one idea ...

How about posting this to the correct subforum?

Questions and issues with 10.04, since it is a Beta, need to be posted to the Development & Programming, Lucid Lynx Testing subforum.

Folks there are a lot better equipped to answer your beta questions.

---

### Post by anidel on 2010-03-23
True, I simply didn't image Ubuntu Beta testing would go into Development & Programming as it looked like it was only for dev and not for actual Beta testing as well.

thanks.

However, I will close this thread as in the end I simply re-installed it from scratch :(

Aniello

---

