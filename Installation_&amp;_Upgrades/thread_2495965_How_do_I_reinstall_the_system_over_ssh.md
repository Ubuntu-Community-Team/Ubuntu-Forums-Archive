---
title: "How do I reinstall the system over ssh?"
date: 2024-03-09
forum: Installation &amp; Upgrades
---

### Post by isprins on 2024-03-09
My server has two ssd drives that I want to use as a mirrored boot.
It is reachable by ssh.
It's in a location that is somewhat cramped, so the most comfortable and convenient way to reinstall the system is to do that by ssh.
My issue is that I don't know how to do that, but I hope that someone here knows how to do it. 
It also has a zfs pool that I don't want to loose the data on.
So, how do I do this?

---

### Post by MAFoElffen on 2024-03-09
The problem is going to be the ssh connection and how to boot the install media remotely... 

I've done it remotely with Dell servers booting remotely through the iDRAC. Other servers through their BMC controller.

Other ways were through PXE booting and installing systems using a fog server.

Next was setting up autoinstalls via the LiveInstaller.

Next was with a helper at the remote location to put in the installer Live Media when needed... Booting from it > Use "Try" and having them install openssh and allowing root as a user... I would then connect to it to do the install, setting up a static IP, then after the install, and before the first reboot... mounting the newly installed via /target, then installing openssh-server and configuring it... Si I can connect to it after the install.

There are many other ways, including server configuration automation  and provisioning with Ansible and Terraform. Which is a rampup to get going and use effectively.

Missing is the scope. That will set boundaries on if the is a one-off, or if you have to replicate the process for many. There are trade offs in the work you need to do to get something working, and where it pays off for your environment. 

Many things are possible. The choices are many. Just because something is possible, doesn't mean it's the best choice for what you need to do.

---

### Post by isprins on 2024-03-10
I found this, but it's from 2018.
[https://gitlab.com/aasaam/ubuntu-overssh-reinstallation](https://gitlab.com/aasaam/ubuntu-overssh-reinstallation)

---

### Post by TheFu on 2024-03-10
> **isprins said:**
> I found this, but it's from 2018.
[https://gitlab.com/aasaam/ubuntu-overssh-reinstallation](https://gitlab.com/aasaam/ubuntu-overssh-reinstallation)

Automatic installations have all changed since 2018.  You can always roll your own install, but that's a bunch of work. 

Around 2012, I had an OS upgrade fail that I was doing over ssh.  The system was down until I could get there a few days later.  Nothing was really wrong with the 10.04 --> 12.04 upgrade, it just needed an <enter> to be pressed on the local keyboard. I was lucky.

If you are paid $50/hour, it is cheaper to get a remote console like a Pi-KVM and do that than waste the time.  Real servers have IPMI/DRAC/RIBLO cards for remote access. Someone will still need to put a DVD or USB storage with the install media into the system. Then you can power it up/down just like being their with those remote console devices.

And as with all data, if you don't want to lose data, BACK - IT - UP!
I would expect ZFS upgrades or new installs to have issues still.  Then when there aren't any issues, be happy.  Always be prepared for problems. That's the safer stance.

---

