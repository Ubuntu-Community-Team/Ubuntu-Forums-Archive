---
title: "Vista  ultima and ubuntu"
date: 2007-10-04
forum: Installation &amp; Upgrades
---

### Post by batista08 on 2007-10-04
Hello, I've tried to install ubuntu so many times that this is my last attempt to make it work. First when I tried to install ubuntu at a random point it freezes. After many trying to install it many times when it boot it freezes, restart and after couple of mins it freezes again and the same goes for vista; it boots and freezes when it logs or it freezes right after it finish loading. What can be wrong? I thought that the problem could be because I had 5 partitions; 5th being the swap, but now I tried to install on a new hd and still the same problem. 
Thank you.

---

### Post by sparcxl on 2007-10-04
I think I am just as new as you however I ran into a similar problem on another machine and it turned out to be a memory problem. Have you tried running the memory test from the Live CD or possibly testing the install media? I am not sure how much more I can offer but I would start there. Good Luck! :)

---

### Post by batista08 on 2007-10-04
> **sparcxl said:**
> I think I am just as new as you however I ran into a similar problem on another machine and it turned out to be a memory problem. Have you tried running the memory test from the Live CD or possibly testing the install media? I am not sure how much more I can offer but I would start there. Good Luck! :)
It can't be the ram because I ran a 2hr test on them to see if they're stable and it passed. What else could be?

---

### Post by amadeus266 on 2007-10-04
This sounds more like a overheating problem. check your fans.

---

### Post by batista08 on 2007-10-04
> **amadeus266 said:**
> This sounds more like a overheating problem. check your fans.
water cooled :lolflag:. BTW right now its running on stock speed so the problems is not related to overclocking.

---

### Post by batista08 on 2007-10-04
bump

---

### Post by LeChacal on 2007-10-04
It sound that your problem is hardware based because if both Visat and Ubuntu exhibited the same behaviors being two different beasts I would start looking at the my hardware. I had the same problem trying to load XP and Ubuntu on a system and it was hardware. As for hardware the first thing i would try is the memory i saw you said that you ran a test but if you hare using multiply dims, I have had memory testers not pick up the bad bit so I would test each memory stick individually, even if they are brand new i bought a pair of brand new 1GB sticks and one had a bad bit in like the last 100,000 bits. The other problem could be that your hard drive(s) have a bad sector near where the OS is trying to be put down or near the end of one of the partions. While you are playing with your HDD check the ribbons/cables for cracks and splits. But I bet it is hardware because I can believe that maybe your Ubuntu had a bad burn but a Vista disk would be strange.

---

### Post by batista08 on 2007-10-04
> **LeChacal said:**
> It sound that your problem is hardware based because if both Visat and Ubuntu exhibited the same behaviors being two different beasts I would start looking at the my hardware. I had the same problem trying to load XP and Ubuntu on a system and it was hardware. As for hardware the first thing i would try is the memory i saw you said that you ran a test but if you hare using multiply dims, I have had memory testers not pick up the bad bit so I would test each memory stick individually, even if they are brand new i bought a pair of brand new 1GB sticks and one had a bad bit in like the last 100,000 bits. The other problem could be that your hard drive(s) have a bad sector near where the OS is trying to be put down or near the end of one of the partions. While you are playing with your HDD check the ribbons/cables for cracks and splits. But I bet it is hardware because I can believe that maybe your Ubuntu had a bad burn but a Vista disk would be strange.
Once I delete the linux partition everything works fine. I have tried burning and the free cds ubuntu sends you and still the same thing. As for the hdd, both hdd cant be bad, one is 500gb and has like 1month running perfectly and the other one is a bit old but was also running fine and like I said when i delete the linux partition everything works fine. I'm going to uninstall one ram stick to see if that solves the problem.

---

### Post by dinub1 on 2007-10-04
> **batista08 said:**
> water cooled :lolflag:. BTW right now its running on stock speed so the problems is not related to overclocking.

Then you may have another hardware issue. 1st go back to rated speed and set all BIOS setting to optimized. See then. If Vista freezes too, then the OS is not at fault.

---

### Post by batista08 on 2007-10-04
> **dinub1 said:**
> Then you may have another hardware issue. 1st go back to rated speed and set all BIOS setting to optimized. See then. If Vista freezes too, then the OS is not at fault.
It is running on optimized settings. I tried installing running one ram stick and with either the installation crashes. The times I've got ubuntu installed I've had to restart the pc more than 5 times because it crashes and then when it does install it crashes when booted and vista also.

---

### Post by Pumalite on 2007-10-04
Post your specs. This can be anything; including Power Supply. What's your memory? What iso are you using? From a Live CD, post: sudo fdisk -lu

---

### Post by batista08 on 2007-10-04
> **Pumalite said:**
> Post your specs. This can be anything; including Power Supply. What's your memory? What iso are you using? From a Live CD, post: sudo fdisk -lu
E6300, gigabyte ds3 rev.3, 2gb ram g.skill, rosewill ps 550w, 500gb samsung, 80gb western digital, lite on dvd burner, I tried running kubuntu and ubuntu. They were both sent by ubuntu and I before I received them I was using some I downloaded from their website. How can it be my memory or ps if i have tested and retested this pc for stability? more than 1 1/2 days under prime95 and over 1 day in memtest but that should matter much because im on stock settings.

---

### Post by Pumalite on 2007-10-04
I still would like to see your fdisk. Also make sure to follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
(particularly, do md5sum on iso and burn at 4x)

---

### Post by batista08 on 2007-10-04
nvm mind mate. Thanks for trying to solve my problem but I've burned too many cds already and I not going to waste one more just to find out that that is not the problem. I think that the issue here is vista because I had the version before 7.04 and it worked fine with xp in this pc so...

---

### Post by Pumalite on 2007-10-04
You might be right. Vista is known to be a computer hog. Besides Micro$%& is always trying to prevent installation of other OS's in the same computer. You might have a 'prefixed' BIOS, who knows?

---

### Post by batista08 on 2007-10-04
> **Pumalite said:**
> You might be right. Vista is known to be a computer hog. Besides Micro$%& is always trying to prevent installation of other OS's in the same computer. You might have a 'prefixed' BIOS, who knows?

This is a custom built so I don't think that's it.

---

### Post by Pumalite on 2007-10-04
If it's a 'custom built' go inside your computer and recheck everything.

---

### Post by batista08 on 2007-10-04
> **Pumalite said:**
> If it's a 'custom built' go inside your computer and recheck everything.
The problem is vista, I disconnected the hd where vista is and installed ubuntu on the other hd and everything works fine. I'm not a linux expert and I thought this was the place to get my questions answered but so far... I'm out of luck.

---

### Post by Pumalite on 2007-10-04
Don't blame Ubuntu or the forums. You found the answer suggested by me. It was Vista. Get rid of Vista and voilá, your computer functions again.

---

### Post by batista08 on 2007-10-04
> **Pumalite said:**
> Don't blame Ubuntu or the forums. You found the answer suggested by me. It was Vista. Get rid of Vista and voilá, your computer functions again.
I didn't blame anyone but luck. It seems like it's not vista after all. After using ubuntu for couple of mins it froze and when I restarted it froze at the login screen so right now I'm more lost than ever. With vista and xp this pc works totally fine but with linux I get problems. I'm going to try another distro tomorrow to see if the problem is ubuntu. If that doesn't work then I'm giving up until I buy a power supply for my second rig. Thanks for you help and I'll post the results with another distro.

---

### Post by Pumalite on 2007-10-04
Good. We'll be here.

---

### Post by batista08 on 2007-10-05
> **Pumalite said:**
> Good. We'll be here.
I'm running ubuntu 7.10 and it's been working fine for over 10mins now. Since this is a beta version would I have to reinstall after the final release comes out or just do an update?

---

### Post by Pumalite on 2007-10-05
You can do either one. I'm planning to do a clean install. I like them better. If you keep on updating, at the end you get the final version anyway.

---

