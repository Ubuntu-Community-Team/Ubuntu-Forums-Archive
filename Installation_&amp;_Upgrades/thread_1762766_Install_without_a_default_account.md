---
title: "Install without a default account"
date: 2011-05-19
forum: Installation &amp; Upgrades
---

### Post by amsayk on 2011-05-19
Hello,

I want to install install an ubuntu server (10.04) VM, but i do not want to create a default user, 

that way i can reuse the vm (login as root and create the default user whenever i need another vm),

the problem is how am i going to login as root, what is the default root password in ubuntu?

or is there another way to do this?

Thanks in avance.

---

### Post by spcwingo on 2011-05-19
The root account is locked by default in Ubuntu (sudo is used to gain root privileges), hence the reason you are prompted to create a non-root account.  I'm certain that you would be able to accomplish what you want, but I have no idea how to do it.  I just thought you would like to know about the root account.

---

### Post by jerrrys on 2011-05-20
the command **sudo su **will open a root terminal, maybe thats what your looking for

---

### Post by amsayk on 2011-05-20
> **spcwingo said:**
> The root account is locked by default in Ubuntu (sudo is used to gain root privileges), hence the reason you are prompted to create a non-root account.  I'm certain that you would be able to accomplish what you want, but I have no idea how to do it.  I just thought you would like to know about the root account.

Thanks for the quick reply,

i wish there was a way to specify the root password at installation time at least for ubuntu server, this was sort of possible with vmbuilder i think.

i'll just create the default user for now.

Cheers.

---

