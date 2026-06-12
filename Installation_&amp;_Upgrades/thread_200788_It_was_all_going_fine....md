---
title: "It was all going fine..."
date: 2006-06-20
forum: Installation &amp; Upgrades
---

### Post by iglablues on 2006-06-20
Firstly, I tried, I really tried, to find some info on this stuff online but the instructions were either very brief and assumed much more Linux knowledge than I have, or weren't specific enough to my issue (eg: live cds). I'm terribly stuck. 

I installed Ubuntu on a pc using an AMD Sempron 2800, 1 gig mem, and a 160gb hdd. I used a dvd that came with The Linux Bible, and burned the iso and everything. I got it installed, and it was working fine. I then did some updates- not command-line but using the desktop update utitlity, and I know for a fact that one of my updates was to a different version of Ubuntu. It hung at the "Ok...booting the kernel" part like so many others have noted. I can't figure out for the life of me how to do what has been suggested with turning off apci and such. I don't know where to enter that info or anything; I'm a complete newb at this. I rebooted it the first time it happened, and all was well. I just turned it back on after doing some more updating (this command to be exact: apt-get install nvidia-settings nvidia-glx linux-restricted-modules-686
nvidia-glx-config enable), and it's back to its old hanging at the kernel ways. 

I then hit Esc during the boot sequence and got into this place where I could obviously edit some stuff, but again I couldn't tell where exactly I would put any of the commands I'd seen online. I then decided to choose the latest kernel version (version 2.6.15-23-386) in what was called Rescue Mode, and it stopped at : Kernel panic- not syncing: no init found. Try passing init=option to kernel".

:confused: What? I don't understand any of what's happening. I started off with a nice, functioning version of Ubuntu and was psyched to be entering Linux-world finally, I did a little hold-me-by-the-hand updating, and now I'm stuck. 

Anyone? Please? And in simple, 5 year-old language if you could...

---

### Post by iglablues on 2006-06-20
Also, if it helps any...I've been playing around and I hit Esc to get to the grub. It shows:

root (hd0,0)
kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash
initrd /boot/initrd.img-2.6.15-23-386
saveddefault
boot

I noticed that the hd numbers in the first two lines are different, so I changed it in the kernel line to match what's in the root line (/dev/hda0) and it got as far as the Ubuntu splash screen, and then hung around "searching for boot files" or something along those lines. I have only 2 partitions on this hard drive: a giant one that I intended to use for Myth, and a smaller one for the OS itself.

---

### Post by jmr on 2006-06-20
OK. You already know how to edit the grub options, fine.  That is where you might pass new kernel parameters such as acpi=off and stuff.  Now, that last change you did (/dev/hda1 -> /dev/hda0) really didn't help, although I understand the reasoning.  Actually it was correct previously.  To grub, hd0,0  means the first partition of the first hard drive.  To the kernel that is written /dev/hda1.  (Not very coherent, I know, but that's the way things are.)

So, try editing grub to:

root (hd0,0)
kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro splash **acpi=off**
initrd /boot/initrd.img-2.6.15-23-386
saveddefault
boot

Or use other kernel options that have been suggested.  Please take care with proper spelling of the options. After editing remember to instruct grub to boot (by pressing B).  These modifications won't be persistent.  If it works you might want to permanently change grub by editing /boot/grub/menu.lst.

If the problem is indeed ACPI related, there may be a real solution but this is quite more involved.  Search for "ACPI" and/or "DSDT" and you should get an idea.

You mentioned you only have two partitions, none for swap space, is that right?  You can certainly run Linux without a swap partition but I can't remember the last time I tried that, and I suspect some distributions might be somewhat uncooperative under such conditions.  Maybe you should consider creating a swap partition.

Hope this helps.

João Rodrigues

---

### Post by iglablues on 2006-06-20
Thanks. I will try this as soon as I get done with memtest; it was the only thing I hadn't tried yet, and it apparently takes a while.

---

### Post by bodhi.zazen on 2006-06-21
I was reading your post. Grub and LInux use differnet numbering systems for partitions/hard drives. 

Here is a brief run-down on GRUB

[http://www.faqs.org/docs/Linux-mini/Multiboot-with-GRUB.html](http://www.faqs.org/docs/Linux-mini/Multiboot-with-GRUB.html)

You will need to change the numbering back to what it was

root (hd0,0)
kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash

You can eliminate the savedefault line if you like.

Note: Tried to reply earlier, but hte Ubuntu servers were too busy.

---

### Post by iglablues on 2006-06-22
Well, the memtest took days, literally. I finally was able to go in tonight and try some edits as suggested. Adding the straight acpi=off took me a little further, but only immediately to the following error message:

"kernel panic- not syncing: no init found. Try passing ini=option to kernel"

I went back in and just for the heck of it (because I noticed this line was different in your post jmr, I took out the "quiet" in my splash and added acpi=off to that. That got me a much longer list of progress, but still eventually took me to the kernel panic line, where it hangs. 

So, if I'm reading this right, there's a file -init?-  that's needed to boot, and it can't be found. How do I manually find it and point grub to it?

---

### Post by iglablues on 2006-06-22
I'm terribly frustrated at this point. It really blows to have it working one minute, do an "update", and have it stop working. I wanna go back to Breezy and stay there; forget Dapper. Is there a manual way to do this, besides slaving my drive to a Windows machine and reformatting it and starting from scratch? None of the earlier kernels in my boot list work either, and I tried to boot from a Knoppix cd and that bit the big one as well. I just want to start over.

---

### Post by jmr on 2006-06-23
Maybe you should try a clean install of 6.06, I don't think you need to revert to Breezy.  If you can boot from the Live/install 6.06 CD, then there should be nothing wrong with Dapper.  Your problem probably came from an incomplete upgrade that left incompatible drivers installed, or something.

If you have a backup of your previous /home directories, or these are in a separate partition, then installing from scratch is a reasonably simple option.  Just boot from the CD, answer the trivial questions, and when you get to the partitioning stage select manual partitioning.  You have to be careful with what you do then.  It's not dificult but you should feel you understand what you're doing.  You probably already have the partitions in place and possibly don't even need to resize them.  If you have partitions with other OSes or other info you'd like to keep, avoid resizing or altering them in any way, if you can.  Otherwise, backing up  is *highly* recommended.  You'll certainly find tutorials/howtos on this if you search a bit.  If you feel unsure, post your current partition table as displayed by the partitioning program (what partitions you have, what data each one has or is meant for, etc).  This will help other people suggest the best course of action.

- I'm assuming you can boot &.06 from the CD.  If not, it's a whole different problem.
- Also, I assume memtest did not report any errors.  If it did, then you almost surely have defective hardware.

João Rodrigues

---

### Post by iglablues on 2006-06-26
Thanks for the suggestions and links. Here's where I am, if you don't mind throwing a little more brainpower this way:

I downloaded the alternate version (not desktop or server) and tried to boot from that. It gave me the same error message about the init file, and I tried to install using the OEM mode and the text mode. I am also unable to use any of the rescue mode boots I see in Grub, each one giving me the same error message stated above. 

I got some advice on how to pass the init value, so I entered init=/sbin/init in the boot line. That worked and got me as far as the Ubuntu splash screen, but it went back to a text menu and gave me a rundown of this:

INIT:version 2.86 booting
INIT: Entering runlevel: 2
INIT: Id"1" respawning too fast: disabled for 5 minutes

It goes all the way through Id 6, and then it says:

INIT: no more processes left in this runlevel


-What does this new error mean?
-If there's something I'm missing in the cd options to fix my current install and move on, could someone let me know? 
-If not, could someone point me to some info on how to overwrite my existing install of Ubuntu with a new 6.06? Again, neither of the install options I chose on the cd worked. I still got an init error message. I would assume that I could somehow pass it the same parameters I passed earlier (/sbin/init) to get somewhere, but if it's looking at the same file, that still won't get me very far as it appears to be...damaged? Missing?

---

### Post by bodhi.zazen on 2006-06-26
iglablues:

I do not know the meaning of your error messages. If the CD will not boot, however, you likely have a bad CD. Check the MD5 sum of your downloaded Ubuntu iso. If it is OK, re-burn the CD. If it is not re-download the iso and re-burn the CD.

Once the CD boots you can try to the repair your Ubuntu installation. If this fails, my advice is to re-install Ubuntu from the (alternate) CD.  

As you may know from my posts, I Upgraded Ubuntu recently (from Beta to LTS) and my Ubuntu install was also toasted. I had different error messages but never found a solution and my posts on the Ubuntu forums were, at times, flamed. I could not repair my Ubuntu installation from the alternate install CD. 

My advice is for you to either re-instll Ubutnu 6.06 LTS from the alternate CD or move to an alternate distro but your current Ubuntu install may be beyond repair.

My dilemma has been if I re-install Ubuntu, what is to keep an update from toasting my system again?

My personal solution is to migrate to an alternate distro and await Ubuntu to "mature".

---

