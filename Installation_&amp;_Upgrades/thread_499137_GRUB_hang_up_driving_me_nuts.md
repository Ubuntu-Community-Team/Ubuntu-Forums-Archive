---
title: "GRUB hang up driving me nuts"
date: 2007-07-12
forum: Installation &amp; Upgrades
---

### Post by voltaic on 2007-07-12
I've installed ubuntu on my machine, and everything went fine, rebooted after the install just fine, everything working great. Then I rebooted my machine and it hangs up at grub, I can't think of what would be causing this.. and since it's my only computer posting questions here can only be done from my work.. which just makes the problem even worse because everytime i find something they might be a solution online, i go home try it out, and have to wait another day to find another possible solution.

I know it's not my install, because i've reinstalled and get the same issue, I even installed mandriva and the same thing happens.. and frankly I'm tyring of reinstalling my operating system.

It's a single boot set up with the master IDE channel as 20GB drive master, and CD/DVDRW as secondary, and two 200GB HDDs on an IDE raid channel.

hda is set up as follows:

hda1 18GB ext3 mount /
hda5 2GB swap

I know the issue is something with grub because when I installed mandriva and got the same issue I tried another install of mandriva using LILO and everything worked fine. 

When the machine turns on and goes through the boot up it halts on:

```

Loading GRUB stage 1.5.

Loading GRUB, please wait.
```

If anyone has any idea please help me out, I'll copy the fstab and menu.lst to a USB drive and post them tomorrow when I come back.

cheers,
Daniel

---

### Post by Pumalite on 2007-07-12
Start by reading a little about your set up and the issues that Ubuntu might have with it;

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

[http://ubuntuforums.org/showthread.php?t=114519](http://ubuntuforums.org/showthread.php?t=114519)

---

### Post by voltaic on 2007-07-12
Thank you, I appreciate the response, and there's some very useful information in there... which will come in handy in the future I'm sure, but I think you may have misunderstood; the ubuntu install is on a harddrive that is not part of the RAID at all, it's just the master drive on the primary IDE controller on the MoBo. The two drives on the tertiary controller aren't even actually set up as raid either, and they just hold data.. these drives show up fine even with just the liveCD

Thanks,
Daniel.

---

### Post by rillip on 2007-07-12
Mmm, Grub has always worked great for me, so I don't really have any troubleshooting howto on it.  But there's nothing that says you can't use the LiveCD to install Lilo and use it instead.  Grub is the default but by no means required.

---

### Post by Pumalite on 2007-07-12
Check this too:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by voltaic on 2007-07-13
> **Pumalite said:**
> Check this too:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

That's a very helpful link, and something tells me I might find my answer somewhere in there, I'll take a closer look when I get home tonight. Thanks.

---

### Post by bulldog on 2007-07-13
You can try to reinstall GRUB using a live cd.
This will make sure you install GRUB on the right hdd and with the right boot options.
Make sure,however,that you BOOT from the hdd were you installed GRUB to.
Do as follows,
Boot into the live Ubuntu cd. 
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next command 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```

Install it to the hdd which is mentioned in the find command (hd0,1) means hd0,(hd1,1) means hd1.
Don't use (hd0,1) or (hd1,1) this will install it into a partition,just use (hd0) or (hd1) or what ever hdd you get in the find command and use this hdd in the setup command.
Setup this hdd as the master boot device in your BIOS and all should be fine.

---

### Post by Sakumo on 2007-08-23
I have the same problem as you do and only have a silly workaround to get my Ubuntu to boot. 

I installed Ubuntu Feisty 64 on my computer with an Asus m2npv-vm motherboard and it freezes at the GRUB screen as the timer is counting down. 

My solution is to keep hitting the ESC when the motherboard logo disappears and then select the appropriate kernel to use.

Hopefully this works for you and you can post the relevant files on this board. (I don't know my way around as of yet.) Additionally, you can then edit the grub menu.lst file to tell it to show the boot options. One less step to boot up. :)

I'm still annoyed because this means I won't be able to do a remote restart. I'm going to try SuperGrub as recommended in an earlier reply and see what I come up with.

---

### Post by voltaic on 2008-02-11
I'm revisting this thread because I remembered earlier this week that I never posted my solution to this problem, and it may be helpful to others. 

I have no idea why this affected GRUB, but all the problems were the result of a USB drive being plugged in. If the flash drive is plugged in GRUB hangs everytime, without it... GRUB works fine. I was happy to fix the problem but still kind of wonder why it was a problem to begin with...

---

