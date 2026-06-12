---
title: "Ubuntu 16.04 lts hangs on shut down."
date: 2016-06-27
forum: Installation &amp; Upgrades
---

### Post by richard51 on 2016-06-27
After installing Ubuntu 16.04 lts on two different PC's. I have found that they both hang on shut down!

I can restart and sleep both PC's fine, but selecting shut down hangs on the Ubuntu logo (shutting down screen ) after a few seconds. Viewing the shut down via a terminal reports the following:

[B]systemd-shutdown[1]: Failed to finalize DM devices, ignoring.
reboot: Power down. [/B](Hangs here).

Restarting the PC's also say **systemd-shutdown[1]: Failed to finalize DM devices, ignoring **but, it continues and restarts.
***Edit:*** I have just noticed that when waking from sleep, **passwords do not work**! Maybe a separate issue, but needs to be resolved.

 I have noticed a few people with the same issue with Ubuntu 16.04 on google, but no fix! Having to press and hold the off button can't be good for the drives.

Any advice would be appreciated, thanks :D

---

### Post by kansasnoob on 2016-06-27
If you disable quiet splash you'll be able to see what process is hanging. For me it was cups and the last answer here helped:

[http://askubuntu.com/questions/760952/slow-shutdown-on-ubuntu-16-04-lts-stopping-thermal-daemon-running-fit-make-remo](http://askubuntu.com/questions/760952/slow-shutdown-on-ubuntu-16-04-lts-stopping-thermal-daemon-running-fit-make-remo)

AFAIK this is the appropriate bug report:

[https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1457400](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1457400)

But, to be perfectly honest, I just quit using 16.04 and plan on sticking with Trusty (installed with 14.04.1 media to avoid HWE EOL) because Xenial is just too buggy. I'll probably wait until 18.04 is released and then decide whether to go straight from 14.04 to 18.04 or see if 16.04 is stable yet.

---

### Post by frank18 on 2016-06-27
> **kansasnoob said:**
> If you disable quiet splash you'll be able to see what process is hanging. For me it was cups and the last answer here helped:

[http://askubuntu.com/questions/760952/slow-shutdown-on-ubuntu-16-04-lts-stopping-thermal-daemon-running-fit-make-remo](http://askubuntu.com/questions/760952/slow-shutdown-on-ubuntu-16-04-lts-stopping-thermal-daemon-running-fit-make-remo)

AFAIK this is the appropriate bug report:

[https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1457400](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1457400)

But, to be perfectly honest, I just quit using 16.04 and plan on sticking with Trusty (installed with 14.04.1 media to avoid HWE EOL) because Xenial is just too buggy. I'll probably wait until 18.04 is released and then decide whether to go straight from 14.04 to 18.04 or see if 16.04 is stable yet.

I agree;everybody should keep out of Ubuntu 1604,it's shame that Ubuntu  puts out some thing so screwed up as 16.04,i never had 1/3 of the issues when they were  first released with either 1204/14.04 as i had with with 16.04 so i think Ubuntu 16.04 is a fop.

---

### Post by richard51 on 2016-06-27
> **kansasnoob said:**
> If you disable quiet splash you'll be able to see what process is hanging. For me it was cups and the last answer here helped:

[http://askubuntu.com/questions/760952/slow-shutdown-on-ubuntu-16-04-lts-stopping-thermal-daemon-running-fit-make-remo](http://askubuntu.com/questions/760952/slow-shutdown-on-ubuntu-16-04-lts-stopping-thermal-daemon-running-fit-make-remo)

AFAIK this is the appropriate bug report:

[https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1457400](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1457400)

But, to be perfectly honest, I just quit using 16.04 and plan on sticking with Trusty (installed with 14.04.1 media to avoid HWE EOL) because Xenial is just too buggy. I'll probably wait until 18.04 is released and then decide whether to go straight from 14.04 to 18.04 or see if 16.04 is stable yet.

I disabled quiet splash, but everything is [ OK ]... It just hangs at **reboot: Power down**.

I have never had a problem with any version of Ubuntu (it just works)... But 16.04, an LTS version is garbage. I have wasted 3 days on it already, and don't really want to go back to 14.04 unless I have to.
[I]
Edit: I did find a lot of others unrelated bugs in 16.04 and have decided to revert back to 14.04. I had problems with the installer, getting LUKS and LVM to work was a nightmare, and there was a problem with CUPS, but unrelated to my shut down problem. Garbage![/I]

---

### Post by frank18 on 2016-06-28
> **richard51 said:**
> I disabled quiet splash, but everything is [ OK ]... It just hangs at **reboot: Power down**.

I have never had a problem with any version of Ubuntu (it just works)... But 16.04, an LTS version is garbage. I have wasted 3 days on it already, and don't really want to go back to 14.04 unless I have to.
[I]
Edit: I did find a lot of others unrelated bugs in 16.04 and have decided to revert back to 14.04. I had problems with the installer, getting LUKS and LVM to work was a nightmare, and there was a problem with CUPS, but unrelated to my shut down problem. Garbage![/I]

Well you are wrong not to go back to 14.04.
you should have installed 16.04 on an extra HDD like i did,i've just have swapped HDD and i was back on 14.04,i still have 16.04 but i will try it when i have assurance that it runs 100% right ,or at least same as 14.04.


just a thought ,did you change in Bios settings from DVD drive to HDD Drive? on some old PC it wont change auto,you have to change the Drive.

---

### Post by richard51 on 2016-06-29
> **frank18 said:**
> Well you are wrong not to go back to 14.04.
you should have installed 16.04 on an extra HDD like i did,i've just have swapped HDD and i was back on 14.04,i still have 16.04 but i will try it when i have assurance that it runs 100% right ,or at least same as 14.04.


just a thought ,did you change in Bios settings from DVD drive to HDD Drive? on some old PC it wont change auto,you have to change the Drive.

I had back up images of Ubuntu 14.04 for both machines, so it wasn't a problem to revert back. I did fix (hack) many of Ubuntu 16.04's many problems, but It's not stable enough (to buggy) to replace **14.04.1**.

---

### Post by noreen on 2016-11-03
Upgrading the kernel to 4.7 RC3 worked for me.

---

### Post by wogga on 2016-12-07
> **noreen said:**
> Upgrading the kernel to 4.7 RC3 worked for me.

I updated to 4.7 rc3 the other day and am having the same hang up issues. Have you experienced any further issues since your kernel update?? Were there any other measures you took on the issue?

My situation is a new install on a fresh machine. No updates [aka horror stories] from a 14.04-16.04 swap. Just a straight fresh install.

---

### Post by KenFF on 2017-02-22
I had this problem on 14.04 also, but it's intermittent on both . Worst part for me is that it seems to CORRUPT Ubuntu! After the first time it does it, I start to get "System Error"s on startup. 

My latest problem is that Software manager won't start!! Seems I HAVE to go back to 14.04 - it's better, but still not good. I run on 3 machines - 2 dual boot with Win XP - both 32bit and one dedicated 64 bit - all Intel 2 to 7 years old.

Whenever I report this BUG it get marked a DUPLICATE & SOLVED -  

REALLY wish I could stop using WINDOWS

---

### Post by QIII on 2017-02-22
Use default fonts and colors.

You have been told before that UF is not a bug reporting venue, so stop acting like it is and stop demanding that we fix something that only Canonical can.

If you create duplicate posts (like this one, but I'll leave it here so you get the message), they will continue to be removed as duplicates.

---

