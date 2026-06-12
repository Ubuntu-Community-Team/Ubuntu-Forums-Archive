---
title: "broken 10.04 upgrade - 3 questions"
date: 2010-05-15
forum: Installation &amp; Upgrades
---

### Post by jazdrv on 2010-05-15
well, i've got three questions based on the fact that i tried to unsuccessfully upgrade to 10.04 and now can't get back into my ubuntu system from the grub menu. (none of the recovery options load either btw)

basically what happened is that when i was doing the upgrade, i lost power -- and when i tried to get back on again -- i cannot. the farthest it goes is the grub menu and from there the ubuntu logo and the 10.04 dots going back and forth. then just a black screen. 

i've checked the menu.lst file and the kernel files referenced there and all the stuff in /boot seems to correlate and be referenced properly. so i can't really discern where it's going awry after grub does the hand-off.

fortunately, i have a dual boot with windows xp. and so i set up wubi -- and have been able to access my partition via wubi and a chroot to the partition. (note that i'm on an acer eee without a disk drive.)

here's the technique i used once i'm in wubi to do the chroot.

i put this in my /etc/fstab so i have access to the old partition upon startup:
UUID=5a721404-f52c-4cda-b4a7-eafe090523a1 /mnt/z2 ext2 defaults 0 0

and, i run this when logged on via wubi:
sudo mount -o bind /dev /mnt/z2/dev 
sudo mount -t proc none /mnt/z2/proc 
sudo cp /etc/resolv.conf /mnt/z2/etc/resolv.conf 
sudo chroot /mnt/z2 su - myusername

so my first question, -- i'm a bit new to this chrooting concept. i extrapolated the above commands off of various write-ups i found on the internet from people having similar problems. i'm not really sure if i'm doing them right, but they do seem to work.  i am however getting this one error though: 

"Can not write log, openpty() failed (/dev/pts not mounted?)" 

so that's my first question: how to fix that? what's the mount command for that? as i don't see /dev/pts inside of my chroot area.

my 2nd question... once i do the chroot, as i stated most everything seems to work ok. but it would be nice to see my old gui ubuntu desktop the way it was (instead of the wubi one). is there a way to restore that look and feel once i've done the chroot?

my 3rd question... and perhaps the most difficult -- how can i successfully troubleshoot where my original login and startup is breaking down? i'm not sure how to troubleshoot it to be honest. perhaps a log file somewhere i can access to see what's screwy? or is there a way of just re-running the upgrade considering i'm in a chroot mode off of wubi that just fixes everything?

i've already tried all these commands without success:

sudo apt-get update
sudo apt-get upgrade 
sudo  aptitude upgrade
sudo apt-get -f  install
sudo dpkg --configure -a
sudo apt-get upgrade 			 		

when i first ran them they completed a whole bunch of setup thingees, but once they've run their course and no longer anything left to complete, i still can't login.

i also tried running the update manager (/usr/bin/update-manager from the cmd line) from the chrooted env, which just seems to endlessly run. it never finishes... so that doesn't resolve my login problem either.

any ideas from any sympathetic gurus out there?

---

### Post by davidmohammed on 2010-05-15
I wont answer the questions you posed directly.  Just the observation that you see the normal boot screen and then black screen.  

Can you see if you can get to the desktop by pressing shift when booting to display grub followed by e to edit your first kernel entry - can you confirm that it is the -32.21/22 kernel?

Remove the quiet splash and type nomodeset xforcevesa and then continue to boot.  Do you get to the desktop.

If you do can you open a terminal and type 
lspci | grep VGA and post the results here.

---

### Post by jazdrv on 2010-05-15
david, 

thank you for the thoughtful reply. 

i never did see the 32.22 kernel in the grub config nor any files in the /boot directory. it did say this, (see following lines) however in the config...

--------------------------------------------------------
title           Ubuntu 9.10, kernel 2.6.31-21-generic
uuid            5a721404-f52c-4cda-b4a7-eafe090523a1
kernel          /boot/vmlinuz-2.6.31-21-generic root=UUID=5a721404-f52c-4cda-b4a7-eafe090523a1 ro quiet splash
initrd          /boot/initrd.img-2.6.31-21-generic
quiet

title           Ubuntu 9.10, kernel 2.6.31-21-generic (recovery mode)
uuid            5a721404-f52c-4cda-b4a7-eafe090523a1
kernel          /boot/vmlinuz-2.6.31-21-generic root=UUID=5a721404-f52c-4cda-b4a7-eafe090523a1 ro  single
initrd          /boot/initrd.img-2.6.31-21-generic
--------------------------------------------------------

i say "did" because when i tried loading in with this kernel, it would always say something about how it couldn't mount -- and had a question of did you mount /dev or something like that.

for this reason, i took out these lines... and reverted back to 31-20 and the other lines for my testing which seemed to get alot farther. but, albeit still unsuccessfully.

i do have a backup of the menu.lst file with 31-21 references (and those kernel files in a backup directory) still intact though.

so i'll try rolling back and trying to do what you mentioned against that particular kernel.

be back in a bit with the results.

---

### Post by jazdrv on 2010-05-15
ok, here's the message when i try to get in with 32.21:

"mount: mounting on /dev failed - no such device090523a1"
"starting up..."

then it goes to an ubuntu screen.
then a black screen and hangs.

gonna try what you suggested now...

---

### Post by ken78724 on 2010-05-15
Hi, apologies, I'm unable to help you but wonder if the problem arises due to the grub loader. 

At least, know I'll be back here to see how you solved matters. Good luck! Ken

---

### Post by jazdrv on 2010-05-15
the latest on this:

taking out the "quiet splash" and setting it to "nomodeset xforcevesa" (as david suggested) reveals more information as to what's going on...

here's the kind of msgs i'm getting:

--------------
fsck from util.linux-ng 2.17.2

/dev/sda5 superblock last write time is in the future (by less time a daay, probably due to the hardware clock being inconsistently set) FIXED

/dev/sda was not cleanly unmounted. check forced.

/dev/sda5 deleted inode 26070604 has zero time. fixed
(repeats like 12 times or so)

/dev/sda5 unattached inode 9182349
/dev/sda5 unexpected inconsistency 

(and then some stuff about how i should run fsck manually without the -a and -p options.)
(and then it just stops doing anything)
--------------

so:

(1) i don't get to the point where i can type "lspci | grep VGA" 
(2) nor am i operating with 32.22...
(3) i'm having a file corruption problem (or disk corruption problem)
(4) i'm not sure if the file corruption thing is my only issue or not. i suspect not...

---------------

so based on this information, i've fired up wubi again, commented out the fstab line that mounts this partition, rebooted, and doing an fsck on the partition. and will try again.

here's the fsck results:

---------------

fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
/dev/sda5 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Unattached inode 9183459
Connect to /lost+found<y>? yes

Inode 9183459 ref count is 2, should be 1.  Fix<y>? yes
Pass 5: Checking group summary information
Block bitmap differences:  -11619423 -11619440 -28844032 -(28844040--28844046) -(28844061--28846079) -(28847088--28847345) -(28847480--28847940) +36739776 +36739790 +36759784
Fix<y>? yes

Free blocks count wrong for group #1121 (5, counted=2).
Fix<y>? yes

Free blocks count wrong (16878773, counted=16881518).
Fix<y>? yes

Inode bitmap differences:  -2670604 -2670606 -(2670609--2670610) -(2670612--2670614) -(2670631--2670632) -2670639 -2901741 -2902924 -7210338 +(9183458--9183459) +9186117
Fix<y>? yes

Free inodes count wrong for group #326 (7926, counted=7936).
Fix<y>? yes

Free inodes count wrong for group #354 (5030, counted=5032).
Fix<y>? yes

Directories count wrong for group #354 (400, counted=399).
Fix<y>? yes

Free inodes count wrong for group #880 (4991, counted=4992).
Fix<y>? yes

Free inodes count wrong for group #1121 (5286, counted=5283).
Fix<y>? yes

Free inodes count wrong (11317990, counted=11318000).
Fix<y>? yes


/dev/sda5: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda5: 1445136/12763136 files (1.6% non-contiguous), 34154971/51036489 blocks

------------------

gonna try booting it up again.... 

fingers are crossed. ;)

---

### Post by jazdrv on 2010-05-15
ok, seems the fsck cleaned up those file and index "issues". and, i'm seeing now an error that i've seen before (again after bypassing the quiet splash).

the error is:

"init: ureadahead-other main process (3147) terminated with status 4"

after that it can't go any further.

incidentally, when i don't do the quiet splash, it gives me an option to go into manual mode due to an external drive that it's asking me whether i want to skip mounting or not. and, when i press "M" for manual and type:

"lspci | grep VGA" on the command line, i get:

00:02.0 VGA compatible controller:
Intel Corp Mobile 9456ME Express Integrated Graphics Controller (rev 3)

i don't believe the file/index/fsck issues are my main problem. i think that's happening either because i'm starting/stopping the login with a hard restart (as it's my only option oftentimes) to get out of the error mode. or some other reason, not sure.

i see a couple bugs along these lines at launchpad.net interestingly...

ie:

[https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/580948](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/580948)

---

### Post by jazdrv on 2010-05-15
i see some encouraging discussion about this problem here:

[http://ubuntuforums.org/showthread.php?t=1343648&page=2](http://ubuntuforums.org/showthread.php?t=1343648&page=2)

seems to imply i should upgrade gdm.... but now i can't mount that drive at all!

dmesg | tail

[ 1284.317353] EXT2-fs: sda5: couldn't mount because of unsupported optional features (4).

:(

dang, i could before... what the???

---

### Post by jazdrv on 2010-05-15
ok, back where i started.

after a little playing around, i *can* still mount the partition from wubi. but, i still *cannot* login into it via grub. it doesn't appear that grub's config itself is the problem because it does infact go into the initialization process.

i see 2 errors:

"mount: mounting none on /dev failed"

-and-

"init: ureadahead-other main process (3147) terminated with status 4"

it doesn't continue after the latter error.

i *did* try upgrading gdm, but it's already up to date. and, it itself doesn't appear to do anything....

i'm truly at a loss as to how to resolve the 3rd of my questions. nor any of the others...

regarding the fsck issues, they seem to be ok. i think that all happened cuz i did the hard restarts in the middle of testing all this. doesn't appear to be my main problem...

so i'm pretty much where i was when i sent off my initial sos flag. hahaha. 

if anyone has anything else to add or something else i can try, i'd be truly grateful!

---

### Post by bluesscream on 2010-05-15
hi,
I ran into similar issues when I tried to upgrade a "heavy customized" (not to say "messed up") 9.10. My solution was an install via a 10.04 usb boot stick over the corrupted installation without formating/deleting partitions as far as possible. System folders were overwritten, but /home stayed untouched.
cheers

---

### Post by jazdrv on 2010-05-15
bluescream,

well, yes -- i may end up doing just that. hate thinking it'll come to that. i also have alot of customizations i'd hate to lose also... plus, for now i can access everything thru the wubi mount so it's workable. (just not optimal and convenient)

my latest thinking is i just need to rebuild the kernel.

i noticed just now that in my wubi setup where it installed 10.04 that the kernel is 32.21 and 32.22, but in my grub config for my old setup, it's 31.21 and less.

i tried to "hack" it by just copying over the kernel files from one to the other. and, adjusting the grub config. well, indeed this fixes the mount error i'm experiencing (that i mentioned in my other msgs). but, it  doesn't fix the "ureadahead" error.

i'm guessing therefore that those kernel files (from the wubi) won't work cuz they're compiled for ntfs. (and not ext3 on my proper linux partition). that would seem to be the obvious - duh! reason anyway... thus my thinking that i should just rebuild the kernel.

i should also add that i did try removing/re-installing gdm as people in the other forum dialog were alluding to (that i mentioned) for the ureadahead issue. but that also didn't work out.

i don't know much about all these different iterations of ubuntu. perhaps the 32.x kernels are required for 10.04? and perhaps my incomplete setup didn't finish rebuilding those kernels that they're suppose to point to...

---

### Post by jazdrv on 2010-05-15
hmm, well i've been following these instructions...

[http://linuxtweaking.blogspot.com/2010/05/how-to-compile-kernel-on-ubuntu-1004.html](http://linuxtweaking.blogspot.com/2010/05/how-to-compile-kernel-on-ubuntu-1004.html)

and it just occurred to me, perhaps it's not "possible" to build an ext3 kernel when i've logged in with wubi and chrooted to a ext3 partition?

i guess i'm about to find out! (but if someone wants to tell me, might save me some time...)

hahaha

---

### Post by davidmohammed on 2010-05-16
just a quick question - since you've now found out (well done for getting this far!) you've got intel graphics,  have you tried booting with either

i915.modeset=0

or 

i915.modeset=1

instead of quiet splash in your grub ? - you might want to try also appending xforcevesa to the above options

I've read else where, one of the options above usually works with 945 intel graphics.

---

### Post by jazdrv on 2010-05-16
david,

haven't yet tried that. (will do next though...)

but a little update on where things stand.

i did try recreating the kernel last night. it does seem to get me a bit farther, but not all the way. i've been prompted for some dialog boxes about my graphics setup. but still haven't been able to punch thru.

the kernels i tried transplanting from my wubi install still stop at the ureadahead error.

i should say that all kernel options show a ureadahead error. just that the new one allows me to get a bit farther along (albeit i need to wait)

one more thing... i've now just uninstalled gdm based on rereading that forum i aforementioned. one person seemed to say that someone got through by *uninstalling* it. i truly don't know what uninstalling it will do however. it seems to convey that i lose ubuntu_desktop in the process when i watch the resulting msgs rolling down my screen.

still plugging away at this... again as i mentioned, i'll try your suggestion next david...

---

### Post by jazdrv on 2010-05-16
david,

the "i915.modeset=1" command seems to adjust the fonts properly on the screen. the "i915.modeset=0" makes it flicker green a little bit, but doesn't seem to adjust the fonts right like the other setting.

unfortunately though that's the only goodness it brings me.

lately, i can't get past the ureadahead error at all even with the new kernel!

still testing...

---

### Post by davidmohammed on 2010-05-16
sounds very intense - I'm intrigued - why are you trying to build a brand new kernel rather than using the [default lucid kernels]("http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=M;O=D") and then inserting what ever modules you need to change?

Are you using something [like this]("http://blog.avirtualhome.com/2010/05/05/how-to-compile-a-ubuntu-lucid-kernel/") to compile?

---

### Post by jazdrv on 2010-05-16
still plugging on this. thanks for the occasional tips david. i get by, but i'm certainly no guru on the inner workings of ubuntu. much less the kernel. so the ideas mentioned are very informative and helpful.

the latest...

well, i've realized the ureadahead error happens when i escape out of the splash screen. it's not necessarily itself an error per se in my situation. perhaps i mentioned this in a prior msg.

i've been trying to relogon with the new kernel i put together last night. i'd say 1 out of 5 times it doesn't hang and brings me to a login screen. it gives me mouse access, but not keyboard access. it also says there's a problem with gnome power manager.

i'm going  to try redoing the kernel again with the technique you specified to see if that makes a difference.

one thing that's a bit odd is that on this new kernel it gives me the message: "resume: libcrypt-version" when it first starts to mount.

just going to be watching the playoffs here and try to fix this the next couple of hours while i do...

---

### Post by jazdrv on 2010-05-17
the latest - i did build a new kernel a 2nd time. this time with git and the instructions that david kindly forwarded to me.

it seems to be a better kernel. it seems faster. but, it -- like the first one i built -- doesn't give me keyboard ability at the gui login.

so close but still not quite yet resolved...

/z

---

### Post by jazdrv on 2010-05-21
ok, i've been looking at this while doing other things... and, i have figured this out to some extent.

i now got it so that i can actually login and the keyboard *does* work while i do it. and, that's without wubi.

i'm guessing this is how i did it...

i read somewhere about how the following commands are in some ways a more "complete" way of upgrading the system. cuz the "sudo apt-get upgrade" doesn't upgrade all apparently. there are some packages that are held back when i try to do the normal upgrade.

so i was thinking perhaps because it's a new distro, i should do these too. these are the commands:

sudo apt-get install openssh-blacklist
sudo aptitude dist-upgrade
sudo apt-get distro-upgrade

anyway, afterwards i tried it again. and yep -- i can login!

it's not perfect, mind you. through all this back and forth of trial and error, i uninstalled my ubuntu-desktop (and reinstalled it). so i don't have what i had before. nor do i have the sexy 10.04 look and feel that you get with a fresh install.

but -- it works. i can login without wubi and doing a chroot. and, i didn't have to reinstall over my exisiting partition.

and, that's essentially what i wanted.

---

### Post by pete_m on 2010-06-11
fascinating thread -- thanks - my broken upgrade dies on boot after ..
need recovery on readonly volume
successfull y tunning init-bottom
fsck.ext3 reporting clean 9 i've done sucessful fsck on unmounted sda1 from USB-booted eb4.

there seem to be issues round plymouth/ upstart  .. anyone come across these ?
and might they relate to the thread's original impetus?  ( i've been lurking ! )

i'll be tryiing the i915 tip,, and learning more about chroot from the notes here.. will keep y'all posted..

[screenshot here]("http://www.youtube.com/watch?v=YoI4wRVVjBs") of my ( presently interrupted ) work in progress

i'm working on an eee pc  I'd successfully updated my kernel to 2.6.32.22 having been running 2.6.24.21 for some time.
 i'd already destroyed older kernel-versions to save space 
and successfully installed grub2 to help with the preparation of USB sticks


observations n wisdom much appreciated . . 

P.S i too had been hit with ureadahead problems also round consolekit libc6 n firends, mountall,upstart and udev
follwing threads about Debian dependency-based Boot . . missing LSB

at that point the upgrade was stalled - probly 'cos some stuff had been looking at Sid-style stuff, tho' i now understand  that Ubuntu is usually sid-based anyway.   . .hmm

i broke the logjam by downgrading insserv and sysvinit and then the upgrade proceeded . .and all seemed good till reboot

 changed SYS -> ATTR in some init complainers to get as far as  i now have. 
i

---

