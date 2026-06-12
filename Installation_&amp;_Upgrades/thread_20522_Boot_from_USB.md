---
title: "Boot from USB"
date: 2005-03-17
forum: Installation &amp; Upgrades
---

### Post by pepposus on 2005-03-17
I've just installed Ubuntu, and the installation finished without error.
Now rebooting the computer i have this error
pivot_root: No such fileor directory
/sbin/init: 429: cannot open de/console: no such file
What can i do?
Thanky you in advance...
Gianni

---

### Post by nutubu on 2005-04-06
Finally, here are the steps to make an initrd.img file so that Ubuntu can boot from an external USB drive.

1) Install from CD
2) After installation, leave CD in drive and reboot with the parameter rescue
3) Pick your language and country
4) Wait for hardware detection to complete(was quite long on my system, seemed stuck for a while)
5) hostname: Ubuntu <enter>
6) Device to mount as root file system: /dev/discs/disc0/part2 (this may be different on your system. I have a boot partition in part1)
7) My system appears stuck here with a blue screen saying "Ubuntu Installer rescue mode"
8) Ctrl-Alt-F2 <enter>
9) mount -tproc proc /target/proc
10) chroot /target
11) su (optional, gives you a few niceties in term of shell)
12) If you have a boot partition: mount /dev/sda1 /boot
13) Add ehci_hcd on a line of /etc/mkinitrd/modules
14) Increase parameter DELAY in /etc/mkinitrd/mkinitrd.conf. I put 10 seconds and it worked.
14b) find the version of your kernel:
ls /lib/modules
15) create the initrd file:
mkinitrd -o /boot/initrd.img-<your kernel version here>-usb <your kernel version here>
16) Edit /boot/grub/menu.lst so that the initrd loaded by the default kernel is the one we've just generated.
initrd /initrd.img-<your kernel version here>-usb
initrd          /initrd.img-2.6.10-5-386-usb
17) If you have mounted a boot partition: umount /boot
18) Exit from chroot: exit
19) umount /target
20) reboot

Until they change the default initrd.img file to include module ehci_hcd, steps 2 to 20 have to be repeated each time the kernel gets updated.

---

### Post by nutubu on 2005-04-06
I am not 100% sure but I think the initrd is generic so the one I made with mkinitrd should work on all systems. I tried to attach it to this thread but it is too big. If anyone is interested, just ask.

---

### Post by pepejeria on 2005-04-26
I have the same problems as the original poster and tried to follow the steps described here, but since I am very new to linux I got stuck on step 12. I did all the steps before that.

[QUOTE=nutubu]
11) su (optional, gives you a few niceties in term of shell)
[/QUOTE]So I can totally skip this step above then?

[QUOTE=nutubu]
12) If you have a boot partition: mount /dev/sda1 /boot
[/QUOTE]I only created on partition on the usb hardrive. A 50 gig big one. Does this mean i have to this step or skip it?

[QUOTE=nutubu]
15) create the initrd file:
mkinitrd -o /boot/initrd.img-2.6.10-5.386-usb 2.6.10-5.386
[/QUOTE]When I did this i got the following error :
/usr/sbin/mkinitrd: /lib/modules/ 2.6.10-5.386 - Not a Directory
/usr/sbin/mkinitrd: MODULES Need to be set to none?

Did I miss something here?

---

### Post by nutubu on 2005-04-26
> When I did this i got the following error :
/usr/sbin/mkinitrd: /lib/modules/ 2.6.10-5.386 - Not a Directory
/usr/sbin/mkinitrd: MODULES Need to be set to none?
I guess the kernel version of your installation is not the same as with Hoary release candidate 5.04. Find the one you have installed.
```

ls /lib/modules

```
Then, replace 2.6.10-5.386 with your kernel version in steps 15 and 16.

15) create the initrd file:
mkinitrd -o /boot/initrd.img-<your kernel version here>-usb <your kernel version here>
16) Edit /boot/grub/menu.lst so that the initrd loaded by the default kernel is the one we've just generated.
initrd /initrd.img-<your kernel version here>-usb

bye

---

### Post by pepejeria on 2005-04-26
Yes, I found that out playing around a bit, and it works great now. Posting this from Ubuntu installed on my usb harddrive. Yiha!

Thank you very much for posting this solution and helping me out.

---

### Post by pepposus on 2005-05-03
:)  :)  :)  :)  :)  :) 
Yes, yes, yes..................
Now It's work!
Thank you very much nutubu

---

### Post by hexade on 2005-08-03
Is there any difference between the Ubuntu kernel and the Debian Sarge (2.6) kernel ? 
I've reached to boot Ubuntu from USB using *Nutubu*'s instructions, but it doesn't work using Debian... I thank that Ubuntu was Debian-based.

---

### Post by SamuraiMan1515 on 2005-08-10
[QUOTE=pepposus]I've just installed Ubuntu, and the installation finished without error.
Now rebooting the computer i have this error
pivot_root: No such fileor directory
/sbin/init: 428: cannot open de/console: no such file

I got the same error except mine had "428". I have did everything in the forum to, but I always get some kind of error. Can someone please help me out from step 15 and up. Also on step 19 it keeps saying the device is busy. I have XP on my main HD and I am trying to put ubuntu on my usb hd. Hope that is enough information for you, I really hope someone can help. I appreciate it!!!

---

### Post by Copter on 2005-08-12
hi!

nutubu's method is very nice i think. it also works on hoary 5.04.

my kernel is 2.6.10-5-686. you will have probably something very similar to this.

15) create the initrd file:
mkinitrd -o /boot/initrd.img-<your kernel version here>-usb <your kernel version here>

on my system it looked something like this:
```

mkinitrd -o /boot/initrd.img-2.6.10-5-686-usb 2.6.10-5-686
```
16) Edit /boot/grub/menu.lst so that the initrd loaded by the default kernel is the one we've just generated.

look for this
```

initrd /initrd.img-2.6.10-5-686
```
or this
```

initrd /boot/initrd.img-2.6.10-5-686
```
and change it to this
```

initrd /initrd.img-2.6.10-5-686-usb
```
17) If you have mounted a boot partition: umount /boot

18 ) Exit from chroot: exit

19) umount /target

here everytime i have also problems. i just ignore it. when system boots next time it will run root partition (or boot?) check for errors

20) reboot

it should work. good luck!

copter :]

BTW : try to install the system without any other hdds physically connected to your motherboard. i used to plug the power out of them. it eliminated some errors during installation / first boot. after ubuntu working ok plug their power back.

---

### Post by trekkie on 2005-09-06
HI, 
Im new to this, but i love ubuntu, so i though it would be kool to but it on thumb drive, so i came here,. i followed the inscructions, bu tno luck. can some one host (bitt torent, or even e-mail) me a disk image i could extract and be done. tnx

---

### Post by hexade on 2005-09-12
[QUOTE=nutubu]
13) Add ehci_hcd on a line of /etc/mkinitrd/modules
14) Increase parameter DELAY in /etc/mkinitrd/mkinitrd.conf. I put 10 seconds and it worked.
[/QUOTE]
Those files does not exist in Ubuntu 5.10 "The Breezy Badger"  :(

---

### Post by 11hjpphty76lkjj on 2005-09-14
Thank you nutubu.  I had searched for 2 weeks and tried many things, using your steps it worked perfectly.  If anyone has any issues using this process I'll help if at all possible.  It works, it rules. woohoo!

And for anyone very new trying to set this up, I used nano to edit the files in the steps. at the prompt, "nano <file_location><file_name>"

Thanks again!

Aaron

---

### Post by 11hjpphty76lkjj on 2005-09-14
Clean install using the steps above, worked perfectly.  I booted into Ubuntu great, can update, install whatever, no problem.  However when I shutdown the system on the next reboot I get:

root (hd0,0)
 Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinuz-2.6.10-5-386 root=/dev/sda1 ro quiet splash
    [Linux-bzImage, setup=0x1600, size=0x1209f6
initrd /boot/initrd.img-2.6.10-5-386-usb
    [Linux-initrd @ 0x1fb8f000, 0x460000 bytes
savedefault
boot
Uncompressing Linux...Ok, booting the kernel.
audit(1126739386.335:0) initialized
Starting Ubuntu...
Waiting for 10 seconds, press ENTER to obtain a shell.
sda: assuming drive cache: write through
sda: assuming drive cache: write though
 stopping tasks failed (1 tasks remaining)
***(lots of drive activity for a long time, 30-60 min)
Buffer I/O error on device sda, logical block 0
***(lots more drive activity 15-30 min)

eventually the kernel freaks out and Ubuntu doesn't load.

Then I boot from the install cd, rescue, go through all the motions until I'm at the console, and then reboot, I don't actually DO anything mind you.

then I get "non system disk or disk error"
then I reboot, again.

then Ubuntu loads as expected, I get I get into GNOME, and do my thing.  Then I shut down and it starts the process over.

This happens the same way everytime.  I've reinstalled several times using 2 different systems, same problem.  Any ideas?

So close..

Aaron

---

### Post by FuguFisch on 2005-09-15
Hello!
I tried everything you wrote in this thread, but i still get an error while booting.
It's not exactly the same that the others get, it says:

```
pivot_root: No such fileor directory
/sbin/init: **428**: cannot open de/console: no such file
```

After trying a few times with hoary I tried it with breezy, but that didn't get me any further.
Anybody some more ideas?
thx

---

### Post by 11hjpphty76lkjj on 2005-09-15
Sorry FuguFisch, wish I could help you with that one.  Can you post the entire boot message?  perhaps turn off quiet in the grub menu.lst and see if there are any other errors and post them.

a quick way to do that is this:

boot..
just before the grub menu appears press esc when prompted.
then highlight the boot item, and hit e (or was it b) I believe, then edit the kernel line and remove the quiet, then boot with the quiet off and post any errors.

As for my issue I think the problem is that the usb sub system is shutdown before the shutdown sequence is completed and is causing the drives to umount incorrectly.  Anyone have any ideas on how to get ubuntu to shutdown the usb system last? if that's possible?

ugh I want this to work already!

Aaron

---

### Post by 11hjpphty76lkjj on 2005-09-15
More research...

I found this at:
[http://forums.fedoraforum.org/showthread.php?t=63183](http://forums.fedoraforum.org/showthread.php?t=63183)

But the modules seem similiar to those in Fedora.  So we may need to load these modules in the modules file (if your usb us 1.0, etc.  although it might be a slow boot...)

ohci_hcd is for usb 1.0 - 1.1 controllers with certain chipsets.
uhci_hcd is for usb 1.0 - 1.1 controllers of other chipsets.
Either one should cover most of the 1.0 -1.1 controllers
ehci_hcd is for just about all 2.0 controllers.

Aaron

---

### Post by 11hjpphty76lkjj on 2005-09-15
Just a quick update if it might help anyone else, for some reason if I disconnect the USB drive just after it's detected (I have quiet mode OFF so I can see what's happening) and then reconnect it it seems to boot 100% of the time.  Odd...but it works.

Aaron

 \\:D/

---

### Post by FuguFisch on 2005-09-16
[QUOTE=kalosaurusrex]

ohci_hcd is for usb 1.0 - 1.1 controllers with certain chipsets.
uhci_hcd is for usb 1.0 - 1.1 controllers of other chipsets.
Either one should cover most of the 1.0 -1.1 controllers
ehci_hcd is for just about all 2.0 controllers.

Aaron[/QUOTE]

I added all of these Modules before, and quess what happend! ;) ahhhh!  ](*,) 

I'll try getting more error messages when i'm back at my machine.
Thank you!

---

### Post by 11hjpphty76lkjj on 2005-09-16
In the modules file try loading only:

ehci_hcd
usb-storage

That's what I'm using currently, and it seems mostly stable.  Every fresh boot Ubuntu doesn't see the hard drive (for some reason) but if I disconnect it and reconnect it after it loads the usb driver it will load fine on the next boot. /shrug

Aaron

---

### Post by 11hjpphty76lkjj on 2005-10-04
Just a small update.  I got a new and better USB hard drive enclosure which fixed all of my problems.  USB booting will not work correctly on cheap POS usb hard drive enslosures, so spend a little more and get a good one.  I spend 25 bucks on mine and it works great everytime.  No issues atall.  And I can boot from any other PC (usb enabled of course) with no problem.  However I do have to reconfigure xorg, but hey it works.

Aaron

---

### Post by RyanGT on 2005-10-12
One thing I had to do differently than the how to post at the beginning of this is to set up grub to use /boot/vmlinuz... and /boot/initrd... because I did not set up a seperate boot partition (which was probably a bad idea, but that is what guided partitioning gave).  So, if you get a message from grub that it cannot find your vmlinuz file, this may help.

---

### Post by 11hjpphty76lkjj on 2005-10-13
I've been trying to get breezy to work with USB boot.  Still having problems.

I added the usb modules (ehci_hcd, uhci_hcd, ohci_hcd, usb-storage) to the /etc/modules

I looked in the file /etc/mkinitramfs/initramfs.conf (which seems to be the next best place related to the hoary mkinitrd.conf) and there is no delay section. I tried putting one in there (after the modules section) and it still didn't work.  on boot it says something like:

ALERT! /dev/sda can't be found.  

And then drops to a shell.

So close..I can almost taste it...

mkinitramfs -o /boot/init...-kernel-usb <kernel> SEEMS to make the new initrd image. but for some reason it's not grabbing the usb modules on boot.

fyi quick vi reference; i - insert then ":wq" (save quit) enter.

Even better is that in the initramfs.conf it even says BOOT=local and in the description it says Hard Drive, USB, etc.  So USB should work?  ideas? thoughts?  We're close to a step by step here..

Someone else want to take a shot?

Aaron

---

### Post by m@gicBe@st on 2005-10-17
Argh. I'm trying to get 5.04 64bit for amd64 booting from usb hard drive. I've read most of the stuff on here and I'm stuck when I try to mkinitrd ... I get the following error message:

dpkg: 'warning on architecture 'amd64' table not in remapping table' 

The kernel under /lib/modules is reported as 2.6.10-6-amd64-k8 and the same under lib64.
I'm using a DVD disc (it boots and works fine on my system if I use 'live'). Help!! I've been trying to get this up and running for a couple of days now :(

I'm installing in expert mode and editing the files with Nano.

---

### Post by m@gicBe@st on 2005-10-18
Ignored the warnings and have a bootable installation now :)

---

### Post by harty83 on 2005-11-08
Hi there.  Been following along and I now have Ubuntu Breezy booting from an external with Grub installed on the external. Couple notes:

Number one: since grub was installed on the external, it recognized the external as hd0. Once Grub was able to boot ubuntu, I also was getting the error "Alert! /dev/sda1 does not exist. Dropping to a shell!"  I found a post here [http://www.ubuntuforums.org/showthread.php?t=57741](http://www.ubuntuforums.org/showthread.php?t=57741) that said "I fixed this myself by adding mptbase and mptscsih to /etc/mkinitramfs/modules and then running 'sudo mkinitramfs -o /boot/initrd.img-2.6.12-6-386.new /lib/modules/2.6.12-6-386'" I just saved the initrd as my original usb initrd.  

It then booted beautifully.

---

### Post by harty83 on 2005-11-08
sigh...so I lied.  I rebooted into the drive and what do you know, good ol sda1 can't be found.  Erg.

I remade the initrd.img file and it booted back into ubunut, no problem.  I wonder what would happen if I tried to reboot again....

---

### Post by harty83 on 2005-11-08
Okay so I found this post: [http://www.ubuntuforums.org/showthread.php?p=316338](http://www.ubuntuforums.org/showthread.php?p=316338)

I added atiixp to the modules file and now I'm booting every time.

---

### Post by harty83 on 2005-11-09
I'm a loser with lots to show for it.  I apologize.

It booted beautifully several times then, sigh, well you know.

I don't have time to mess with this so I'm going to Hoary with the hopes that someone figures this out soon.

---

### Post by kyachopstix on 2005-11-10
[QUOTE=nutubu]
12) If you have a boot partition: mount /dev/sda1 /boot
[/quote]It says:
mount: /dev/sda1 already mounted or /boot busy
mount: /according to mtab, /dev/sda1 is mounted on /

I hope that's fine?

[QUOTE=nutubu]
13) Add ehci_hcd on a line of /etc/mkinitrd/modules
14) Increase parameter DELAY in /etc/mkinitrd/mkinitrd.conf. I put 10 seconds and it worked.
16) Edit /boot/grub/menu.lst so that the initrd loaded by the default kernel is the one we've just generated.
initrd /initrd.img-<your kernel version here>-usb
initrd          /initrd.img-2.6.10-5-386-usb
[/QUOTE]
how do I do those steps? I'm new to linux sorry :(

edit:
also ... there's no file/folder '/etc/mkinitrd/modules' it's just 'scripts' what do i do?

---

### Post by tonysathre on 2005-11-21
open then with: sudo vi /etc/mkinitrd/modules and find the lines where things need to be modified or added in

for the other one do: sudo vi /boot/grub/menu.lst

---

