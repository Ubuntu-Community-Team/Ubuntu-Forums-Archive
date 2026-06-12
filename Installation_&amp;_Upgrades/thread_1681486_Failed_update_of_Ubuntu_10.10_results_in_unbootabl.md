---
title: "Failed update of Ubuntu 10.10 results in unbootable system"
date: 2011-02-04
forum: Installation &amp; Upgrades
---

### Post by chessweb on 2011-02-04
Hi,

  yesterday I performed an automatic security update suggested by the  update manager on my virtualized (with VirtualBox on a Windows 7 host)  Ubuntu 10.10 installation.

  The update somehow failed and left me with an unbootable system. When  I try to boot, I am told that various folders, files, and what not are  missing. Then the system drops into a busybox and leaves me with an  (initramfs) prompt.
  
This happens with all kernels I get offered by GRUB, although the error messages are quite different from kernel to kernel.
  
Well, the short of it is this: I don't have the slightest idea on how  to get back to a working system and this site is the final straw I'm  willing to grab.
  A complete disaster like this following an update initiated and  executed by the system is unheard of in Windows-land; at least I haven't  heard of it, yet, and therefore I am going to abandon Ubuntu and Linux  altogeteher, if there is no remedy.

  Regards, RSel

---

### Post by mörgæs on 2011-02-04
Please post the error message you are getting.

---

### Post by akureyri on 2011-02-04
Hello,

I have this same problem. My MacBook does not boot up and my pc boots up into command prompt where I can sign me in and than after a while the login screen appears and all is normal. This all happened after the first reboot after updating.

regards

---

### Post by mörgæs on 2011-02-05
As above: Please post the exact error messages the Macbook is showing.

---

### Post by akureyri on 2011-02-08
Hello,

It seems that I have a hard disk failure in my macbook. Now my pc works fine. I had some error messages that it could not mount the hard drive. When I booted the computer with the ubuntu cd I was unable to access the hard drive. I was also unable to format or partition. So it seems that the problem was not because of the upgrades.

---

### Post by tigerZERO on 2011-02-21
Hello,

I seem to be having the same problem with my macbook-based Ubuntu 10.10. The machine crashed after I tried to wake it from a screensaver last Friday (the 18th), so I'm not sure if it was that last update or what. I'm currently booting from the install CD, but even when I am using this OS I cannot mount the computer's hard drive to get at the files, nor can I run a clean install; the computer just freezes.

When I try to boot from the hard drive, the machine goes rapid-fire through a bunch of lines of code, faster than I can read, but it crashes after the following:

Begin: Running /scripts/init-bottom ... mount: mounting /dev on /root/dev failed: no such file or directory
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /proc on /root/proc failed: no such file or directory

Target filesystem doesn't have /sbin/init
no init found try passing init= bootarg

Then it apparently recognizes my USB drives as new hardware devices, after which it just hangs.

---

### Post by deconstrained on 2011-02-21
This has to be the 7th or 8th time I've seen this problem crop up in the forums in the past 36 hours, to which I'll give the same answer: boot to the live disk, mount your Linux partition, chroot and rebuild the initrafms.

Please, people. Use Google. Use the wikis. Scour the forums. You're not alone.

---

### Post by tigerZERO on 2011-02-21
I would love it if the solution were that simple, but when I attempt to mount the partition nothing happens, and I get the 
"DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending" 
error if I try to do anything else with it.

EDIT: Also this error after about 20 minutes of trying to mount:
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

And in the terminal when I run e2fsck I get 
"Device or resource busy while trying to open /dev/sda2
Filesystem mounted or opened exclusively by another program?"

---

### Post by tigerZERO on 2011-02-22
Hello,
I've spent some more time on the forums, still with no luck.

I tried gparted, and the terminal returns
glibmm-ERROR **:
unhandled exception (type std::exception) in signal handler:
what: basic_string::_S_create

so between not being able to boot, not being able to mount, and not being able to even run gparted, there's nothing I can do to my knowledge.

EDIT: tune2fs tells me the filesystem state is clean with errors. Still can't run fsck, I just get "Filesystem mounted or opened exclusively by another program?"

---

### Post by Nonsense on 2011-02-23
Same problem here.

Can't boot into system (no updates made).
When I use a Live-CD and try to mount my HD I get the dBus-error.
If I force mount the filesystem the disk is empty.
WTF?

I can't believe this is my filesystem corrupt and all my files gone/inaccessable?

EDIT: Will try this
[http://ubuntuforums.org/showthread.php?t=1563529&highlight=mount+root](http://ubuntuforums.org/showthread.php?t=1563529&highlight=mount+root)

---

### Post by tigerZERO on 2011-02-23
SystemRescueCD was able to run fsck, we're back in business. I suppose this was a learning experience, at any rate.

---

### Post by dwllui on 2011-03-01
I have a similar problem described here. Does anyone have any idea on how to resolve this

[http://ubuntuforums.org/showthread.php?p=10509980#post10509980]("http://ubuntuforums.org/showthread.php?p=10509980#post10509980")

---

