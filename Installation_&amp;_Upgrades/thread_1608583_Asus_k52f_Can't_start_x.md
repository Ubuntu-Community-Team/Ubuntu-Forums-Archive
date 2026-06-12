---
title: "Asus k52f Can't start x"
date: 2010-10-29
forum: Installation &amp; Upgrades
---

### Post by Kevinc1 on 2010-10-29
I recently got an asus k52f and am having a nightmare of a time trying to get maverick on it. x will not start and i can't find much out about it as the laptop is fairly new. I do (temporarily at least) get the login prompt and i have installed all of the updates/upgrades to maverick via sudo apt-get update && sudo apt-get upgrade but no luck. The laptop has the Intel HM55 Express chipset with intel gma hd graphics, p6100 cpu, 3gb ddr3.. not sure what all details are needed but I hope someone can help me, as I am pretty bummed about not being able to use my new laptop lol.

Thanks for any and all help.

---

### Post by Kevinc1 on 2010-10-29
Ok may have hope if someone can help me install kernel 2.6.36 mainline from the limited interface that i get instead of x. I can still login and use terminal commands.. can't seem to find a guide for installing the new kernel from there. thanks again for the help.

---

### Post by jbarkawi on 2010-11-21
> **Kevinc1 said:**
> I recently got an asus k52f and am having a nightmare of a time trying to get maverick on it. x will not start and i can't find much out about it as the laptop is fairly new. I do (temporarily at least) get the login prompt and i have installed all of the updates/upgrades to maverick via sudo apt-get update && sudo apt-get upgrade but no luck. The laptop has the Intel HM55 Express chipset with intel gma hd graphics, p6100 cpu, 3gb ddr3.. not sure what all details are needed but I hope someone can help me, as I am pretty bummed about not being able to use my new laptop lol.

Thanks for any and all help.

I had a lot of troube with this, and after some searching and trial and error I found a solution to starting X. I have an Asus K52F with the 32-bit Maverick distro.

Basically, you need to blacklist an intel driver. Boot normally and into a terminal. Type "sudo vi /etc/modprobe.d/blacklist.conf"
This opens the vim text editor.

You can read the comments in the file to get a better idea of what blacklisting means. 

Next, press 'i' to go into insert mode. On the first free line (one that does not start with #), type 'blacklist intel_ips' (no quotes).

Next, press the escape key to exit insert mode. Then press the character sequence :wq! and press enter. This will save the file and exit back to the terminal. Type reboot, and you should be good to go.

Hope this helps.

Joe

---

### Post by brianterrel on 2011-04-27
> **jbarkawi said:**
> I had a lot of troube with this, and after some searching and trial and error I found a solution to starting X. I have an Asus K52F with the 32-bit Maverick distro.

Basically, you need to blacklist an intel driver. Boot normally and into a terminal. Type "sudo vi /etc/modprobe.d/blacklist.conf"
This opens the vim text editor.

You can read the comments in the file to get a better idea of what blacklisting means. 

Next, press 'i' to go into insert mode. On the first free line (one that does not start with #), type 'blacklist intel_ips' (no quotes).

Next, press the escape key to exit insert mode. Then press the character sequence :wq! and press enter. This will save the file and exit back to the terminal. Type reboot, and you should be good to go.

Hope this helps.

Joe

I was having the same problem with a K52F I was configuring and blacklisting the driver solved the problem for me.  

I actually was able to get into X by booting into recovery and starting in failsafeX, so I used gedit to blacklist X, which might be a bit easier for a noob (such as myself) than using vim.

Cheers

---

