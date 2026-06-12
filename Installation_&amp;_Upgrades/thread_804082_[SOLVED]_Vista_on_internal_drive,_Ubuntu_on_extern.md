---
title: "[SOLVED] Vista on internal drive, Ubuntu on external drive [GRUB error 22]"
date: 2008-05-22
forum: Installation &amp; Upgrades
---

### Post by animefan82 on 2008-05-22
Jumping right on it. As the title states, I have Vista on the internal drive, whereas Ubuntu was installed on the external drive. 

--Background info --
I used to have Feisty on the external drive, so I installed hardy right on top of it. It went great until I restarted the computer to load Vista and got a Grub error, but this isn't my problem. That one I already solved.

--My problem / What I want--
This is as specific as I can get regarding what I want:

I want Vista to load automatically. No GRUBs or whatever. When I start the laptop, and the external drive is in, GRUB kicks in, allowing me to start Ubuntu.

-----

Now before you start sending me to other topics regarding the same issue, let me do a list of what I've tried and what I already know. Btw it's unordered.

Boot order:
1. USB drive - It boots. Did it before, and doesn't work now.
2. CDROM - In case the first fails, I'll get back to this one.
3. Internal drive - When the usb drive is unplugged and no bootable cd's are in, the laptop jumps right into vista startup.

Super Grub Disk:
Tried it. Doesn't change anything, apart from more experience.

Grub reinstall:
Tried it. This is part of my problem which I need help with.

Partitions:
hd0/sdc7 - Where grub sees ubuntu
hd0/sda - Where Ubuntu sees Vista
hd1 - Where grub sees Vista
hd2 - Where Ubuntu sees Ubuntu

Drives:
sda - Main internal drive (Vista)
sdb - another internal drive
sdc - Usb drive
--

menu.lst combinations tried (separated by &&):
# groot=(hd0,6) &&  root (hd0,6)
# groot=(hd2,6) &&  root (hd0,6)
# groot=(hd2,6) &&  root (hd2,6)
# groot=(hd0,6) &&  root (hd1,6)
# groot=(hd1,6) &&  root (hd1,6)
# groot=(hd1,6) &&  root (hd2,6)
# groot=(hd2,6) &&  root (hd2,6)

alternate cd method:
tried it. didn't work.

reinstalling Hardy with different grub installations:
mbr on sda --> hd0 aka Windows partition mbr
mbr on sdc7 --> hd2 aka Ubuntu root partition
mbr on sdc4 --> usb-drive mbr.

I won't post the famously requested "fdisk -l" and/or "menu.lst" as the conclusion from that info is already posted above.

---What works (right now)----
As I wrote at the boot order part, the usb-drive has "no partition" aka GRUB error 22, where it jumps to the livecd bootup. Here I choose the "start from first hard drive"-or-something-option, which takes me right to the grub loader, and I can start Ubuntu, or Vista or whatever from there.
If the usb-drive is disconnected at startup I believe I get "GRUB error 15", but this is understandable, since I haven't fixed the mbr on the vista drive yet, which is easy enough for me:
(Machine powerup-->boot from livecd-->start vista (normal startup)--> run cmd--> %program_dir%\fixmbr /vista /yes-->vista mbr is fixed) In other words, this isn't a problem.

-- The question --
How do I go about with the grub commands and/or yet another fresh install of Hardy in order to be able to start up the computer the way I want it to?

---

### Post by animefan82 on 2008-05-22
Forgot the commands I've tried on "sudo grub":
root (hd2,6) && setup (hd2,6)
root (hd2,6) && setup (hd2)
root (hd2,6) && setup (hd0)
root (hd0,6)  --> no such partition

That last one really bugs me.
I know the first command should enable the grub loader on the usb-drive at bootup, but then again I also know that when using the livecd, (hd0,6) is the root used to start ubuntu.
Worse even, both (hd0,6) and (hd2,6) give me the same "error 22" message.

---

### Post by iaculallad on 2008-05-22
> I want Vista to load automatically. No GRUBs or whatever. When I start the laptop, and the external drive is in, GRUB kicks in, allowing me to start Ubuntu.

Seems like a problem with your vista MBR. Try looking at this  [windoze]("http://support.microsoft.com/kb/927392") page on how to fix it.

---

### Post by animefan82 on 2008-05-22
yeah... That's not the problem. The problem is that Grub sends me that infamous 22-error when booting up with the usb-drive connected.
I also have a fixmbr.exe on the vista-partition, but even then I get the same error when I connect the usb-drive.

---

### Post by iaculallad on 2008-05-22
> **animefan82 said:**
> yeah... That's not the problem. The problem is that Grub sends me that infamous 22-error when booting up with the usb-drive connected.
I also have a fixmbr.exe on the vista-partition, but even then I get the same error when I connect the usb-drive.

Since you installed m$ vi$ta on your internal drive, that should make it clear that you did install it first before installing Ubuntu (so, in the first place, nothing's wrong with vi$ta's mbr). Why not just disconnect your external drive (the one which contain your Ubuntu OS connected to your USB port) and configure your BIOS boot option to just load your internal drive and nothing else.

---

### Post by Steve413z on 2008-05-22
I just helped my friend with this same exact thing the other day...

use a ubuntu live cd to edit
edit /boot/grub/menu.lst (on the external hard drive)
it might be something like /media/EXTERNAL-DRIVE/boot/grub/menu.lst

> ## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

uncomment "groot=(hd0,0)" so it's like

> ## default grub root device
## e.g. groot=(hd0,0)
groot=(hd0,0)

then scroll down to the bottom, and find where the GRUB entry for ubuntu is, and where it says root, change it to, (or make sure it is set to):
> title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)

I hope that works for you

oh, and the way my friend set it up, he just turned his external hard drive on when he wanted to use ubuntu, and off when he wanted to use windows, and he just didn't deal with the bootloader on his home computer, and we actually set it up using my laptop, not his home desktop, but when he got home, it worked fine for him..

IMPORTANT NOTE: when he installed ubuntu on to the external hard drive, he made sure to specify to install the GRUB bootloader to his external hard drive.

---

### Post by animefan82 on 2008-05-22
> **Steve413z said:**
> 
IMPORTANT NOTE: when he installed ubuntu on to the external hard drive, he made sure to specify to install the GRUB bootloader to his external hard drive.

Yep, that's what I did the first time. Didn't work. Imagine my surprise roaming the forums stating "that should do the trick"...

--EDIT--
I haven't tried the uncommenting line though. I'll give that a try.

---

### Post by animefan82 on 2008-05-22
> **iaculallad said:**
> Since you installed m$ vi$ta on your internal drive, that should make it clear that you did install it first before installing Ubuntu (so, in the first place, nothing's wrong with vi$ta's mbr). Why not just disconnect your external drive (the one which contain your Ubuntu OS connected to your USB port) and configure your BIOS boot option to just load your internal drive and nothing else.

Because I want Ubuntu to boot, only without the "hassle" of watching the grub everytime I actually wanna use vi$ta.

On a sidenote: for the most part, I can't be bothered installing and dual-booting Ubuntu for developing, so I installed it inside vi$ta, using virtualbox. Now the thing with vista and development is, OpenGL is EXTREMELY crappy, and virtualization doesn't support hardware acceleration. Yet. This way, when I need to code some opengl, I'll restart the computer and start Ubuntu instead by plugging in the external drive.

btw I fixed the vista mbr, and it turns out I didn't get the "error 22"

It was 21. can't remember which one that is...

---

### Post by animefan82 on 2008-05-22
Tried uncommenting # groot(hd0,0) and # groot(hd2,6) (One at a time, of course)
Didn't work. This is starting to annoy me. A lot. I don't get annoyed easily....

---

### Post by animefan82 on 2008-05-23
This is my situation right now:
-Windows (internal drive) MBR: 
Clean. If I unplug the usb-drive, the computer boot right into Vi$ta, as if nothing was done at all. But this I already knew. I just put it here FYI.

-Ubuntu (external drive):
As I see it at boot-up, it jumps right over to the LiveCD, which I interpret as the drive not being bootable. I followed the steps from [this]("http://ubuntuforums.org/showthread.php?t=761817") tutorial, but still the usb doesn't boot, and I know it has, previously.

So now I have two problems:
1. How does GRUB interpret the usb-drive? (eg. hd0, hd1, ...., hdn)
2. Something has changed in order for bootup not to recognise the external drive as being bootable.

Any suggestions?

PS: All necessary information is at my first post, and the tutorial. I'm going to try a fresh install yet again, just in case I missed something at the GRUB installer.

---

### Post by meierfra. on 2008-05-23
Couple of comments:

1) Do not remove the # in front of groot. It needs to be there. (groot is an instruction to the program which updates grub during kernel updates. But it is not supposed to be read by  Grub during boot up.


2)   You need to use the same numbers for #groot and root. 

3)   Grub in the terminal and Grub at boot up number the hard drive differently. For example Grub at boot up always sees the drive  you are booting from as (hd0). For this reason you have to use "(hd0,6)" for root and #groot.


4)  Try this:   Boot from the Live CD. 

Make sure you use "#hiddenmenu" in menu.lst (not "hiddenmenu")
(You want to know whether the grub menu appears at boot-up)

Also  use "(hd0,6)" for  #groot and for  root

```
sudo grub
find /boot/grub/menu.lst
```

The output should be (hdx,6) with x=0,1 or 2.
Then

```
root (hdx,6)
setup (hdx)
quit

```

So  for example if "find /boot/grub/menu.lst" gives "(hd2,6)" use "root (hd2,6), setup (hd2)"

Reboot with external drive  first in the boot order.

---

### Post by Steve413z on 2008-05-23
please attach entire /boot/grub/menu.lst

---

### Post by Steve413z on 2008-05-23
did you try setting
root (hd0,0) in the grub entry?
```

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0) 			 		
```

---

### Post by animefan82 on 2008-05-24
Yep, I had tried all of the options. Regarding posting the complete menu.lst, look at my first post in the topic, not that it matters anymore...

My solution was an abnormal one though. As it turns out, before merging the old xp and ubuntu partitions into one, the xp partition was a PRIMARY partition on an already EXTENDED partition. It turns out the Hardy LiveCD can't grasp the concept of a PRIMARY partition inside an EXTENDED partition, so the installation process always created a LOGICAL partition, which my bios doesn't support, thus making the external drive non-bootable. I only had to back up the stuff on the NTFS partition, delete all partitions and THEN the Hardy LiveCD managed to create PRIMARY partitions.

Now that I think about it, I could probably have done the primary partition part in windoze, since that OS can make primary partitions within extended partitions (GParted wasn't able to do that :(). Then again, it might've been something I did wrong, which doesn't matter right now. 
Hardy was then installed from the LiveCD on the primary partition of the external drive, chose advanced options right before installing, chose GRUB to be installed to that same primary partition, installed, then tested.

Now, when the USB-drive is unplugged, the computer boots right into Vi$ta, without knowing anything about GRUBs or whatever. When the USB-drive in plugged at startup, GRUB is loaded, and Ubuntu starts.

NOTE: I had to change groot and root from (hd2,1) to (hd0,1) in /boot/grub/menu.lst because when the external drive is loaded first, that will be the first hard drive on the computer. The LiveCD loads the internal hard-drives first, then the external, making the external the third loaded drive. And that's it. I hadn't realized how much I missed compiz-fusion until now, hehe.

Thanks for all your help anyway.

---

### Post by XBones on 2009-03-17
Recently i've become interested in two Os's, with one being on a external drive.
I too have run across these same issues.
My solution to this was as follows....

1. install Easy BCD so you can get Vista to boot without external
   drive being attached

with this working again,i proceeded to boot UBUNTU

to achieve this i downloaded, installed and made a boot cd of Auto Super Grub

With this installed and use of cd, i can now go back to using UBUNTU off the external drive

Unfortunately this brings us back to original issue of needing the external plugged in to operate properly

Its seems to be a simple solution to those who don't know enough to edit and modify entries.

---

