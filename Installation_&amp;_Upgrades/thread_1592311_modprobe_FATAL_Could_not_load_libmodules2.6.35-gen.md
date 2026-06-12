---
title: "modprobe: FATAL: Could not load /lib/modules/2.6.35-generic/  After upgrade"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by jeetendra.choudhary on 2010-10-10
Hi Experts,

After upgrading to ubuntu 10.10 from 10.04 i am getting following two errors while booting

1. modprobe: FATAL: Could not load /lib/modules/2.6.35-generic/modules.deb, no such
file or directory. 

2. intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled

I have no idea what to do the 1st error comes two time one by one in two different lines and 2nd one come only once in separate line.

before upgrading there was no problem. Please help.

Thanks & Regards
Jeetendra

---

### Post by dino99 on 2010-10-10
are you using only genuine maverick repos ? (synaptic repo tab)

if you have an other kernel installed, select 2.6.35 into synaptic to remove/purge then reinstall

---

### Post by cariboo on 2010-10-10
Does your system boot up to a desktop?

---

### Post by fjones243 on 2010-10-10
I'm also getting the same modprobe: FATAL error message after upgrading from 10.04 to 10.10 today.  I get the message twice, then my system boots to desktop without any other problems.  

Did anyone figure this out yet?

---

### Post by jeetendra.choudhary on 2010-10-10
> **dino99 said:**
> are you using only genuine maverick repos ? (synaptic repo tab)

if you have an other kernel installed, select 2.6.35 into synaptic to remove/purge then reinstall

thanks for your quick response,
yes i think i am using genuine maverik repos (as i think because i did an upgrade from upgrade manager only but i don't have much i dea about this.)

and please tell me how to select 2.6.35 into synaptic to remove/purge then reinstall, i am a newbie and don't have much idea about this.

Thanks & Regards
Jeetendra

---

### Post by Kash88 on 2010-10-12
> **jeetendra.choudhary said:**
> 
2. intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled


yeah, i am getting this at boot as well after installing the nvidia driver in ubuntu 10.10
Anyone know how to fix this?
Thx

---

### Post by mag1 on 2010-10-12
I also get this but it seems to work fine otherwise?  This won't cause problems will it?  I just installed from usb if that helps.

---

### Post by johnnytm on 2010-10-12
I have the same errors every time I boot. There is only one kernal installed because I uninstalled 10.04 before installing 10.10.  But evrything still boots up fine and all appears working after the .modprobe errors

---

### Post by jeetendra.choudhary on 2010-10-12
Hi all,

Yes presently its working fine for me also means i still boot and every thing seems fine but those problems are still there which i posted above i love this os but don't like to see those error. i wonder if it was working fine in lucid why it came now.

Apart from this i can't see the proper boot screen with nice ubuntu logo on center of screen and also when i restart or shutdown the system. Any help will be appreciated.

Thanks & Regards
Jeetendra

---

### Post by phillipvh on 2010-10-13
Hello,

I am also getting the modprobe error printed out twice, then a few seconds later I am at the login screen. Everything seems to work well, I just don't like having to look at it.. I Just upgraded from Ubuntu 10.04 and I never had the problem there.

Thanks in advance.

---

### Post by ChaosCon on 2010-10-13
Same here; two modprobes, then everything seems to boot fine, although my internet connectivity is broken at first (due to some issues with /etc/resolv.conf). Worked perfectly prior to 10.10

---

### Post by aksoutherland on 2010-10-13
I had the same issue. 
After a quick google search, I found this.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/642421](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/642421)

I used this to fix it.
Try to edit /etc/initramfs-tools/initramfs.conf (sudo gedit /etc/initramfs-tools/initramfs.conf in the console) and change the line MODULES=most to MODULES=dep.

Then use Synaptic to reinstall initramfs-tools like "durlo" suggested.

---

### Post by LorDVipeR on 2010-10-13
> **aksoutherland said:**
> I had the same issue. 
After a quick google search, I found this.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/642421](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/642421)

I used this to fix it.
Try to edit /etc/initramfs-tools/initramfs.conf (sudo gedit /etc/initramfs-tools/initramfs.conf in the console) and change the line MODULES=most to MODULES=dep.

Then use Synaptic to reinstall initramfs-tools like "durlo" suggested.


thnks man, work for me...!!:guitar:

---

### Post by phillipvh on 2010-10-14
Thanks 'aksoutherland' ! It works for me :)

---

### Post by Kash88 on 2010-10-15
Any update on how to fix the second error mentioned?

---

### Post by jeetendra.choudhary on 2010-10-16
Hi All,

Today i did a clean install (not upgrade) and the problem related to modprobe seems solved by this and no more modprob problem is coming but still that no graphics symbol  error is there. Does anyone find a fix or workaround for this.?

Regards
Jeetendra

---

### Post by johnnytm on 2010-10-16
I had done a clean install from the beginning and this modprobe error has always appeared.

---

### Post by Devinim on 2010-10-16
[FONT="Arial Narrow"][SIZE="3"]Have same problem on Kubuntu and aksoutherland's advice works well on Kubuntu too.
[/SIZE][/FONT]

---

### Post by eltel on 2010-10-17
> **aksoutherland said:**
> I had the same issue. 
After a quick google search, I found this.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/642421](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/642421)

I used this to fix it.
Try to edit /etc/initramfs-tools/initramfs.conf (sudo gedit /etc/initramfs-tools/initramfs.conf in the console) and change the line MODULES=most to MODULES=dep.

Then use Synaptic to reinstall initramfs-tools like "durlo" suggested.

Thanks for the advice. What does this actually do?

---

### Post by mhdzaki on 2010-10-18
my /lib/modules/ is;

$ ls /lib/modules/
2.6.35-22-generic

and my kernel is;
$ uname -an
Linux zaki-desktop 2.6.35-22-generic #34-Ubuntu SMP Sun Oct 10 09:26:05 UTC 2010 x86_64 GNU/Linux

i'm doing this, to fix my problem;

$sudo update-initramfs -c -k 2.6.35-22-generic 

base on my googling result...
[http://www.irregularactivity.co.uk/2009/07/27/modprobe-fatal-could-not-load-libmodules2-6-29-4modules-dep-fix/](http://www.irregularactivity.co.uk/2009/07/27/modprobe-fatal-could-not-load-libmodules2-6-29-4modules-dep-fix/)

---

### Post by vanquishedangel on 2010-10-18
That fix worked for me, the modprobe error is gone, it still hangs on start up when the modprobe error would show but without the error. Not sure if the speed improved for boot up at that part, but this fix improved all other boot up speeds and load times for the OS so good job :). Also i use less memmory, like 2% less.

I have a Hp dc7100, intel 3.8 ghz HT, 4 gigs ram, ty aksoutherland

---

### Post by DogMatix on 2010-10-19
I did try the mentioned fix before reinstalling but it didn't work for me.

---

### Post by mag1 on 2010-10-20
So when is this going to get an official fix?

---

### Post by johnnytm on 2010-10-22
This fix did not work for me. After i tried to re-install initramfs-tools I started getting all kinds off errors after updates. Always got a message that an update was not installed correctly, this kept happening even from update manager..Continued to happen until I changed the .conf entry back to the original. Bad part was the original error message never did go away.

---

### Post by venturax on 2010-11-07
> **aksoutherland said:**
> I had the same issue. 
After a quick google search, I found this.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/642421](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/642421)

I used this to fix it.
Try to edit /etc/initramfs-tools/initramfs.conf (sudo gedit /etc/initramfs-tools/initramfs.conf in the console) and change the line MODULES=most to MODULES=dep.

Then use Synaptic to reinstall initramfs-tools like "durlo" suggested.

It worked and the error message is gone. However boot time is the same as when the error was displayed. Btw I upgraded from 10.04 to 10.10.

Hope there will be an official way to get this problem properly fixed, as the description (even though it worked) seems more like removing the symptom rather than fixing the root problem.

---

### Post by asn_knight on 2010-11-14
> **aksoutherland said:**
> I had the same issue. 
After a quick google search, I found this.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/642421](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/642421)

I used this to fix it.
Try to edit /etc/initramfs-tools/initramfs.conf (sudo gedit /etc/initramfs-tools/initramfs.conf in the console) and change the line MODULES=most to MODULES=dep.

Then use Synaptic to reinstall initramfs-tools like "durlo" suggested.

Thanks a lot!!! Worked for me too!!! :)

---

### Post by mag1 on 2010-11-18
This has been known about for quite a while now and still no official fix, come on its getting a bit pathetic, i doubt its that hard and its quite visible so i don't get why its being ignored?

---

### Post by ballisox on 2010-11-18
I changed MODULES=most to MODULES=dep.  But this only worked on the first reboot.

This was a clean installation of Maverick, not an upgrade.

---

### Post by irwan_up on 2010-11-21
wew... it worked guys ! thanks a lot :D

---

### Post by mag1 on 2010-11-29
We shouldn't have to fix these kind of problems ourselves, especially when it sounds like the fix isn't even a proper one, i get the feeling this issue is actually a simple one and they just don't care to fix it, i thought ubuntu was good when it came to updates so its seems strange to me they can't or won't even though its an obvious one that shows up on boot.

---

### Post by wujj123456 on 2010-12-25
Sorry for digging up this thread. 

I'm getting the same error after upgrading my Ubuntu 10.10 from 2.6.35-23 to 2.6.35-24 today. I upgraded from 10.04 to 10.10 way back, but the boot up was fast, and with no errors/warnings. However, the boot was significantly slowed down after I plugged in my controller. It remains slow after this upgrade, but displays two "modeprobe: FATAL" now. The system is still functioning as it was though. 

I tried "update-initramfs -c -k 2.6.35-24-generic", but it didn't fix my problem.

---

### Post by VanceVEP72 on 2011-01-02
I'm not sorry for digging this back up. None of the "fixes" suggested in this thread got rid of the annoying double *FATAL: Could not load lib/modules/2.6.35-24-generic* messages at reboot.

I DID fix this annoying bug (thanks Canonical for the headache) by going to Synaptic and completely removing **linux-generic-2.6.35-24** and then re-installing it. Now I do not have the "FATAL" messages at bootup anymore.

Hope this helps others.

Happy computing :p

---

### Post by jeetendra.choudhary on 2011-01-04
Hi Guys,

This is **really pathetic** that we don't have any official fix for this even **after 3moths of release** of this version. I have switched from windows over last year only by getting suggestion from some of my seniors and friends as well, I do remember that **while working on windows I didn't had any problem for so long** (Is this because ubuntu is free?). As I have only a year experience with ubuntu I am not able to fix such issue myself and waiting for an official fix but I tried a-lot of googling and available workarounds  but nothing seems working for that **graphics problem** now I am facing some more issues Like system freezing after sometime of booting and I have doubt (I'm not sure) that is because of this issue. Its really annoying with such a great operating system, I really **love this OS and willing to contribute** for improvement but to learn it will take some time.

Regards
Jeetendra

---

### Post by unix1980 on 2011-01-10
For the moment it appears to be fixed in a test release.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/642421](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/642421)

---

### Post by DutchieR on 2011-01-19
Tried same thing, didn't work
However, I noticed that when running the "sudo update-initramfs -u" command , the error-message mentioned

 "FATAL: Could not load /lib/modules/2.6.35.25-generic/modules.dep: No such file or directory

This is correct and may be cause of the error since the folder names do not match with the actual folder name which is

 "2.6.35-25-generic" (a dash - between 35 and 25 in stead of a . period)

Is this the cause of the error?

---

### Post by foxdmatt on 2011-01-23
Try to edit /etc/initramfs-tools/initramfs.conf and change the line MODULES=most to MODULES=dep.

This worked for me on Ubuntu 10.10 on an old Dell Dimension 8400. It cut the boot time down by about 10 seconds. Thanks for the help.

---

### Post by DutchieR on 2011-01-24
Read previous. Did that already, no solution.

> **foxdmatt said:**
> Try to edit /etc/initramfs-tools/initramfs.conf and change the line MODULES=most to MODULES=dep.

This worked for me on Ubuntu 10.10 on an old Dell Dimension 8400. It cut the boot time down by about 10 seconds. Thanks for the help.

---

### Post by jfacemyer on 2011-02-04
Great...I tried this fix, and while it took away the message, it also took away my spdif sound!!!!!

It's the only thing I changed, and spdif was working perfectly fine before.

I reversed the changes and still no spdif.

Please, someone, tell me how to get my sound back. I realize there's little info here, but it was directly related to this "fix", so please let me know if you have some idea of what happened to my sound. (onboard intel sound)

---

### Post by Murdoc_of_puts on 2011-02-15
So what do I do if the new 6.35-24 kernel won't load, at all, and the 6.32-29 kernel will?

---

