---
title: "Just ran into a Mountall/Plymouth problem"
date: 2009-12-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by autocrosser on 2009-12-16
I just did my evening updates & ran straight into a "interesting" problem--I installed the .8 kernel. new version of GDM and a bunch of "normal" seeming stuff....Upon reboot I got a "mountall problem--can't mount plymouth" "droping to maintenance shell or Control-D to reboot"

I installed plymouth a bit ago to wait to see of it would ever work w/nvidia (forlorn hope I know) & had not thought much about it....

In any case. I fussed with it for a while & then thought I'd wait & use my backup install...Image of Opps included.....Not the best image--but informational......

---

### Post by ranch hand on 2009-12-16
I would try removing and installing Plymouth.  I do use an ATI card but have had no trouble with Plymouth and the ...-8 kernel.

I see you do self portraits, or at least pictures of your camera.

---

### Post by autocrosser on 2009-12-16
Nice idea---but it's a unresolvable issue---I chroot'd onto my Lucid from the Stable backup & tried to remove either plymouth or mountall--both cases would remove almost all of xorg & many others....   Interesting, but not very fun right now.....I'm playing with my b0rked backup Lucid to see if I can fix it enough to use it....perhaps it is time to retire the old main I'm using---it has been around from Karmic Alpha 4.......

Not a very good one--was a tad more interested in the screen info :)

---

### Post by ranch hand on 2009-12-16
I thought I could remove some stuff that turned out like that.  One package wanted to take 270 something packages with it.  I decided that was not the way to go.

Heck in a day or two the updates may have fixed it.

---

### Post by autocrosser on 2009-12-16
Yes---I'm in the backup Karmic install, so I'll just wait & keep a eye on the updates---maybe think of D/L a current Live build & install it to the backup b0rked Lucid this weekend if things don't smooth out.....

---

### Post by zika on 2009-12-17
> **autocrosser said:**
> Nice idea---but it's a unresolvable issue---I chroot'd onto my Lucid from the Stable backup & tried to remove either plymouth or mountall--both cases would remove almost all of xorg & many others....   Interesting, but not very fun right now.....I'm playing with my b0rked backup Lucid to see if I can fix it enough to use it....perhaps it is time to retire the old main I'm using---it has been around from Karmic Alpha 4.......

Not a very good one--was a tad more interested in the screen info :)I've installed plymouth manually in anticipation of some development with it. But, only thing that happened is white ubuntu logo. So I removed "splash" from boot line. If I try to remove plymouth (complete uninstall) it is possible without a single other package being removed. I'm on ATI HD3650. I had several mountall warnings but that was only when fsck was scheduled or, for some reason, file-system was mounted as read-only. Try forcing   file-system check ... I'm sorry if I misunderstood Your original message.

---

### Post by ranch hand on 2009-12-17
I have just had a mountall failure on Lounge and booted to recovery.  This did not go all the way and froze.  Tried it again and it went through to the menu.  "return to normal boot" and CLI log in an startx.

Rebooted and used the regular entry and booted right up.

This just said "mounall failed" no mention of Plymouth.

---

### Post by autocrosser on 2009-12-17
Weirder & weirder---I tried to boot into the main again & I can say for sure that mountall is trying to treat plymouth as a filesystem & the process dies--droping me to a maintenance shell--no filesystems are mounted & a forced fsck on the partition gives it a clear bill of health....I guess that I could manually mount all the main filesystems & see if it would continue booting, but this early in the game perhaps a reinstall would serve me better......I've not had to hand mount everything in a long time & it was a fair bit simpler back then.........

---

### Post by philinux on 2009-12-17
I've decided to purge plymouth for now. Still waiting for nvidia package to be rebuilt as well.

---

### Post by ronacc on 2009-12-17
I'm getting the same mountall failure during boot and just before that usplash failure ,terminated , so I don't think it is plymouth that is the problem . my sys continues on to low graphics mode without action on my part .

---

### Post by ronacc on 2009-12-17
I updated and when I rebooted it went back to using the 195.22 driver at full res .

---

### Post by autocrosser on 2009-12-17
> **ronacc said:**
> I'm getting the same mountall failure during boot and just before that usplash failure ,terminated , so I don't think it is plymouth that is the problem . my sys continues on to low graphics mode without action on my part .


I'm just posting the error messages--take a look at the image I posted---It clearly states that mountall terminated because plymouth could not be mounted......crazy I know--but the screen output is in black & white......I had run into the [update-initramfs error]("http://ubuntuforums.org/showthread.php?t=1357388") just before rebooting---so that could have b0rked things.

I'm going to reinstall both of my Lucid's this weekend--they are both b0rked--one due to the nvidia driver issue & the other with this problem--they both were from the Karmic era.....so it looks like a good time to start fresh.

---

### Post by philinux on 2009-12-18
Well removing plymouth made my box unbootable with mountall errors and startx failed. Reinstalled plymouth and booting back to normal.

The joys of testing. ;)

---

### Post by zika on 2009-12-18
> **philinux said:**
> Well removing plymouth made my box unbootable with mountall errors and startx failed. Reinstalled plymouth and booting back to normal.

The joys of testing. ;)I've removed plymouth (ATI HD3650) without any ill effects ...

---

### Post by Vanishing on 2009-12-18
> **zika said:**
> I've removed plymouth (ATI HD3650) without any ill effects ...

strange enough after i solved the ati driver issue, i got this error(i installed plymouth before solving the driver issue), this sure is testing..lol

---

### Post by Vanishing on 2009-12-18
> **Vanishing said:**
> strange enough after i solved the ati driver issue, i got this error(i installed plymouth before solving the driver issue), this sure is testing..lol

Somehow it works now...
i just chroot to the install and reinstalled plymouth*, did a fsck -f and reboot a couple times, then it worked...

---

### Post by autocrosser on 2009-12-19
Very interesting---I just went thru a reinstall on my main system--did the low graphics thing & then went to install the nvidia driver---I had been using 195.22 from deb [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu) lucid main --It HAD been working until the "little" problem I had--guess what?  I rebooted afterwards & was greeted with the SAME PROBLEM...... Looks like the 195.22 driver from that PPA causes the problem I've been having.......

Quick tally......what nvidia drivers are people using & where are they from?

---

### Post by Starks on 2009-12-19
I think the mountall from the ubuntu-boot ppa is causing this.

---

### Post by autocrosser on 2009-12-19
Nice thought---but I'm not using that PPA....I don't have many PPA's in my sources.list---mostly cairo-dock, gnome-colours & nvidia stuff.

---

### Post by Vanishing on 2009-12-19
> **autocrosser said:**
> Nice thought---but I'm not using that PPA....I don't have many PPA's in my sources.list---mostly cairo-dock, gnome-colours & nvidia stuff.

What i found out is:
if you use plymouth now, you cannot take "quiet" and "splash" off the grub config(kernel line), if you take them off, there will be the mountall and plymouth issue.
try to add them back and boot, it should work, at least in my case it does.

---

### Post by autocrosser on 2009-12-19
Are you using a nvidia driver?  I had not removed quiet & splash from the kernel line---this was a fresh reinstall that b0rked....

---

### Post by Vanishing on 2009-12-19
> **autocrosser said:**
> Are you using a nvidia driver?  I had not removed quiet & splash from the kernel line---this was a fresh reinstall that b0rked....

Nope..I'm using a thinkpad t500, with ATI HD3650, with open source dirver. If I take the "quiet" and "splash" off grub, it will show the mountall plymouth problem.

---

### Post by autocrosser on 2009-12-19
BLODDY CRUD!!!! I did have the ubuntu boot PPA in my list--I had thought it was turned off--but not...so I did have that ***! version of mountall & as soon as I did a aptitude remove plymouth I found it.....(insert VERY red-faced smiley!!!):oops:

---

### Post by TerminX on 2009-12-22
I just ran into this last night.  This is really a horrible situation, as it's apparently no longer possible to even boot a system without an initrd containing plymouth.  Kinda sucks for those of us who still roll our own kernels and otherwise don't even use an initrd... downgrading the mountall package and the initramfs-tools and initramfs-tools-bin packages fixes this situation and allows the installation to boot fine.

---

### Post by Vanishing on 2009-12-22
> **TerminX said:**
> I just ran into this last night.  This is really a horrible situation, as it's apparently no longer possible to even boot a system without an initrd containing plymouth.  Kinda sucks for those of us who still roll our own kernels and otherwise don't even use an initrd... downgrading the mountall package and the initramfs-tools and initramfs-tools-bin packages fixes this situation and allows the installation to boot fine.

I found a possible "solution", if you got the ubuntu-boot ppa, keep it, when you got the plymouth problem, restart, in grub add "force-fsck" in your kernel line.
If you didn't have ubuntu-boot ppa, find some way to fsck -f, then you are good to go.

It work for ME.....

---

### Post by scradock on 2009-12-23
This popped up for me today, after the 12/23 updates. I use radeon/ati OS drivers, so no nvidia involved.

The error message is as originally reported: mountall: cannot connect to Plymouth.

There is also an error message just before the system creaks into the desktop (3min 45s boot-time, anyone?) about:
cannot create session: no such file/directory

Once I got the low-graphics start-up; another time the system eventually started a normal session despite the message just above.

---

### Post by caryb on 2009-12-24
Doing the same on a Intel Video chipset, Kubuntu 64 bit setup.


Cary

---

### Post by l8gravely on 2009-12-24
Oh good, other's are running into this problem too.  I have an AMD x86_64 system, single disk, NFS mounts /home and /local from another box.  Self compliled kernels, not initrd at all.   System hangs on bootup with the dreaded "mountall: cannot connect to Plymouth" which is strange since I didn't have Plymouth installed at all.  I think I've also got the grub2 stuff installed as well, which might be some of the issue.  This is a Jaunty->Karmic -> Lucid system.  The joys of bleeding edge!

So I installed it.  No change.  I had already run into mountall problems with NFS /home and other filesystems.  It's certainly gottem more fragile lalely.  

I guess now it's time to check my PPA sources and see what I can do to fix this.  Note to self, next time test all this in a VM instead... much quicker!

At least I've got something to work on now over Xmas holidays....

---

### Post by autocrosser on 2009-12-24
I fought with this for 4~5 days & then just gave up/reinstalled...If any of you are getting into the desktop after the "problem" you are fairing better than I...

I did not find anything that would help with this---Side note: as there seems to be more of these coming up it looks like a bug report might be in order......

---

### Post by scradock on 2009-12-24
> **autocrosser said:**
> I fought with this for 4~5 days & then just gave up/reinstalled...If any of you are getting into the desktop after the "problem" you are fairing better than I...

I did not find anything that would help with this---Side note: as there seems to be more of these coming up it looks like a bug report might be in order......
Bugs have been filed both on mountall and on Plymouth - both quickly marked "Invalid" by the dev. 

After checking them out, I tried the "force fsck" suggestion; running e2fsck -f from gparted in a karmic install on the same disk took nearly 20 minutes, much longer than normal, so I guess there was something to fix.

Now I get a quick boot, with NO plymouth ubuntu-logo; bootchart shows neither plymouth nor plymouthd starting up, and normal desktop.

Still getting the "mountall: cannot connect to Plymouth" and "error creating session" error messages before and after the fsck output.

---

### Post by scradock on 2009-12-24
Stranger and stranger! 

I removed Plymouth (but not libplymouth2) without any complications, and re-booted. Exactly the same messages, except that the switch to smaller text between Grub and console messages didn't happen until nearly the end of the boot messages. Normal startup, otherwise.

Then I re-installed Plymouth, and got the same again. Looks as if plymouth itself is not essential - now I have no Plymouth, no usplash, no xsplash. Boot times around 50s.

---

### Post by orlox on 2009-12-25
Am I just lost, or this is NOT supossed to work with the official nvidia drivers?? Perhaps the mountall problem is something aside, but as far as I know, plymouth requires kernel mode setting, which cannot be implemented in the official driver due to licensing issues. Also, I doubt the nv driver has any kms implemented into it...

The only hope in here is that nouveau matures enough to become a reasonable alternative to the official drivers (isn't it?)...

---

### Post by plun on 2009-12-25
> **orlox said:**
> 
The only hope in here is that nouveau matures enough to become a reasonable alternative to the official drivers (isn't it?)...

No the Nouveay driver is just plain crap with newer cards which the majority uses...  just a joke that Ubuntu should implement this crap.

---

### Post by orlox on 2009-12-25
> **plun said:**
> No the Nouveay driver is just plain crap with newer cards which the majority uses...  just a joke that Ubuntu should implement this crap.

I think I've heard this comment several times from your side...You didn't even answered my question properly, just went on a random rant about how much you think nouveau is crap.

Private drivers can't implement KMS because they have to link to libraries licensed under the GPL, not the LGPL. As such, only an open-source driver could comply with this, and enable a plymouth powered boot process. The other open-source alternative is the nv driver, but that thing is hardly modified, and probably has no kms support at all...

And on the other hand, nouveau is very crearly stated to be at an experimental stage, with no stable releases at all. It may work like crap for you, but atm, that's expected to happen to many people. I for myself think this drivers will mature in a short time, and become a very viable (if not better) alternative to the official ones.

---

### Post by cheesypoof on 2009-12-26
I get a similar boot message as previous posts. I end up at a root command line. I do not have plymouth installed, nor do I use any PPAs besides the nvidia 195 sevenmachine one. I connect to the internet wirelessly. I tried removing quiet splash, used fsck -f, and added noveau.modeset=0. When I startx, it tries for a couple seconds then fails and returns to root command line. Any advice on what I can do to correct this? Recovery mode does the same by the way...

---

### Post by Yellow Pasque on 2009-12-30
Same problem here. I installed the daily build today and haven't even been able to boot it to recovery console yet. $%@% Plymouth. I despise boot splash screens anyway.

---

### Post by MacUntu on 2009-12-30
Would be great to know if this is even supposed to work right now (given working KMS support). Currently I can only see the logo during shutdown if I've manually started Plymouth (sudo plymouth --show-splash).

---

### Post by plun on 2009-12-30
> **MacUntu said:**
> Would be great to know if this is even supposed to work right now (given working KMS support). Currently I can only see the logo during shutdown if I've manually started Plymouth (sudo plymouth --show-splash).

I dont believe its supposed to work.....  Nouveau breaks the real nVidia driver and must be blacklisted if nVidias driver is use.

Fedoraforums guide.

[http://forums.fedoraforum.org/showthread.php?t=204752](http://forums.fedoraforum.org/showthread.php?t=204752)

> this command adds rdblacklist=nouveau option to /boot/grub/grub.conf

Code:

su -
sed -i '/root=/s|$| rdblacklist=nouveau|' /boot/grub/grub.conf
mv /boot/initramfs-$(uname -r).img /boot/initramfs-$(uname -r)-nouveau.img
dracut /boot/initramfs-$(uname -r).img $(uname -r)



But this also kills Plymouth as I understands it.....

So this is real c***:-\" for me.... forcing users to something they doesn't want... maybe a few...

There are also some articles around the net about vga=ask which is deprecated with Grub2.

A challenge....:)

---

### Post by Jordanwb on 2009-12-31
> **ronacc said:**
> I'm getting the same mountall failure during boot and just before that usplash failure ,terminated , so I don't think it is plymouth that is the problem . my sys continues on to low graphics mode without action on my part .

I get the former every boot and the later sometimes. I'm using the OS drivers for my ATI Radeon X1200

> **Vanishing said:**
> What i found out is:
if you use plymouth now, you cannot take "quiet" and "splash" off the grub config(kernel line), if you take them off, there will be the mountall and plymouth issue.
try to add them back and boot, it should work, at least in my case it does.

I have the quiet and splash params set. So what was the temp fix? fsck-ing the file systems?

---

### Post by _khAttAm_ on 2010-01-30
I enabled quiet splash and Plymouth worked for me. I have Intel GMA 3100 on a Gigabyte G31.

---

