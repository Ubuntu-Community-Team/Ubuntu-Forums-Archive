---
title: "Lost root password?"
date: 2010-12-14
forum: Installation &amp; Upgrades
---

### Post by chasem1991 on 2010-12-14
I just did a clean install of Ubuntu Server 10.10. 

I decided to install a shell on it for kicks... Bad idea. Now for some reason if I try to access the package manager, it says that authentication failed. I have the original password written in front of me.

What happened?

PS what I did to install the shell was ```
sudo apt-get install ubuntu-desktop
```

---

### Post by jerz4lunch on 2010-12-14
I used the command on my Ubuntu 10.10 desktop. I'm sure it would work on the server edition too:

```
sudo passwd root
```

This changes the previous password to the password that you choose in the terminal after executing the command.

---

### Post by tad1073 on 2010-12-14
If that doesn't work, you can edit the kernel line from grub. Ad a 1(one) at the end of the kernel and this will drop you to tty1 w/root access, you can change the password from there.

---

### Post by tad1073 on 2010-12-14
> **jerz4lunch said:**
> I used the command on my Ubuntu 10.10 desktop. I'm sure it would work on the server edition too:

```
sudo passwd root
```This changes the previous password to the password that you choose in the terminal.
I think you still have to know the original password.

---

