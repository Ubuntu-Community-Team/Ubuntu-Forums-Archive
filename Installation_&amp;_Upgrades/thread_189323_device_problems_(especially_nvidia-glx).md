---
title: "device problems (especially nvidia-glx)"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by antcodd on 2006-06-05
Hi, I just upgraded to dapper from breezy using the upgrade distro button I noticed in the upgrade manager

X won't start complaining about not being able to find the nvidia kernal module.

sound was working(it seems to have fixed itself, dunno how that happened), and my ethernet cards have decided they are eth2 and eth3 instead of eth0 and eth1 (I also have bridge set up, maybe that is the problem, I can't remember how I did it though)

I have managed to get X to start with the nv driver.

I have tried reinstalling nvidia-glx, but to no avail. I was using the latest nvidia driver from the nvidia website at the time of upgrade, I think that may be the problem but I don't know how I can fix it.

I am about to try uninstalling the nvidia driver from the nvidia website, remembered I should try that as I was posting this, but I need to quit X and I don't feel like writing this out again.

Any help would be most appreciated! :-D
 
2x nvidia geforce 6800gt in SLI(I have disabled it in xorg.conf for now)
Asus a8n sli deluxe motherboard
1 nforce 4 inbuilt nic, 1 marvell 88e81001 gigabit lan
Realtek alc850 onboard sound

EDIT: uninstalling the nvidia driver from the nvidia website and installing nvidia-glx did not help, neither did installing the latest driver from nvidia again, same problem.

I also seem to be having problems with my ethernet cards, they seem to need activating and deactivating with the networking config program (doesnt work from command line) to work, it is getting really annoying

---

### Post by antcodd on 2006-06-16
Any ideas how to fix this?

Thanks,
Antcodd

---

