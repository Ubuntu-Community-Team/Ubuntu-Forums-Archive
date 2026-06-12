---
title: "Error in GRUB"
date: 2012-10-23
forum: Installation &amp; Upgrades
---

### Post by sbratna14 on 2012-10-23
Dear user,
My Ubuntu Linux was working fine. I have upgraded my Linux today but it couldn't boot after I restarted the machine. I tried most of the options but didn't  get any success. Now, after restarting my PC, it directly goes to "GRUB" window with cursor blinking.
Could you please suggest how can I reboot my PC successfully.
At least the previous version of Linux is also OK for me.
I am realizing that it was a mistake to upgrade though everything was working fine with the previous version.
I am eagerly waiting for your reply.
SBR

---

### Post by Bucky Ball on 2012-10-23
You upgraded from 12.04 to 12.10 using the Update Manager method?

---

### Post by sbratna14 on 2012-10-23
Thanks for your reply. I don't remember exactly the last version I used. The last time I upgraded was a year ago. Today I have upgraded online the current version. Yes, i used "Update manager" method.
Thanks.
SBR

---

### Post by Bucky Ball on 2012-10-23
You might try using Boot Repair. You can boot from a LiveCD and install it via Synaptics (yes, even in a live environment) or download the ISO, make a disk, and boot from that. 

Run Boot Repair and see if it fixes but remember to post the report it creates if not.

---

### Post by sbratna14 on 2012-10-23
Hi,
Thanks for your reply. As, I don't have boot repair live CD, I used  Ubuntu live CD and I tried to repair the GRUB in command mode using the information from [http://howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/](http://howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/)

Now, I restarted my PC and found different GRUB screen. I checked that the "grub.cfg' file is available inside /boot/grub/ directory. However, I am not able to boot my PC.

My present GRUB screen appears with the following information.

GNU GRUB version 1.99-21ubuntu3.4
Minimal BASH-like editing is supported......
Grub>

Could you please tell me how to proceed further.

Thanks.
SBR

---

### Post by YannBuntu on 2012-10-23
Hello
Please indicate your [Boot-Info URL]("https://help.ubuntu.com/community/Boot-Info").

---

### Post by dino99 on 2012-10-23
the problem is that 12.10 use grub 2.0, and that one is so different that previous 1.99 and are not compatible.
so, when you are booted, open synaptic to purge ALL the grub installed packages, then reinstall grub-pc. Thats the first step, as the installed grub is 1.99 now.
Then boot on 12.10, and redo the above  command, to get grub 2.0 installed.
Take care to let that grub 2.0 as the master bootloader if you also have some other distros with a non grub 2.0 installed.

---

### Post by sbratna14 on 2012-10-23
@yannbuntu
Hi, Thanks for your reply. I shall try the boot repair and let you know the Boot-info URL.

Regards
SBR

---

### Post by sbratna14 on 2012-10-23
@dino99
Hi, Thanks for your reply and suggestions. I am trying to follow but couldn't understand properly.
1) so, when you are booted....
Is this booting of my default Linux PC or with Live CD

2)  open synaptic to purge ALL the grub installed packages, then reinstall grub-pc....
Could you please elaborate what exactly I need to do. Is this in GRUB command or Live CD.

Is this possible without Boot-repair.

Thanks.
SBR

---

### Post by YannBuntu on 2012-10-23
> **dino99 said:**
> the problem is that 12.10 use grub 2.0, and that one is so different that previous 1.99 and are not compatible.

I don't have such problem on my system. Any bug report please?

---

### Post by sbratna14 on 2012-10-24
Dear All,
Thanks for your kind help and suggestions. I could successfully boot my PC using the 'boot repair' live CD.

Sincerely
SBR

---

### Post by Bucky Ball on 2012-10-24
Excellent news and you're welcome. If all fixed please mark as 'Solved' to help others, from 'Thread Tools' at top right.

---

