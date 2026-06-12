---
title: "Xubuntu Hardware abstraction layer pause"
date: 2007-07-03
forum: Installation &amp; Upgrades
---

### Post by mjhs on 2007-07-03
Hi,

I recently installed Ubuntu 5.10 on my PC, but want to upgrade to the newest version of Xubuntu (not possible through the normal means because 5.10 is no longer supported). I have this on CD and have tried to install it, but the installation stops at 'Starting hardware abstraction layer hald'. I've tried a number of times, leaving it between half and three-quarters of an hour each time before restarting, but to no avail. 
As a linux newbie, I have no idea what this means or how to get beyond it - is anyone able to point me in the right direction? You can probably safely treat me as a complete idiot, and keep it simple!
Just ask if you need more details.

Thanks!

---

### Post by mjhs on 2007-07-04
Nobody any idea at all what this means? Even just a slight clue would help, I'm sure.

Thanks!

---

### Post by Mike_RM on 2007-07-07
I've got a slightly different but related problem. I installed Ubuntu Edgy from CD a couple of weeks ago. Then upgraded to Fiesty Dawn. The upgrade installed OK, but now during bootup it hangs for about 4 minutes on the line 'Starting Hardware Abstraction layer hald'. It finally continues and the installation works normally, but it's a real pain taking so long to boot. This problem didn't occur with the Edgy version.

In the Restricted Drivers Manager I found an Atheros Hardware Access Layer (HAL) entry and tried disabling it but it made no difference. Anyone got a suggestion? Might help mjhs as well. Thanks in advance.

---

### Post by AstarothCY on 2007-09-16
bump, any news on this? i have the same problem

---

### Post by Pumalite on 2007-09-16
All of you guys should post your specs at least.

---

### Post by AstarothCY on 2007-09-16
Fujitsu Siemens Scenic P320 ([spec sheet](http://www.fujitsu-siemens.co.uk/rl/servicesupport/techsupport/professionalpc/Scenic/ScenicP/scenicP320.htm) - i have the D1961)
+ the following:
SB Audigy
ASUS ATI Radeon 9550 AGP 128MB
Logitech Cordless Desktop LX500
Western Digital Caviar RE2 500GB
NEC DVDRW 16x

Hope that helps.

BTW just to provide some more information, I have tried the following kernels:
17.1-10
17.1-11
20-15
20-16
22-11

After upgrading to Feisty, I cannot boot with any kernel except the 17.1 kernels which are left over from Edgy. All the newer ones have exactly the same problem, they boot up to the "Starting hardware abstraction layer hald" stage, get stuck there for 2-3 minutes, then print out a couple more lines and go to an unresponsive blank screen. BTW, if I try to shut down while it is stuck at the hald bit, i get some shutdown messages and there is a [fail] at the avahi-daemon line.

---

### Post by Pumalite on 2007-09-16
How much actual memory do you have?

---

### Post by AstarothCY on 2007-09-16
512MB + 1GB = 1.5GB

I should also mention that I have recently been (unsuccessfully) trying to install a wireless USB adapter (ZyXEL G-260) using ndiswrapper, just in case it's relevant. Ndiswrapper is uninstalled now.

Also, I am on Ubuntu, not Xubuntu, but I don't think it matters since we seem to have the same problem.

---

### Post by Pumalite on 2007-09-16
I think you better start checking your hardware: cables, connections, memtest, etc.

---

### Post by AstarothCY on 2007-09-16
> **Pumalite said:**
> I think you better start checking your hardware: cables, connections, memtest, etc.

I don't see how that would be of any use, since I can boot into the old kernels just fine, as well as winxp. I did check anyway, i removed everything and plugged it back in.

---

### Post by Pumalite on 2007-09-16
[http://ubuntuforums.org/showthread.php?t=494775](http://ubuntuforums.org/showthread.php?t=494775)

[http://ubuntuforums.org/archive/index.php/t-494775.html](http://ubuntuforums.org/archive/index.php/t-494775.html)

---

### Post by AstarothCY on 2007-09-16
Uh yeah, you might notice that I actually bumped that thread earlier since it's unsolved :P

---

### Post by Pumalite on 2007-09-16
Sorry, just trying to help and a little sleepy here.

---

### Post by AstarothCY on 2007-09-16
No worries, thanks for trying. At least SOMEONE is. I have 2 threads going that have pretty much been ignored even though other people are having the same problems, I think everyone just gives up and reinstalls Ubuntu, and that to me is unacceptable, you can't really have situations like this and claim that Ubuntu is more stable than WinXP. Don't mean to start an argument or anything but I've been a big fan for many months and Ubuntu has just dropped the ball on this one.

---

### Post by Pumalite on 2007-09-16
I think that Ubuntu is definitely more difficult to install than XP, but at the end is more rewarding.

---

### Post by AstarothCY on 2007-09-16
I don't really see anything rewarding about setting everything up perfectly and having an update completely break your system and you having to set up everything from scratch, something that could take weeks. What's worse is there is no way to even downgrade, and the old Edgy kernel I am currently running is crippled, it's missing most of its tools, I can't configure or make packages manually.

---

### Post by Pumalite on 2007-09-16
I'm running Feisty 7.04, Gutsy Tribe 4, Gutsy Tribe 5, LinuxMint, Zenwalk and others in 5 different computers and have had little problems; including updates and upgrades.

---

### Post by AstarothCY on 2007-09-17
I don't know how relevant this is but a google search came up with [this bug report.](https://launchpad.net/hal/+bug/92647)

I will try upgrading HAL to the Gutsy version when I get home from work today and will report back.

EDIT:

[This one](https://answers.launchpad.net/ubuntu/+question/8086) is even less relevant but I will try removing my ATI and using the onboard video.
Well hey, at least I have things to try now :P

---

### Post by AstarothCY on 2007-09-17
SOLVED by installing the gutsy HAL packages as described [here](https://launchpad.net/hal/+bug/92647). I also had to remove the gutsy kernel and reinstall the latest feisty kernel (20-16) and it boots fine. HOWEVER I still have other problems, I will make a new thread though since the problem has changed a lot.

---

### Post by Pumalite on 2007-09-17
Well, glad you got it working. You sound happier too.

---

### Post by AstarothCY on 2007-09-17
I suppose. Sorry about the ranting earlier but I'm sure you can understand my frustration. Not that it works ok now but at least it boots.

---

