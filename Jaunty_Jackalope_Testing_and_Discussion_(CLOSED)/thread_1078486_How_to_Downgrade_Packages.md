---
title: "How to Downgrade Packages ??"
date: 2009-02-23
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by WorldTripping on 2009-02-23
OK,

So I've been running before I can walk and the latest updates to Jaunty have borked my system.

According to this thread I need to downgrade a few packages.

[http://ubuntuforums.org/showthread.php?t=1076190]("http://ubuntuforums.org/showthread.php?t=1076190")

How do I actually do this if I cannot get past the lvm login ?

Cheers.

---

### Post by philinux on 2009-02-23
You're in the wrong forum. Also dont forget that jaunty is not intended to be run on your main machine. At this stage it is for testing and reporting bugs only.
[http://ubuntuforums.org/forumdisplay.php?f=352](http://ubuntuforums.org/forumdisplay.php?f=352)

However. Reboot and let the login window fail. Press ctrl alt f1.
Login and then use this command.

```
sudo apt-get update && sudo apt-get upgrade
```

This bug has been fixed with updates. I think

---

### Post by WorldTripping on 2009-02-23
Ah,

OK then.

Mods feel free to move my post.

That solution does not work anyway as you don't get anywhere near the login screen.

Cheers.

---

### Post by philinux on 2009-02-23
Choose recovery mode then from grub and update from the command line.

---

### Post by WorldTripping on 2009-02-23
> **philinux said:**
> Choose recovery mode then from grub and update from the command line.

Sorry,

That's a no-go too.

My HDD is encrypted (lvm+luks) and after booting I see a list of these messages:

/sys/devices/virtual/block/dm-0 (#######)
/sys/devices/virtual/block/dm-0 (#######)

With constant disk activity.

I need to boot from a live CD and downgrade some of the packages in the existing installation.

I just don't know how to do that.

Ah well, Mods feel free to move whilst I 'Carry on Googling'.

Cheers.

---

### Post by philinux on 2009-02-23
ok post five of your link has the clue. Press esc at grub and choose the previous kernel to boot.

---

### Post by WorldTripping on 2009-02-23
See this the other thing.

I only have kernel(s)
2.6.28-8-generic
and
2.6.28-8-generic (recovery)

I think I'm going to have to go for a fresh install.

Ah well nothing lost and plenty learnt.

Cheers philinux

---

### Post by WorldTripping on 2009-02-23
Aha,

I might be getting somewhere.

I edited the kernel command and managed to get to a busybox  terminal.

But I have still not logged in, just decrypted the HDD so that it can be read.

How from here can I downgraded a package ?

---

### Post by philinux on 2009-02-23
Cant be much help here as I've never had to do this. But googling got this.
[http://www.google.co.uk/search?q=ubuntu+downgrade+package&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.co.uk/search?q=ubuntu+downgrade+package&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)
[https://lists.ubuntu.com/archives/ubuntu-users/2007-June/116572.html](https://lists.ubuntu.com/archives/ubuntu-users/2007-June/116572.html)

You'll have to explore the links or wait for an answer in the Jaunty forum. ;)

---

### Post by WorldTripping on 2009-02-23
> **philinux said:**
> Cant be much help here as I've never had to do this. But googling got this.
[http://www.google.co.uk/search?q=ubuntu+downgrade+package&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.co.uk/search?q=ubuntu+downgrade+package&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)
[https://lists.ubuntu.com/archives/ubuntu-users/2007-June/116572.html](https://lists.ubuntu.com/archives/ubuntu-users/2007-June/116572.html)

You'll have to explore the links or wait for an answer in the Jaunty forum. ;)

Cheers and thanks for your time.

:)

---

### Post by philinux on 2009-02-23
Your Jaunty thread just got a new reply.

---

### Post by WorldTripping on 2009-02-23
BINGO !

I have a solution that works for me.

Booted using a live CD.

Noticed that my Grub partition still had all the old Linux 2.6.28x-generic heahers in it.

They were just not showing on my boot menu.

Manually changed menu.lst, booted into a recovery mode as I guessed that X would need repairing.

Worked like a treat and I got straight back into my lvm.

Only issue now is that 'kcryptd' and 'udevd' are running like crazy and hogging the CPU.

But that resolution is tomorrows problem.

Cheers for all the inputs.

---

### Post by bapoumba on 2009-02-23
Moved to Jaunty.

---

### Post by dentaku65 on 2009-02-23
Actually you can use aptitude in order to downgrade a package
```
sudo aptitude remove package_name
```
You must choose n (no) a couple of times in order to get the question:
Do you want to downgrade to the version xx.yy.zz of the package_name?
Choose Y (yes)

---

### Post by ugkbunb on 2009-02-23
> sudo dpkg -i --force-downgrade packagename.deb

iirc

---

### Post by nanog on 2009-02-23
sudo dpkg -i --force-downgrade packagename.deb 

nifty!

---

