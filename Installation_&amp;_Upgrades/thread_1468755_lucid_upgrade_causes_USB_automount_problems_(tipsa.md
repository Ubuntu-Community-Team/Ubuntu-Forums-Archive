---
title: "lucid upgrade causes USB automount problems (tips/advice)"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by euchrid on 2010-05-01
I had some trouble after upgrading to Lucid Lynx (10.04) where my USB drives would automount, but were only available to root. Hopefully, this post will help others with similar problems.

I use Thunar file manager, not Nautilus or Dolphin or anything else except Midnight Commander. Thunar automounts using HAL - but HAL is being pushed aside in favour of udev, as I understand it.

Ultimately, I found that I had to go into Synaptic and remove the 'usbmount' package, as that was causing my USB drives to mount at /media/usb0, /media/usb1 and so on - and when mounted, it was only as root. It would seem that having usbmount and pmount and HAL causes the automount some kind of permissions problem, and so the device is only available to root.

I did NOT have the problem where nothing was automounted; USB devices were automounting fine, but only under root.

I saw a lot of advice about changing udev rules, editing /etc/fstab, changing preferences, group permissions and so on, but none of it helped - the only solution for me was to remove 'usbmount'. I hope this helps someone else Googling for the same issue.

---

### Post by yundo on 2010-05-02
Thank you so much Euchrid - this was driving me (a little bit) crazy. 
Your solution worked!
Thanks again

---

### Post by skaboss on 2010-05-02
Thanks a lot !!
At a certain stage in Lucid beta, i had to install usbmount because an update messed the automount thing, and forgot to uninstall it when the devs fixed it.

---

### Post by tmazzotta on 2010-05-02
I have a similar problem, HOWEVER, it is not due to usbmount. I upgraded 9.10 to 10.4 (released) yesterday. Running Gnome/Nautilis on desktop. Upon inserting a usb disk, nothing is automatically mounted, although if I look at the "Computer" file browser window, I do see the inserted device and I can mount it from the properties menu or by double clicking. After several hours of Google searches, I found the following post [http://ubuntuforums.org/showthread.php?p=9167961](http://ubuntuforums.org/showthread.php?p=9167961) which was closed when Lucid was released. The cause of the problem was a floppy device that is not always connected to the system. I have the same situation w/ my old Compaq Evo N410c which I had just upgraded. The floppy is part of a docking station which I rarely use. After I connected the laptop to the docking station, usb drives would automount and appear on the desktop as they had previously in 9.10.

Hope this info helps others with similar problems.

tm

---

### Post by pimseb on 2010-05-04
I've switched to Lucid Lynx and I have the same automount problem. When I plug an usb drive, I do see it under "Computer" and can mount it with a double click.However it isn't done automatically. Once the drive is mounted, I can't unmount it. I see a warning saying that I can't unmount because the device isn't listed in fstab ...
This automount problem has surely something to do with the floppy. I have a floppy0 device listed under "computer". But I don't have any floppy drive installed in my PC ... lol
This floppy drive has now disappeared because I have added # in front of floppy in /etc/fstab
BUT I still have the usb autmount problem. I don't see what I can do with my ghost floppy problem ... Maybe someone has an idea ?


EDIT : I've disabled floppy support in my BIOS and now everything is working :)

---

### Post by ngregory on 2010-05-08
Worked like a charm. Thanks so much for posting that fix.

---

### Post by H.R.Rambler on 2010-05-09
This also fixed my problem. Just for clarity's sake I'm going to describe a symptom that no one else has mentioned.

In Nautilus I was seeing two icons for my USB:
1) "contents" name of the usb (such as TRK_3-3) 
2) the mount name /usb0

Clicking on /usb0 showed me the device but it belonged only to root, clicking on the name of the device would not go anywhere.

---

### Post by timgood on 2010-05-17
I had the similar problems after an upgrade to Lucid - but in my case USB drives were not automounting and were not showing up in Nautilus either. After much pulling out of the greying hairy fibrous material, I solved the problem by uninstalling pmount, and then re-installing it together with libpmount0.0

This seems to have solved the problem. I hope this may help others in the same situation.

---

### Post by Username4 on 2010-05-18
Thanks, euchrid. Your proposed solution worked great.

I had no problems with automatic USB drives mounting (at least by PCMan File Manager) before the upgrade to 10.04. Then first time after inserting the device it began to be atomatically mounted with absolutely wrong options - owned by 'root' as already described. It also had some files with non-Latin characters to appear as "??????" so character encoding also broke. I wonder if autodetection of non-FAT filesystems got broken too.

Just removing that "usbmount" package helped. I don't think I would be able to figure out the problem without stumping by chance on this thread. Adding such raw, badly tested packages to an LTS distribution release is IMHO bad practice.

---

### Post by Bombenbach on 2010-05-20
Although I made a Lucid clean install, I also faced that USB automount problem: my USB flash drive was always autmounted to /media/disk and owned by root so that I couldn't really use it. The solution was to remove hal
```
sudo apt-get remove hal
```Don't know how I got hal installed (maybe an odd dependency), but removing it definitely solved the problem.

---

### Post by Xeroid on 2010-05-29
> **timgood said:**
> I solved the problem by uninstalling pmount, and then re-installing it together with libpmount0.0


Thanks for the above post. :)

I was having problems with mounting CDs, DVDs, or any USB devices.  I checked and **pmount** had never been installed on my PC.  I had done a clean install of 10.04.  After installing **pmount & libpmount0.0** my problem seems to have been solved.

---

### Post by jtgd on 2010-06-24
> **Bombenbach said:**
> Although I made a Lucid clean install, I also faced that USB automount problem: my USB flash drive was always autmounted to /media/disk and owned by root so that I couldn't really use it. The solution was to remove hal
```
sudo apt-get remove hal
```Don't know how I got hal installed (maybe an odd dependency), but removing it definitely solved the problem.

When I did this it also removed xubuntu-desktop.  Not really what I wanted, so I put that back and it dragged hal back again.

---

### Post by SoFl W on 2010-06-24
I have noticed differences between 10.4 and 9.10 on how automount works.  It used to be I had to type in a password to mount my Windows partition, which I didn't mind and USB drives automounted and I could use them.  With 10.4 the Windows partition was available without a password.  I found a fix for this but now my usb drives need a password as well. I don't want other users of this computer to be able to access the Windows partition but I do want them to be able to mount USB drives.

Will the above fix work for that?

---

### Post by Bagustrix on 2010-07-05
Dear All,
According to me, just remove usbmount, NO remove is needed for pmount and hal. You can combine remove them (usbmount, pmount and hal), to know the effects. It work for my machine. Thanks a lot.

---

### Post by atulkakrana on 2010-07-05
I have same problem and nothing seems to work. Strange though, USB automounts after I logout and Login.

---

### Post by danardel on 2010-07-07
many thanks timgood - your solution did solve my problem!
my ipod appeared in Nautilus, but it couldn't be neither mounted, nor unmounted.

---

### Post by alcarola on 2010-07-07
See this post: [https://bugs.launchpad.net/ubuntu/lucid/+source/udisks/+bug/536670/comments/16]("https://bugs.launchpad.net/ubuntu/lucid/+source/udisks/+bug/536670/comments/16")

---

### Post by SpyderBite on 2010-07-09
Still no luck here.. have tried three different devices, 2 different blackberries & and an iPod.. nothing automounts anymore when I plug them in like they did before upgrading to Lucid.

Tried all the fixes on the forums, google & launchpad with no luck. :(

---

### Post by deadman62 on 2010-07-11
same issue here clean install, if usb is in at boot it mounts, if not nothing.

---

### Post by SonicMetalMan on 2010-07-11
I posted earlier as to my frustration with this USB nightmare, but a REAL solution just appeared. I saw the suggestions about installing HAL if not already installed, so I just checked the repository. There is an upgrade available RIGHT NOW for HAL, I just installed it my USB drives work! 

Happiness abounds and Angels sing in praise of a real fix!

---

### Post by SonicMetalMan on 2010-07-11
Well crap, the Angels are tone-deaf. The fix was short-lived, it only worked until I rebooted. I should have known better.

OK Dev Team, why do HAL and udev not play well together? Somebody blew this up badly and it looks really embarrassing.

---

### Post by SonicMetalMan on 2010-07-11
I did much more experimenting to test what, if anything HAL had to do with the problem.

Uninstall HAL and automount works until you reboot. Reinstall HAL and automount works until you reboot. I turned off floppy support in the bios and it made absolutely no difference in automounting. I installed pcmanfm-nohal to test its automount, no dice. I dumped that and loaded the standard pcmanfm using HAL support, no dice.

This is looking more and more like a bad script or a udev issue, possibly something with permissions? I'll give this another 24 hours to find a workaround, after that I kick Ubuntu to the curb. Again.

---

### Post by SonicMetalMan on 2010-07-18
Just an update out of courtesy. Since the silence surrounding the USB automount failure is so overwhelmingly deafening, I have pulled the plug on Ubuntu, RIP. Fedora 13 does all that I am looking for and the damn automount works. I will miss the large repo of Debian apps but I will persevere. I've no doubt that either a Debian contributor or a Canonical employee will eventually figure out how to really fix this problem without the myriad of silly workaround suggestions I've seen that didn't work.

Happy Trails dudes and dudettes.

---

### Post by SpyderBite on 2010-07-24
I got it working but I have to boot in to VirtualBox, plug in my Blackberry, shutdown VirtualBox to get it to recognize it each time. Pita.. but it'll do in a crunch until a solution is coded in to an update later.

---

### Post by technoholic on 2010-07-25
I cant explain why it does, but I got this to work. Here's how I did it:

Plug in USB flash drive
Launch palmiset, USB drive should be visible
Format the drive to NTFS 
Use "Safe Removal" function to unplug the drive

Now, my USB drives automount just like before upgrading to Lucid even after rebooting the computer. 

Like I said, don't ask me why, I am not a Linux geek (wish I was). All I know is that now automount works even dynamically updating the desktop icon. Seems too easy which makes me a bit uneasy. Will post follow up if it fails again but so far so good, even after a reboot. :D

---

### Post by mauribera on 2010-09-07
...installing pmount and libpmount0.0 solved the problem for me. Thanks for the suggestion

---

### Post by asoundmove on 2010-09-11
Just like many others, worked beautifully well for me (removed usbmount).
Thanks & keep posting such gems ;-)

---

### Post by syllamo on 2010-09-25
Thanks for the advice on this but mine tricky.

First - I upgrade to 10.04 and everything seems to work (everything that was Internet and programs)
Plug in USB drive = nothing - no mount no root no nothing
Try to launch Disk Utility - won't launch, just busy mouse icon, then nothing.
Create root password, logout, login as root - launch Disk Utility - same deal - try to uninstall using graphical software manager and reinstalled it - no change (I have not fixed that problem yet)
OK, so I check into things, get to this forum, try some things such as remove usbmount - wait it is not there, OK, install that. 
Now it mounts as root - what a pain in the a$$, logout, login as root - something was amiss in the drive, kept getting error when trying to view folder that it may have been moved or deleted - WTF (not going well so far).
So I remove usbmount - reboot, nothing mounts, back to where I started. Reinstalled and removed HAL, same - root only. Removed HAL (sudo apt-get remove hal) and usbmount (sudo apt-get remove usbmount) then mounted using pmount -w /dev/sdb1 - works with access, OK, take a break and enjoy the music collection.
Come back here, and then decide to install Thunar (sudo apt-get install thunar), it installs HAL and everything just works.
So I guess my solution would have been to just install Thunar
I am at the 2 year mark with Ubuntu as the only OS that I run, there have been some ups and downs but PLEASE, if there is going to be a LTS release - MAKE SURE IT WORKS.

---

### Post by GhostCoder on 2010-10-03
> **syllamo said:**
> Thanks for the advice on this but mine tricky.

First - I upgrade to 10.04 and everything seems to work (everything that was Internet and programs)
Plug in USB drive = nothing - no mount no root no nothing


Mine automount just stopped working after some updates. Everything still starts to work normally if I manually "sudo modprobe usb-storage" after boot. Still investigating what happened.

---

### Post by kiers on 2011-01-03
EUCHRID! LOVE OF MY LIFE! 
(don't tell the wife! LOL) 

you solved a MAJOR problem. MAJOR. Ubuntu is baaaaack! Wooo hooo! awwwright!

You don't know how depressing it is to run a terminal and sudo this sudo that everytime i want to run a thumb drive. I was about to look for a bumper sticker: "Ubuntu fried my brain".

I agree with the above post that if Canonical release a "LTS" version, at the least they should make sure everything works.

Windoze R.I.P.  every day you die a little more !  ):P

---

### Post by kiers on 2011-01-03
> **syllamo said:**
> 

First - I upgrade to 10.04 and everything seems to work.... 
Plug in USB drive = nothing......
Create root password, logout, login as root ...check into things, get to this forum, ...remove usbmount... 
Now it mounts as root - what a pain in the a$$, logout, login as root - something was amiss in the drive, kept getting error when trying to view folder that it may have been moved or deleted - WTF (not going well so far).
So I remove usbmount - reboot, nothing mounts, ... Removed HAL (sudo apt-get remove hal) and usbmount (sudo apt-get remove usbmount) then mounted using pmount -w /dev/sdb1 - works with access, OK, take a break..... install Thunar (sudo apt-get install thunar), it installs HAL and everything just works.
...PLEASE, if there is going to be a LTS release - MAKE SURE IT WORKS.

Syllamo, i'm only 5 months in as an ONLY Ubuntu user (with more white hairs now) but i wish i could buy you a drink! This experience you describe is SOOOO TYPICAL! Touche. cheers.

---

### Post by El_Belgicano on 2011-03-30
OK, same problem, new mix: I got hal installed and neither usbmount or pmount, but still no automounting with something other than root as the owner. Any ideas?

---

### Post by FroL_Onn on 2011-04-27
Had all usb-drives mounted in /mnt/usb0 usb1 usb2 and so on. only for root. In fact it was like i pluged 2 devices: one was automounted in /mnt/usb0 and the second - impossible to mount...

Removing usbmount really helped!

Thanks a lot!

---

### Post by raja_s_patil on 2011-11-26
> **euchrid said:**
> I had some trouble after upgrading to Lucid Lynx (10.04) where my USB drives would automount, but were only available to root. Hopefully, this post will help others with similar problems.

I saw a lot of advice about changing udev rules, editing /etc/fstab, changing preferences, group permissions and so on, but none of it helped - the only solution for me was to remove 'usbmount'. I hope this helps someone else Googling for the same issue.

Thanks euchrid,

I was able to automount USB HDD/Pen Drives successfully so that a Normal user can R/W. But some how on one fine morning I found that its allowing only root to have r/w and others only r permissions though usb storages kept on automounting. I removed usbmount package and every thing was back to normal once again.

Thanks a lot and warm regards.

hope it helps others like me.

Raja

---

