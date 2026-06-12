---
title: "Dual Boot -- which size is for Ubuntu?"
date: 2007-10-06
forum: Installation &amp; Upgrades
---

### Post by kkruecke on 2007-10-06
When I get to the install prompt about partion sizes--"Resize IDE1 master, partition #1 (hda1) and use freed space"--the slider is set to 61% (of my 291GB HD).  I've got a 291GB Harddrive with Windows Vista installed.  I want to install Ubuntu server/Dual Boot

Q1: Is that 61% for Ubuntu or Windows?

Q2: How much should I allocate in GB for Ubuntu?  In the Ubuntu partion I will install MySql, Postfix, Lighttpd, Dovecot, gcc, php5 and Roundcube and Distcc.  if I don't want to run out of space on the Window partion since this will remain primarily a Windows pc.

thanks,
Kurt

---

### Post by rsambuca on 2007-10-06
Whoa, stop right there!

If you are using Vista, I **highly recommend** that you use Vista's Disk Management utility to "shrink" the Vista partition first.  Then use the Ubuntu installer to use the free (unallocated) space.  There have been a lot of problems with Vista not booting after being resized with the Ubuntu gparted partitioner.

---

### Post by Pumalite on 2007-10-06
With Vista; use the Vista partitioner.
One you have the new partition a good scheme is:
10 Gb for '/'
2x RAm for /swap up to 2 GB
The rest for home.
(go Manual)

---

### Post by Pumalite on 2007-10-06
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

### Post by ryanVickers on 2007-10-06
Please!  Just set it up manually!  Don't use the "I'll just let you do whatever and assume it won't ruin my system" tool!  (also called "automatic sizing" (or something):p)

---

### Post by Pumalite on 2007-10-06
I prefer Manual too.

---

### Post by jean noel on 2007-10-07
> **Pumalite said:**
> [http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

as a vista user i consider the "how to forge...."link a great one. as for doing back to windows after using ubuntu. I doubt it.
It may not be as user friendly, but it is great.
PS I left 20gb for ubuntu.

---

### Post by kkruecke on 2007-10-07
Thanks for the replies!

---

### Post by Pumalite on 2007-10-07
Happy Ubuntuing!

---

### Post by fizgig on 2007-10-18
Nobody answered his question near as I can tell.  I had exactly the same question when I saw that slider.  I would like to know since I dual-boot with XP so I don't have the problems associated above.

My guess is that the slider shows you the new size for the windows partition.

---

### Post by secretkeeper81 on 2007-10-18
> **kkruecke said:**
> When I get to the install prompt about partion sizes--"Resize IDE1 master, partition #1 (hda1) and use freed space"--the slider is set to 61% (of my 291GB HD).

Q1: Is that 61% for Ubuntu or Windows?

I think it's for Windows. It means that the hda1 partition's size will be shrinked to 61% of what it used to be.

---

### Post by kkruecke on 2007-10-18
The intial reponses recommended NOT using the Ubuntu partioner when installing Ubuntu on Vista, but to
to use the Windows Vista partioner to shrink the windows partion. 

[[COLOR="Red"]Ubbuntu Dual boot 1[/COLOR]]("http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first")

[[COLOR=RED]Ubuntu dual boot 2[/COLOR]]("http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?")

Both URLs recommended this technique.

Then when the Ubuntu installer load the disk partitioner, choose "Manual - use the largest continuous free space." This will This will automatically select the unpartitioned space we created earlier using the Shrink tool.

---

### Post by cddot on 2007-10-20
> **Pumalite said:**
> With Vista; use the Vista partitioner.
One you have the new partition a good scheme is:
10 Gb for '/'
2x RAm for /swap up to 2 GB
The rest for home.
(go Manual)

Can someone clarify about the 10 GB for '/' ?

The 10GB is for the OS, as well as "reasonable" amount of room for all the additional application software?

Or just the core OS?

---

### Post by rsambuca on 2007-10-20
> **cddot said:**
> Can someone clarify about the 10 GB for '/' ?

The 10GB is for the OS, as well as "reasonable" amount of room for all the additional application software?

Or just the core OS?

If you have a separate /home partition, then 10GB should be plenty for most users.

---

