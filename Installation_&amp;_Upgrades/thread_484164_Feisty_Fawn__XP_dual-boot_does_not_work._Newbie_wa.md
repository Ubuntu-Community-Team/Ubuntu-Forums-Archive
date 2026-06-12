---
title: "Feisty Fawn / XP dual-boot does not work. Newbie wants Ubuntu! HELP!"
date: 2007-06-25
forum: Installation &amp; Upgrades
---

### Post by soggywaffle on 2007-06-25
I'm a techie, trying to depend less on Windows. I want to learn and love Ubuntu and kiss windows goodbye.... eventually. In the meantime I need to dual-boot and it has not been working. I have tried twice. I was running XP on a SATA hard drive. I keep all my media, documents, etc on a 400GB IDE hard drive.

**_My goal here is to have both OS on one partitioned SATA drive, both accessing my media files on a seperate IDE hard drive_.**


FIRST ATTEMPT
Booted with 7.4 live CD and installed on a large unallocated space of the SATA drive (about 100gb). It created its partitions but the nightmare began when I rebooted. Spent hours on forums reading and playing with grub. Decided that I should start over leaving my second drive (IDE) out of the equation and adding it back on after a successful install and dual-boot scenario.

Wiped out the linux partitions, restored XP's MBR. Disconnected my second drive (IDE) and started over.


SECOND ATTEMPT
With just the SATA connected with its XP partition, I booted the live CD, installed Ubuntu on the unallocated free space. Worked like a charm. Both OS would boot up smoothly. Then I added back the second hard drive (IDE) and XP will no longer boot, though Ubuntu boots up fine.

In Gparted I saw that the IDE drive had a boot flag turned on (might have been from the first installation attempt), i removed it - that didn't do anything. The boot flag is on the windows partition of the SATA drive.

I downloaded and booted Super Grub. Selected the Fix Windows boot option. That didn't do anything.

Any suggestions? I figured I would try out this board and the support of its users before giving up. I've spent a weekend trying to get this to work. Any help would be greatly appreciated.

Thanks!

---

### Post by loserboy on 2007-06-25
I don't know the answer but at least I'm bumping this for you.

so theres no problem unitl you hook up the IDE?

---

### Post by soggywaffle on 2007-06-25
Thats right... I'm thinking it might be because when I first tried to install Ubuntu I had both drives present  and maybe some boot info was erroneously put on it. I think Grub was automatically put my IDE the first time around.

I say this because the first time I tried installing I was only able to dual-boot with no problems when I selected "boot from first hard disk" from the live CD.

---

### Post by loserboy on 2007-06-25
Ive never mixed Sata and IDE before, does the Sata assume master automatically and IDE takes slave?

---

### Post by michaelzap on 2007-06-25
Check your BIOS settings. I did exactly this on my first Ubuntu install (not long ago), but in my mobo's BIOS I can set which hard drive should boot first. If for some reason you can't set this in your BIOS you may need to make the IDE drive a slave instead of master and make sure that your SATA drive is on the master chain.

I successfully installed XP and Ubuntu on my SATA drive and kept my IDE drive as a file storage device (although I had to use wingrub to do it). But then I actually decided that I wanted each OS to have its own drive and I moved the Ubuntu partition to the IDE drive and left XP on the SATA drive (actually first I tried moving XP to the IDE drive, but it refused to boot so I gave up). Either way works, but I wanted to give my Ubuntu installation more room than the 50GB partition it started out with.

I found that it was good to keep an XP installation CD around to use the fixmbr command if that got messed up, but it sounds as if you're almost there.

---

### Post by soggywaffle on 2007-06-25
Its first in the boot order on the BIOS. 

I read in another thread that Ubuntu will always look at IDEs first, then SATA. I think Grub got messed up somehwere along these lines the first time around. 

Obviously. grub installed properly on the SATA, the second time around but I think some remnants of that first install attempt remain on the IDE and when I added it back after the second (successfull) dual-boot install, it messed things up somehow.

---

### Post by logos34 on 2007-06-25
> **soggywaffle said:**
> Thats right... I'm thinking it might be because when I first tried to install Ubuntu I had both drives present  and maybe some boot info was erroneously put on it. **I think Grub was automatically put my IDE the first time around**.

I say this because the first time I tried installing I was only able to dual-boot with no problems when I selected "boot from first hard disk" from the live CD.

Bold: Agree.

You didn't explain in your initial post what exactly happened, but it sounds as if grub went on the IDE drive's MBR -- it seems to go by default to the mbr of any IDE drive present regardless of bios hard disk boot order.  

So you had to use the live cd the first time to get both OS's to boot?

What's clear is that you now have grub on the mbr of both drives and the minute you add the IDE back into the mix, it's automatically becoming the first boot disk--'(hd0)' to grub--and you're booting to grub on that.  You can get into Ubuntu fine but not windows (which won't boot on a non-first hard disk).

If you haven't already go into the BIOS and make sure that the Sata drive is first in the **hard disk boot priority**--it's not enough that 'First boot device' is set to 'hard drive'.  

See it that works.  If not, you could still use grub on the IDE to boot ubuntu windows--except in the latter case you will have to edit your grub config files.  It can be done.

---

### Post by logos34 on 2007-06-25
sorry I was a little behind the curve on that last post...but try what michaelzap suggested and put the IDE as slave (never tried that).  Note: all sata drives are by definition 'master'.

---

### Post by soggywaffle on 2007-06-25
Good tip, just tried it.. BIOS picked it up as slave, but XP will still not boot. Could grub still be getting its instruction from the IDE? If so, how do I erase grub from the IDE?

---

### Post by michaelzap on 2007-06-25
Have you tried just pressing e at the grub menu to edit which drive partition to boot? If your grub is a little bit confused it might be trying to boot Windows from the wrong place, so try all of the possible options. Depending upon the error you receive, you may have also fried your Windows MBR (in which case you just need to use a Windows installation CD to repair it; search the forums for more specific instructions if you're not already familiar with that).

---

### Post by logos34 on 2007-06-25
What michaelzap is saying is that you have to hit 'e' on the windows entry in grub and change the 'root' line to either (hd**1**,0) or (hd**0**,0) -- assuming windows is the first parition on the disk.  Make sure to hit 'enter' after the edit.  

But that alone won't work for win if the grub you're booting to is on the ide drive--you'll need to add mapping to menu.lst.  could be wrong though

---

### Post by soggywaffle on 2007-06-25
Yeah, I tried changing the drive using the "e" command. Same result. I just restored the windows MBR from a backup to the windows drive. Now my computer is on an endless restarting loop. Doesn't even go into Grub anymore, just posts up and reboots. I'm about to forget Ubuntu until I upgrade my IDE to an SATA, then try again some day. I would love to get it working though. I have Super Grub, could that help me? Any other suggestions?

---

### Post by logos34 on 2007-06-25
> **soggywaffle said:**
> Yeah, I tried changing the drive using the "e" command. Same result. I just restored the windows MBR from a backup to the windows drive. Now my computer is on an endless restarting loop. Doesn't even go into Grub anymore, just posts up and reboots. I'm about to forget Ubuntu until I upgrade my IDE to an SATA, then try again some day. I would love to get it working though. I have Super Grub, could that help me? Any other suggestions?

try changing the ide back to master.  see if the boot loop stops 

add:  [don't forget the jumper settings]

check that the IDE is set as first in the bios hard disk boot priority.  Then boot to grub and see if you can get into ubuntu as before.  Windows won't work, we know that.  Then unconnect it and try again to boot up windows on the sata.  If successfull then you know the windows bootloader you just restored is still ok.

Then replug the IDE, set it as first in hard disk boot priority, and boot back into ubuntu.  Post back when you get there and I'll give you some line you can try to add to windows entry in menu.lst and device.map.

---

### Post by soggywaffle on 2007-06-25
with the IDE set to first, I get "Error loading operating system"...   I boot from the ubuntu disk and try to "boot from first hard disk"... I get the same error. I put the SATA back as the first hard disk to boot and it goes back to the endless loop....

---

### Post by logos34 on 2007-06-25
hmmm...here's what I'd suggest: you first try to get windows back and then worry about linux.  I would try one more time to restore winxp booloader to the mbr of the sata drive and see if THAT stops the looping and you can get into windows.  Then at least you'd have one working OS.  Use your xp install cd and do 'fixmbr' or fixboot' in the recovery console or whatever you did last tiome (forgive me if I get details wrong--I'm reading a lot of threads and they start to run together).  You could also use Supergrub cd.  

Then the next step is your choice: either forget dual-booting for now (you've had your fun for the day) or try to restore grub to the IDE drive MBR--this will keep it segregated frm the windows drive and hopefully with not too much effort we can manage to get it to boot windows and ubuntu by tweaking the partitions paths.  The standard way is to add some map lines to the grub menu config to enable booting winxp on a non-first hard drive (may have mentioned that).  That's the hurdle.

---

### Post by soggywaffle on 2007-06-25
Thanks for your help, I'm going to recover windows and try Ubuntu again after I upgrade my storage drive to an SATA... I bet with no IDEs present, Ubuntu will have little or no problems. Your help was not a waste as it has allowed me to look at things differently and I am more confident that I will be able to set up Ubuntu when I try again.

Thanks!

---

### Post by logos34 on 2007-06-25
alright then.
Good luck to you.

Here's a link to a dual-booting that might interest you:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

