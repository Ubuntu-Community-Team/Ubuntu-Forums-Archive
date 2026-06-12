---
title: "Issue with Grub : does not aut-boot anymore"
date: 2007-02-24
forum: Installation &amp; Upgrades
---

### Post by mcglnx on 2007-02-24
Dear All,

  Issue with Grub : does not auto-boot anymore  

Since a certain amount of time, Grub locks itself while counting before boot. It stops at '2'.
I have to manually select the Kernel I want to boot.

On the /boot/grub/menu.lst I got timeout of 3. And everything seems ok.

Any idea?

Thanks in advance,
M.

---

### Post by rsambuca on 2007-02-24
Can you post your /boot/grub/menu.lst file?

---

### Post by mcglnx on 2007-02-25
here it is...

---

### Post by rsambuca on 2007-02-25
Try adding this line to your default kernel options and rebooting```
## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=cbddae00-c8f9-43a2-876b-f3a218776ea5 ro
[COLOR="Red"]# kopt_2_6=root=/dev/hda1 ro[/COLOR]
```
If that doesn't work, you might just try updating grub from the terminal.

---

### Post by mcglnx on 2007-03-03
> **rsambuca said:**
> 
[COLOR="Red"]# kopt_2_6=root=/dev/hda1 ro[/COLOR][/CODE]
If that doesn't work, you might just try updating grub from the terminal.

I tried it as well as using kopt=root=/dev/sda2 (this is my root '/' partition).
Does not help :(

---

### Post by rsambuca on 2007-03-03
Recently there was another thread about this where there was much speculation.  In the end the only way he could get it to autoboot was to set the timeout to 0.  Not a fix obviously, but nothing else worked.

Sorry I can't help you out here.

---

### Post by mcglnx on 2007-03-03
Thanks!
It's an idea for sure. But I'd like to keep the possibility to select the 'single' mode. just in case.

Strange however. May be I need to re-install Ubuntu from scratch?

---

### Post by rsambuca on 2007-03-03
I'm not sure re-installing would change anything.  Although I have absolutely no way of knowing, my feeling is that it is a hardware issue sending a signal to grub that a key has been pressed, even when one hasn't been.

---

### Post by mcglnx on 2007-03-03
Could be indeed: I've noticed a couple of time the 'numlock' led is green at boot time.
I'm using Dell inpsiron 6400. There is may be something to be change on the BIOS.
I'll check.

---

### Post by mcglnx on 2007-03-05
**UPDATE**:

I've kept your change. However, it is not related apparently.

It seems to be realted to a bug of Kernel + Hwclock + Dell's Bios.

After loosing the counter, I tried to change some settings on the Bios. I touched the time as well and got a strange message just after the bios startup and before the grub start:

time-of-day clock stopped.

Searching the Web and contacting the Dell support, I've done the following:
- Remove the battery cell for 5 minutes to reset the BIOS.
- Reboot. (worked!!!)
- set HWCLOCKPARS=--directisa in /etc/init.d/hwclock.sh


See: 
* [http://www.ubuntuforums.org/showthread.php?t=149565](http://www.ubuntuforums.org/showthread.php?t=149565)
* [https://launchpad.net/ubuntu/+bug/43745](https://launchpad.net/ubuntu/+bug/43745)

---

