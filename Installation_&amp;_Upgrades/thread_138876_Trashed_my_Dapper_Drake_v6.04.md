---
title: "Trashed my Dapper Drake v6.04"
date: 2006-03-02
forum: Installation &amp; Upgrades
---

### Post by n1gke on 2006-03-02
Dang! I did it again. Well, not so badly this time anyway.

Using Adept, I deleted the wrong kernel and now get only error message 15 when trying to boot. Grrrrr......

I would like to finger out how to re-install the kernel without losing everything on the drive. 

To compound the trouble, I have three IDE drives and Ubuntu Dapper Drake v6.04 was installed on /dev/hdc1, which is the secondary master.

On /dev/hda1 is installed Kubuntu. I can use that, but prefer using it is a back-up to research information about my Dapper troubles, phew.

Oh well, back to work I go. . .  

Cheers.

---

### Post by andrewsawyer on 2006-03-02
When you say you deleted the wrong kernel, do you mean that you deleted all of them?  If not, could you not just boot off the old one?  That or maybe boot off a livecd, chroot into the dapper system and then reinstall the kernel.

---

### Post by n1gke on 2006-03-03
Ummm.....
I am using now the live cd.

I can see that everything is still on the /dev/hdc1

Using Adept, I was releasing, or deleting older kernel versions and accidently deleted the working kernel, v2.6.15-15-386

The only working version kernel available is on /dev/hda1, but I would like to boot from /dev/hdc1 instead, as I was doing before.

---

