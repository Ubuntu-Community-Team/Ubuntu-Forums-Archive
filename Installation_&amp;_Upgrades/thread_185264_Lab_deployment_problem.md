---
title: "Lab deployment problem"
date: 2006-05-31
forum: Installation &amp; Upgrades
---

### Post by misterv on 2006-05-31
I have used breezy badger in my compter lab and have succesfully cloned machines across network using rsync command

/usr/bin/rsync --exclude='/etc/hostname' --exclude='/etc/X11/xorg.conf' --exclude='/etc/network/interfaces' --delete -zvrpogDtSlH -e 'ssh -p 443' 142.30.90.54:/mnt/backup/images/kubuntunew/ /mnt/hda1/

I installed dapper on computer (looks great) and tried cloning using  same method.  The network card fails (eth0 no such device) when I try to start network, doesn't matter if I  use dhcp or static as device isn't found.  To check, I pulled hard drive out and put in new machine and got same error, so problem is not with rsync command.  Is this to do with each card having unique MAC address?   Is there some config file somewhere that needs to be unique in each computer?  I'm perplexed and a little frustrated.  I would like to upgrade my lab to dapper in June for next year.

NIC info:
eth0: SiS 900 PCI Fast Ethernet (onboard).

I'm totally stuck and would appreciate any ideas.  Blessings.  Tom

---

### Post by ssam on 2006-05-31
why excude /etc/network/interfaces ? are you making a unique one for each machine?

/etc/iftab
maybe causing trouble.

---

### Post by misterv on 2006-05-31
/etc/iftab was the problem, thanks!  If I delete it, computer boots fine. Is there any problem in not having one?  Can I recreate it w/ proper MAC address rather than manually editing it?

Thanks again, I was pulling my hair out!

---

### Post by ssam on 2006-05-31
its there so that your network cards get the same ethX each time. useful for laptop where a pcmcia wireless card can steel eth0 from the built in ethernet if its plugged in at boot time.

for desktops with static network hardware you dont need it

---

