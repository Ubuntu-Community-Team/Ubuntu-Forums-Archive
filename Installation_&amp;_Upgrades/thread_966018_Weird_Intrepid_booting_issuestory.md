---
title: "Weird Intrepid booting issue/story"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by bloomtom on 2008-11-01
Hi everyone. I've got an odd issue related to grub and Intrepid. I've been running the Intrepid release candidate for a few days now with no complaints, however last time I tried to boot Grub gave me an error 15 file not found. I assumed the kernel info in grub was wrong and so booted into parted magic and checked the /boot folder. I was right grub was trying to boot into a fictional file named vmlinuz-2.6-24-20-generic when the only file there was vmlinuz-2.6-27-7-generic. I rebooted, plugged the correct info into grub and carefully tapped b. The normal text, most of which I don't understand, started scrolling across the screen then abruptly stopped. I stared at it like an idiot for about a minute before realizing whatever the system is waiting for isn't gonna show up to the party. I was like oh no kernel panic I better raise elephants as to not anger the Linux gods. I pressed ctrl then alt and was moving my other hand to sys rq when I noticed more text was scrolling across the screen and my hdd churning away, but as soon as I released ctrl-alt it stopped again. hmm... press ctrl, nothing. press alt, stuff moves along. 

What the hell? I had to hold ctrl until everything was mounted and going automatic like (this took 10 maybe 15 seconds). There were NO updates since the reboot before this one, I have no idea how the kernel number changed and even less of an idea of why grub wasn't informed of this change. Also I don't know if I'm still running the release candidate or not, I haven't had a good dose of updates since 10/28.

Could anyone tell me what just happened? I checked the sys logs and they tell me it was a flawless boot.

---

### Post by doas777 on 2008-11-01
I'm getting the same thing on my HP dv9810us, with the hold ctrl thing, except I haven't had any grub errors and it happens on every boot. didn't have any problems like this in hardy

please let me know if you find an answer, this is most annoying. 

have fun,
Franklin

---

### Post by keltose on 2008-11-01
Same problem here....but sometimes the system will crash for no reason.  then i do a restart and get error 15;  this was from the RC.

---

### Post by bloomtom on 2008-11-01
It seems like it happens every time I boot now. If you have the problem where grub doesn't work it is easily fixed by editing grub's menu.lst

To do this run: 

gksu gedit /boot/grub/menu.lst 

in the terminal. 

Then edit the kernel number in the Ubuntu section. Look for something like this. (Mine are already edited). 

title		Ubuntu 8.04.1, kernel 2.6.27-7-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-7-generic 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet


title		Ubuntu 8.04.1, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-7-generic
initrd		/boot/initrd.img-2.6.27-7-generic

Edit the kernel line, the initrd line and the title line to match the vmlinuz and initrd.img files in /boot.

Still nothing on the hold alt thing except it seems to work if you hold down any key, alt works better because it doesn't spam your screen with unnecessary text.

---

### Post by bloomtom on 2008-11-03
Anyone? I'm still having the same problem...

---

### Post by keltose on 2008-11-04
I am,but I am thinking that it was my hard drive.  I was having some other issues.  I have a new one on its way and we'll see if that's the case.  If I keep having issues I will post them.

---

### Post by bloomtom on 2008-11-05
Well I'm not experiencing any problems once the OS gets going. It's annoying that I need to hold down a button until a little after "Reading files needed to boot", but it's tolerable. I guess I can live with it but it's not something I'd from a non-beta release. The only thing I can think of is that the update silently failed somehow. I really don't want to reinstall. <--I kinda typed my thoughts there.

---

