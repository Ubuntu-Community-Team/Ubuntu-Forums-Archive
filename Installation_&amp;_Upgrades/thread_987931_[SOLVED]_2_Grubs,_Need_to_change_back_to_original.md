---
title: "[SOLVED] 2 Grubs, Need to change back to original"
date: 2008-11-20
forum: Installation &amp; Upgrades
---

### Post by VastOne on 2008-11-20
Hi all,

I upgraded Hardy to Ibex on SATA1 with no issues...In order to see if there were any differences with a new install, I installed Ibex to SATA2....and due to issues with that install I need to remove it but, I boot from the Grub of that install back to my original SATA1 Ibex...

I want to eliminate SATA2 Ibex, but before I do that I need to re-establish Grub on SATA1 so that I can get back to my original Grub...

Can one of you gurus point me in the general direction?

I appreciate the help

VastOne

---

### Post by Mr_JMM on 2008-11-20
I do this kind of thing all the time.

It should just be a case of reformatting SATA2 and changing the BIOS to boot from sata1 first. As you installed Ibex a fresh on sata2 then the grub on SATA1 should be untouched.

If for some reason this has not worked then you can do the following:

From Ubuntu on SATA1 or the disk if you can't boot):

> sudo grub

From the new grub command line run ( customized to your system ) the following commands.

>root (hd0,0)
>setup (hd0)


Replace hdx,y with what is relevant to your system.

(hd0) = the MBR for HDD where grub resides.

(hd0,0) is the partition that contains GRUB.

[EDIT] You may want to grab a copy of the SGD (SuperGrubDisk). Once done, boot from and choose what I think is the 3rd option (the first option after the ones that involve a help menu, forget what it says, something like "Linux >> MBR Auto ;-)))"

---

### Post by VastOne on 2008-11-20
Mr_JMM,

I appreciate the response...Do you have any idea as to why a new grub was installed on SATA2 when I made no changes to the bios to begin with?  I was surprised by this as I thought it would just use the grub on SATA1. Might it have to do with me installing Ibex on SATA2 using the defaults, meaning no custom, just letting gpart create what it needed and install?  Just curious...

One final question,  I can run grub from a normal boot of Ibex on SATA1 and not from the live CD? I can re-install grub to SATA1 using your instructions while in that environment?

Thanks.

VastOne

> **Mr_JMM said:**
> I do this kind of thing all the time.

It should just be a case of reformatting SATA2 and changing the BIOS to boot from sata1 first. As you installed Ibex a fresh on sata2 then the grub on SATA1 should be untouched.

If for some reason this has not worked then you can do the following:

From Ubuntu on SATA1 or the disk if you can't boot):



[EDIT] You may want to grab a copy of the SGD (SuperGrubDisk). Once done, boot from and choose what I think is the 3rd option (the first option after the ones that involve a help menu, forget what it says, something like "Linux >> MBR Auto ;-)))"

---

### Post by Mr_JMM on 2008-11-20
Installing GRUB is just part of the installation. Sometimes it doesn't cause an issue, sometimes it does but when it does then it's usually quite simple to correct problems.

I just ran a test where I repaired GRUB from within the actual installation (I installed openSUSE on a seperate HDD then removed it again to replicate the situation).

I'm not saying that this is the best / safest method but it this instance it worked. I simply used the SGD to boot into my Ubuntu, logged in as regular user then did as above from terminal using:

```
sudo grub

grub> root (hd0,0)
grub> setup (hd0)
grub> quit

exit

[EDIT]Not forgetting:
Replace hdx,y with what is relevant to your system.

(hd0) = the MBR for HDD where grub resides.

(hd0,0) is the partition that contains GRUB.

```

. Rebooted and all is well.

If you get stuck, post and I'll try and walk you through it.

---

### Post by VastOne on 2008-11-20
Mr_JMM

I got the following trying your solution

Appreciate your help


grub> root (hd0,0) 
root (hd0,0)
grub> setup (hd0)
setup (hd0)

Error 17: Cannot mount selected partition
grub> 



> **Mr_JMM said:**
> Installing GRUB is just part of the installation. Sometimes it doesn't cause an issue, sometimes it does but when it does then it's usually quite simple to correct problems.

I just ran a test where I repaired GRUB from within the actual installation (I installed openSUSE on a seperate HDD then removed it again to replicate the situation).

I'm not saying that this is the best / safest method but it this instance it worked. I simply used the SGD to boot into my Ubuntu, logged in as regular user then did as above from terminal using:

```
sudo grub

grub> root (hd0,0)
grub> setup (hd0)
grub> quit

exit
```

. Rebooted and all is well.

If you get stuck, post and I'll try and walk you through it.

---

### Post by VastOne on 2008-11-20
I think I solved it...

I was (hd0,1)

and ran it again with that and it succeeded

Rebooting now to see if it worked....

> **VastOne said:**
> Mr_JMM

I got the following trying your solution

Appreciate your help


grub> root (hd0,0) 
root (hd0,0)
grub> setup (hd0)
setup (hd0)

Error 17: Cannot mount selected partition
grub>

---

### Post by Mr_JMM on 2008-11-20
Sorry, I forgot to mention when I repeated the code...

Change hd0,0 to what ever is relevant to your situation. Will edit the post for anyone else viewing it.

---

### Post by VastOne on 2008-11-20
It did...

Thank you Mr_JMM

for your help and patience...

VastOne


> **VastOne said:**
> I think I solved it...

I was (hd0,1)

and ran it again with that and it succeeded

Rebooting now to see if it worked....

---

### Post by Mr_JMM on 2008-11-20
No worries. Glad I could help.


For the benefit of others, a reminder that if this doesn't work for you then you will probably need to run the above code using a LIVE CD environment.


Please feel free to ask if you have any more questions regarding GRUB etc.


Enjoy.

---

### Post by VastOne on 2008-11-23
Kudos JMM...

Marked as solved with you the solver.....

VastOne

> **Mr_JMM said:**
> No worries. Glad I could help.


For the benefit of others, a reminder that if this doesn't work for you then you will probably need to run the above code using a LIVE CD environment.


Please feel free to ask if you have any more questions regarding GRUB etc.


Enjoy.

---

