---
title: "Help grub2: chainloading not ok - but switch to configfile ok"
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by frafu on 2009-11-24
Hi,

I have an Ubuntu installation on my first harddrive and a second Ubuntu installation on my second harddrive; both are using grub2. 

When I start the computer, I get the menu from grub2 of the first Ubuntu installation, to which I have entered the following custom entry (in 40_custom) to chainload to the second Ubuntu installation:

menuentry "SecondUbuntu" {
	saved_entry=0
	save_env saved_entry
	insmod ext2
	set root=(hd1,1)
	chainloader +1
#	configfile /boot/grub/grub.cfg
}

If I try to use chainloading as indicated in the menuentry, when the menu of the first grub2 installation disappears, I get a black screen with "GRUB _" at the top left corner. 

However, it works when I remove the chainloader command from the menu entry and remove the # to make it switch to the menu list of the second grub2.

Consequently, I assume that it is the boot sector of sdb1 that is the problem!?

Could anybody please tell me what I can do to make it work by using the chainloader? 

Thanks in advance for any help.

Francesco

---

### Post by oldfred on 2009-11-24
When I installed Karmic alpha I installed grub2 to the partiton boot record so I could chainload. I has complained about blocklists being BAD but has worked. When I did a clean install of Karmic it did not give me a chance to choose the PBR. There are ways to install to the PBR but if you only have one operating system on the second drive you can install grub2 for the second drive into the second drives MBR and chainboot to that. 

Instead of 
root (hd1,1)
use
root (hd1)
It will chain to the grub in the MBR of hd1.

---

### Post by coffeecat on 2009-11-24
My experience was similar but not the same as oldfred's. When I installed Karmic alpha to this laptop, I was able to install grub2 stage 1 to the PBR, and chainload from my legacy grub in Jaunty just fine. I used the 'advanced' button at the last stage of the graphical installer. Then, when the final was released, I did a clean install to my desktop and again I was able (apparently) to install grub2 to the PBR with the advanced button. But when I tried to chainload from that Jaunty partition, it failed with some sort of legacy grub error. Which was when I found other posts describing the same thing and I assumed that there was something about grub in the Alpha which made the difference.

But I was wrong.

I recently did a fresh install of Karmic final to a spare partition on the laptop, told the installer to install grub2 to the PBR and I was able to chainload from Jaunty's legacy grub. Clearly stage 1 did get written to the PBR. Peculiar - it fails on one machine but not on another.

I've solved the problem now by chainloading from grub2 to legacy grub - it seemed easier. :rolleyes: That doesn't help you but I do have a suggestion which might give you a way of appearing to chainload from one grub2 to another.


One solution for legacy-grub -> grub2 was to use this stanza:

```
title Karmic/Whatever menu 
root (hd0,6) 
kernel /boot/grub/core.img     
```I have no idea how it works, but the grub2 menu pops up as good as gold without grub2 stage 1 on the PBR. Of course that's a legacy-grub stanza, but it must be possible to adapt it to work in grub2 for grub2 -> grub2. I haven't tried it myself, but how about.....

```
menuentry "Blah Blah" {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set incomprehensible-uuid-string
    linux    /boot/grub/core.img
}
```I have no idea whether that will work, and I might be blowing hot air, but I offer it as a possibility.

**Edit:** obviously, change the root lines, and .... I have to ask. Are you really still using Edubuntu Edgy? :wink:

---

### Post by frafu on 2009-11-24
Hi,

Thanks for the reply; unfortunately there are more than one operating system on the second drive and installing it to the MBR will not suit my needs. 

In the meantime I was able to find a solution: 
- I booted by using the configfile method to the second Ubuntu installation. 
- While running the second Ubuntu installation I followed the instructions about "grub-setup --force" [on this page]("http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#grub-setup"). 

Cheers 

Francesco

---

### Post by coffeecat on 2009-11-24
> **frafu said:**
> Thanks for the reply; unfortunately there are more than one operating system on the second drive and installing it to the MBR will not suit my needs. 

oldfred and I were referring to the PBR  - partition boot record.

---

### Post by frafu on 2009-11-24
Hi coffecat,

I saw your first post only after writing my previous reply. (In fact, after starting my reply, I was interrupted and could only finish it later.)

Your idea about loading core.img as if it was a kernel to simulate chainloading is interesting; but I have not tried it anymore as I was able to make the normal chainloading work. 

Finally, in my previous comment, I was referring to oldfred explaining that if there was only one system on the second harddisk, I could also use the MBR instead of the PBR.

In any case, thanks to both of you for your help. 

Francesco

---

### Post by Tobis84 on 2009-12-06
Hi all
I'm not sure if my problem is to go here or not, but here goes:
A few days ago my laptop motherboard got fried (something with some orangejuice...) But I was able to get the harddrive going in a dockingstation and boot it from my desktop as an ordinary USB-device. 
Before the mishab I had both Ubuntu 9.04 and Windows 7 installed seamlessly using Grub Legacy. and now my aim is to get this secondary hdd going alongside the internal one in my desktop - as in multibooting using Grub2 on my desktop.
My desktop is running Ubuntu 9.10 Karmic hence Grub2. I had it going once using StartupManager but when I selected the OS' on the external hdd it came up with some errors:
 selecting Ubuntu 9.04: error xx: u need to run kernel first (or something like that)
 selecting Win7: invalid signature.
(as a remark I must say that the Win7 installation is currupted and may need re-install - not a priority)

For now I have downgraded my desktop to Ubuntu 9.04 in order to try out if Grub legacy can solve my problem, but I haven't got much grip on Grub so this for me is a dead end.

I really appriciate any help as this dying laptop is the one I am using at my study and I really need it going - at least the harddrive anyway.

Thanks in advance.
HJ

---

### Post by coffeecat on 2009-12-07
> **Tobis84 said:**
> Hi all
I'm not sure if my problem is to go here or not, but here goes:

Not really because, if I read you correctly, you've now got two Jaunty installations and hence you have a problem with legacy grub, not grub 2 the subject of this thread. You might be better off with your own thread. Suggest you use the 'report' button [IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG] to ask a mod to move your post and my reply to a new thread. That's OK - although it says 'report abuse' it can also be used for benign requests like this. You'd need to suggest a thread title. You'll be better off with your own thread. This has the 'solved' tag and people are unlikely to look at it. I only came here because I'm still subscribed to the thread.

Anyway, to get you going. With the laptop drive connected to the desktop, post the output of:

```
sudo fdisk -l
```Presumably when you say you 'downgraded' to 9.04 on the desktop, you did a fresh install of Jaunty replacing Karmic. Have I understood you? Also, post the contents of your desktop Jaunty /boot/grub/menu.lst. It should be fairly easy to edit the desktop Jaunty menu.lst to get you booting into the laptop HD menu.lst - possibly even Windows 7.

**Edit:** or if you still have Karmic on your desktop HD and you are booting with grub2, post the contents of /boot/grub/grub.cfg. You shouldn't edit grub.cfg, but there will be ways of getting you going.

---

