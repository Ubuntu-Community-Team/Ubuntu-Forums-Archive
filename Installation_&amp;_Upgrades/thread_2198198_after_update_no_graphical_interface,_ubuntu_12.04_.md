---
title: "after update no graphical interface, ubuntu 12.04 64bit desktop"
date: 2014-01-07
forum: Installation &amp; Upgrades
---

### Post by ziemowitzima on 2014-01-07
Hi 
After update and restart I did not have graphical interface anymore...
After some google search:
[http://askubuntu.com/questions/145195/nvidia-driver-problem-after-updating-to-12-04](http://askubuntu.com/questions/145195/nvidia-driver-problem-after-updating-to-12-04)
 I foud to type:
sudo apt-get purge nvidia*
sudo apt-get install nvidia-current-updates-dev

but after that situation gets even more strange:
I can see first graphical menu to choose user.
for my defoult user, I am mostly working on, after log in, I can see only black screen, and it comes back to
first graphical menu to choose user, again.

If I choose some other user it loads fine...

What shoud I do to fix it ?

Best
and Thanks
Ziemo

---

### Post by andyhelloween on 2014-01-10
Hi ziemowitzima,

I'm on the same boat as you. Upgraded one of my laptops yesterday, and now I can't see the desktop, just black screen after login. Startup takes longer than I'm used to. I tried with a previous kernel version and a popup came up saying "My system is running on low graphics". This definitely points to nvidia driver's issue.

Guest user can login fine, but Unity 3D is no longer available. My user just see a black screen with the mouse pointer floating around.

I'll see what I can find and update the thread. In the meantime, if someone has a solution, please share!

Cheers,
A.

---

### Post by mastablasta on 2014-01-10
have you tried removing nvidia driver completely, reinstalling noveou (or whaterevr the opensoruce drivers are called) and then rebooting, then (if you get into graphical interface) you can reinstall nvidia drivers.
for example: 
[http://askubuntu.com/questions/128113/how-do-you-remove-nvidias-proprietary-drivers](http://askubuntu.com/questions/128113/how-do-you-remove-nvidias-proprietary-drivers)

---

### Post by andyhelloween on 2014-01-10
Hi mastablasta,

I solved the problem just now by directly reinstalling the nvidia driver. Download latest driver from nvidia website (my version was 331.20), start in recovery mode, give execute permission and run it. It uninstalled the previous driver (the same version) and reinstalled it. No problema after that.

Thank you for your response.

Regards,
A.

---

