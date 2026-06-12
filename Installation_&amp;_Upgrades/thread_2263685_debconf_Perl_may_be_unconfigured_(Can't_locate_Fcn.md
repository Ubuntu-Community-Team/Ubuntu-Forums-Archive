---
title: "debconf: Perl may be unconfigured (Can't locate Fcntl.pm in @INC (you may need to ins"
date: 2015-02-02
forum: Installation &amp; Upgrades
---

### Post by authentictech on 2015-02-02
I've had a problem since running recent updates resulted in errors. I submitted bug reports for them here: 

  [URL="https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1410324"]
https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1410324[/URL]

  [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1404353](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1404353)

  
Since these update errors, I am now unable to install any new software or updates because:
> [INDENT]   debconf: Perl may be unconfigured (Can't locate Fcntl.pm in @INC (you   may need to install the Fcntl module)

 [/INDENT]

The usual resolutions are inaccessible because apt-get and dpkg  depend on Perl which is now broken and I am unable to update or install any software. I am now getting security warnings from software vendors that the software is out of date and at risk.

I am fairly new to Ubuntu. I don't use the command line very often and I generally stick with the LTS and install / update  using the Ubuntu Software Center so it is concerning that an update error can break Ubuntu so badly in this way.


  I really need step-by-step help fixing  this. Can you help? 

(If you would like Ask Ubuntu points you can post your answer here instead: [http://askubuntu.com/q/577061/18599](http://askubuntu.com/q/577061/18599))

Thank you.

---

### Post by MAFoElffen on 2015-02-02
The last time I saw that error was about 4-1/2 years ago, with someone using version 10.04 LTS. They ended up reinstalling 10.04 to fix that.

What I didn't know back then, I know something about now. What is missing is a part of the PERL package. But the apt-package depends on PERL. So you just can't un-install Perl, and re-install it on it's own . But you could boot from a LiveCD, chroot into your installed system to do it...

What i would do first is to boot from a LiveCD and do a backup of the current state, then try to fix it from that LiveCD. Is this server or desktop? Version?

---

### Post by authentictech on 2015-02-03
Thanks for your answer.

I decided this morning to go ahead with re-installing Ubuntu as it just seemed like the easiest option but I'm curious about alternative solutions for the future.

It is the desktop version (32-bit).

What about just copying missing files - would that work? What could I use on the LiveCD to help besides using it to back up? I used to find the recovery tools quite helpful on Windows. I'm wondering if there is some kind of equivalent (or better) recovery tool for Ubuntu when system files get corrupted and broken? There's none that I know of so far.

Also, do you actually know what caused this in the first place? I was taking a shot on it being the upgrade problems I mentioned before but I don't actually know for sure that's how it happened other than the problem occurred very shortly after.

---

### Post by MAFoElffen on 2015-02-03
There is a function on the LiveCD, where if you select install, and if it finds an installation of Ubuntu already, it should ask you if you want to repair the installed system... Like I said previously, I would get a backup before trying something like that (or any other fix like that)./ That option is not 100 percent. As far as I know, success using that option has been spotty. That would probably work on what you have going on, as it just relates to something in the system core framework.

Since you were planning to reinstall fresh anyways, might be worth it to try that... No more to really loss, right?

I don't know you that would happen. Like I said- Yours is only the 2d I've seen with that problem in almost 5 years. That just is not a normal occurance.

---

### Post by MAFoElffen on 2015-02-03
But then again, you could Boot on a LiveCD, > Open a terminal >
```

sudo blkid

```
Find drive and partition of your installed system, for example "/dev/sda5".
```

sudo mount /dev/sda5 /mnt
sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /sys /mnt/sys && sudo mount -t proc /proc /mnt/proc
sudo chroot /mnt /bin/bash

```
You will be chrooted into the installed system at a root prompt...
```

apt-get install --reinstall perl
exit

```

---

### Post by authentictech on 2015-02-06
I had already reinstalled Ubuntu but your comments should be helpful for someone else who reads this or the next time it happens to me. :) Thanks.

Do you want to provide this answer on AskUbuntu? Otherwise, I'll copy your answer and credit you with a link to your forum post here but, if you're a member of AskUbuntu, I'd rather give you the points.

---

