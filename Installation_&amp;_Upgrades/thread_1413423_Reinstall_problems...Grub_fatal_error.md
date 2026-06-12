---
title: "Reinstall problems...Grub fatal error?"
date: 2010-02-22
forum: Installation &amp; Upgrades
---

### Post by trekon86 on 2010-02-22
Hi there,
I was (stupidly) experimenting with removing Pulseaudio and screwed up  my sound, seemingly irreparably. So, I decided to burn a mini-iso and try to install regular ol' Ubuntu.

Problem is, I keep running up against this error:

Configuring GRUB-PC
Unable to Install GRUB in HD0
Executing 'GRUB-install  hd0' failed.
This is a Fatal Error.

What did I do wrong? I burned the iso to a CDRW disc (all I had), popped it into the drive, rebooted, went through the steps and every time, it throws me this error.

One thing I have noticed...for some odd reason, every time I retry this, it seems to show more and more partitions. Perhaps it is spawning too many of them? LOL...

Thank you in advance for any help you may be able to offer.

Cheers,
PMZ

---

### Post by dabl on 2010-02-22
> **trekon86 said:**
> 

I burned the iso to a CDRW disc 



Probably that is the problem -- CD-RWs are famous for not working.

---

### Post by trekon86 on 2010-02-23
Well I burned the mini iso to a DVD-R and it still doesn't work. Keeps giving me errors like "Grub loading: No such partition/disk-Grub Rescue" etc etc.
This is driving me up the wall. I don't understand how it could be so hard to install an OS esp. Ubuntu. 

Anybody with any suggestions (entry level)?
I am relatively new to this but if somebody gives me a command to enter at a prompt I will certainly try it...thanks.
PMZ

---

### Post by trekon86 on 2010-02-23
One thing I guess I should mention is that throughout the installation, it seems to be doing fine. Everything works the way it should, and there are no errors.
But when I go to remove the disc and reboot, it gives the errors.

What am I doing wrong?
There seem to be about 9 or 10 SDA partitions on there now...:confused:
PMZ

---

### Post by gillmt on 2010-02-23
Please note - I am definitely not an expert! I have used GParted to format an HD and it was easy enough for a beginner like me. You could try using the partition editor on your live CD or burn a GParted live CD and format the whole HD, then try to install again?

---

### Post by trekon86 on 2010-02-24
Well, I burned the regular old Ubuntu ISO onto a regular old cd and it seemed to work fine.
But it's still not working.
And now, when I boot into LiveCD mode, it is telling me that there are "many bad sectors" on your HD. After which it promptly freezes and I have to reboot. I can't even use the Live CD. And yes, I checked the integrity of the CD after I burned it so it's not the damn CD.

I don't know what to do. I've been reading reports of this happening to people with Samsung and Fujitsu HDD's. Mine is an old Fujitsu.  I will "try" to run fsck and see if it confirms my HD being screwy...

PMZ

---

### Post by trekon86 on 2010-02-24
Well my attempts to access the command line didn't work at all, it kept saying "no such command."

So I'm in the process of downloading 9.04, and I'm going to try to reinstall Jaunty.
I'm getting the feeling that most folks tend to stick with the prior release for at least a year, till most of the bugs are worked out of the next one...methinks I will disable automatic updates next time:rolleyes:
PMZ

---

### Post by trekon86 on 2010-02-24
Bingo...the downgrade to 9.04 did the trick.
No HDD errors as far as I know. It's certainly not reporting any now.:rolleyes:
PMZ

---

