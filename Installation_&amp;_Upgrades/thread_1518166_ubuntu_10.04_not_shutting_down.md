---
title: "ubuntu 10.04 not shutting down"
date: 2010-06-26
forum: Installation &amp; Upgrades
---

### Post by rejuvenate on 2010-06-26
i have installed ubuntu 10.04 in my system,when i try to shut it down or restart it is not working...the screen goes off but system remains on.
after surfing...i tried following:

1.edited the grub
> sudo gedit /etc/default/grub

change : GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

by : GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi=force"


2.disabled openoffice quick starter:

3.tried the command line shut down:

sudo halt
sudo init0
sudo poweroff..
for shutting down properly i need to log out then have to shut down..
the commands are working when i am logged in command line only


every time to check these solution i need to hard power off ....is there any way i can check the solution without actual power off..


my graphics card is 
ATI/AMD proprietary FGLRX graphics driver.

in one solution it is written that to disable driver then again reinstall them....is it neccessary...

---

### Post by rejuvenate on 2010-06-28
i think this is a serious  problem.....did i posted it in a wrong forum or what...i need help on this issue...this is effecting my laptop very badly...

---

### Post by cmatal on 2010-07-06
I have the same problem and tried what you have tried also

My motherboard is an ECS RC410L/800-M (V2.0)
with ATI Radeon Xpress 200 video

After changing the grub file to "quiet acpi=force"
I can see in text mode that the system halts and stays there

---

### Post by Neal121 on 2010-07-08
I am also having the same problem. But not yet done anything other than searching a solution.
When I shut down my machine automatically I am being redirected to login screen.

---

### Post by valiant32 on 2010-07-09
> **Neal121 said:**
> I am also having the same problem. But not yet done anything other than searching a solution.
When I shut down my machine automatically I am being redirected to login screen.

Same with laptop and desktop. Wonder if 10.04 is ready for prime time?

---

### Post by Devi1903 on 2010-07-09
Try
> sudo init 6
or
> sudo shutdown now

I am running 10.04 over about 10 different laptops and 30 PCs (about 5 different hardware configurations) and have not experienced this problem.

---

### Post by keiffee30 on 2010-07-17
I am also having the same problem too. But not yet done anything about it.
When I shut down my machine automatically I am being redirected to login screen.

I jump into a terminal and 

**sudo shutdown now**
or it i need a reboot
**sudo reboot now**

command and this dose what it said on the tin. i then have to hold on until the pc shuts down then i have to power off. This is a 1st for me as i have used 6.04 upwards to and never had this problem.

---

### Post by su-37 on 2010-07-30
Same problem here. Its annoying as this is a fresh install.

found this.
[http://ubuntuforums.org/showthread.php?t=1469595](http://ubuntuforums.org/showthread.php?t=1469595)

---

