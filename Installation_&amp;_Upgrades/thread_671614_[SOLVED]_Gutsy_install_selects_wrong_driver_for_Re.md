---
title: "[SOLVED] Gutsy install selects wrong driver for Realtek RTL8111C"
date: 2008-01-18
forum: Installation &amp; Upgrades
---

### Post by deanfred on 2008-01-18
****
This is not the same problem as discussed in several threads about dual boot with Windows XP and how it disables the ethernet device on exiting Windows XP!!!
*****

I put together a new PC with integrated GbE on the motherboard.  I installed Ubuntu 7.10 and It failed when trying to DHCP.  I went ahead and manually configured the IP addresses with known good addresses.  There was no Ethernet availability.  The link light is on, but never any blinking lights on the status LEDs on my switch (or motherboard NIC connector) to indicate activity.  I then wiped out the Ubuntu installation and partition and installed Windows XP to confirm the hardware was working and to update all the drivers and BIOS on the motherboard.  All is working correctly in Windows XP Pro, with full connectivity.  I reinstalled Ubuntu, with the same failed Ethernet results as before.

I would appreciate ANY pointers, but I read several posts and ran the lspci and lsmod commands.  To be brief, I believe the problem is that Gutsy is selecting the wrong Ethernet driver for the RTL8111C that is on my motherboard.  It picks r8169, which is incorrect.   I went to Realtek's web site and they have an updated linux driver (for kernels 2.6.x and 2.4.x)  for the RTL8111C, which is part of a series of several chips which include RTL8111B/RTL8168B/RTL8111/RTL8168/RTL8111C.  It looks like when it's all done, the driver that *should* be loaded is r8168 (NOT r8169).

I followed the instructions in the update and was able to tar the archive, make clean, make install, depmod, and insmod the results.  After that, lsmod showed r8168 AND r8169 loaded.  I did a rmmod r8169 and it showed only r8168.  The problem is, I don't know where to go from there.  I tried rebooting and I see that r8169 is listed when I right-click the ethernet icon and view the properties.

Can anyone speak to whether there is a bug in Gutsy in the driver installation for this chip?  How can I fix the problem and get my ethernet working?  A detailed description of what to do is asking a lot, I know, but I'm a newbie and don't know Linux/Ubuntu very well.  If you could provide that, it would help me (and those who have yet unanswered queries on this topic) immensely!

Thanks!
Dean

---

### Post by deanfred on 2008-01-19
OK, it's fixed!  I did one thing I had never done until now: wait!

I don't know how or why, but after posting this message I gave up and went to watch TV for a couple of hours with the family.  When I came back, it was working!(?)  One of those rare times when watching TV was time well-spent!  :)

If anybody has ideas of what happened, I would love to hear them.  I didn't see waiting for two hours as part of the installation procedure!

---

### Post by deanfred on 2008-01-20
NOT SO FAST! :confused:

It's broken again.  I installed Samba, and had everything working on my network.  I had attached an external drive to copy the files to be served to this machine.  I then rebooted and ...no Ethernet.  I rebooted a dozen times.  I tried unplugging the pc and unplugging the Ethernet cable, letting it sit for 30 minutes.  I tried plugging the Ethernet in first, then power, and vice-versa.  I tried, as one suggestion I saw, forcing the on-board Ethernet to boot from the ROM.

NOTHING gets it working, except booting up under Windows XP, where it works fine.  The first OS I used on this system was Ubuntu, so I KNOW this isn't a problem of Windows leaving the hardware in some unusable state.  (And, by the way, Windows has no problem bringing it back up EVERY time!)

It is clear that this is an intermittent problem, and I was lucky a couple times.  I did right click the network connection icon after it successfully DHCPd that one time: it claims to be using r8169 (which is *supposed* to be the wrong driver.

I'm getting few views, and NO replies to this thread.  Is that nobody believes me, or nobody knows how to fix this?  It's really quite frustrating and similar questions on the forums have gone unanswered.

Thanks for any help you can give!
Dean

---

### Post by jio23 on 2008-01-20
Hi Dean,

You seem to have a similar problem to me, as you spotted.  I have updated my thread with details of my efforts this morning.  They didnt work for me.  However, your problem may be different, and they may help you out.  Here's as link to my entry which tells you what i did:

[http://ubuntuforums.org/showthread.php?p=4174201&posted=1#post4174201](http://ubuntuforums.org/showthread.php?p=4174201&posted=1#post4174201)

Hopefully this will do the trick for you.

You probably got no reply yet because of the weekend.  There are plenty of people out there who check these boards and help out.

John

---

### Post by deanfred on 2008-01-21
John,
I followed your instructions and all went well, except it didn't work!
The blacklist of r8169 didn't work...lsmod still shows them both.  I found a link that appears to say that blacklisting isn't working...

[https://bugs.launchpad.net/ubuntu/+source/module-init-tools/+bug/133434](https://bugs.launchpad.net/ubuntu/+source/module-init-tools/+bug/133434)

Geeze, I didn't think this would be easy, but it's like a brick wall!

Oh, your detailed instructions are VERY welcome and helpful (thank you!) but there are a couple of typos you might want to fix regarding the 8169.  The numbers were transposed differently in a couple of spots.  Anyway, I am still hammering away at this.  I used the latest driver for my chip (RTL8111C) that was on the Realtek site, not the one you listed (my chip is different but still won't work with the 8169 driver).

Thanks for all the help.  Sure wish I could get this to work.

Dean

---

### Post by Globemaster on 2008-01-26
I had the same problem. I had to use Google for a long time, till i found a solution in a german forum (i am from germany; sorry for my english if it's too bad). Here are the instructions:

First, you need to rename the r8169 driver, because it won't work with this one.

> mv /lib/modules/`uname -r`/kernel/drivers/net/r8169.ko /lib/modules/`uname -r`/kernel/drivers/net/r8169.ko.old
> depmod -a

To save the current ramdiscimage and make a new one:
> mv /boot/initrd.img-`uname -r` /boot/initrd.img-`uname -r`.old
> mkinitramfs -o /boot/initrd.img-`uname -r`

Now you have to reboot. After this, it worked for me. To see weather the right module is loaded, you can use this:
> lsmod | grep r81*

There it showed me the right module, r8168.

Maybe it helps you, too.

Globemaster

---

### Post by deanfred on 2008-01-27
Globemaster,
THAT WORKED!!!!  Finally!  I did manage to break my Ubuntu installation first...anyone who does this be careful not to make my error (* below):

[LIST=1]
[*]Download the the updated driver from Realtek at [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2)
[*]Follow the instructions in the Realtek readme.
[*]Follow Globemaster's instructions in this thread.
[*]Reboot.
[/LIST]

*My error: When I did the mkinitramfs, I used the tab key to fill out the long name for the kernel.  This method adds a "." to the end.  When my PC rebooted, it couldn't find the ramdisc and I had to boot from the installation CD, fix the error, and then I was able to recover.

Note that when you do the lsmod | grep r81*, it will list BOTH drivers until you reboot.  After you reboot, it uses the correct driver, r8168.

Thanks to everyone who helped and gave suggestions, with my greatest thanks to Globemaster who added the needed final steps!
Dean

---

### Post by skaura on 2008-01-28
If I could give you guys a kiss -- I would!!! Thanks for the useful posts!!!

---

### Post by kc600 on 2008-01-30
Same here. Thanks, guys!

---

### Post by Bodai on 2008-01-30
Same applies for RTL8169
Thnks boys.Great job=D>=D>=D>

---

### Post by Globemaster on 2008-01-30
No problem. For the completeness: the original source is [http://www.vdr-portal.de/board/thread.php?postid=688040](http://www.vdr-portal.de/board/thread.php?postid=688040)

I hoped it would help somebody.

Globemaster

---

### Post by Ralakan on 2008-02-20
I'm having some major issues with the same card (on-board) and I'm a little confused as to how to continue.  

I followed the instrcutions from RealTek, but had to "down" the eth0 in order to rmod r8169

after doing the realtek instructions, I could not ifconfig eth0 up (not found)

I then tried to follow Globemaster's instructions, but lsmod | grep r81* returns nothing... just another command line.  Now the adapter is gone and I can't seem to do anything with it.  

Any ideas?  Or data I can provide to help.  ifconfig is no longer reporting an eth0 at all

yes, I'm a newbie, trying to learn as fast as I can.

---

### Post by tr333 on 2008-02-24
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/141343](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/141343) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				If this helps, I managed to get ethernet working with the r8169 driver by adding the option "pci=nomsi" to the boot options for the system.

---

### Post by Ralakan on 2008-02-25
I figured it out, I had a syntax error.  Being new, I didn't know uname  meant your kernel name.

---

### Post by Nordkraft on 2008-03-10
Thanks for the how-to :)

Ive followed the instructions (i.e. follow the Realtek instructions and then the ones from Globemaster). lsmod gives me r8168 but there is absolutely no internet connection. Currently, Im running a 7.04 Live disc and everything works fine. Does anyone have an idea about how I might fix this?

Thanks

---

### Post by tr333 on 2008-03-10
I have tested the latest hardy alpha and this issue seems to be fixed.

---

### Post by Ron Petch on 2008-03-14
I had the same problems, no connection between the router and the computer of connection and no handshaking and connection after waiting for an hour or so! There may be a hardware problem, it has to warm-up of boots too fast?
I found a solution via [http://wiki.centos.org/HardwareList/RealTekRTL8111b](http://wiki.centos.org/HardwareList/RealTekRTL8111b).
The RealTek download from choice 2 gave me the tar bzipped file. The installation instructions work.
I have tested by coldstarting in Ubuntu and had success - it doesn't depend on Windows XP setting the port.

regards Ron Petch

---

### Post by Globemaster on 2008-06-10
> **tr333 said:**
> I have tested the latest hardy alpha and this issue seems to be fixed.

I can confirm, that the bug is fixed in the final Ubuntu 8.04.

Globemaster

---

