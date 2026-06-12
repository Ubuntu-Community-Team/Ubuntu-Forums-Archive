---
title: "HFS partition disappears sometimes (MacOS/Linux dualboot)"
date: 2015-09-02
forum: MINT
---

### Post by etienne.bouvier on 2015-09-02
Hello,

I have got problems with a HFS partition on my hard drive.   When I use some command on this partition, it disappears from my files  system and cannot be unmounted - nor mounted. Sometimes only some  folders of the partition disappear. I use a dual boot on my MacBook 2.1  between MacOS 10.6.8 and Linux Mint Cinnamon 17.2 32 bits (since 2 weeks,  Linux is quite new for me). I have 3 partitions :
- MacOS partition  (440 Go) which contains all my documents, formatted in HFS,  journalization inactivated in order to be writeable from Linux  Partition.
- Linux partition (40 Go), in ext3
- Swap (3 Go)

In  Linux Mint, I have modified /etc/fstab file to automatically mount the  MacOS partition. I did it thanks to various fora, using mtab to see with  which options Mint mounts this partition. The added fstab line is :
UUID=30f0e226-8086-3403-89d6-cdb642eccf18 /mnt/DisqueMacOS hfsplus rw,nosuid,nodev,uhelper=udisks2 0 0

I have also added lines in my /etc/rc.local file in order to bind documents folder in the linux home with the MacOS folders :
mount --bind /mnt/DisqueMacOS/Users/Girafenaine/Documents /home/Girafenaine/Documents
mount --bind /mnt/DisqueMacOS/Users/Girafenaine/Music /home/Girafenaine/Musique - and so on

When  I run Linux Mint, the automatic mounting works and I can access all my  documents (which is great) at the beginning. I can read and write them.  But after some operations or command, either some folders or all of them  disappear. This problem occurs on one session out of two or three. For  instance : after running Banshee on my Music folders, the content of some  folders disappear from Nemo and cannot be found, as if they were deleted  (but actually they appear again after a reboot). Or : after using  "locate" command on this partition, the whole partition may disappear from  Nemo. I don't get any error message. It is seen as mounted in the Disks  utility, but the mounting point is empty in Nemo, and I cannot unmounted  the partition (error : Error unmounting /dev/sda2: Command-line `umount   "/dev/sda2"' exited with non-zero exit status 1: umount:  /mnt/DisqueMacOS: not mounted (udisks-error-quark, 0)). I have to reboot  to find the partition and my documents again.

Is anyone able to help me with this strange "unstable" HFS partition ?

Girafenaine

---

### Post by este.el.paz on 2015-09-04
@EB:

I don't have enough knowledge to read all of your post details, but, first thing, these days the linux partition is formatted "ext4" not "ext3" . . .  and, on my triple boot 09 MBPro 5,4 I found that "Cinnamon" is a little too demanding for my processor . . . I use MATE flavor DE, much more stable . . . .  I don't have "cross platform" read/write from OSX to linux, but, also OSX should be "HFS+" these days, no??  "journaled, extended" . . . .  Best of luck.

e..p

---

### Post by etienne.bouvier on 2015-09-05
Thanks este.el.paz for your message.

You're right : actually it is an ext4 formatted Linux Mint partition, and an HFS+ MacOS partition (not journaled, in order to be writable from Linux).

I didn't know that mate was less demanding that cinnamon, I could try. But as I begun with Linux 2 weeks ago, I am going on carefully, step by step... perhaps I will understand this cinnamon before changing for something else.

My HFS+ partition is still unstable, with folders disappearing when some applications access files on this partition. I am trying two changes :
- fstab line modified : UUID=30f0e226-8086-3403-89d6-cdb642eccf18 /mnt/DisqueMacOS hfsplus force,rw,user,umask=022 0 0
- Linux main user group id changed from 1000 to 501 to match Mac OS main user group id (the user id was already changed from 1000 to 501)
I will tell if it changes anything...

Girafenaine

---

### Post by coffeecat on 2015-09-05
*Thread moved to **MINT**.*

---

### Post by este.el.paz on 2015-09-05
@EB:

. . . it seems like "you've got skills" but it does seem like the "general wisdom" is that as far as OSX is concerned, "It's too ships passing in the night and the twain shall never meet."  You've possibly done something that works for windows and linux, but is creating problems for OSX in whatever it is you have done.  Someone else might be able to provide comment on the exact commands; actually someone named "sensei" something or other, posted in a thread I was involved with and suggested that the application "MacFUSE" or "OSXFUSE" was an application that could be used to write OSX files in Linux, but that to try to write linux in OSX . . . could be done, but, which could cause "instability" in OSX . . . .  See if you can find that app, or the thread with my name and see if you can find it.  If you can't I'll look to see if I could find it.

Point being, I think it's better to format OSX as HFS+ (journaled, extended) and linux as (ext4) and not try to share files . . . unless you find this FUSE app . . . OR, possibly better, run linux in virtual app.  And, yeah, "32 bit Cinnamon" . . . sort of oxymoronic . . . .  Cinnamon is all about flash . . . no point in running it in 32 bit.  Try MATE or XFCE . . . they are very nice . . . and stable.
e.e.p.

---

### Post by etienne.bouvier on 2015-09-07
Hello e.e.p,

Thank you for your attention and your help. I will give a try to this "...fuse" to see if it can help me. But the described "instability" seems to be deeper in the system, probably because of HFS+ management by Linux Mint.

The 32 bits is because I didn't succeed with a 64 bits installation on my MacBook 2,1 (the USB or DVD was not seen at starting, even with rEFInd). There is no reason why 32 bits could work better on such a MacBook as I understood through fora and ubuntu pages, but indeed it did... That's said, I note what you told me : Mate and xfce are stable and nice options !

My philosophy (at the present time) : I like my MacOS 10.6.8, but it doesn't run safe safari or firefox anymore (no more updates). My MacBook cannot run a newer version of MacOS. And I like changes. The MacBook is beautiful and does work, so I just need another OS to go on the net and try something new. That's how I came to Linux. Then I gave a try to Linux Mint, and it seems to be good, so I try to make it run "as I want"... and of course I need my documents (music, pictures, the whole "home") under both MacOS and Linux Mint, and HFS+ without journalization is the only way to set the system. Perhaps later I will step forward and try other things in the Linux world !

---

### Post by este.el.paz on 2015-09-07
> **etienne.bouvier said:**
> Hello e.e.p,

Thank you for your attention and your help. I will give a try to this "...fuse" to see if it can help me. But the described "instability" seems to be deeper in the system, probably because of HFS+ management by Linux Mint.

Yes.  Try to find that application, that should provide some read/write capacity back and forth, but saying again, OSX doesn't like to "play with others" so I think you will have problems if you try to use linux to run OSX files.

> The 32 bits is because I didn't succeed with a 64 bits installation on my MacBook 2,1 (the USB or DVD was not seen at starting, even with rEFInd). There is no reason why 32 bits could work better on such a MacBook as I understood through fora and ubuntu pages, but indeed it did... That's said, I note what you told me : Mate and xfce are stable and nice options !

I think that the MacBook 2,1 is probably 32 bit machine.

> My philosophy (at the present time) : I like my MacOS 10.6.8, but it doesn't run safe safari or firefox anymore (no more updates). My MacBook cannot run a newer version of MacOS. And I like changes. The MacBook is beautiful and does work, so I just need another OS to go on the net and try something new. That's how I came to Linux. Then I gave a try to Linux Mint, and it seems to be good, so I try to make it run "as I want"... and of course I need my documents (music, pictures, the whole "home") under both MacOS and Linux Mint, and HFS+ without journalization is the only way to set the system. Perhaps later I will step forward and try other things in the Linux world !

I understand very well the "why" of what you are doing in terms of "no more support" . . . but I run a triple boot set up on my MBPro with the default partition being 10.6.8 and I am still getting FF updates for it, but without this OSXFUSE or MacFUSE app I don't think you can ***safely*** share files or apps back and forth.  Best possible option would be to get Parallels or VMFusionware and run a "linux" window inside OSX . . . no problems with "fan control" and or other stuff to think about when the Apple is running OSX.

e.e.p.

---

### Post by etienne.bouvier on 2015-09-08
Hello e.e.p,

Thank you for your message. I checked online and OSXfuse seems to be a Mac app to be able to deal with non native partition formatting. It would not be a package for any Linux distribution.

MacBook 2,1 has got a 64 bits processor (which make it able to run 64 bits apps and should make it able to run 64 bits Linux distribution), but a 32 bits EFI (that may mess into the installation...). I don't know more about that and probably I do not need :)

Your experience with MacOS 10.6.8 is interesting for me. On my firefox (under MacOS 10.6.8), I cannot run a simple gmail.com page because "I use an old version that is no more supported". I can run a lot of pages but there is often slow display or missing parts of the page.

Eventually the Parallels solution for a virtual Linux on my MacBook sounds good. I will probably try it soon ! However... after a few weeks with Linux Mint... I like it (except for these HFSplus files management, it is great) and I think about what will be my next laptop ! (I am not sure MacOS is changing in a more user friendly and efficient way through his last versions).

Girafenaine

---

### Post by este.el.paz on 2015-09-08
> **etienne.bouvier said:**
> Hello e.e.p,

Thank you for your message. I checked online and OSXfuse seems to be a Mac app to be able to deal with non native partition formatting. It would not be a package for any Linux distribution.
Your experience with MacOS 10.6.8 is interesting for me. On my firefox (under MacOS 10.6.8), I cannot run a simple gmail.com page because "I use an old version that is no more supported". I can run a lot of pages but there is often slow display or missing parts of the page.
Eventually the Parallels solution for a virtual Linux on my MacBook sounds good. I will probably try it soon ! However... after a few weeks with Linux Mint... I like it (except for these HFSplus files management, it is great) and I think about what will be my next laptop ! (I am not sure MacOS is changing in a more user friendly and efficient way through his last versions).

Girafenaine

@E.B:

OK, sounds like OSXfuse is the app that "sensei xxxx" referred to, "non-native" to OSX is anything that is not OSX, so I believe it is installed on the OSX side, and it can be then used to "read" files on both sides; to "write" on both sides takes some gambling apparently.
On the FF in 10.6.8 . . . I do see these Gmail "no longer supported" windows in my PPC systems, but so far not yet in 10.6.8.  You could try to move up a notch to 10.7 or 10.8 whenever you can't get FF upgrade.  That's what my "triple boot" set up is about, 10.6.8 I can still use Appleworks for some older docs, so I have one OSX partition set up for that, and then another with rEFInd installed that I have 10.9.4??? and then 50 GB that is now running LM Rebecca MATE.  I can move files back and forth between the two OSX partitions obviously, but don't waste time or money trying to get back and forth between OSX and linux.  You seem to have found one of the reasons why that isn't the best way to go.
And, yeah, I will check other options to compare, although in the dabbling in other OSs, OSX is a very nice operating system, very stable and is . . . has been, my "native" system.

e.e.p.

---

### Post by etienne.bouvier on 2015-09-10
Hello,

Thank you again for your message.

I have to thank you for your observation about firefox under MacOS 10.6.8. I tried, updated and now have a fine firefox under MacOS 10.6.8 (with no "no longer supported" message). I was probably stuck with safari, which cannot be updated under 10.6.8. So my MacOS is perfectly running and I can do all that I need with it... (I also updated Calibre and Alfred and that's perfect).

As far as Ubuntu (or Mint, it's probably the same with both OS) and MacOS are concerned : I tried and I like, so I will probably keep this dualboot on my Macbook for a while, and after a few months I will perhaps make a choice between these OS. Linux Mint is sure less stable than MacOS 10.6.8, and I have to try and understand a lot of things to make the whole thing running... But I have a little time, and find it interesting to learn about Linux world. I know I will use it in the future, on older machines, or by choice if Apple does not change for better.

Girafenaine

---

### Post by este.el.paz on 2015-09-11
@e.b:

That's good news on the upgrade to FF, yeah, it should be OK in 10.6.8 for a little while longer, 10.6.8 is a very good OS.

And, yes, lots to do and explore in the linux world, always something new coming along, it's definitely more "dynamic" . . . but, then the price is not always stable or sometimes things break.  Have to keep a sense of humor, that's why I think for Apple users, "dual boot" . . . or "triple" is the way to go.

But, back to my reminder to try adding a DE or two, on top of your LM base Cinnamon, it's very easy, and then you just "log in" and out of DE sessions . . . just gives yet another "flavor" to taste on the olde machine . . . .  : - )

Enjoy.

e...

---

### Post by este.el.paz on 2015-09-12
@e.b:

One final word, stating what so far has not been overtly stated; if your HFS partition continues to disappear with LM, try to do an experiment and try to do an install/re-install of your set up ***the same way that you did the first time*** . . . except try using Xubuntu or Lubuntu, probably 14.04 would be fine, but you could try 12.04 . . . and then see if that fixes your problem.  If it doesn't, you would then completely qualify to post here, at least back on the Apple Hardware forum, or if that doesn't even get a reply, then the Lubuntu Users List Serve has some very knowledgeable people that might be able to help out. 

Once you get comfortable with doing dualboot installs you'll see that it doesn't take too much time to erase and install a new system.  That has been the required method for LM up until recently . . . and often times if something goes wrong somewhere it is easier to just wipe the old and install the new than it is to try to find the exact problem. Destroy the old, enjoy the new . . . test drive one of the ubuntu flavors and you will be welcomed with hugs and kisses . . . and, hopefully some more help.  Main thing would be to try to get some technical comment on what you have tried to do with the HFS partition, beyond my "that don't work that way" . . . which I think is correct, but I don't exactly know why in command line lingo.  And, if Mohammad won't come to the mountain, bring the ubuntu to Mohammad . . . .  Simple.

e.e.p.

---

