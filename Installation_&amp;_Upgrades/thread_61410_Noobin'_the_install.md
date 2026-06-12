---
title: "Noobin' the install"
date: 2005-08-31
forum: Installation &amp; Upgrades
---

### Post by sullenday on 2005-08-31
Okay, so I downloaded the x86 install iso file at work (old crappy mac) and burned on a disc.  Got home, dragged the file to my desktop, then made a boot disk.  Once i inserted the boot disk and restarted, up came the intsall menu and I went through the process and was stoked!  But after I removed the cd and it restarted my computer to "finish the installation" it went straight to windows boot ( by the way, I'm trying to install this on a separate maxtor 120gb drive).  I have a sata raptor for xp, and this ide maxtor for ubuntu.  Everything is set in my bios, each drive is designated master on its resptective controller.  Anyway, I decided to unhook the raptor, and reboot, well, then grub shows its face and I select ubuntu, and then as it trys to boot, I get some horrible kernal issue now.  So I can't finish whatever is left of the installation, obviously.  Also, I hooked the raptor back up, and now grub will work with both drives connected, but kernal error and no start up for ubuntu.  So what did I do wrong?  Everything seemed fine till it restarted for the boot :? 

Athlon 64 3200
AN8-SLI delux
geforce 6800gt
sata plextor drive

---

### Post by Lord Illidan on 2005-08-31
Ouch..

but can you specify the kernel issue... just "horrible" is not enough, I'm afraid.. write it down on a piece of paper and post it here, we can help out better that way.

Have you tried to boot as fail-safe?

---

### Post by xaque on 2005-08-31
I had the same problem with my install. It was because of some freaky-weird BIOS thing where the order of the hard drives is specified in the BIOS. It boots off the first drive the BIOS sees, which means if it sees the Windows drive first, it won't boot Ubuntu. That's why taking the drive out fixed it. The kernel problem is because of the way GRUB handles the hard drives. The BIOS assigns the hard drive's ID based on which order you have em set up in the BIOS, so  when you were installing (and had the Windows HD set to Drive 1, and the Ubuntu HS to Drive 0), GRUB thought Ubuntu would be on Drive 1, and that's where it's looking for the kernel. Since you rearranged the drives by taking one out, the Ubuntu HD is now Drive 0 and Drive 1 doesn't exist anymore. That's why the kernel error. To fix it, just edit the GRUB boot entry for Ubuntu (by pressing 'E' while it's highlighted), and change the part that says (hd1,0) to (hd0,). Then, you'll have to figure out how to configure your BIOS to detect the Ubuntu disk as Drive 0 and the Windows disk as drive 1... or something. Good luck, hope I explained that well, I know it's a little messy

NOTE: All of this may be completely irrelevant to your situation, all I know is this is what fixed it with my particular BIOS/setup.

---

### Post by sullenday on 2005-08-31
[QUOTE=Lord Illidan]Ouch..

but can you specify the kernel issue... just "horrible" is not enough, I'm afraid.. write it down on a piece of paper and post it here, we can help out better that way.

Have you tried to boot as fail-safe?[/QUOTE]


Of course, just thought I'd shoot it out there at work, while I had some "spare" time.  So here's my dreadful report:

pivot_root: No such file or directory
Kernal panic
not syncing:  Attempted to kill init!

Sounds scary

---

### Post by sullenday on 2005-08-31
[QUOTE=xaque]I had the same problem with my install. It was because of some freaky-weird BIOS thing where the order of the hard drives is specified in the BIOS. It boots off the first drive the BIOS sees, which means if it sees the Windows drive first, it won't boot Ubuntu. That's why taking the drive out fixed it. The kernel problem is because of the way GRUB handles the hard drives. The BIOS assigns the hard drive's ID based on which order you have em set up in the BIOS, so  when you were installing (and had the Windows HD set to Drive 1, and the Ubuntu HS to Drive 0), GRUB thought Ubuntu would be on Drive 1, and that's where it's looking for the kernel. Since you rearranged the drives by taking one out, the Ubuntu HD is now Drive 0 and Drive 1 doesn't exist anymore. That's why the kernel error. To fix it, just edit the GRUB boot entry for Ubuntu (by pressing 'E' while it's highlighted), and change the part that says (hd1,0) to (hd0,). Then, you'll have to figure out how to configure your BIOS to detect the Ubuntu disk as Drive 0 and the Windows disk as drive 1... or something. Good luck, hope I explained that well, I know it's a little messy

NOTE: All of this may be completely irrelevant to your situation, all I know is this is what fixed it with my particular BIOS/setup.[/QUOTE]
 alright, give that a shot... I thought all I could do in my bios is set master or slave...well, time to get to know my bios better.  Thanks for your reply!

---

### Post by sullenday on 2005-09-01
[QUOTE=sullenday]alright, give that a shot... I thought all I could do in my bios is set master or slave...well, time to get to know my bios better.  Thanks for your reply![/QUOTE]
 ummm..okay, I'm still drowning.  Any other ideas?

---

### Post by plb on 2005-09-01
try reinstalling again.....seriously

---

### Post by sullenday on 2005-09-02
[QUOTE=plb]try reinstalling again.....seriously[/QUOTE]


Okay, but should I do it with only the one drive I'm putting ubuntu hooked up?  Or will that screw grub up when I put the seperate windows drive back in afterwards for dual booting on different hard drives?

---

### Post by xaque on 2005-09-02
Try installing with just the one drive hooked up, and see if Ubuntu will install at all. If it won't, you may have somewhat more serious problems... if it works, then you can start figuring out how to get it to work with Windows.

---

### Post by sullenday on 2005-09-05
Okay, so I went ahead and installed the amd64 version this time, with only the single ide drive connected and it worked fine, got to check out ubuntu finally!  Then, I did it with both the sata windows drive and the ide ubuntu drive, ran the installation procedure, and after the restart, it skipped straight to windows again (where's the grub?).  So I disconnect windows drive, restart with ubuntu drive, and there is grub, and everything works fine.  Now I reboot with the windows drive back online and when I choose to boot windows in the grub, it goes to "booting windows" and just hangs there.  But I can still get into ubuntu fine at this stage.  

So I'm thinkin' that with native sata controllers on my board, maybe the ide controller can't communicate to the sata controller when trying to acces the boot loader on the windows sata drive.  So I either try this with two sata drives, or just unplug the windows drive everytime.  I'll call asus just to be sure (even though you could call them 5 times in an hour with the same question and get a different answer each time).

---

