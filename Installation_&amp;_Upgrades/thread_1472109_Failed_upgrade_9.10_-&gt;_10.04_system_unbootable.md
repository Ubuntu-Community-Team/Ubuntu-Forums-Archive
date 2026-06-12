---
title: "Failed upgrade 9.10 -&gt; 10.04: system unbootable"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by The_Noise on 2010-05-04
Hi folks

I've just reported a launchpad bug report about my desktop system being unbootable after upgrade to lucid lynx.

[https://bugs.launchpad.net/ubuntu/+bug/574973](https://bugs.launchpad.net/ubuntu/+bug/574973)

I opened this thread to ask if someone else experienced a similar problem and for collecting information and workarounds (none yet) about this quite serius problem.

The system has an nvidia graphic card and proprietary drivers were installed before the upgrade. However I'm not sure the problem is related to this.

FYI, the system booted regularly from a usb stick with ubuntu lucid lynx. SO the problem is in the upgrade path.

---

### Post by cs.thor.ro@gmail.com on 2010-05-04
the problem is in the grub, I do the same and i tried before to make a clean install with the live cd and the result is the same, the grub show the corect option but xp (in my case w7) do not boot

---

### Post by The_Noise on 2010-05-04
I may be wrong but I don't think it's a grub problem. 

Windows XP boots correctly. And also the ubuntu kernel are launched but after some seconds the system locks.

I've added some screen-shots of the boot in the LP entry:

[https://bugs.launchpad.net/ubuntu/+bug/574973](https://bugs.launchpad.net/ubuntu/+bug/574973)

---

### Post by Neo2 on 2010-05-04
Thanks Noise, indeed looking at the screendumps the problem looks very similar, mine gets as far as 'checking battery  OK' before hanging. But fails to get out of 'DOS' mode. I have Acronis loaded, so I get the Acronis startup screen fine, click on Win xp there which takes me to grub screen with XP, XP backup (Tune UP utilities) and Ubuntu listed. I click on Ubuntu and it takes me to the 9.10.. kernel 2. something page and then says failed to ount with /dev in there somewhere. It then goes on to try to load but eventually hangs. I wonder if the MBR has become corrupted by the upgrade? I was going to install the new Ubuntu into windows directly using WUBI but maybe now I'll wait and see!

---

### Post by bcbc on 2010-05-04
Post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net").

From another thread you mentioned you're using wubi, so perhaps the grub menu failed to get updated. Did you have any problems during the upgrade?

I can think of two possible fixes. a) manually boot from grub command line, and b) boot live cd/usb and chroot into wubi install and update. But post the results of the script above first.

Edit: I'm combining comments from Neo2 since you have said you have the same problem. However, this may not be the case. That's why it's important to post the script output.

---

### Post by The_Noise on 2010-05-04
bcbc,

my problem does not seems related to grub since the kernel starts and filesystem seem to be mounted. Booting with init=/bin/bash I get the bash shell and the root filesystem is correctly mounted.


Neo,
(to understand if we have the same problem...)
can you also try to boot the grub "system rescue" entry, deleting from the kernel line "single" (the last word) and putting "init=/bin/bash" (without quotes) instead? When you try this do you reach the shell (what you call DOS mode)? Do you see the filesystem (try ls for example)?

---

### Post by Neo2 on 2010-05-04
Thanks guys, bootinfoscript seems to only be downloadable once you're into Ubuntu (which I can't do) so not sure how useful that will be. Noise, I am flattered by your thoughts that you think I am so technical... but really I am not, I am a hobby Linux person who loves to play, so learn as I go on. Your comments didn't make a lot of sense I'm afraid. What I call 'DOS' is the black screen with white writing on it. That's where it hangs. I'd take a screendump but doubt it would work at that stage. I can't write anything at that stage (or can I?). It doesn't seem to respond to 'enter' command too. What (in layman's terms) can I do to get beyond that last line of battery check....[ok]? As I said, it is looking for the wrong install anyway at the start so is doomed to fail. 
The other question related to WUBI and I haven't used that yet.I merely did an upgrade from the updates screen in update manager (and yes, I did make sure everything was individually updated first before I started). The whole upgrade went well and no problems at all, on reboot it just went wrong. Thanks for trying to help here guys, we learn so much by doing these things, even if the first reaction is frustration... for now XP it is, but let's hope for not too much longer!

---

### Post by Neo2 on 2010-05-04
Noise, in particular 'try to boot the grub "system rescue" entry' isn't clear. I haven't ever seen one of these on the black screen. also 'delete from kernel line single? Not sure I read that either, and at boot stage I can't edit any lines I think.


Neo,
(to understand if we have the same problem...)
can you also , deleting from the kernel line "single" (the last word) and putting "init=/bin/bash" (without quotes) instead? When you try this do you reach the shell (what you call DOS mode)? Do you see the filesystem (try ls for example)?[/QUOTE]

---

### Post by The_Noise on 2010-05-04
Neo,
at boot time you should see the grub boot menu from which you choose WinXP right now. A screenshot of the grub menu is this one

[https://bugs.launchpad.net/ubuntu/+bug/574973/comments/1](https://bugs.launchpad.net/ubuntu/+bug/574973/comments/1)

Each line in the grub menu can start a different system. Once a menu entry is selected you can boot it hitting ENTER or you can edit it hitting 'c'. In particular you should select the second entry (the second line) and type 'c'.

Now some lines of text are showed. Go to the line that ends with "ro single" and delete the world "single" and replace it with "init=/bin/bash" (without quotes). Now boot typing CTRL-X.

If your problem is not due to grub then you should see some text and, after a few seconds, a prompt like this "root@(none):# ". This indicate that bash is running, so grub correctly booted the kernel and the first program (bash in this case). To reboot CTRL+ALT+CANC.

If, on the contrary, the system locks earlier and you cannot see the prompt showing "root@(none):# " then the problem is quite surely related to grub.

---

### Post by Neo2 on 2010-05-04
Thanks. I've printed a copy of that out and will try. Won't be straight away, too much to do but will post back what happens! I certainly didn't know about a right click option on that grub menu!

---

### Post by The_Noise on 2010-05-04
Just to be clear: you should press the 'c' key on the keyboard, not to use the mouse. You can also find Grub help messages in the bottom part of the screen, just read :).

Ignore this message if it was already clear.

---

### Post by Neo2 on 2010-05-04
Thanks Noise, I did understand. Not tried it yet, will do so tomorrow.

---

### Post by bcbc on 2010-05-04
> **Neo2 said:**
> Thanks guys, bootinfoscript seems to only be downloadable once you're into Ubuntu (which I can't do) so not sure how useful that will be.
If you have an ubuntu install/live CD you can use that to run the script. 

> **Neo2 said:**
> 
The other question related to WUBI and I haven't used that yet.I merely did an upgrade from the updates screen in update manager (and yes, I did make sure everything was individually updated first before I started). The whole upgrade went well and no problems at all, on reboot it just went wrong. Thanks for trying to help here guys, we learn so much by doing these things, even if the first reaction is frustration... for now XP it is, but let's hope for not too much longer!
You can find check if you have wubi - look under windows explorer for c:\wubildr or c:\ubuntu\disks\root.disk. If these exist you have wubi - in which case ignore the rest of this post.

If you don't have wubi, and assuming the upgrade went well as you said, you can manually boot the current working kernel through grub. This is assuming that for whatever reason the grub menu didn't update correctly (which seems unlikely for a successful upgrade, but it won't hurt to try this)

When you see the grub menu that still shows the 9.10 kernel, select the first entry and hit 'e' to edit it. Then change it as follows:
Where it says "linux /boot/vmlinuz-2.6.31-21-generic ..." or similar change the first two parts only to 
```
linux /vmlinuz root=...(**leave this part from root= unchanged**)
```
Where it says "initrd /boot/initrd.img-2.6.31-21 generic" change to 
```
initrd /initrd.img
```
Then hit CTRL+X to boot.

If you have a working kernel, it should boot it. Otherwise you definitely need an ubuntu install CD.

---

### Post by logan_2k6 on 2010-05-04
Hi,

I also have a problem of booting with WUBI - Ubuntu/Kubuntu 10.04 (never happened in 9.10)
So to put it simple after every reboot my devices (hard disks) gets different names
For instance one boot my windows partition is hda2 and another reboot is hdc2 (also the hd0,2 must change to hd2,2). Because of this i always end with the message asking if it waits enough for root device (or whatever)
So if i reboot chances are 90% to change the device name and doing so i can finally boot up in ubuntu.
Any idea how can i fix this?
I've tried update-grub but I don't know how to make grub to use UUID instead of /dev and just for info i have "#GRUB_DISABLE_LINUX_UUID=true" in /etc/default/grub

I keep searching for a fix in ubuntu forum but it's a huge forum...couldn't find anything similar.

---

### Post by hexwind on 2010-05-04
I had the same problem last weekend but I had to go for a fresh install instead !

---

### Post by Neo2 on 2010-05-05
ok, here goes:
I tried noise's solution and the following happened (in some detail I hope for all you experts out there).
Got to the grub page.
highlighted the ubuntu, type 'c', nothing happened. No letters worked on any of the 3 options (XP etc).
Had to 'enter' ubuntu, got the count down screen to boot. During the count down, pressed 'esc' as listed, to enter options.
Whole list of ubuntu releases listed with 9.10 kernel 2.6.31-32-generic at the top, and repeated line 2 with recovery mode after. No 10.04 at all listed.
Went for recovery option, eventually up comes a blue box with some options. Not sure what to go for so opted for 'run normal boot' (first option). Then had lots of lines and finally at the bottom 10.04 appears with desktop name being asked for and password. I enter both, accepts and then hangs asking for xx-desktop:~$ which I have NO idea about. Switch computer off.

For completion sake, I also went back into the normal boot mode to write down what the screen says when it hangs and it is this:
mount: mounting none on /dev failing no such device. followed by filesystem etc.

This is very complicated it seems and prob beyond me unless someone can give me step by step instructions. Maybe I should just fully uninstall 9.10 through windows (it doesn't appear in the add/remove progs but is still installed in folders in C). I am afraid to use the WUBI as it seems so many are having problems with that too and if I lose XP too I'm scuppered. BTW, for the person who asked if WUBI was installed, no it isn't. I checked in C:\ and non existent. Assuming then WUBI didn't install at upgrade? Will try your ideas out later, but so far trying to 'edit' any of the lines doesn't work as above.

Thanks for the help.

---

### Post by fatmcgav on 2010-05-06
> **Neo2 said:**
> Thanks Noise, indeed looking at the screendumps the problem looks very similar, mine gets as far as 'checking battery  OK' before hanging. But fails to get out of 'DOS' mode. I have Acronis loaded, so I get the Acronis startup screen fine, click on Win xp there which takes me to grub screen with XP, XP backup (Tune UP utilities) and Ubuntu listed. I click on Ubuntu and it takes me to the 9.10.. kernel 2. something page and then says failed to ount with /dev in there somewhere. It then goes on to try to load but eventually hangs. I wonder if the MBR has become corrupted by the upgrade? I was going to install the new Ubuntu into windows directly using WUBI but maybe now I'll wait and see!

I get to the same point as you, 'Checking Battery OK' and then hangs... 

I've tried the 'init=/bin/bash' edit and I can get to a bash shell... 

Any ideas on how I can recover my system?

Cheers
Gavin

---

### Post by Neo2 on 2010-05-06
Sorry, no idea as yet, no-one has answered me with anything that has helped. Still waiting for that Ubuntu expert to ride and solve the issue...

---

### Post by fatmcgav on 2010-05-06
> **Neo2 said:**
> Sorry, no idea as yet, no-one has answered me with anything that has helped. Still waiting for that Ubuntu expert to ride and solve the issue...

Did a bit more googling and found this one:
[http://www.uluga.ubuntuforums.org/showthread.php?p=9248839](http://www.uluga.ubuntuforums.org/showthread.php?p=9248839)

Worked a treat for me :) Now back in a fully working system... 

Cheers
Gavin

---

### Post by richardh9936 on 2010-05-17
My pc lost its keyboard and mouse during the upgrade, when it asked me to confirm replacing a dkms configuration file.  When I rebooted, it failed at "checking battery".

I'm now using a KDE cd to re-install, but that seems problematic, too.

Would my KVM switch cause this?

---

