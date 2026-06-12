---
title: "Problem with updating to 11.04:  stuck at GRUB"
date: 2011-08-21
forum: Installation &amp; Upgrades
---

### Post by sjogan on 2011-08-21
I have been running 10.04 for awhile within a VM machine on my Windows 7 box.  No problems.

Updating from 10.04 to 10.10 went smoothly.

Updating from 10.10 to 11.04 went smoothly until the VM rebooted.  It is stuck at "GNU GRUB version 1.98-1ubuntu7" and it looks like it is waiting for a command.

I have never done this before and am wonder what to do next.

Any advice would be appriciated.

thank you

---

### Post by YesWeCan on 2011-08-21
Hi, welcome.
See [https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode)

---

### Post by sjogan on 2011-08-22
Thank you for your reply.

I have read over your response and read the link you have provided.

Unfortunately, there was no change to my system.

I have tried to find some command(s) that would install GRUB 2, but nothing is working.  (i am assuming my problem is that I need GRUB 2)

I tried this:
"grub> root (hd0,1)
grub> linux /vmlinuz root=/dev/sda1
grub> boot"

it showed a long list of information but the command prompt stopped working.

I have not found out how to "boot from CD" on the vmware machine when it is defaulting to my ubuntu. (i'm sure there is an easy solution, i just do not know what it is.)

I have been reading through others help both within these forums and Google.  I have not found any solutions that work yet.

any further help would be appreciated.

thank you.

---

### Post by sjogan on 2011-08-22
i have re-read what you showed me and reviewed other solutions.

i have to modified my original post and say i now have a working ubuntu vm machine again.

my code that I ran was:

grub> set root=(hd0,1)
grub> linux /vmlinuz root=/dev/sda1 ro
grub> initrd /initrd.img
grub> boot

i had to modify a few lines for my own configuration.

thank you again for your help.

---

### Post by sjogan on 2011-08-22
new related problem.

i get the GRUB screen every time i run my VM version of Ubuntu.

How do I install this GRUB to have a permanent fix?

thank you

---

### Post by YesWeCan on 2011-08-22
Glad you got it working...at least once.
I am not very knowledgeable about grub-legacy but I think you have to edit /boot/grub/menu.lst to have those same instructions. You may also need to do[COLOR=Navy] sudo install-grub /dev/sda[/COLOR].

[edit] I just realised this statement is rubbish because you are using Grub 1.98 which is Grub2. So instead, once booted run sudo update-grub and sudo grub-install /dev/sda.

---

### Post by sjogan on 2011-08-26
Noobie question.

how do i mark this as solved?

---

### Post by YesWeCan on 2011-08-26
You use the [COLOR=Red]Thread Tools[/COLOR] menu above. :)

---

