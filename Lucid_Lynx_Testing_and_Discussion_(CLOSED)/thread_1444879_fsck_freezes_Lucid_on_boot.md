---
title: "fsck freezes Lucid on boot"
date: 2010-04-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by VMC on 2010-04-01
First time this happened to me. When it was time for a fsck, it displayed:

```
Checking disk 1 of 1 (71% complete)
```

Using ext4 file system, fsck version:fsck from util-linux-ng 2.17.2

then froze. The keycodes worked, so issued Alt+sysrq+b and on reboot it booted up without checking file system.

then I issued ```
sudo touch /forcefsck
``` and rebooted. It froze again at the same place. It then stayed that way because the empty file *forcefsck* was still there. Had to remove it using another install.

anyone else have problems with fsck? Can someone do a forcefsck to confirm.

I'll check Launchpad for any bugs.

---

### Post by dcstar on 2010-04-01
> **VMC said:**
> First time this happened to me. When it was time for a fsck, it displayed:
........

How long did you **wait** for it to actually process?

Also, do **not** "quote" code or data, use the Code tags.

---

### Post by VMC on 2010-04-01
**Long enough**...

---

### Post by keturn on 2010-04-02
this is currently happening on my Lucid system.  It's been at 78% for over 20 minutes now.

---

### Post by VMC on 2010-04-02
> **keturn said:**
> this is currently happening on my Lucid system.  It's been at 78% for over 20 minutes now.

What install is yours? If daily-live, when did you install it, and have you been keeping updated?

Mine just happened in the past two daily-live installs. I have a older install that's not effected, but I have installed any updates.

Edit: I read your entry on the bug report. Next time when the boot process stops, try Alt+Crtl+F2(or F3,4,5) then login and type:
```
ps -F -C mountall
```

One sure way to get this same error is to force fsck. From a terminal on your booted "defective" install, type

```
sudo touch /forcefsck
```

on the next re-boot it should try to do a file system check.

---

### Post by george1984 on 2010-04-03
Hello

Running fully updated lucid64.

I had this same problem last night (12 hours ago).

Lucid is on sda. I booted into sdb (Mandriva 2010) and ran 
       sudo fsck /dev/sda2
Booted back into sda. Same problem. I went to bed.

( I should mention that I don't really know what I am doing, but I have an earlier image of sda2 backed up, so I could get around this problem that way.) 

This morning I booted into sda. There was no file system check. The boot was completed successfully. Repeated the boot to be sure.

Apart from running fsck from sdb I have in no way changed sda. 

A random event?

Bye

---

### Post by awam66 on 2010-04-03
This happened to me also but only since the upate to kernel 2.6.32-19 the other day. Don't know if it is related. I have three different instances of lucid, two 32bit and 1 64 bit and it happenes on all three.

---

### Post by VMC on 2010-04-03
> **george1984 said:**
> 
Lucid is on sda. I booted into sdb (Mandriva 2010) and ran 
       sudo fsck /dev/sda2
Booted back into sda. Same problem. I went to bed.

...
Look on the root of sda. You should find a file *forcefsck*. Use your Mandy to delete it. You need super root powers to do so.
Then you will be able to boot Ubuntu again.

---

### Post by grandtoubab on 2010-04-03
I generally use
```
fsck -y
```
 to repair files system

---

### Post by Rackstar on 2010-04-03
I had the same problem (at 72%). Did anyone file a bugreport?

---

### Post by Fred2a on 2010-04-03
This is happening to me too, I think it happened on the previous kernel as well.

I don't think I've ever had a startup disk check work in lucid, they always hang the system.

This time it got to 79% and stopped. I managed to Ctrl+Alt+F1 and log in, but on going back to Terminal 7 and trying to Alt+PrtScr+K my way out resulted first in a login screen, which worked, and then it froze again. A second Alt+PrtScr+K rebooted the machine.

---

### Post by VMC on 2010-04-03
> **Rackstar said:**
> I had the same problem (at 72%). Did anyone file a bugreport?

Yes, the bug report is [**_here_**]("https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/554079").

---

### Post by chewit on 2010-04-05
Thank god I am not the only person with this problem.

Did think my SSDs have failed on me.

---

### Post by teejay17 on 2010-04-06
I also have the same problem:
I updated Lucid last night. This morning, when I rebooted, it started  doing a FSCK check in the Plymouth screen and it seems to have entered a  never ending loop, going up to 3% over and over and over again *ad  infinitum*. Pressing C does not stop it. Pressing Esc. only freezes  it. 
This is on an Acer Aspire 1, with 10" screen and a 160 gig hard drive. 
This seems like a pretty worthwhile bug.
My other test machine, on the other hand, an older T41 Thinkpad, did not  suffer the same fate with this update so maybe it is hardware specific?  
I have reformatted the netbook (with Windows 7) and will wait until the official release  of Lucid Lynx before reinstalling Ubuntu.

---

### Post by michaelpagz on 2010-04-07
same issue as teejay17 but on an acer extensa 4420. Endless loop at disk check. C and F do nothing. I'm lost.

---

### Post by cariboo on 2010-04-07
I had the same problem on my Compaq Mini 110 netbook, I just restarted and booted from a live usb drive, and once at the desktop ran fsck in a terminal, it took less than a minute to repair. Once done I rebooted, and everything is as it should be.

---

### Post by michaelpagz on 2010-04-07
> **cariboo907 said:**
> I had the same problem on my Compaq Mini 110 netbook, I just restarted and booted from a live usb drive, and once at the desktop ran fsck in a terminal, it took less than a minute to repair. Once done I rebooted, and everything is as it should be.

I tried running fsck but it said

> no such file or directory while trying to open /dev/hda2

The superblock could not be read or does not describe a correct ext2 filesystem. If the device is valid and it really contains an ext2 filesystem (and not swap or ufs or something esle), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock: e2fsck -b 8193 <device> 

So I tried running that e2fsck command and it said the same thing.

Is there something specific in fsck you ran for the fix?

---

### Post by teejay17 on 2010-04-08
> **VMC said:**
> Yes, the bug report is [**_here_**]("https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/554079").
I noticed that this bug report is "unassigned." Anyone know if it is being worked on?

---

### Post by VMC on 2010-04-08
> **teejay17 said:**
> I noticed that this bug report is "unassigned." Anyone know if it is being worked on?

I think the problem is the beta freeze. I noticed it now is *confirmed*.

Once the freeze is over, it will inspire one of the developers.

---

### Post by Sennaista on 2010-04-08
Same here, have had it a couple of times. Always stuck at 71%.

---

### Post by zika on 2010-04-08
I've set "Maximum mount count" on my Ubuntu partition to -1 to skip possible problems when I least want them... Waiting for bug to be fixed... Still no shut-down... Probably these two bugs will be solved simultaneously... :)

---

### Post by null_pointer_us on 2010-04-09
I encountered this bug (coincidentally?) after updates this morning.

When it freezes with the fsck message, if you hit the power button and let the system shutdown, subsequent boots should be fine.

---

### Post by zika on 2010-04-09
> **null_pointer_us said:**
> I encountered this bug (coincidentally?) after updates this morning.

When it freezes with the fsck message, if you hit the power button and let the system shutdown, subsequent boots should be fine.What about file-system? It's a disaster waiting to happen... I do not like to interrupt power on an idle system let alone on a fsck...

---

### Post by mcduck on 2010-04-09
> **zika said:**
> What about file-system? It's a disaster waiting to happen... I do not like to interrupt power on an idle system let alone on a fsck...

just wait a bit before you reboot, the fsck actually completes just fine, it's just the Plymouth that seems to freeze.

---

### Post by zika on 2010-04-09
> **mcduck said:**
> just wait a bit before you reboot, the fsck actually completes just fine, it's just the Plymouth that seems to freeze.You know(assume) that, I know(assume) that, but, what about (certainly existing non-patient) others... I've disabled automatic checking and I'm very sad that a great tool /forcefsck is now, out-of-reach... If You try to use it, You get into infinite loop, since the file is not erased, after (assumed) completion of fsck, and the only way, I've seen, was to use LiveCD...
Actually, the only plausible argument against removing Plymouth, I got, here on this Forum, was that I could watch the progress of fsck with Plymouth switched on... This problem, makes that argument void...

---

### Post by mcduck on 2010-04-09
> **zika said:**
> You know(assume) that, I know(assume) that, but, what about (certainly existing non-patient) others... I've disabled automatic checking and I'm very sad that a great tool /forcefsck is now, out-of-reach... If You try to use it, You get into infinite loop, since the file is not erased, after (assumed) completion of fsck, and the only way, I've seen, was to use LiveCD...
Actually, the only plausible argument against removing Plymouth, I got, here on this Forum, was that I could watch the progress of fsck with Plymouth switched on... This problem, makes that argument void...

You could just boot into recovery mode, that should allow the fsck to run normally without anything freezing.

Still, I hope this bug gets fixed soon. It's quite annoying, and will definitely be a very bad thing if it's not fixed in the final release. But I do have enough faith in Ubuntu's developers that they wouldn't allow such thing to happen. :)

---

### Post by zika on 2010-04-09
> **mcduck said:**
> You could just boot into recovery mode, that should allow the fsck to run normally without anything freezing.

Still, I hope this bug gets fixed soon. It's quite annoying, and will definitely be a very bad thing if it's not fixed in the final release. But I do have enough faith in Ubuntu's developers that they wouldn't allow such thing to happen. :)Nope, I've tried that... Doesn't work...

---

### Post by VMC on 2010-04-09
I see the latest *mountall* has been updated to 2.11, but that still hasn't fixed this *fsck* issue:

---

### Post by mammoth23 on 2010-04-11
I'm happy to see that I'm not the only guy with that freeze problem (71% complete -> freeze). I hope that they fix the problem soon.

> I've disabled automatic checking and I'm very sad that a great tool  /forcefsck is now, out-of-reach... If You try to use it, You get into  infinite loop, since the file is not erased, after (assumed) completion  of fsck, and the only way, I've seen, was to use LiveCD...

I think it's easier to switch to another console using using ALT+<F1> for example. Then you can log in and remove the file using **sudo rm /forcefsck**. After that you can reboot with **sudo reboot**.

---

### Post by Didius Falco on 2010-04-11
I had the 71% issue a while back, with the difference that mine just went ahead and booted after a few seconds of being hung at 71%.

Since then, it never checks the disk at all. I didn't set it to not check it, it just doesn't happen,

As a workaround, I use[FONT=monospace] [/FONT]```
[FONT=monospace][/FONT]sudo touch /forcefsck
``` every few days.[FONT=monospace][/FONT]

---

### Post by zika on 2010-04-12
> **mammoth23 said:**
> I'm happy to see that I'm not the only guy with that freeze problem (71% complete -> freeze). I hope that they fix the problem soon.



I think it's easier to switch to another console using using ALT+<F1> for example. Then you can log in and remove the file using **sudo rm /forcefsck**. After that you can reboot with **sudo reboot**.Oh, I've tried that, of course...

---

### Post by zika on 2010-04-12
> **Didius Falco said:**
> I had the 71% issue a while back, with the difference that mine just went ahead and booted after a few seconds of being hung at 71%.

Since then, it never checks the disk at all. I didn't set it to not check it, it just doesn't happen,

As a workaround, I use```
sudo touch /forcefsck
``` every few days.As I said earlier, that gets my system in a sort of infinite loop. Plymouth crashes, I have to force reboot, /forcefsck doesn't get erased, on next boot, again fsck starts and... I'll try again in several days, when I gather some spare time and nerves to fiddle with that, to see if anything changed... At least I'll try it with plymouth disabled (no, it can not be unistalled (at least according to my knowlegde), I just rename /etc/init/plymouth{ ,-log,-splash,-stop}.conf)...

---

### Post by djchandler on 2010-04-12
I just had this happen on a forced fsck (x number of boots reached) because I still can't read the screen when Plymouth puts garbage up. I keep hoping the next update will fix it, but it doesn't. 

So I decided to see what would happen if I forced fsck myself (touch /forcefsck) on the next boot. Same thing. Fsck apparently won't 't finish unless you choose recovery mode in GRUB. When the screen garbage changed and the disk access led stopped blinking, I hit ctrl-alt-delete. That reboot got to a log-in screen finally, but Plymouth is still making garbage screens. I'm going to remove all Plymouth themes so maybe I can see what's happening next time. There'll be no more Plymouth themes installed on either of my two beta testers until everything else is fixed.

We need to see what's going on. Plymouth isn't helping.

This is an updated beta 1 install, so it is essentially beta 2 with the latest kernel, 2.6.32-20 AMD64.

Here's the latest update installed:

```
Start-Date: 2010-04-12  00:08:47
Install: linux-headers-2.6.32-20 (2.6.32-20.29), linux-image-2.6.32-20-generic (2.6.32-20.29), linux-headers-2.6.32-20-generic (2.6.32-20.29)
Upgrade: hplip-cups (3.10.2-1ubuntu5, 3.10.2-2ubuntu1), fglrx (8.721-0ubuntu10, 8.723.1-0ubuntu1), ia32-libs (2.7ubuntu22, 2.7ubuntu23), gnome-disk-utility (2.30.1-0ubuntu1, 2.30.1-1), hpijs (3.10.2-1ubuntu5, 3.10.2-2ubuntu1), linux-generic (2.6.32.19.20, 2.6.32.20.21), hplip (3.10.2-1ubuntu5, 3.10.2-2ubuntu1), libgdu-gtk0 (2.30.1-0ubuntu1, 2.30.1-1), libhpmud0 (3.10.2-1ubuntu5, 3.10.2-2ubuntu1), xserver-xorg-video-r128 (6.8.1-2, 6.8.1-2ubuntu1), libgdu0 (2.30.1-0ubuntu1, 2.30.1-1), linux-headers-generic (2.6.32.19.20, 2.6.32.20.21), linux-image-generic (2.6.32.19.20, 2.6.32.20.21), pm-utils (1.3.0~rc3-2git1, 1.3.0-1), fglrx-modaliases (8.721-0ubuntu10, 8.723.1-0ubuntu1), nvidia-96-modaliases (96.43.14-0ubuntu12, 96.43.14-0ubuntu13), media-player-info (5-1, 6-1), fglrx-amdcccle (8.721-0ubuntu10, 8.723.1-0ubuntu1), hplip-data (3.10.2-1ubuntu5, 3.10.2-2ubuntu1)
End-Date: 2010-04-12  00:12:41


```

---

### Post by djchandler on 2010-04-12
I found a way to make Plymouth not draw a screen and let the usual text be displayed. My last experience mentioned above yielded a bitmapped screen having  ascii text sent directly to it. Apparently a routine (with the fglrx  driver) to render the text to graphics mode is being skipped because all  you see is various colored pixels across the top of the screen.

In GRUB2, hit "e" when you have the kernel selected that you wish to boot. This allows you to edit the boot command (emacs commands work). You will see something similar to the following:
> recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 12291b72-5e88-486e-a7e6-60a57bdeefed
    linux    /boot/vmlinuz-2.6.32-20-generic root=UUID=12291b72-5e88-486e-a7e6-60a57bdeefed ro  quiet vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.32-20-genericGo down to this line:
> linux    /boot/vmlinuz-2.6.32-20-generic  root=UUID=12291b72-5e88-486e-a7e6-60a57bdeefed ro  quiet vga=769  quiet  splashRemove the part that instructs Plymouth to draw a graphic screen, which in this case leaves:
> linux    /boot/vmlinuz-2.6.32-20-generic  root=UUID=12291b72-5e88-486e-a7e6-60a57bdeefed ro  quiet  splashI got this tip from Fedora's forum, but adapted for grub2. Don't save; this is for an emergency such as my previous message.

Hit "ctrl-x" to boot with the edited command. The boot will proceed with no splash, text messages will appear as you are used to seeing when booting in recovery mode in previous releases without Plymouth.

In fact, this may be a real good idea when booting in recovery mode.

The recovery mode line would look like this:
> linux    /boot/vmlinuz-2.6.32-20-generic root=UUID=12291b72-5e88-486e-a7e6-60a57bdeefed ro single[COLOR=Red][B][SIZE=4]Disclaimer: Do this at your own risk. I am not responsible for mis-application of this solution.[/SIZE]
[/B][/COLOR] 
Here's the [Fedora Forum thread and post]("http://forums.fedoraforum.org/showpost.php?p=1202839&postcount=4") this is derived from.

If anybody sees any problem with any of this, please post objections, enhancements, etc. I've been wrong before.

---

### Post by Artemis3 on 2010-04-13
I have also experienced these, and I have 3 partitions to mount, originally in ext3 (now upgraded to ext4) so you can imagine how long this was taking... I noticed disk activity stops after a LOOOOOONG while, and also did the alt sysrq reisub thing, which results in a successful boot.

Hope this gets fixed soon :)

---

### Post by null_pointer_us on 2010-04-13
> **zika said:**
> What about file-system? It's a disaster waiting to happen... I do not like to interrupt power on an idle system let alone on a fsck...

The file-system is fine. This can be repeated indefinitely with no danger. Computers these days come with an ACPI power button, which normally just sends a shutdown message to the kernel so that it can do a normal shutdown.

People who have ACPI disabled as a workaround would probably just get an immediate power-off, which, I agree, would be really bad to use recklessly.

---

### Post by zika on 2010-04-13
> **null_pointer_us said:**
> The file-system is fine. This can be repeated indefinitely with no danger. Computers these days come with an ACPI power button, which normally just sends a shutdown message to the kernel so that it can do a normal shutdown.

People who have ACPI disabled as a workaround would probably just get an immediate power-off, which, I agree, would be really bad to use recklessly.Then, I would suggest kernel-line switch **acpi_os_name=linux**, also... :) Considering that shutdown doesn't work on my system, yet, ...

---

### Post by cuby on 2010-04-13
This freeze also happened to me on the Ubuntu Netbook Remix 10.04, on a asus eee 901 with ssd and ext2 file system.
If the system was not properly shutdown, I think it is recommended to run fsck.
To solve the problem I booted from the Ubuntu USB disk and used the console to run fsck:

```
sudo fsck /dev/<your partition>
```

After this it booted ok again.

---

### Post by BrokeMahPC on 2010-04-14
This fsck thing affected me for the first time today, but, luckily did not get stuck in a loop.
Plymouth displayed for 2 seconds with the "checking disk" message, then it all went black and froze.
I did this as it was all I could remember, and it rebooted successfully.
```
Alt-SysRq-reisub
```

I got todays updates and rebooted to let the graphics drivers take effect.
fsck started again and got to 93% on disk 1 before freezing - the plymouth screen stayed up but was frozen.
I did the "reisub" thing again and it rebooted ok. Hope that was the last of it? I will add to the bug report.

---

### Post by Yofel on 2010-04-14
The original report was marked as a duplicate. This is now being tracked in [Bug 554737]("https://bugs.edge.launchpad.net/bugs/554737")

---

### Post by Ibidem on 2010-04-14
Here, I'm seeing something similar except it's dosfsck.
If I press C, it *usually* freezes at least a minute w/ an error about encountering an unrecoverable error.

What I really miss is how on Jaunty the machine would skip fsck if it was not plugged in.
Where did that go?

Ibidem

---

### Post by VMC on 2010-04-14
Udate:A fix has been commited. If you can't wait here is a [_**[COLOR="Blue"]ppa fix[/COLOR]**_]("https://bugs.edge.launchpad.net/ubuntu/+source/plymouth/+bug/554737/comments/25").

---

### Post by psyke83 on 2010-04-14
I don't know if it's related, but I was suffering from some corruption on my EXT4 partition (due to sudden power loss - my laptop's battery no longer works). The automatic scan was getting stuck at 70% or 71% and never changed, and pressing the "C" key had no effect.

After some fiddling, I managed to switch to another VT and saw that fsck was being run in an infinite loop, with an error to the effect of "filesystem errors cannot be corrected with automatic -a/-y parameters" (or something to that effect). I solved the problem by booting from the live CD, then running a fsck and interactively repairing the filesystem errors.

---

### Post by BrokeMahPC on 2010-04-14
Downloaded new plymouth from the vorlon ppa and did the "sudo touch /forcefsck" test.
Plymouth gets to "1 of 2 partitions, at 72%." then the screen blacks out for 5 seconds. then GDM login appears.  I logged in and checked / - the forcefsck file is gone.

I guess this will stop systems getting stuck but plymouth still isn't right.

---

### Post by VMC on 2010-04-14
> **psyke83 said:**
> I don't know if it's related, but I was suffering from some corruption on my EXT4 partition (due to sudden power loss - my laptop's battery no longer works). The automatic scan was getting stuck at 70% or 71% and never changed, and pressing the "C" key had no effect.

After some fiddling, I managed to switch to another VT and saw that fsck was being run in an infinite loop, with an error to the effect of "filesystem errors cannot be corrected with automatic -a/-y parameters" (or something to that effect). I solved the problem by booting from the live CD, then running a fsck and interactively repairing the filesystem errors.

Yes you can fix it that way, but usually on the partition that has the problem, once you change VT's type this next time

```
ps -F -C mountall
```

That should reveal that fsck is stuck. That doesn't mean *mountall* is the culprit, just that its stuck at that point.

The "ppa fix" is still causing issues with some folks.

---

### Post by Ibidem on 2010-04-14
> **VMC said:**
> A fix has been commited. If you can't wait here is a [_**[COLOR=Blue]ppa fix[/COLOR]**_]("https://bugs.edge.launchpad.net/ubuntu/+source/plymouth/+bug/554737/comments/25").
Was that aimed at anyone in particular?
Myself, I am quite happy eradicating anything "graphical" that isn't needed; I just let Plymouth install for "fun"...
And now it is *gone*.:)
No splash screens for me...I might ditch the DM again.

What's more significant to me is,
[I][B][SIZE=5]WHERE DID THE "SKIP FSCK ON BATTERY" GO?[SIZE=1]
[/SIZE][/SIZE][/B][/I][SIZE=5][SIZE=1] (not aimed at anyone in particular, but I do miss it)[/SIZE][/SIZE]

Ibidem

---

### Post by VMC on 2010-04-15
> **Ibidem said:**
> Was that aimed at anyone in particular?
Myself, I am quite happy eradicating anything "graphical" that isn't needed; I just let Plymouth install for "fun"...
And now it is *gone*.:)
No splash screens for me...I might ditch the DM again.

What's more significant to me is,
[I][B][SIZE=5]WHERE DID THE "SKIP FSCK ON BATTERY" GO?[SIZE=1]
[/SIZE][/SIZE][/B][/I][SIZE=5][SIZE=1] (not aimed at anyone in particular, but I do miss it)[/SIZE][/SIZE]

Ibidem

I added that by post was just an update. It appears taht the ppa fix still has issues , reading from some of the launchpad comments.

I wasn't aware of the skip fsck for laptops. I'm mainly using a desktop.

---

### Post by MrCheese on 2010-04-15
I haven't tried the ppa fix but can confirm my HP nc6220 laptop freezes on fsck (ext4 for root & home). A ctrl-alt-del reboots the laptop normally.

Paul.

---

### Post by mammoth23 on 2010-04-17
After the latest update the fsck freezes bug seems to be fixed. :)

The file /forcefsck was deleted and my computer stated without any problems.

---

### Post by zika on 2010-04-17
> **mammoth23 said:**
> After the latest update the fsck freezes bug seems to be fixed. :)

The file /forcefsck was deleted and my computer stated without any problems.Cool! The freeze is gone, but, at least on my machine, forcefsk doesn't get deleted... That is a minor annoyance, it is important that we have forcefsck working, again...

---

### Post by VMC on 2010-04-17
> **zika said:**
> Cool! The freeze is gone, but, at least on my machine, forcefsk doesn't get deleted... That is a minor annoyance, it is important that we have forcefsck working, again...

Your right. If anyone wants to try it, type:

```
sudo touch /forcefsck
```

and then reboot. It should pass the file system check and boot up. Then see if the file *forcefsck *is still in the root "/" directory. If it is you need to delete it or it will remain forever and do a file system check every time.

I checked a few bug reports. Not sure which one is correct. Will file a bug report a little later after *plymouth *updates settle down.

---

### Post by Yofel on 2010-04-17
That would be odd. the /forcefsck file gets deleted by 
```

post-stop script
    rm -f /forcefsck 2>dev/null || true
end script

```in mountall.conf

So the file should be deleted once mountall finishes (that might be before or several minutes after login,  depends on what mountall actually does)

---

### Post by VMC on 2010-04-17
> **Yofel said:**
> That would be odd. the /forcefsck file gets deleted by 
```

post-stop script
    rm -f /forcefsck 2>dev/null || true
end script

```in mountall.conf

So the file should be deleted once mountall finishes (that might be before or several minutes after login,  depends on what mountall actually does)

I'm aware of that script and what its suppose to do, it just doesn't do it.

Edit: strange that mountall is still running:

$ ps -F -C mountall
```
UID        PID  PPID  C    SZ   RSS PSR STIME TTY          TIME CMD
root       257     1 76  1400  4152   0 19:43 ?        00:00:32 mountall --daemon --force-fsck

```And indeed after the mountall daemon quits(33 seconds its gone), it does indeed remove /forcefsck

---

### Post by teejay17 on 2010-04-18
> **mammoth23 said:**
> After the latest update the fsck freezes bug seems to be fixed. :)

The file /forcefsck was deleted and my computer stated without any problems.
Yes, I think it is too. Last night my computer stopped at 70% and I thought it was stuck, but then after about it continued to boot.

---

### Post by george1984 on 2010-04-22
> **george1984 said:**
> Hello

Running fully updated lucid64.

I had this same problem last night (12 hours ago).

Lucid is on sda. I booted into sdb (Mandriva 2010) and ran 
       sudo fsck /dev/sda2
Booted back into sda. Same problem. I went to bed.

( I should mention that I don't really know what I am doing, but I have an earlier image of sda2 backed up, so I could get around this problem that way.) 

This morning I booted into sda. There was no file system check. The boot was completed successfully. Repeated the boot to be sure.

Apart from running fsck from sdb I have in no way changed sda. 

A random event?

Bye


I just now started up and it did it again. Reached 73% and then a blank screen. I waited a few minutes. Then did keyboard Alt+Ctrl+F1 followed by
sudo shutdown -r now. The reboot showed no file system check, and proceeded to the login normally. ( Does this suggest that despite the blank screen the fsck completed successfully?) 

My install is fully up to date. Can anyone clarify if there is a fix in the pipeline? 

I am not bothered by this, but a really raw newbie would be stumped and the formal release is in a week.

p.s. Could this be only happening with particular hardware combinations (I have a test install on one machine only).

---

### Post by george1984 on 2010-04-23
It booted ok a couple of times, but it has just done it again.

Am I the only person having this experience?

---

### Post by Didius Falco on 2010-04-24
Mine is not freezing, but it never completes the fsck. It will get to 71%, then the screen goes black for a second before taking me to the log in screen.

Other than that (which I consider a huge problem - I'd rather have it not run an fsck at all than have it quit before it finishes - I see more potential for harm there), my Plymouth is working okay.

---

### Post by teejay17 on 2010-04-26
> **Didius Falco said:**
> Mine is not freezing, but it never completes the fsck. It will get to 71%, then the screen goes black for a second before taking me to the log in screen.

Other than that (which I consider a huge problem - I'd rather have it not run an fsck at all than have it quit before it finishes - I see more potential for harm there), my Plymouth is working okay.
Yes, this seems to be the issue that has replaced the former fsck freeze. It staggers at 70% for a bit, then continues to log on. I was under the assumption that the fsck was continuing in the background without the ticker giving progress status. Perhaps I was wrong.

---

### Post by Didius Falco on 2010-04-26
> **teejay17 said:**
> Yes, this seems to be the issue that has replaced the former fsck freeze. It staggers at 70% for a bit, then continues to log on. I was under the assumption that the fsck was continuing in the background without the ticker giving progress status. Perhaps I was wrong.

I have a separate Home partition, so when the fsck started, it said 1 of 2 partitions, or words to that effect. It never even got to the second partition...

That leads me to lean very strongly towards the first one not completing either. If it **is **completing, my pc has somehow gained a previously unattainable speed at running fsck.

---

