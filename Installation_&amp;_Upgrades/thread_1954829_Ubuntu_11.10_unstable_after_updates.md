---
title: "Ubuntu 11.10 unstable after updates"
date: 2012-04-08
forum: Installation &amp; Upgrades
---

### Post by tazz4vr on 2012-04-08
Approximately 2 weeks ago I did the system updates that were listed via Update Manager, since then, I have noticed issues with my puter.  At this time I am able to access some programs such as Gimp, Inkscape, Digikam, basically anything that I installed prior to this update I can access with the exception of Banshee, totally lost that application.  However, after accessing said applications, sometimes they hang once opened or I lose what I am trying to save.  Very unstable applications at this time.

Started noticing issues after the update when I attempted to locate Banshee, Software Center will open, but just hangs there.  I am unable to access Startup Manager, Update Manager or Startup Applications.  When I attempt to find or open applications via Dash Home, I get nothing.

Although I tried to get assistance in the thread below, it appears that the thread was marked solved so unsure where to go from here as I am still having issues.
[http://ubuntuforums.org/showthread.php?p=11826954#post11826954](http://ubuntuforums.org/showthread.php?p=11826954#post11826954)

At this time I am having to go back into my Windows OS.... please help!

---

### Post by tazz4vr on 2012-04-10
Any suggestions on this issue?

---

### Post by PhantomTurtle on 2012-04-11
It could be because you are using Wubi, since using Wubi is a bit slower than a normal install.

---

### Post by tazz4vr on 2012-04-11
The initial install went pretty much flawlessly.  The issues started about two weeks ago following the suggested updates that appeared via 'Update Manager'.  Since then I have not been able to open Software Center or locate programs via the dash...  It was suggested to go back to a previous version, however I am unable to access the necessary steps to get to it.

Re: Wubi being a bit slower.... while waiting for the Software Center to fully open, I had to leave for about an hour or so, returned and the program was still trying to open upon my return.

---

### Post by Curtis6767 on 2012-04-11
Apparently reverting to the old kernel has solved this problem for many of those who posted in that thread.

That would be 3.0.0-17-generic.

I can't tell you how to get there, but maybe someone else can.

GL

---

### Post by tazz4vr on 2012-04-11
> **Curtis6767 said:**
> Apparently reverting to the old kernel has solved this problem for many of those who posted in that thread.

That would be 3.0.0-17-generic.

I can't tell you how to get there, but maybe someone else can.

GL

That is what I am hoping as I initially started to get help in another thread, but it has since been marked 'Solved'.  

Here is the initial thread I sought help in.... perhaps there is someone out there who can help me resolve the issue I am having.

[http://ubuntuforums.org/showthread.php?p=11826954#post11826954]("http://ubuntuforums.org/showthread.php?p=11826954#post11826954")

---

### Post by bcbc on 2012-04-12
How many kernels do you have? (look in /boot )

Do you see the grub menu at boot - if not hold down SHIFT after selecting Ubuntu from the Windows boot manager. Then look under 'Previous linux versions' and select one of those. See if it makes a difference.

Check your available space:
```
df -h
```
Look at the first line of that and make sure /dev/loop0 has space remaining.

---

### Post by tazz4vr on 2012-04-12
> **bcbc said:**
> How many kernels do you have? (look in /boot )

Do you see the grub menu at boot - if not hold down SHIFT after selecting Ubuntu from the Windows boot manager. Then look under 'Previous linux versions' and select one of those. See if it makes a difference.

Check your available space:
```
df -h
```
Look at the first line of that and make sure /dev/loop0 has space remaining.

When you mention 'kernels', is that in reference/same as other versions of Linux that I should be looking for in the boot manager?  Can I do this through the terminal in Ubuntu or does it have to be when I am booting up my puter?

Regarding the available space, here is what I got....  Just so ya know, I have no idea what any of the info below means, what the %'s should be, heck, I may have a dinosaur of a puter for all I know.  But she's not smoking, clicking or ticking, so not ready to toss her out just yet!

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0             17G  7.3G  9.6G  43% /
udev                  868M  4.0K  868M   1% /dev
tmpfs                 351M  764K  350M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  877M  2.3M  875M   1% /run/shm
/dev/sdb3              70G   11G   60G  15% /host
/dev/sdb2              70G   35G   35G  51% /media/OS
```

---

### Post by bcbc on 2012-04-12
Space is good. 

Yes you can select an older kernel when you boot only. The first menu you see is the Windows Boot Manager - just Windows and Ubuntu here. Select Ubuntu. The second menu is Grub's menu. This is probably hidden (recent changes for Wubi). So to show it, press the SHIFT key immediately and hold it after selecting Ubuntu. This will cause it to show.

Then you'll see your current bad kernel at the top, the recover mode next, and following that 'Previous linux version'. Hit enter on that and you'll see the older kernels. Select the first one and Enter to boot it. According to the other thread you pointed to this should work better until you can download the latest updates.

---

### Post by tazz4vr on 2012-04-12
Thanks for the detailed instructions, very much appreciate the help.  Hopefully by this time next year, I will be able to help others as well.

I will give the 'Previous Linux version' a shot and post a status update when done.  Wish me luck!!!!!

---

### Post by tazz4vr on 2012-04-12
Okay... so, I rebooted, hit the 'Ubuntu', pressed and held down the 'shift' key and nothing but a black screen for several minutes without change. I tried doing this step twice with the same result. 

On the chance that I was doing it entirely wrong, I rebooted, hit the 'Ubuntu' and then pressed and released 'shift' key, and was taken to my desktop in Ubuntu with same issues.

](*,) - where's my kicking bear when I need him... ughhhhhhhhhhhhh!

---

### Post by bcbc on 2012-04-12
Yeah, not sure why they decided to hide the menu. You could try to change the default, but not sure this is a good idea. 

You could just uninstall the problem kernel - that would work provided you still have your old ones. How about the contents of:
```
ls /boot
```

Not sure why you aren't able to get the updates that apparently fix this problem. And I suppose there's a possibility that your problem is different, even if the symptoms appear to be the same.

---

### Post by tazz4vr on 2012-04-12
At this time I am just wondering if it's better to uninstall the version I have and wait for a newer release or reinstall the one I have and hope for the best.  On the other hand though, I have to wonder what is causing this issue to begin with and who's to say it will not occur again to me or anyone else regardless of the version being used.  Basically, I would love to know where this issue began and why.

In any case, here is additional info you asked about.

```
abi-3.0.0-12-generic         memtest86+_multiboot.bin
abi-3.0.0-16-generic         System.map-3.0.0-12-generic
abi-3.0.0-17-generic         System.map-3.0.0-16-generic
config-3.0.0-12-generic      System.map-3.0.0-17-generic
config-3.0.0-16-generic      vmcoreinfo-3.0.0-12-generic
config-3.0.0-17-generic      vmcoreinfo-3.0.0-16-generic
grub                         vmcoreinfo-3.0.0-17-generic
initrd.img-3.0.0-12-generic  vmlinuz-3.0.0-12-generic
initrd.img-3.0.0-16-generic  vmlinuz-3.0.0-16-generic
initrd.img-3.0.0-17-generic  vmlinuz-3.0.0-17-generic
memtest86+.bin
```

---

### Post by bcbc on 2012-04-12
-17 is the [latest kernel]("http://packages.ubuntu.com/oneiric/linux-image"). Not sure why in the other thread they said -19 was available. Maybe in -proposed ? Yes, in fact -19 is in proposed: [https://launchpad.net/ubuntu/oneiric/+package/linux-image-3.0.0-19-virtual](https://launchpad.net/ubuntu/oneiric/+package/linux-image-3.0.0-19-virtual)

So I guess you can add proposed to your software-sources to get -19, or alternatively just uninstall -17 and then it will boot -16 automatically:

**Either**
1. Add proposed
Run update-manager
Click Settings (bottom left)
Click on Updates Tab
Select "Pre-released updates (oneiric-proposed)
Click Close
Then you can install -19 using either the update manager or through the command line (sudo apt-get update && sudo apt-get dist-upgrade)

**Or**
2. remove -17 so it boots -16 
```
sudo apt-get remove --purge linux-image-3.0.0-17-generic
```

Note: adding proposed will expose your system to pre-release software. It may be better in this case, but there's more risk (in general).
Note: removing a kernel may expose you to risks associated with the older kernel (usually the newer ones are released because of security risks).

---

### Post by tazz4vr on 2012-04-13
If I uninstall the current version using the add/remove programs in Windows and then reinstall using a CD this time, is it possible that the problem will resurface with updates?

---

### Post by bcbc on 2012-04-13
> **tazz4vr said:**
> If I uninstall the current version using the add/remove programs in Windows and then reinstall using a CD this time, is it possible that the problem will resurface with updates?
I don't know. If the problem is in the updates then that should end up the same.

---

### Post by tazz4vr on 2012-04-13
> **bcbc said:**
> I don't know. If the problem is in the updates then that should end up the same.

What to do, what to do? :-k Something I need to think about before just doing it. 8-[

---

