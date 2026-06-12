---
title: "Replacing the files vmlinuz and initrd.gz?"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by dab on 2007-10-25
Alright! I've spent the day sick and then ended it by becoming even more exhausted looking for solutions to my room mates problems but, no avail. Except that I've got this Live CD of Ubuntu 7.04 running--which is nice, but doesn't treat my room mate nicely--as far as her classes go.

Ok -- so, I am attempting to satisfy GRUB's problems and linux's problems.

 See the files that are mentioned in Grub's menu.lst file were never downloaded during the upgrade from 7.04 to 7.10 -- I know because Grub complains about it with Error 15: file not found.

The all-consuming question of my post: Where can I find the files vmlinuz-2.6.22-14-generic and initrd.img-2.6.22-14-generic?

 Secondary question: When I get these files in a place where grub will recognize and run 
these files, is this all that is necessary to get a working copy of Ubuntu 7.10 working?

 Secondary question: Is there anything that could possibly be more familiar or comfortable to my friend, a student, so that she can get things done? The upgrade to 7.10 is really messing things up for her. I have access to the drive -- where is Firefox's bookmarks folder, is there better way to find it than the 'find' toolbar provided by 7.04?

 Secondary question: Can I downgrade from 7.10 to 7.04 somehow?

 Secondary question: Is there some sort of automated repair process that any one can point me to?

 Anyway... on with my progress so far (not much):

 Using grub's 'install' commands and the menu.lst file -- I attempted to load the 7.04 files (vmlinuz and initrd.img) in hopes of getting a system that would work from the hard drive, but that's not happening--guess the 7.04 vmlinuz and initrd.img files are looking for things that were removed by the 7.10-upgrade process?

 This is all a reference to a previous question which no one seems interested in answering any more. Called [_"Should I let my friend restart her computer?"_]("http://ubuntuforums.org/showthread.php?t=586637")

 Thanks for your time,

 Dominick


 -- here's what that menu.lst file looks like, in case any one is interested. The only thing that actually works is the memtest86+ file. The files I am looking for are mentioned here by whatever application the 7.10 upgrade and are _underlined_.

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		_/boot/vmlinuz-2.6.22-14-generic_ root=UUID=7e5a6bb4-8e09-49ca-a804-c4b08e0644d3 ro quiet splash
initrd		_/boot/initrd.img-2.6.22-14-generic_
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7e5a6bb4-8e09-49ca-a804-c4b08e0644d3 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=7e5a6bb4-8e09-49ca-a804-c4b08e0644d3 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=7e5a6bb4-8e09-49ca-a804-c4b08e0644d3 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

---

### Post by sixela on 2007-11-26
Hi I am a Gutsy newb,

I pretty much have the same problem as the above which was posted 4 weeks ago.

I accidentally was messing around with my /boot partition and ended up losing 
vmlinuz-2.6.22-14-generic and initrd.img-2.6.22-14-generic

:(

**How exactly can I get these files back?**

Is it as simple as downloading the two files and placing tham back in my boot partition?

:confused:

Been scouring the internets...no luck. Any help or a point in the right direction would be much appreciated.

Thanks.:)

---

### Post by sixela on 2007-11-27
Seriously anyone at all? I am having to access my computer through...<gulp>...windows.:(

---

### Post by sixela on 2007-11-27
[B]Ok solved my own problem...
[/B]
:KS

to get said files, I simply did a virtual gutsy install on vmware running in windows. Copied the files from the /boot that I needed onto an SD card.

The booted with puppy linux, and transferred files from SD card to the /boot directory of my original ubuntu install.

I'm sure someone has a more eloquent command line driven way of doing this, so please let me know if possible.

Hope this helps someone anyways.
:)

---

### Post by mondomunchies on 2007-12-15
Is it possible for someone that has these files to post them as attachments?  That would be much faster and less painful I think.

I deleted those files too. I guess I should be backing everything up.

---

