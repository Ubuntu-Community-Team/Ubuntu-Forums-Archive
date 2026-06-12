---
title: "Iso Burn"
date: 2007-07-01
forum: Installation &amp; Upgrades
---

### Post by lukanikos on 2007-07-01
Hi Guys!

Can someone tell me please how I can burn the ISO on a CD and Install the Ubuntu 7.04 on my desktop with dual boot (XP and Ubuntu).
Also can someone tell me if I can do the burn on DVD instead of a CD?

---

### Post by steveneddy on 2007-07-01
Did you search the forums?

[Look here]("http://ubuntuforums.org/showthread.php?t=489189"). It's only a few minutes older than yours.

After you install - please [look here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty").

---

### Post by az on 2007-07-01
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Not sure if you can burn a cd iso to a dvd...

---

### Post by Pumalite on 2007-07-01
In general is a poor idea to burn a CD image to a DVD. I did it once, by mistake, and I got errors.

---

### Post by lukanikos on 2007-07-01
I tryed to boot from cd and wont work?
It's going back to windows...
I have done all procedures and when I click f10 on boot and then start booting from the cd drive with the ubuntu cd i get a msg
ntls missing
click ctrl+atl+delete

what do i do wrong?

---

### Post by steveneddy on 2007-07-01
> **lukanikos said:**
> I tryed to boot from cd and wont work?
It's going back to windows...
I have done all procedures and when I click f10 on boot and then start booting from the cd drive with the ubuntu cd i get a msg
ntls missing
click ctrl+atl+delete

what do i do wrong?

PEBKAC me thinks.

---

### Post by dabl on 2007-07-01
Is that message nt_L_s or nt_F_s missing?  I think maybe you need to enter "Setup", aka BIOS configuration, and get to the screen with "Boot Device Sequence", and set it so the CD ROM is the FIRST boot device.  When you first turn on your computer, after having shut it completely down, in the first few seconds there is a momentary message that says something like "Press F1 To Enter Setup" (or Ctrl-F2 or something along this line).  When you have changed the Boot Device Sequence, save your BIOS settings, exit, and restart your computer with the Ubuntu CD in the CD ROM drive, and see what happens.

:D

---

### Post by lukanikos on 2007-07-01
what do you mean when you say PEBKAC?

---

### Post by lukanikos on 2007-07-01
done!!!!

Thank you all.

I managed to make a bootable cd!!

How will i do a dual boot now without losing the xp files??

Can i just have a hard drive for xp and one for ubuntu without interference?

what will be the procedure for ubunto 7.04?

---

### Post by steveneddy on 2007-07-01
> **lukanikos said:**
> 

Can i just have a hard drive for xp and one for ubuntu without interference?



Yes

[Look here]("http://www.psychocats.net/ubuntu/installing").

---

### Post by lukanikos on 2007-07-01
I dont get the 3 options on the partitioner
i only get the 2....

Guided use entire disk and manua.

which is the right for me?

---

### Post by lukanikos on 2007-07-01
I tried 3-4 times to reboot and do the same with partitioner and there always comes up with 2 options instead of 3.
I think I need the first one for dual mode.

---

### Post by az on 2007-07-01
> **lukanikos said:**
> I tried 3-4 times to reboot and do the same with partitioner and there always comes up with 2 options instead of 3.
I think I need the first one for dual mode.

Try booting into windows and defragmenting your hard drive.  You should get that option.

Also, do you have enough free space on the disk?

---

### Post by lukanikos on 2007-07-02
yes
i have 4 disk drives of 160 g each

---

### Post by lisati on 2007-07-02
> **az said:**
> [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Not sure if you can burn a cd iso to a dvd...

Done it!

I had trouble using the "Live CD" on my laptop and ended up burning the "Alternate CD" iso to a DVD, which worked well enough for me to install Ubuntu 7.04...... I burnt it on a machine running Windows XP, but can't remember if it was with the copy of Sonic MyDVD that came with the machine or if it was with one of the OEM copies of Nero that I have.....

---

### Post by lukanikos on 2007-07-02
i tried defrag many times but still there is a problem with the option one....
I still get the second and 3rd option.

why is it so duficult to install this OS??

---

