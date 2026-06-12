---
title: "Linux kernel 2.6.31-rc7"
date: 2009-08-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rudenko_ruslan on 2009-08-22
Released today. A message from Linus Torvalds:
[QUOTE=Linus Torvalds]You know the drill, so all together now: "Another week, another -rc 
kernel".

Most of the changes are small one-liners, but the dirstat shows the areas 
that got a bit more tender loving care:

  17.4% arch/arm/mach-omap2/
   2.2% arch/arm/mm/
   3.8% arch/arm/plat-omap/
  24.3% arch/arm/
   2.5% arch/microblaze/
  29.2% arch/
   9.6% drivers/gpu/drm/radeon/
  13.2% drivers/gpu/drm/
   3.2% drivers/i2c/busses/
   2.8% drivers/media/dvb/frontends/
   4.7% drivers/media/dvb/siano/
   7.6% drivers/media/dvb/
   2.6% drivers/media/video/em28xx/
   8.2% drivers/media/video/
  16.2% drivers/media/
   3.0% drivers/net/e1000e/
   3.4% drivers/net/ixgbe/
   2.6% drivers/net/netxen/
  16.6% drivers/net/
  50.2% drivers/
   2.9% fs/xfs/
   5.7% fs/
   2.5% include/linux/
   3.1% include/
   3.1% mm/
   2.0% net/
   2.5% security/
 290 files changed, 3366 insertions(+), 1777 deletions(-)

ie we have some arm and microblaze updates, radeon/drm and media updates, 
and network drivers. The rest tends to be a random smattering all over.

But apart from a couple of bigger ones (OMAP GPIO/UART fixes and the 
radeom/kms changes), it's really pretty small. The bulk of those 290 files 
changed are basically few-liners in 213 commits (shortlog below), and in 
general we should have cut down the regression list another tiny bit.

Worth testing: if you've seen NULL pointer oopses with reiserfs under 
load, I committed something I hope fixes it. I'd have wished to get 
a firm confirmation before doing that, but I wanted to get the fix in 
before -rc7, so now I'll just have to wait for results after.

And if you had odd lock-ups with older dual-CPU machines (PPro, P2, P3, 
Athlon XP), that should be fixed too.

There's some inotify fixes here too, but I don't think we've confirmed 
whether they help the (apparently very  hard to trigger) oopses some 
people have seen. So please test and report.[/QUOTE][http://lkml.org/lkml/2009/8/21/446](http://lkml.org/lkml/2009/8/21/446)

I guess that this will be in the mainline pretty soon - [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc7/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc7/)

---

### Post by plun on 2009-08-22
> **rudenko_ruslan said:**
> 
I guess that this will be in the mainline pretty soon - [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc7/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc7/)

Yup... up and running  !

The sound volume got muted again....:) no other findings.

---

### Post by Slug71 on 2009-08-22
Wonders if Radeon KMS will be enabled by default this time?

---

### Post by taavikko on 2009-08-22
> **Slug71 said:**
> Wonders if Radeon KMS will be enabled by default this time?

Just be sure to checkout the changelog when it arrives to be sure.

I'm just waiting for libdrm / mesa updates to come through that have the radeon improvements...

---

### Post by rudenko_ruslan on 2009-08-24
linux 2.6.31-7.27 - [https://lists.ubuntu.com/archives/karmic-changes/2009-August/007059.html](https://lists.ubuntu.com/archives/karmic-changes/2009-August/007059.html)

---

### Post by taavikko on 2009-08-24
> **rudenko_ruslan said:**
> linux 2.6.31-7.27 - [https://lists.ubuntu.com/archives/karmic-changes/2009-August/007059.html](https://lists.ubuntu.com/archives/karmic-changes/2009-August/007059.html)

Pretty minimalistic changes to mainline kernel...
I'll bet a hug, that there will be an other one, before it's pushed to repos.

---

### Post by Matt Behrens on 2009-08-24
Mmm.  I wonder if ath9k is going to be fixed in time.  Doesn't look like there are any changes here.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/414560](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/414560)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/407040](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/407040)

[http://bugzilla.kernel.org/show_bug.cgi?id=13807](http://bugzilla.kernel.org/show_bug.cgi?id=13807)

At least I have ndiswrapper to keep me working, I guess.

---

### Post by taavikko on 2009-08-24
> **Matt Behrens said:**
> Mmm.  I wonder if ath9k is going to be fixed in time.  Doesn't look like there are any changes here.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/414560](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/414560)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/407040](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/407040)

[http://bugzilla.kernel.org/show_bug.cgi?id=13807](http://bugzilla.kernel.org/show_bug.cgi?id=13807)

At least I have ndiswrapper to keep me working, I guess.

ath9k is working "more/less" here, still lot of disassociations/reassociations, and few stuck-ups once in a while, but mainline kernel was an improvement.

---

### Post by chronosMark on 2009-08-24
> **plun said:**
> Yup... up and running  !

The sound volume got muted again....:) no other findings.
LOL i can't remember a time when an update didn't screw up the sound in some way.
On another note update manager seems to have been screwed up for me not really a problem as I use apt but thought might as well point it out.

---

### Post by Starks on 2009-08-24
Packages just landed.

[https://edge.launchpad.net/ubuntu/karmic/+queue?queue_state=0&queue_text=linux](https://edge.launchpad.net/ubuntu/karmic/+queue?queue_state=0&queue_text=linux)

---

### Post by jerrylamos on 2009-08-24
> **Slug71 said:**
> Wonders if Radeon KMS will be enabled by default this time?
Last time I tried Radeon KMS it was slower than vesa.....

I'll be interested to see what comes out this time.

Jerry

---

### Post by nanog on 2009-08-25
I tested Fedora 11 after reading pulse developers talking smack about Ubuntu. Static, drop outs, and crashes.

---

### Post by plun on 2009-08-25
Meta package built and out...

> linux-meta (**2.6.31.7.18**) karmic; urgency=low

  * Karmic ABI 7


[https://lists.ubuntu.com/archives/karmic-changes/2009-August/007115.html](https://lists.ubuntu.com/archives/karmic-changes/2009-August/007115.html)

No problems with my laptop.

EDIT

Its is a problem.... hangs during shutdown...

modem-manager, caught signal 15 shutting down and no more...

---

### Post by biasquez on 2009-08-25
problems with my laptop (acer 6930G):

- hangs during shutdown
- wifi doesn't work (Intel Corporation Wireless WiFi Link 5100)
- ethernet doesn't work ( Atheros AR8121/AR8113/AR8114 PCI-E )

---

### Post by rudenko_ruslan on 2009-08-25
Hm, tried to reboot few minutes ago, and my PC hanged :confused: So I was forced to use "reboot" button.

---

### Post by plun on 2009-08-25
Filed a bug about the shutdown hang.

[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/418509](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/418509)

---

### Post by rudenko_ruslan on 2009-08-25
> **plun said:**
> Filed a bug about the shutdown hang.

[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/418509](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/418509)
Should I confirm this? :confused:

---

### Post by plun on 2009-08-25
> **rudenko_ruslan said:**
> Should I confirm this? :confused:

Yes, please if its the same for you....

---

### Post by rudenko_ruslan on 2009-08-25
> **plun said:**
> Yes, please if its the same for you....
Alright, but I can't say that I saw this:
> modem-manager, caught signal 15, shutting down
When my computer hanged during reboot. Just black screen after usplash :confused:

---

### Post by plun on 2009-08-25
> **rudenko_ruslan said:**
> Alright, but I can't say that I saw this:

When my computer hanged during reboot. Just black screen after usplash :confused:

OK.. you have a hang nevertheless....

---

### Post by rudenko_ruslan on 2009-08-25
> **plun said:**
> OK.. you have a hang nevertheless....
Confirmed! :KS

---

### Post by taavikko on 2009-08-25
> **plun said:**
> OK.. you have a hang nevertheless....

Same here on my laptop:
```
Checking for unattented-upgrades * Asking all remaining processes to terminate
```

Mainline kernel-rc7 worked nicely, bringed in working suspend, but it would hang after that if trying to shutdown.... Funny :)

---

### Post by biasquez on 2009-08-25
x plun:

can you give me how to report a complete bug (like your bug with all logs attached) about problem with this kernel (wifi+eth problem)?  thanks!

---

### Post by taavikko on 2009-08-25
> **biasquez said:**
> x plun:

can you give me how to report a complete bug (like your bug with all logs attached) about problem with this kernel (wifi+eth problem)?  thanks!

```
ubuntu-bug linux
```

---

### Post by plun on 2009-08-25
> **biasquez said:**
> x plun:

can you give me how to report a complete bug (like your bug with all logs attached) about problem with this kernel (wifi+eth problem)?  thanks!

OK....

You just runs this command

ubuntu-bug packagename

in this case
```

ubuntu-bug linux-image
```

More about it:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Scroll down a bit to "**Filing a bug with ubuntu-bug**"



--

---

### Post by taavikko on 2009-08-25
Just a quick side note:
SysRq keys work, so don't resort to hard shutdown!

---

### Post by peacewithall on 2009-08-25
Just to confirm I also have the shutdown hang, but before that I had problems booting into Karmic, Ubuntu seems to have messed up with configuring GRUB, and I was met with the following:

"error: You need to load the kernel first.", and I could not get past GRUB.

I fixed it in the GRUB configuration file for now, I had to manually enter the location of the kernel, because Ubuntu left it blank.

---

### Post by biasquez on 2009-08-25
i can't use ubuntu-bug to report bug because wifi and eth don't work....i tried ubuntu-bug /var/crash/_linux_image.crash but i have error ("invalid directory/no such file). how can i report bug without internet connection on latest kernel?

---

### Post by taavikko on 2009-08-25
> **biasquez said:**
> i can't use ubuntu-bug to report bug because wifi and eth don't work....i tried ubuntu-bug /var/crash/_linux_image.crash but i have error ("invalid directory/no such file). how can i report bug without internet connection on latest kernel?

Use the previous kernel version, the _.crash file contains all the info.

Unless using KDE which has a little bug on apport...

---

### Post by plun on 2009-08-25
> **biasquez said:**
> i can't use ubuntu-bug to report bug because wifi and eth don't work....i tried ubuntu-bug /var/crash/_linux_image.crash but i have error ("invalid directory/no such file). how can i report bug without internet connection on latest kernel?

> As a last resort, at a minimum, your bug report should contain the output of the following commands:

$ uname -a > uname-a.log
$ cat /proc/version_signature > version.log
$ dmesg > dmesg.log
$ sudo lspci -vvnn > lspci-vvnn.log




From this wiki

[https://wiki.ubuntu.com/KernelTeam/KernelTeamBugPolicies](https://wiki.ubuntu.com/KernelTeam/KernelTeamBugPolicies)


--

---

### Post by biasquez on 2009-08-25
> **taavikko said:**
> Use the previous kernel version, the _.crash file contains all the info.

Unless using KDE which has a little bug on apport...

ubuntu-bug doesn't create file in /var/crash but it only report error send report...

---

### Post by taavikko on 2009-08-25
> **biasquez said:**
> ubuntu-bug doesn't create file in /var/crash but it only report error send report...

you can use ubuntu-bug to report crashes
```
ubuntu-bug /var/crash/_my-crash_file.crash
```
It doesn't care what kernel you run.

---

### Post by biasquez on 2009-08-25
> **taavikko said:**
> you can use ubuntu-bug to report crashes
```
ubuntu-bug /var/crash/_my-crash_file.crash
```
It doesn't care what kernel you run.

yes, i do ubuntu-bug /var/crash/_my-crash_file.crash, then a dialog pops up with "No such file or directory"...

---

### Post by zoomy942 on 2009-08-25
i installed this and no it doesnt seem that my machine shuts down all the way.  it will sit with a blinking cursor.  i will test more

---

### Post by tekstr1der on 2009-08-25
> **taavikko said:**
> Just a quick side note:
SysRq keys work, so don't resort to hard shutdown!

Shutdown hang got me too. While it is true that NumLock and other buttons are still responsive, I can switch to tty, but can't type to login. How do you suggest shutting down without hard power-off?

---

### Post by miegiel on 2009-08-25
> **biasquez said:**
> yes, i do ubuntu-bug /var/crash/_my-crash_file.crash, then a dialog pops up with "No such file or directory"...

```
ls -al /var/crash/
``` and pick the coresponding *.crash* file

---

### Post by miegiel on 2009-08-25
> **tekstr1der said:**
> Shutdown hang got me too. While it is true that NumLock and other buttons are still responsive, I can switch to tty, but can't type to login. How do you suggest shutting down without hard power-off?

Hibernate works for me, it's just *restart* and *shut down* that hang. Alternatively there's always 2.6.31-rc6.

---

### Post by tekstr1der on 2009-08-25
> **taavikko said:**
> Just a quick side note:
SysRq keys work, so don't resort to hard shutdown!

Oh, my problem is that while SysRq key works, my numpad keys become mapped to the keys I need (netbook keyboard), and I cannot disable them. So, unfortunately [Alt-SysRq-P] becomes [Alt-SysRq-*], which does nothing.

---

### Post by infamousrev on 2009-08-25
> **Matt Behrens said:**
> Mmm.  I wonder if ath9k is going to be fixed in time.  Doesn't look like there are any changes here.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/414560](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/414560)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/407040](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/407040)

[http://bugzilla.kernel.org/show_bug.cgi?id=13807](http://bugzilla.kernel.org/show_bug.cgi?id=13807)

At least I have ndiswrapper to keep me working, I guess.


My ath9k on my asus 1000HE is working great with the latest drivers:

My daily build script:

dependencies: sudo apt-get install unp


~/daily-wireless/dailyscript:
> wget [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2) --output-document=compat-wireless-2.6.tar.bz2
unp compat-wireless-2.6.tar.bz2
cd compat-wireless-$(date +%F)
./scripts/driver-select ath9k
make
sudo make install
sudo make unload
And then reboot


EDIT: After suspend resume do:
sudo rmmod ath9k
sudo modprobe ath9k

---

### Post by tekstr1der on 2009-08-25
> **taavikko said:**
> Same here on my laptop:
```
Checking for unattented-upgrades * Asking all remaining processes to terminate
```

Has a bug been submitted yet for this hanging issue?

---

### Post by plun on 2009-08-25
> **tekstr1der said:**
> Has a bug been submitted yet for this hanging issue?

Yup

[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/418509](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/418509)

I also asked at IRC #ubuntu-kernel but noone answered....

---

### Post by Totzo on 2009-08-25
> **tekstr1der said:**
> Shutdown hang got me too. While it is true that NumLock and other buttons are still responsive, I can switch to tty, but can't type to login. How do you suggest shutting down without hard power-off?

alt + Sys_Rq + R, S, E, I, U, B. (Raising Skinny Elephants Is Utterly Boring!)  :)

---

### Post by tekstr1der on 2009-08-25
Totzo: I understand that, but thanks.

> **tekstr1der said:**
> Oh, my problem is that while SysRq key works, my numpad keys become mapped to the keys I need (netbook keyboard), and I cannot disable them. So, unfortunately [Alt-SysRq-P] becomes [Alt-SysRq-*], which does nothing.

---

### Post by nanog on 2009-08-25
> alt + Sys_Rq + R, S, E, I, U, B. (Raising Skinny Elephants Is Utterly Boring!) 

Works fine on my desktop but I cannot find the Sys_Rq on any of my laptops (all 3 of them).

(yet another reasons that default inactivation of ctrl-alt-back space was very bbad)

---

### Post by taavikko on 2009-08-25
Most laptops comes with "fn" button which is used to use extra functions of keyboard.
So it would be "fn+alt+sysrq+reisub"

sysrq key might be mapped under prtsc or delete

---

### Post by tekstr1der on 2009-08-25
I also need to use [Fn] key. I didn't specify that earlier.

Silly netbook keyboard. My I=5, U=4. So the best sequence I can perform on this machine is [Fn + Alt + SysRq + RE5S4B] I don't know what proceeses are not killed and I am not sure how important it is to remount filesystems in read-only prior to forcing reboot.

Overall, for my case this ends up not really any different than pressing the power button.

---

### Post by slakkie on 2009-08-25
My laptop cannot shutdown as well, hangs when it is telling/asking all other services to shut down.

I removed the kernel, running -6 again.

---

### Post by VMC on 2009-08-25
> **plun said:**
> Filed a bug about the shutdown hang.

[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/418509](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/418509)

Thanks. I followed up with one also.

---

### Post by jerrylamos on 2009-08-25
Updated to rc7 today, now Firefox can't get the internet?  Internet is still there because apt-get works as usual.  Firefox 3.5 and Firefox 3.0 can't reach the internet?  They just sit there trying to access google or aol or yahoo or whatever until they time out.

I dual boot to Intrepid, same hardware, gets internet fine.  

Internet on yesterday's 2.6.31-6 was fine, but with today's updates on booting 2.6.31-6 is no better than -7.

This is a 32 bit 2.0 gHz Celeron with i845 graphics and built-in ethernet, all of which are working.

How do I get enough data to put in a launchpad bug, since there isn't any hang or crash - Firefox just sits there until it times out waiting for response.  Apt-get gets response fine, the Wired Connection applet is fine, what do I do?

Thanks for any ideas.

Jerry

---

### Post by slakkie on 2009-08-25
Jerry, check your /etc/resolv.conf in karmic.

Could be some networkmanager interfering...

---

### Post by Regenweald on 2009-08-25
> **Totzo said:**
> alt + Sys_Rq + R, S, E, I, U, B. (Raising Skinny Elephants Is Utterly Boring!)  :)

First time i got to use this, it was quite fun stretching about. Although i held down 'r' for a bit too long though :)

---

### Post by jerrylamos on 2009-08-25
> **slakkie said:**
> Jerry, check your /etc/resolv.conf in karmic.

Could be some networkmanager interfering...

Thanks for the reply.  /etc/resolv.conf looks O.K.

After the umteenth shutdown (-rc7 hang) reboot it finally cleared itself.  Firefox internet O.K. now.

Jerry

---

### Post by miegiel on 2009-08-26
I saw this post in another thread :
> **dino99 said:**
> for me, it refused to shutdown coz of files into trashbox & nautilus busy with these files. After deleting them, i'll shutdown at least.
[s]Could this shutdown-hang be related to nautilus/trash ?

I remember having the same thing when shutting down after emptying my trash. Taunting fate, I just deleted something unimportant and emptied my trash again and when I shuttdown I'm getting the warning that nautilus is still taking out the trash again. I hope this gives someone some inspiration,[/s] I'm as clueless as ever :)

The nautilus thing happens in 2.6.31-6 too ](*,)

---

### Post by garvinrick4 on 2009-08-26
I have done an ugrade 3 times from 9.04 and every time 9.04 works like a charm.
9.10 works just fine until I try to reboot or shutdown and it just will not, crash's everytime
on shutdown or reboot. 9.04 where I am at again works like a jewel. Still have desire
to be at 9.10 for some reason. Been there for over a month. If someone knows fix or
I have to wait for fix. Let me know.
 64 bit---Vista dual boot-- Share machine with my Pop's who is 80 and can use word and
check e-mail in Windows. For him he has come a long way to do that. He get's what ever
he wants from me. He has earned it. Will get a laptop without dual boot when 9.10 is released as stable.
 Anyway Alpha 4 doe's not take kindly to dual boot but will boot first time out but not shutdown or reboot. HMMM?

---

### Post by Paqman on 2009-08-26
> **garvinrick4 said:**
> If someone knows fix or
I have to wait for fix. Let me know.

Install the 2.6.31-6 kernel for now, the -7 is b0rked.

---

### Post by ilna on 2009-08-26
> **Paqman said:**
> Install the 2.6.31-6 kernel for now, the -7 is b0rked.What does 'broken' mean except for shutting down issue?

BTW, any software is broken, isn't it?

---

### Post by plun on 2009-08-27
Shutdown bug triaged and a milestone to Alpha 5

[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/418509](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/418509)


--

---

