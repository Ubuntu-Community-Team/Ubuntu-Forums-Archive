---
title: "uninstall grub"
date: 2010-08-08
forum: Installation &amp; Upgrades
---

### Post by moment92 on 2010-08-08
How can I uninstall grub?
I have have dual boot between Gentoo and Ubuntu and I want to use the grub, that is on Gentoo partition, as its my main system. I would not care about it as it takes almost no space, but Ubuntu automatically restores its own bootscreen after updates. This is annoying... How to get rid of it?

---

### Post by chopinhauer on 2010-08-08
> **moment92 said:**
> How can I uninstall grub?
I have have dual boot between Gentoo and Ubuntu and I want to use the grub, that is on Gentoo partition, as its my main system. I would not care about it as it takes almost no space, but Ubuntu automatically restores its own bootscreen after updates. This is annoying... How to get rid of it?

```
sudo dpkg-reconfigure grub-pc
```and when asked where to install Grub, uncheck all entries.

PS: There is no splash screen in the Ubuntu grub, unless configured. The splash screen starts from the initrd.

---

### Post by dreamsR4living on 2010-08-08
Normally, when I install another Linux distro next to Ubuntu, which is my main OS I am able to restore it's grub menu with the help of the Live CD to overwrite the other OS's GRUB.

See this post for more info (I don't know if it is up to date for GRUB 2); [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I never used Gentoo, but it should have a similar option.

---

### Post by moment92 on 2010-08-08
> Normally, when I install another Linux distro next to Ubuntu, which is  my main OS I am able to restore it's grub menu with the help of the Live  CD to overwrite the other OS's GRUB.

I know, I did it. The problem is, that Ubuntu automatically modifies its grub conf sometimes and also overwrites the previous grub.

---

### Post by chopinhauer on 2010-08-08
> **moment92 said:**
> I know, I did it. The problem is, that Ubuntu automatically modifies its grub conf sometimes and also overwrites the previous grub.

Grub modifies its **own** configuration (when 'update-grub' is called, mainly when new kernels are added), so your Gentoo grub is safe.

However I don't think it ever installs itself in the MBR without asking the user first. Anyway you can reconfigure it not to install anywhere.

---

### Post by moment92 on 2010-08-08
> **chopinhauer said:**
> 
However I don't think it ever installs itself in the MBR without asking the user first.

Ubuntu most certainly installed itself into MBR without asking me.

dpkg-reconfigure grub-pc didn't work, it froze for some reason. Nevertheless I got rid of it with apt-get purge grub-pc. I would've done it before, but I didn't know, that the name of the package was grub-pc.

---

