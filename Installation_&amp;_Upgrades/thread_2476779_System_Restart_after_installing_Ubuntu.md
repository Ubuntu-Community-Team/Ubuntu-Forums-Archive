---
title: "System Restart after installing Ubuntu"
date: 2022-07-06
forum: Installation &amp; Upgrades
---

### Post by pilif2 on 2022-07-06
[https://paste.ubuntu.com/p/qVPqKyPZxh/](https://paste.ubuntu.com/p/qVPqKyPZxh/)

So as the title says after installing Ubuntu and restarting after im stuck in an infinite loop of my Pc logo and small message saying System Restart. Did anyone have any similar issues? In the boot repair it says No boot loader is installed in the MBR of /dev/sda, maybe thats the issue?

---

### Post by tea for one on 2022-07-06
> **pilif2 said:**
>  In the boot repair it says No boot loader is installed in the MBR of /dev/sda, maybe thats the issue?
I don't think that this is the issue because it refers to BIOS/MBR (i.e.legacy) installations and you have UEFI with GPT, which is the modern way.

When you are in this loop, can you gracefully reboot your PC with Ctrl Alt Del?
Then use the dedicated key to reach the one-time boot menu?
Is your disk visible?
Can you select it and boot?

---

### Post by grahammechanical on 2022-07-06
Can you load the Ubuntu live session on the USB memory stick? I am  guessing that this restart is happening before the motherboard UEFI  utility can load the Grub boot loader. Can you access the UEFI settings  utility?

Faulty hardware can cause restarting. RAM not seated in  the slots properly. CPU overheating (fans not working). Power supply  failing. 

Regards

---

### Post by pilif2 on 2022-07-07
I can access bios and select my HDD from there but that just brings me back to the loop. Idk if that is what you meant.

---

### Post by pilif2 on 2022-07-07
I can enter bios and get to the uefi setting from there but i only have the option to switch from uefi to legacy mode and thats it

---

### Post by tea for one on 2022-07-07
> **pilif2 said:**
> I can access bios and select my HDD from there but that just brings me back to the loop. Idk if that is what you meant.

Yes, that is what I meant and I was hoping that booting from the one-time boot menu may have triggered a result.

Do you have other security settings in your UEFI firmware which may prevent the PC from booting?

If not, I would now ensure that my data is backed up and then try the recommendation from boot-repair.
Don't forget to boot the live session in UEFI mode and then install the boot-repair utility.

---

### Post by pilif2 on 2022-07-07
Like i said it just brings me back to the loop, and for the uefi settings i only have the option to change from uefi to legacy, pretty slim compare to what i saw on other machines. I did repair boot multiple times but the result is always the same

---

### Post by tea for one on 2022-07-07
Can you provide some system specifications?
Model?
Age?
Ram?

If you have very limited UEFI firmware, then it may be that the age of the PC would suggest that a different member of the Ubuntu family may be more appropriate?

---

### Post by pilif2 on 2022-07-07
Its a Toshiba laptop CPU is intel core i5-4300u 1.90ghz, the graphics card is Intel family i think, not sure, 8gb of ram and its 5 or 6 years old give or take. Previously it ran windows 10 with the latest updates with no problem. Its wasnt slow or anything, couldnt play latest games on it, but for coding and designing(what i did the most) it was doing a pretty good job.

---

### Post by tea for one on 2022-07-07
More than adequate specification for Ubuntu 20.04.

Perhaps reset the UEFI settings back to default?
However, you mention that the PC is  only 5/6 years old so I would expect to see many options in the UEFI set up screens, especially under Security and Boot.
No sign of TPM (Trusted Platform Module) or similar?
Sata mode set to AHCI?

---

### Post by pilif2 on 2022-07-07
Soo good news i got it working, turns out i just had to disable fast booting in my bios, but it wasn’t straight forward since that option is called something else so after a few tries i got it to work i even upgraded it to version 22.4. Buut that was maybe a mistake because now it’s kinda slow and not as smooth as i was hoping to be. Any tips on increasing the speed/overall performance? Or i just have to buy a new pc which kinda isn’t a option rn at at least.

---

### Post by tea for one on 2022-07-08
> **pilif2 said:**
> Soo good news i got it working, turns out i just had to disable fast booting in my bios,
Yes, that is good news - well done.
It is beneficial to mark threads as solved to help other forum members/searchers.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Then open a new thread with details of the slow performance i.e. usual things:-
What were you doing?
What did you expect?
What happened?

---

