---
title: "Two kernels installed- how do I switch to the new one?"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by tobydeemer on 2008-04-30
Hi-
I ran the upgrade on the 23rd, and everything went very well- it even fixed a couple of things. I have MonoDevelop installed, and prior to upgrade it would crash when trying to save a project. Now, it works perfectly. Also, when I would use the key board function keys to change LCD brightness, the little indicator bar up in the corner would be a garbled mess on top of Ubuntu. Now, it looks like it's supposed to- a little bar graph following brightness.

However, the quibbles-

First, my swap partition seems to be gone. If I open System Monitor and look at resource, I see Swap used: 0 of 0 bytes. This hasn't caused any problems (as of yet) but it seems like it could be a little iffy down the road.

Second, the upgrade installed the new kernel, but did not switch over from the old one. So if I look in Synaptic, I see 2.6.22 and 2.6.24 both installed, with all the accompanying headers, etc. But my system is still running from 2.6.22, and the new one is not in Grub. 

Will it work properly if I uninstall the old kernel through Synaptic, and then run [HTML]sudo update-initramfs -u -k 2.6.24-16-generic[/HTML] ?

---

### Post by tobydeemer on 2008-04-30
Almost forgot-

When I did the upgrade, it also broke my wireless. (The dreaded Broadcom bcm-4311) I had to switch from the new firmware cutter back to the old one, and then take it off the blacklist. Once I did that, it was working as well as ever.

---

### Post by frodon on 2008-04-30
For your old kernel you can uninstall it from synaptic, for the update-initramfs command it should do the trick, i would just run a sudo update-grub after this.
Other option if you want to keep your old kernel which can be handy too is just to open your menu.lst file and change the default booting kernel after having solved your previous issue.

PS: if you want to contribute a little you can detail the steps you followed to fix your wireless, it might help some other users with the same hardware.

---

### Post by tobydeemer on 2008-04-30
Hi-
Thanks for the reply. And the wireless workaround I did was actually kind of simple-

Since my wireless was not working, I plugged into the ethernet at home. I went into Synaptic and removed the new b43-fwcutter, and reinstalled the bcm-43xx-fwcutter.

Then I ran

[HTML]sudo gedit /etc/modprobe.d/blacklist[/HTML]

And commented out bcm-43xx so that it was not blacklisted. Upon restart, it was functioning again.

However, I did see a post the said the new cutter, if you can get it to work, has much better connectivity reception, so I think I may keep trying to get it to work.

---

### Post by tobydeemer on 2008-04-30
Update-

I did uninstall the old kernel through Synaptic, and then ran the update initramfs command, and also update-grub. During the removal, it asked me what to do about menu.lst- keep local version, install package maintainer's version, etc. I kept the local, which I think was my issue, because...

On reboot, I got Error 15- File not found. So I hit e to edit the boot lines, changed all the numbers to match the new kernel, and it worked. So when I was logged in, I made a backup of the old menu.lst, and changed all the kernel numbers to match, and it worked. Rebooted twice now without any hangs. The only snag is that the splash quits about half way through, and dumps to verbose mode.

BUT****

Now with the new kernel, I am using the new b43 fwcutter, and it's acting spotty. I can see that the card is recognized and picking up networks, and I can connect to my home network. When it's live, it's great connectivity- up to 100% depending on where I'm at. I never had that good of signal. But it will randomly drop connection, reconnect, lose signal strength, generally fluctuate a lot. So... I'm gonna have to do some digging and make sure I always carry an ethernet cable with me.

It's all about learning, right?

---

