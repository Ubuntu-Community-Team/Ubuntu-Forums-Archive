---
title: "Upgrade to 10.4 - general error mounting filesystems"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by JC Denton on 2010-05-17
Hello All,
Using upgrade manager I upgraded my 8.x LTS installation to 10.4. After rebooting the system failed to reboot and dropped to the recovery consolte.
It appeared to be a problem caused by ureadahead as described here: [http://ubuntuguide.net/howto-fix-ureadahead-problem-after-upgrading-to-ubuntu-10-04](http://ubuntuguide.net/howto-fix-ureadahead-problem-after-upgrading-to-ubuntu-10-04). So I renamed ureadahead.conf to ureadahead.moved (after remounting the partition rw). this did not help so I renamed the file back again.

After rebooting the following error appears:

ureadahead terminated with status 5.
udev_monitor_new_from_netlink: error getting socket: Invalid Argument
mountall:mountall.c:3204 assertion failed in main: udev_monitor = udev_monitor_new_from_netlink(udev,"udev")
init: mountall main process (2532) killed by ABRT signal.
General error mounting filesystems

How will I get my system to boot again properly? thanks

_____________________________

following instructions from here sort of helped: [http://www.linode.com/forums/viewtopic.php?p=28115](http://www.linode.com/forums/viewtopic.php?p=28115) . the only problem was it configured my grub menu incorrectly. Edited the menu.lst to point to the right hd but the id's don't seem to match

Grub:

gave up waiting for root device:
alert /dev/disk/by-uuid/[id] does not exist. Dropping to a shell

---

### Post by hufemj on 2010-05-17
> **JC Denton said:**
> Hello All,
Using upgrade manager I upgraded my 8.x LTS installation to 10.4. After rebooting the system failed to reboot and dropped to the recovery consolte.
It appeared to be a problem caused by ureadahead as described here: [http://ubuntuguide.net/howto-fix-ureadahead-problem-after-upgrading-to-ubuntu-10-04](http://ubuntuguide.net/howto-fix-ureadahead-problem-after-upgrading-to-ubuntu-10-04). So I renamed ureadahead.conf to ureadahead.moved (after remounting the partition rw). this did not help so I renamed the file back again.

After rebooting the following error appears:

ureadahead terminated with status 5.
udev_monitor_new_from_netlink: error getting socket: Invalid Argument
mountall:mountall.c:3204 assertion failed in main: udev_monitor = udev_monitor_new_from_netlink(udev,"udev")
init: mountall main process (2532) killed by ABRT signal.
General error mounting filesystems

How will I get my system to boot again properly? thanks

_____________________________

following instructions from here sort of helped: [http://www.linode.com/forums/viewtopic.php?p=28115](http://www.linode.com/forums/viewtopic.php?p=28115) . the only problem was it configured my grub menu incorrectly. Edited the menu.lst to point to the right hd but the id's don't seem to match

Grub:

gave up waiting for root device:
alert /dev/disk/by-uuid/[id] does not exist. Dropping to a shell

I'm eager to find out myself. I have the exact same problem. I was upgrading from 8.04 via ssh and the system ran out of memory and hung. Now it doesn't want to mount on reboot.

Mark

---

### Post by Avionix on 2010-05-27
Hi I have just upgraded from 8.04 LTS to 10.04 LTS, the upgrade tool would apparently down load but no further instructions appeared on the screen so I copied the 10.4 ISO and tried the upgrade using the CD. I have the same problem, booting normally into 1 of the 10.4 kernels leaves me with a black screen. Screen stays active but nothing displayed.Booting into recovery mode I get the following,
init: ureadahead main process (2603) terminated with status 5
libudev: udev_monitor_new_from_netlink: error getting socket:Invalid argument.
Mountall: mountall.c:3204: Assertion failed in main: udev_monitor = udev_monitor_new_from_netlink (udev,"udev")
init: mountall main process (2606) killed by ABRT signal
General error mounting file systems
A maintenance shell will now be started

etc
 I have no idea where to go from here, pretty much still a noob, help

---

### Post by weiswang on 2010-05-27
I got the same error. :(

---

### Post by ondeaander on 2010-05-28
Me too. When I did the upgrade from 8.04 to 10.4 I encountered some warnings - mostly errors about flashplugin-nonfree not being upgraded - and at the end I got a message to the effect of: "Upgrade completed successfully but with warnings ... somethingorother may be in an unstable state .. running <some dpkg command>". Then the update window closed, and nothing happened. I couldn't see any interesting processes running so I went ahead and rebooted and my **** was broken (I must admit I wasn't that surprised). I suspect the upgrade didn't quite finish properly, and now I'm stuck in recovery mode.

So I tried fixing things up with apt-get but I kept running into the flashplugin-nonfree problem again: trying to install any packages for which it's a dependency resulted in "Package is in a very bad inconsistent state - you should reinstall it before attempting a removal". So I tried to install it again, which failed because it depends on flashplugin-installer. Then I tried to install flashplugin-installer, which in turn failed because "Package flashplugin-nonfree is in a very bad inconsistent state - Please reinstall before attempting a removal." VERY CUTE. 

Fortunately I managed to fix this after reading [http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475) 

Now I can run apt-get again (still in recovery mode), but somehow I get this uncanny feeling that I'm not connected to the internet. Guess it's something to do with all the "could not resolve host" errors :). Anyone care to share how to load up my network adapter? I read somewhere to run "ifup eth0" but that didn't do crap for me. I'm getting tired of fudging about in recovery mode so if somebody can at least tell me how to get the system back on the internet, I may be able to at least provide some more ..uhm.. "what not to do" advice. Process of elimination ;)

---

### Post by Avionix on 2010-05-30
I carried out the instructions from [http://www.linode.com/forums/viewtopic.php?p=28115](http://www.linode.com/forums/viewtopic.php?p=28115), now on bootup  I get the following : please use ATT= to match the event device or ATTRS{}to match a parent device in /etc/udrules.d/85-hplj10xx.rules:X Xbeing any one of 30 or so lines. If I page down I get a splash screen with a purple background and the word ubuntu.
I cannot get a terminal to do any thing about this, any ideas ? I have been without my main computer for over a week now I have installed an instance of 8.04 on the machine which works OK, I can see all the files and folders on the main drives but of course do not have permissions for them. I could stuff about with these but I would rather get the entire machine running on 10.4. Any help would be appreciated. Cheers,

Steve.

---

### Post by Avionix on 2010-06-02
OK, round 2, I can get nowhere with this, after downloading and installing the kernel using the info from [http://www.linode.com/forums/viewtopic.php?p=28115](http://www.linode.com/forums/viewtopic.php?p=28115) my system is completely koozed, I can not get a terminal up at all so can't do anything. In desperation I have hooked up another drive which also has 8.04 on it, I have upgraded this to 10.04, I have the same problem with ureadahead as before init: ureadahead main process (2603) terminated with status 5
libudev: udev_monitor_new_from_netlink: error getting socket:Invalid argument.
Mountall: mountall.c:3204: Assertion failed in main: udev_monitor = udev_monitor_new_from_netlink (udev,"udev")
init: mountall main process (2606) killed by ABRT signal
General error mounting file systems
A maintenance shell will now be started
I attempted to fix this as above by moving ureadahead.conf to ureadahead.conf.disable as described here: [http://ubuntuguide.net/howto-fix-ure...o-ubuntu-10-04](http://ubuntuguide.net/howto-fix-ure...o-ubuntu-10-04). 
Now I am presented with the following ;
libudev: udev_monitor_new_from_netlink:error getting socket: invalid argument mountall: mountall.c:3204: Assertion failed in main: udev_monitor = udev_monitor etc etc
init: mountall main process (2639)killed by ABRT signal
General error mounting filesystems etc 
Can anyone give me an idea where I can go from here?
Can I just forget about udev and comment it out somewhere??

Any help would be appreciated.

Steve:confused:

---

### Post by Avionix on 2010-06-02
Never mind that last comment I'm confusing udv with ureadahead.

---

### Post by Avionix on 2010-06-03
Could I re-install udev from the net? How would I do that?
sudo apt-get reinstall /lib/udev  ??:confused:

---

### Post by lightninlouie on 2010-06-07
I'm also having this exact problem after upgrading from Hardy Heron to Lucid Lynx (10.04 LTS). Haven't been able to solve it yet, and my laptop is down for the count. Hopefully this gets figured out soon. I'll keep trying, and checking back here. 

-L

---

### Post by mbernstein on 2010-06-15
I've also got the same issue after upgrading from 8.04.  There was nothing unusual about the upgrade, but now I get stuck at this point on every reboot (okay, I can get everything running to a fashion by entering the recovery console, but it's not ideal).

Has anyone had any more luck?  I'll report back if can get anywhere with this...

---

### Post by mbernstein on 2010-06-16
I've resolved my boot issues. There's no guarantee the cause is the same, but in case it's of use to anyone still with the problem (or who encounters the problem and finds this thread), this is what was wrong in my case:

On the previous version, my boot partition was noauto, i.e. it was not automatically being mounted under /boot at startup.  I didn't think to do so manually before running do-release-upgrade, so when that process copied in the new kernel and initramfs, they were copied into an unmounted /boot (i.e. a folder of my root partition and not the root of my boot partition).

Something in the user userspace udev stuff was clearly not happy with the udev support in my old kernel, hence the errors.  I moved the stuff it had put into the "fake" /boot into the live one, re-ran the grub installer, and all was well...
 
:-)

---

### Post by Avionix on 2010-06-18
Re: Upgrade to 10.4 - general error mounting filesystems
I've resolved my boot issues. There's no guarantee the cause is the same, but in case it's of use to anyone still with the problem (or who encounters the problem and finds this thread), this is what was wrong in my case:

On the previous version, my boot partition was noauto, i.e. it was not automatically being mounted under /boot at startup. I didn't think to do so manually before running do-release-upgrade, so when that process copied in the new kernel and initramfs, they were copied into an unmounted /boot (i.e. a folder of my root partition and not the root of my boot partition).

Something in the user userspace udev stuff was clearly not happy with the udev support in my old kernel, hence the errors. I moved the stuff it had put into the "fake" /boot into the live one, re-ran the grub installer, and all was well...                                                                   


Can you explain how you did this ?, how did you see it was 'noauto'   Still pretty much a newbie.I would appreciate your help.

---

### Post by RichMom on 2010-07-03
Hello, I upgraded to Lucid from Hardy and had this same issue.
Please could anyone give more directions on what mbernstein did to solve it?
Plain language for newbies thank you ^__^

---

### Post by mcilroy_je on 2010-09-24
For me the reason for this was that chose during installation to update grub's menu.lst myself, but I never did. Once I corrected menu.lst, all was well. mcilroy_je

---

### Post by lightninlouie on 2010-09-27
OK, so this damn problem has put my linux computer out of commission since upgrading to 10.04 several months ago. Believe me, I scoured every forum and tried every other suggested solution out there. Thanks to mcilroy_je for turning me onto what finally turned out to be the fix.

For any other newbies like me, here's a more detailed description of what to do. 

If you're getting an error something like:
[I]
ureadahead terminated with status 5.
udev_monitor_new_from_netlink: error getting socket: Invalid Argument
mountall:mountall.c:3204 assertion failed in main: udev_monitor = udev_monitor_new_from_netlink(udev,"udev")
init: mountall main process (2532) killed by ABRT signal.
General error mounting filesystems[/I] 

I suggest rebooting using CTRL-SHIFT-D, and logging into your recovery shell.
Then, try typing at the prompt: 
*locate menu.lst*

If your problem was anything like mine, you'll probably see something like 
[I]/boot/grub/menu.lst
/boot/grub/menu.lst~
/usr/share/doc/grub/examples/menu.lst/usr/share/doc/memtest86+/examples/grub-menu.lst
/var/lib/ucf/cache/:var:run:grub:menu.lst[/I]

The /boot/grub/menu.lst was my menu.lst from Ubuntu 8.04 (what I was using before the upgrade); I took a look at it (*less /boot/grub/menu.lst*) and sure enough, I could tell it hadn't been changed by the upgrade. Same old kernels, no changes to my dual boot instructions at the bottom of the file. Some example menu.lst files in /usr/share didn't seem weird. But the one in /var/lib/ did seem pretty odd. So I looked at that (*less /var/lib/ucf/cache/:var:run:grub:menu.lst*) and sure enough, it looked like a newer version of menu.lst. 

So, I wanted to try moving the menu.lst in /var/lib to the boot directory and try rebooting, in case the upgrade to 10.04 had mistakenly put the new menu.lst file in the wrong place. To be safe, I first moved /boot/grub/menu.lst to /boot/grub/menu.lst.save: 

*mv /boot/grub/menu.lst /boot/grub/menu.lst.save* 

Then I copied the other menu.lst into the grub directory: 

*cp /var/lib/ucf/cache/:var:run:grub:menu.lst /boot/grub/menu.lst*

Then I rebooted (CTRL-SHIFT-D), and voila, successful upgrade to Ubuntu 10.04. Hope this works for you. If you continue to get errors related to flashplugin-nonfree, you might try following the instructions at the top of [http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475) first. 

Cheers, and hope this helps someone. 

-Lewis

---

### Post by MatteoTaiana on 2010-11-18
Hello everybody,
I see that this thread is quite old, I hope you solved your problems one way or the other. But, well, I run into the problem today and I just managed to solve it (in my particular case), so I'm posting my solution hoping it can be helpful if someone runs in the same problem in the future.

Just to give you some context, I upgraded Ubuntu 8.04 to 10.04 on a server machine, through ssh. Everything seemed to have worked, but at reboot the computer got stuck complaining about **ureadahead** being terminated with status 5 and about a **General error mounting filesystems**.

In my case it was sufficient to add a few options to the boot line in GRUB (and then in menu.lst, to make the change permanent) to make the computer boot normally.

This was the line of menu.lst when it didn't work:
>kernel     /boot/vmlinuz-2.6.32-25-server  root=UUID=c2f70199-ae76-4e5f-9401-4c18ca0cda91 ro quiet splash 

And this one is the line in the version that works
>kernel     /boot/vmlinuz-2.6.32-25-server  root=UUID=c2f70199-ae76-4e5f-9401-4c18ca0cda91 ro quiet splash acpi=off  noapic nolapic nomodeset

I'm almost sure that the "nomodeset" option has nothing to do with the problem, but I don't have time to confirm that now.

Ciao,

Matteo

---

### Post by MatteoTaiana on 2010-12-07
Hey guys,
I got a better understanding of what is happening on our server.

The kernel option that matters for our case is "**nolapic**": the kernel gets stuck if started without it.
This options tells the kernel to only use one of the cores of the CPU (we have 8 cores on that machine) and, of course, this is something we do not like.

We updated the BIOS, but the problem persisted.
At the moment we are wondering whether it is a hardware problem that's causing the kernel to get stuck, because the same kernel boots normally on a machine that's an exact copy of the one I'm talking about.

ciao,

Matteo

---

### Post by exiledone on 2010-12-27
Just a quick note to say this solution worked for me. Since menu.lst had not been updated, it had to be manually changed.

One additional complication I had was that I could not modify menu.lst when in recovery mode. I kept getting a 'Read Only File System' error. I was able to press 'e' from the grub menu and edit the boot command there. Then, once Ubuntu booted correctly, I could then change the menu.lst.

One lesson learned from my first upgrade.

---

### Post by The Hypnotoad on 2012-08-27
> **exiledone said:**
> Just a quick note to say this solution worked for me. Since menu.lst had not been updated, it had to be manually changed.

One additional complication I had was that I could not modify menu.lst when in recovery mode. I kept getting a 'Read Only File System' error. I was able to press 'e' from the grub menu and edit the boot command there. Then, once Ubuntu booted correctly, I could then change the menu.lst.

One lesson learned from my first upgrade.

Hi

I have the exact same issue as this, could you (or anybody) do a step by step guide showing what you did to boot ubuntu from the boot command?


thanks

---

### Post by The Hypnotoad on 2012-08-27
Can anybody help with this.

I updated to 10.4 today and I have the exact same issue as [lightninlouie]("http://ubuntuforums.org/member.php?u=1091349") but when I do either 


*mv /boot/grub/menu.lst /boot/grub/menu.lst.save* 

or

*cp /var/lib/ucf/cache/:var:run:grub:menu.lst /boot/grub/menu.lst*

it comes up saying read Only File System' error. The PC is one of my works PCs so im in a bit of a desperate situation

---

### Post by The Hypnotoad on 2012-08-27
> **MatteoTaiana said:**
> Hello everybody,
I see that this thread is quite old, I hope you solved your problems one way or the other. But, well, I run into the problem today and I just managed to solve it (in my particular case), so I'm posting my solution hoping it can be helpful if someone runs in the same problem in the future.

Just to give you some context, I upgraded Ubuntu 8.04 to 10.04 on a server machine, through ssh. Everything seemed to have worked, but at reboot the computer got stuck complaining about **ureadahead** being terminated with status 5 and about a **General error mounting filesystems**.

In my case it was sufficient to add a few options to the boot line in GRUB (and then in menu.lst, to make the change permanent) to make the computer boot normally.

This was the line of menu.lst when it didn't work:
>kernel     /boot/vmlinuz-2.6.32-25-server  root=UUID=c2f70199-ae76-4e5f-9401-4c18ca0cda91 ro quiet splash 

And this one is the line in the version that works
>kernel     /boot/vmlinuz-2.6.32-25-server  root=UUID=c2f70199-ae76-4e5f-9401-4c18ca0cda91 ro quiet splash acpi=off  noapic nolapic nomodeset

I'm almost sure that the "nomodeset" option has nothing to do with the problem, but I don't have time to confirm that now.

Ciao,

Matteo

Tried this but still got the same error

---

### Post by oldos2er on 2012-08-28
exiledone hasn't visited the forums since Dec. 2010; please start a new thread per the posting guidelines:

"If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful."

---

