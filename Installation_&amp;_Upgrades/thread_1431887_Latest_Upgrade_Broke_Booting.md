---
title: "Latest Upgrade Broke Booting"
date: 2010-03-17
forum: Installation &amp; Upgrades
---

### Post by raashell on 2010-03-17
I just did the latest upgrade in 9.10 via the update manager and it required a reboot.  When I rebooted Ubuntu failed to load.  In recovery mode it fails saying that it can't find my root device and has some suggestions about what might be wrong.  I looked at the file it listed in /proc/something and the devices available by uuid in /dev/ and what's listed in /proc/something isn't in dev.  I haven't made any changes yet for fear of causing worse damage.  The shell it bumps to is ASH and it doesn't look to have much editor support to make changes to the proc file(ECHO > ?).  Is there a safer way to get my system back online?

I'm running 9.10 AMD64 on a Dell Inspiron laptop with a dual boot to Windows 7 (For browser testing web apps/sites)

---

### Post by jimeikner on 2010-03-17
Similar problem here. Today's update to 2.6.31-20-generic on a Dell Inspiron 5305 64-bit fails to find the kernel. Reverting to 2.6.31-14-generic boots as expected.

---

### Post by raashell on 2010-03-17
Unfortunately, none of my kernel options boot.

The message is:

"Gave up waiting for root device
Common problems..."

"... ALERT! /dev/disk/by-uuid/69845... Does Not Exist!"

---

### Post by reiniheini on 2010-03-17
same issue here. after update booting leads to black screen and then an automatic reboot.

---

### Post by nerdy_kid on 2010-03-17
ive had this happen to me a couple times (only the other kernels would boot).  Booting off a LiveCD and updating GRUB should fix it.

---

### Post by raashell on 2010-03-17
So I tried to update grub and re-run setup in grub via the live cd.  I kept getting error messages and thought that nothing had worked, when I rebooted though, I was back in.  Unfortunately, it was somewhat of a hundred monkeys, hundred type writers approach, so I can't say for sure what worked.

I think, most likely, it was mounting the partition and running grub-setup with it pointed at the mount and the device. (Like I said though, this, and everything else, returned errors).

I was loosely following the instructions here:

[https://help.ubuntu.com/community/Grub2#line-724](https://help.ubuntu.com/community/Grub2#line-724)

---

### Post by reiniheini on 2010-03-18
no luck here. grub reinstall did not help. grub seems to work fine. i can see the white ubuntu logo for a few seconds. when the ubuntu login screen should appear i only get a black screen and a reboot.
booting to recovery mode gives me a messed up recovery menu where no action leads to anything.

---

### Post by Will.V.King on 2010-03-18
I updated my  Ubuntu 20 ours ago. And first after a restart, the newest kernel (2.6.31-20,which has been used for days and works good) can't be load. error:"You need to load the kernel first" when choose the newest kernel to boot.
then booting to the older kernel and reinstall the newest kernel, then even the booting list is also disappeared. The Grub version is 1.97 ~4beta... It seems still not 2. 
Now I have reinstalled the whole ubuntu. And I won't choose to update (At least in a month).

PS: my Ubuntu is running in wubi.

---

### Post by moon_raker on 2010-03-18
Am dual booting with Ubuntu Hardy 8.04 using the chainloader +1 method to boot Karmic from Hardy.
Luckily I had made a bootable Grub2 CD so was able to boot into Karmic. First thing I did was to run the boot info script which told me core.img could not be located. See below:-

sdb1: _________________________________________________________________________

File system: ext4
Boot sector type: Grub 2
Boot sector info: Grub 2 is installed in the boot sector of sdb1 and 
looks at **sector 5281543** of the same hard drive for 
core.img, [B]but core.img can not be found at this 
location.[/B]
Operating System: Ubuntu 9.10
Boot files/dirs: /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img


(Before kernel update it looked like this:-

File system: ext4
Boot sector type: Grub 2
Boot sector info: Grub 2 is installed in the boot sector of sdb1 and 
looks at **sector 5281543** of the same hard drive for 
core.img, core.img is at this location on /dev/sdb and 
looks on partition #1 for /boot/grub.
Operating System: Ubuntu 9.10
Boot files/dirs: /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img)

So from within the running Karmic OS I reinstalled grub2 using the command sudo grub-setup --force /dev/sdb1 (for install to the partition boot sector of sdb1).
Now the Grub2 menu displays when selecting Karmic on boot-up, but the 'Grub Loading..' message shows for about 10 secs. before the menu is displayed and the hdd sort of churns, for want of a better word, during those 10 secs.
Running boot info script again, shows that core.img is found but now looks for UUID instead of "looks on partition #1 for /boot/grub" and looks at a different sector. See below to compare:-

sdb1: _________________________________________________________________________

File system: ext4
Boot sector type: Grub 2
Boot sector info: Grub 2 is installed in the boot sector of sdb1 and 
looks at **sector 6237455** of the same hard drive for 
core.img, [B]core.img is at this location on /dev/sdb and 
looks for 
(UUID=15fa6747-0c8f-4d00-9a57-0d0820687904)/boot/grub.[/B]
Operating System: Ubuntu 9.10
Boot files/dirs: /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img


There is obviously something that Grub2 does not like but I am not sure how to proceed.

PS. Am talking about the latest kernel update to Karmic.

---

### Post by kidoxer on 2010-03-18
> **reiniheini said:**
> no luck here. grub reinstall did not help. grub seems to work fine. i can see the white ubuntu logo for a few seconds. when the ubuntu login screen should appear i only get a black screen 

The same here - after last update GRUB is starting fine, I can choose between Ubuntu and Windows. Ubuntu starts loading, white logo shows for a few seconds and then the only thing i get is a black screen. Nothing else happens, not even it reboots automatically. Only it seems that this black screen produces some considerable CPU load as the fan starts to spin faster.

Reinstalling GRUB from LiveCD had no effect.

It's a standard 9.10 Ubuntu x64 running on AMD Phenom II x955 and XFX ATI HD5770 installed on ECS A790GXM-AD3 motherboard.

---

### Post by moon_raker on 2010-03-19
OK - all fine now. I decided to run grub-install /dev/sdb1
This runs grub-probe, makes a new device map, builds a new core.img and calls grub-setup to install the grub boot.img and the core.img
Then grub-mkconfig -o /boot/grub/grub.cfg (for new grub config file)

Now I no longer have the probs. mentioned previously and grub is my friend again.

---

### Post by reiniheini on 2010-03-20
upgrading my ati-radeon driver solved the problem. i was able to access my ubuntu by adding the line "vga=normal" to grub.

---

### Post by kidoxer on 2010-03-21
> **reiniheini said:**
> i was able to access my ubuntu by adding the line "vga=normal" to grub.

Could you please explain how to do that on GRUB 2? VGA= seems to be deprecated. There is GRUB_GFXMODE= instead but setting the resolution with that command didn't resolve the problem - I still got black screen few seconds after the Ubuntu logo appears. All I noticed was different resolution (the one I set) in GRUB menu at booting.  

Oh and which version of ATI driver did you use? I was running 10.2 at the time Ubuntu committed suicide with an update.

---

### Post by reiniheini on 2010-03-21
my driver version was 10.1 and i have no idea how to do vga=normal in grub2. i am no ubuntu-expert. can somebody else help?

---

### Post by fbicknel on 2010-03-21
This looks like the right thread to share this:

I have two Karmic installations: one on an HP dv6000 laptop and the other on a home-built AMD+M2NPV-VM setup which I use for MythTV.

The laptop usually gets upgraded first so that I'm less likely to lose the Mythbox setup (don't want to be without TV, ya know.)   So when I upgraded successfully to 2.6.31-20-generic #57, I thought all would go smoothly.  No... the mythbox failed to boot just as many of you have previously described.

The main differences between the two are: the laptop is Intel, the mythbox is AMD.  Nah.  The laptop is a one-disk setup, the mythbox has raid1 on both /boot and /root.  Maybe.  But I never was able to prove it.

I managed to get back to my level 0 dump of /, which was an interesting adventure, as it changed the UUID of my root disk.  Some fiddling with grub fixed that, however.  An old 9.04 hard disk partition made booting and testing much less painful than waiting for the CD to boot.

After getting my pre-upgrade image to boot, I tried upgrading again.  Same result.  However, I was able to use grub from my /boot partition without any problems.  I discovered I was able to boot the old 2.6.31-19 kernel ok, so  that's what I did for a week.  See aforementioned importance of TV.

When I booted recovery mode, I could see the errors many of you posted previously about not being able to find the root device.  I  did several double-checks of UUIDs, but no discrepancies showed up.  I theorized that maybe it was unable to find the root device because it was RAID, but I never could figure out whether that was the case or not.  

So fast forward to today.  When I saw that there were several updates dealing with the kernel - moving to 2.6.31-20 #58, I figured maybe someone found some problems and fixed them.

Happily, I am glad to report that seems to be the case.  #58 fixed whatever was ailing my mythbox install.

---

### Post by MarioA on 2010-05-02
Try this, it worked for me:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

