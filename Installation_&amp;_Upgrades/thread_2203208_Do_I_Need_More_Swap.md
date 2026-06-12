---
title: "Do I Need More Swap"
date: 2014-02-02
forum: Installation &amp; Upgrades
---

### Post by byrondallas on 2014-02-02
Hi guys. I just recently increased my Ubuntu partition with 10 gbs and was wondering if I need to increase my swap partition as well. I have 2 gbs of RAM and I'm dual booting Windows XP along side Ubuntu 13.10. You can see the details in the screen shot below. If I do need to increase the swap, how much more and how much for the extend area? Is there anything else I would need to do after increasing the swap if I actually do increase it?

sda1 = Windows XP
sda2 = Ubuntu

---

### Post by grahammechanical on 2014-02-02
Do you hibernate or suspend this machine? If we do that then the System information in RAM is stored onto the hard disk in the swap partition. This is my understanding. You have not increased your RAM. I have 1GB RAM and Ubuntu partitions as large as 38GB. I have 2GB of swap. I do not use hibernation. It is my understanding that with hibernation we should have swap larger  than the RAM or we may have problems coming out of hibernation.

Regards.

---

### Post by byrondallas on 2014-02-02
Forgive my ignorance but can you explain what you mean by suspend or hibernate?

---

### Post by nothingspecial on 2014-02-02
It means when you turn the computer off but you don't really. It kind of saves everything it was doing and stops rather than completely shutting down, then starts up again a lot quicker than if you actually cut the power. Kind of .....

---

### Post by byrondallas on 2014-02-02
I kinda thought that's what you meant but wanted to clarify. I normally just close the lid and let it sleep. So your saying I probably don't need to add any more swap area? Just out of curiosity how would I go about adding more swap and how much space should the extended area be? I know I would have to resize the Ubuntu partition to grab the extra space and move it but how much for both extended and swap?

---

### Post by grahammechanical on 2014-02-02
When we shutdown will lose the state of the OS. Suspension and Hibernation are methods of saving the state of the OS which not only is convenient but makes for a quicker re-loading of the OS. Suspension and hibernation both involve shutting down some of the hardware and so save power.

Suspension is more accurately Suspension to RAM. Power is cut to most parts of the hardware but not the RAM and so it is possible to quickly power up the machine and also bring it back to the working state that we had before.

Hibernation is more accurately Suspension to Disk. The system state is saved to disk in the swap partition and the machine is completely powered down including removing power from the RAM chips. It is a slower method of resuming than suspension to RAM but it has the advantaged of not losing the system state if a laptop's battery goes flat.

Hibernation is not activated by default in Ubuntu. We do not have an option for it in the power/cog menu. But is hibernation necessary on a desktop machine?

Regards.

---

### Post by nothingspecial on 2014-02-02
> **byrondallas said:**
>  So your saying I probably don't need to add any more swap area? 

You do not need to increase your swap partition. Everything will work fine as it is. Messing about with partitions is risky whereas the worst that will happen with your current set up is that hibernation might fail. I would say don't worry about it.

---

### Post by byrondallas on 2014-02-02
> **nothingspecial said:**
> You do not need to increase your swap partition. Everything will work fine as it is. Messing about with partitions is risky whereas the worst that will happen with your current set up is that hibernation might fail. I would say don't worry about it.


Ok great! As far as loosing anything on this machine, I'm not to worried. It's an extra laptop that was given to me and I use it to try new stuff.

---

### Post by varunendra on 2014-02-02
Since you didn't know about hibernation, obviously you don't use it. Even if you now care about it, hibernation is something that doesn't always work well with Ubuntu, that's why it was disabled by default.

In simple terms, forget about hibernation, and leave the partitions as they are. You don't need extra swap. What you currently have is more than plenty for your current needs, and probably always will be even if you upgrade your physical memory (RAM) to any amount you wish.

---

### Post by byrondallas on 2014-02-02
> **varunendra said:**
> Since you didn't know about hibernation, obviously you don't use it. Even if you now care about it, hibernation is something that doesn't always work well with Ubuntu, that's why it was disabled by default.

I understand Hibernate and Sleep from using Windows but Suspend was something new. I went and checked my power options and it suspends when the lid is closed. 

> In simple terms, forget about hibernation, and leave the partitions as they are. You don't need extra swap. What you currently have is more than plenty for your current needs, and probably always will be even if you upgrade your physical memory (RAM) to any amount you wish.

Sounds good! I'll do as you suggested and just leave it alone. Thanks for all the help guys.

---

