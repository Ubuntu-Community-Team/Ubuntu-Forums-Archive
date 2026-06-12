---
title: "Problem in 9.10 (grub wants more space)"
date: 2010-06-28
forum: Installation &amp; Upgrades
---

### Post by ramnarayan on 2010-06-28
Hi

Was trying to update my 9.10 install.

Seems like there are some new kernal updates which meant that somethings were being written to grub. My Grub is located in a separate /boot parition of about 99 mb (which used to be enough but is not suddenly not enough)

and now i get this message
"Volume Boot has only 698 kb disk space left"

You can free up disk space by removing unused programs or files or by removing
files or programes to another partition or disk.

The problem does not end there itself - all the current updates failed to get updated and now when i try synaptic i get the following error

"
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to
correct the problem.
E: _cache->open() failed, please report. "

and when i try the
sudo dpkg --configure -a
this is what happens

Setting up initramfs-tools (0.92bubuntu53) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31-22-generic-pae

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.31-22-generic-pae
dpkg: subprocess installed post-installation script returned error exit status
1
-laptop:~$

***
i have atleast 4 different kernals installed and am not sure how to navigate he new Grub - its not as easy as earlier and am not sure how to create more space .(there is a tutorial to move grub but it seems quite dicey to me)

This is affecting my OS performance as some programmes are beginning to crash or freeze (firefox) and i can't help but think its because of incomplete updates. Also i cannot install new programmes or uninstall old ones (as in old kernals to free up space) apt-get also does not work


so refine the problem - my 100 MB /boot has become over crowded with kernals and one of the stupidities of the new grub (ver 2) is that it tends to accumulate all the old kernals.

The solution seems to be here
[http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/](http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/)

however its a catch 22 situation - i cannot use synaptic (or apt-get) to uninstall the older kernals - and because of that i cannot free up blocked space and then i comes back to the same state

Question is can i just go into /boot and delete the older kernals manually and hope that grub will just pick up the latest install ??

maybe i can keep the previous two kernals and hope that it at best shows an error and then continues to boot

any advice would be much appreciated and i feel i am sitting in a crippled system

ram

---

### Post by darkod on 2010-06-28
> **ramnarayan said:**
> 
so refine the problem - my 100 MB /boot has become over crowded with kernals and one of the stupidities of the new grub (ver 2) is that it tends to accumulate all the old kernals.


This has nothing to do with grub2. Why do you people keep blaming it for every silly thing you do, because it's the new "kid on the block"?

Whether the grub2 boot menu shows 1 or 100 kernels doesn't mean anything, it's just a text menu.

Your problem is that YOU didn't make sure to have enough space on /boot before starting to install/update the new kernels.
YOU didn't remove older kernels from time to time. Did you think those 100MB will last forever?

It's not grub2 that keeps older kernels, it's the ubuntu OS. And it does keep them until you remove them. They should design it to remove them automatically? What is someone doesn't want them removed?

The link you provided is useless, it just tells you to reorganize the grub2 menu. Your problem is not enough space on /boot and an update process which stopped half way, so now you can't use apt-get or Synaptic to remove the older kernels.

You can try the manual delete you mentioned, and hopefully that should allow you to finish the dpkg --configure -a process. I'm not sure it's the best thing to do, but it seems as one of the options if you can't remove the kernels another way.

Be careful which ones you delete. For example, if you can boot the newest kernel now, even with errors, delete the oldest one, and just one should be enough for now. Then see if you can finish the update process.

And unless you have specific reason to use /boot, I recommend not to use separate /boot partition anyway, it's pointless. As I said, unless you really need to use it on your machine. Don't use it just because you've seen a tutorial that you can use separate /boot, only if you really need it.

---

### Post by varunendra on 2010-06-28
> **darkod said:**
> This has nothing to do with grub2.............. [B]You can try the manual delete you mentioned, and hopefully that should allow you to finish the dpkg --configure -a process. I'm not sure it's the best thing to do, but it seems as one of the options if you can't remove the kernels another way.

Be careful which ones you delete. For example, if you can boot the newest kernel now, even with errors, delete the oldest one, and just one should be enough for now. Then see if you can finish the update process.[/B] 

And unless you have specific reason to use /boot, I recommend not to use separate /boot partition anyway, it's pointless. As I said, unless you really need to use it on your machine. Don't use it just because you've seen a tutorial that you can use separate /boot, only if you really need it.

+1.

You may wish to follow this thread: [http://ubuntuforums.org/showthread.php?t=1489924](http://ubuntuforums.org/showthread.php?t=1489924).

---

### Post by ramnarayan on 2010-06-28
> **darkod said:**
> This has nothing to do with grub2. Why do you people keep blaming it for every silly thing you do, because it's the new "kid on the block"? 

Accepted, its just that the new grub is more difficult to manage

> **darkod said:**
> 
Your problem is that YOU didn't make sure to have enough space on /boot before starting to install/update the new kernels.
YOU didn't remove older kernels from time to time. Did you think those 100MB will last forever? 

Actually i thought it would - because forever was until the next Ubuntu version (unfortunately i haven't upgraded and thus the problem)

> **darkod said:**
> 
It's not grub2 that keeps older kernels, it's the ubuntu OS. And it does keep them until you remove them. They should design it to remove them automatically? What is someone doesn't want them removed? 

You can try the manual delete you mentioned, and hopefully that should allow you to finish the dpkg --configure -a process. I'm not sure it's the best thing to do, but it seems as one of the options if you can't remove the kernels another way.

Be careful which ones you delete. For example, if you can boot the newest kernel now, even with errors, delete the oldest one, and just one should be enough for now. Then see if you can finish the update process.


Thanks for the tips, i think its a risk but if it fails i have a separate /home and am sitting next to a broadband connection so i should be able to reinstall 10.04 (maybe the latest mint)
 
> **darkod said:**
> 
And unless you have specific reason to use /boot, I recommend not to use separate /boot partition anyway, it's pointless. As I said, unless you really need to use it on your machine. Don't use it just because you've seen a tutorial that you can use separate /boot, only if you really need it.

Always seemed like there was good reason - but the reasons are fast shrinking - 

On an aside i have been having problems with Ubuntu's ability to pick up preinstalled Wincedows OS - in 4 recent dual boot installs without fail Ubuntu 10.04 has failed to recognize a preinstalled Windows 7 (or Vista) and has left me a bit redfaced at Ubuntu's (grub's) ability  , Can't help wondering what is going wrong. 

thanks
ram

---

### Post by Elfy on 2010-06-28
I'd try clearing the trash and apt cache before I tried manually deleting files

sudo apt-cache autoclean or sudo apt-get clean

---

### Post by ramnarayan on 2010-06-28
> **forestpiskie said:**
> I'd try clearing the trash and apt cache before I tried manually deleting files

sudo apt-cache autoclean or sudo apt-get clean

already did that
$ sudo apt-get clean 

however my /boot does not get affected by this

/dev/sda5              99M   93M  693K 100% /boot

**
am wondering if i could use a live cd to increase the size of the /boot partition.

ram

---

### Post by Elfy on 2010-06-28
> **ramnarayan said:**
> already did that
$ sudo apt-get clean 

however my /boot does not get affected by this

/dev/sda5              99M   93M  693K 100% /boot

**
am wondering if i could use a live cd to increase the size of the /boot partition.

ram
Yea that was a bit of a d'oh moment from me - sorry.

You coudl use a livecd to increase the size.

---

### Post by ramnarayan on 2010-06-28
> **forestpiskie said:**
> Yea that was a bit of a d'oh moment from me - sorry.

You coudl use a livecd to increase the size.

Thats ok, all of us are in the either early morning or late night moment - what with world cup and Wimbledon on at the same time.

Will try out expanding the partition a bit later, i actually have set aside enough space (more than enough rather) for a second OS - so if something goes wrong will just do a fresh install of Mint or Ubuntu 10.04 ;)
 
ram

---

### Post by ramnarayan on 2010-06-29
Problem with low disk space on /boot is solved

Got help from another Ubuntu mailing list i am on

There were two suggestions 
using dpkg -r linux .......
and in this to find the oldest linux headers that were available

so on double tabbing i got 

```

$ sudo dpkg -r linux-headers-2.6.31-
linux-headers-2.6.31-14    
linux-headers-2.6.31-15              linux-headers-2.6.31-20
linux-headers-2.6.31-16              linux-headers-2.6.31-20-generic-pae
linux-headers-2.6.31-16-generic-pae  linux-headers-2.6.31-21
linux-headers-2.6.31-18              linux-headers-2.6.31-21-generic-pae
linux-headers-2.6.31-18-generic-pae  linux-headers-2.6.31-22
linux-headers-2.6.31-19              linux-headers-2.6.31-22-generic-pae
linux-headers-2.6.31-19-generic-pae  linux-headers-2.6.31-9-rt
ram@ram-laptop:~$ sudo dpkg -r linux-headers-2.6.31-
linux-headers-2.6.31-15              linux-headers-2.6.31-20
linux-headers-2.6.31-16              linux-headers-2.6.31-20-generic-pae
linux-headers-2.6.31-16-generic-pae  linux-headers-2.6.31-21
linux-headers-2.6.31-18              linux-headers-2.6.31-21-generic-pae
linux-headers-2.6.31-18-generic-pae  linux-headers-2.6.31-22
linux-headers-2.6.31-19              linux-headers-2.6.31-22-generic-pae
linux-headers-2.6.31-19-generic-pae  linux-headers-2.6.31-9-rt


```

So i used
```

$ sudo dpkg -r linux-headers-2.6.31-14
(Reading database ... 671073 files and directories currently installed.)
Removing linux-headers-2.6.31-14 ...
laptop:~$

```

and now things seem back to normal

***
it seems dpkg is able to rifle through things that apt-get is prevented from so quite useful to know

so am now going to remove a few more of the old kernels and then do a reboot and see if my system is still all hunky dory

ram

---

### Post by varunendra on 2010-06-29
Very useful post Ram! Thank you for this.

Please mark the thread as [Solved] now as the original problem is solved. It helps others struggling with same problem.

---

### Post by ramnarayan on 2010-06-29
> **varunendra said:**
> Very useful post Ram! Thank you for this.

Please mark the thread as [Solved] now as the original problem is solved. It helps others struggling with same problem.

Hi

Actually i did mark it as solved ?? but it ain't fully solved here is the second part of the solution

** 
Well maybe it worked but partially

my boot still was at 100 % usage and on rebooting this status did not change

so went to synaptic and tried to get rid of yet another older kernel

the process got stopped with the first error message - not enough space

so this time i went into /boot via sudo nautilus and deleted files
that had to do with 2 of the older uninstalled kernels

dpkg did uninstall but not physically remove it. So no new space was created.

So understanding this i dpkg -r one more linux kernel and have
physically removed  some more stuff from /boot now reading only 78 $%
usage

so after this through synaptic am removing  some of the other older kernels

IF removed through synaptic there is a clear and direct creation of space in /boot

it seems i have from 2.6.31-16 through to .22 installed - thats quite a bit

so have uninstalled till-19 an now have about 55 % space in /boot
ram

---

### Post by ramnarayan on 2010-06-29
Aha

How does one mark a thread as "solved"

searched and have not found anything

i know from the past its supposed to be quite simple like right clicking on something ??

help me mark this one as solved

ram

---

### Post by arpanaut on 2010-06-29
At top of posts in red "Thread Tools"
Prety ovious from there 

FYI you probably only need 2 or so kernels installed, current and one previous just in case.

---

### Post by ramnarayan on 2010-06-29
> **arpanaut said:**
> At top of posts in red "Thread Tools"
Prety ovious from there 

FYI you probably only need 2 or so kernels installed, current and one previous just in case.

Thanks , now its so obvious, though i hope some one puts it in the FAQ

Regarding Number of kernels - yes have kept the previous 3 - but will go about uninstalling the oldest of the 3

thanks
ram

---

