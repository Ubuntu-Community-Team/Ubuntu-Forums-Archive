---
title: "Moving Virtual Machine Installations to other drives to upgrade..."
date: 2008-03-05
forum: Installation &amp; Upgrades
---

### Post by dbsoundman on 2008-03-05
Ok, so here's my sad story. I'm pretty sure my installation is somehow broken, and I'm tired of pissing around with it. I do a lot of audio stuff on here, and I can't seem to get JACK to run on the right time (it runs slow), and now, I have uninstalled Ardour, and after compiling Ardour 2.3, it won't launch because the install didn't create a file in /usr/bin. I'm just really getting tired of messing with this, and I think maybe if I just upgrade to the newest Ubuntu Studio via a fresh install, things will be better because they will already be installed and I don't have to piss around with it.

Here's what I want to do, though. I have a Windows 2000 virtual machine installed using VMware server. I want to move the whole installation to my USB hard drive so that when I do the upgrade, I can just move it back onto the computer. Is this possible, or do I need to start over with that as well? Quite honestly, I really don't want to do a fresh install anyway because it means I have to re-download and configure EVERYTHING that I've set up so nicely on here, but I'm really thinking that some things just have to be re-done, especially with my JACK issue. The reason it's such a big problem is because it means that when I export recorded audio, it plays at 2x speed because it was recorded at 1/2x speed essentially, which is a bad thing unless I want a session with the Chipmunks...

If anyone has a better idea of what I can do, please tell me, but right now, I'm just about ready to give up on this. Ubuntu is really nice, and much more efficient than Windows, but sometimes it's so damn complicated unless you know everything about computers, which I don't.

Thanks,
Dan

---

### Post by smylie on 2008-03-06
Yup. You should be able to save your vmware virtual machine.
The folder you need to take is (probably)  /var/lib/vmware/Virtual Machine/<your machine name>
If you've saved your machine somewhere else, you'll need to go look there =)

After you've reinstalled vmware, just copy that folder back to your hard drive, and from within vmware console, choose to open an existing machine and browse to were you've copied it.

after that, it should just work =)

cheers

---

