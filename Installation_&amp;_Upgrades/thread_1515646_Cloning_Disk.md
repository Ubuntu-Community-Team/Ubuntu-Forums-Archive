---
title: "Cloning Disk"
date: 2010-06-22
forum: Installation &amp; Upgrades
---

### Post by ZER01NE1NE on 2010-06-22
Hi,

So I'm upgrading from a 186GB hard drive with Windows and Ubuntu on it to a 500GB that I recently bought. I used Clonezilla 1.2.5 to clone the old hard drive onto the new one. When I boot from the new one, Grub works fine, showing all the operating systems and options. Windows XP works fine. Ubuntu loads the kernel, but that's when it runs into problems. As the kernel boots, it comes up with all kinds of error messages as it tries to read from the new disk. Sometimes it boots successfully, and sometimes it doesn't. Can anyone help me? Thanks in advance.

---

### Post by stlsaint on 2010-06-22
Sounds as if you have a bad hard drive with your new drive or maybe that old drive was bad that you cloned. I dont know the specifics of how clonezilla works but it may have copied the bad sectors and placed them onto the bad drive or maybe a bad corrupt filesystem.
Just my two cents on it.

---

### Post by pytheas22 on 2010-06-22
It could be that the file system is corrupted.  I would boot to a live CD, mount the hard disk that's giving you trouble and run the "fsck" utility on it.  If you need more specific instructions than this let me know.

Assuming there are file system errors, hopefully fsck will be able to fix them, and then you'll be all set.

---

### Post by Don Barzini on 2010-06-22
> **ZER01NE1NE said:**
> Hi,

So I'm upgrading from a 186GB hard drive with Windows and Ubuntu on it to a 500GB that I recently bought. I used Clonezilla 1.2.5 to clone the old hard drive onto the new one. When I boot from the new one, Grub works fine, showing all the operating systems and options. Windows XP works fine. Ubuntu loads the kernel, but that's when it runs into problems. As the kernel boots, it comes up with all kinds of error messages as it tries to read from the new disk. Sometimes it boots successfully, and sometimes it doesn't. Can anyone help me? Thanks in advance.


Did you use Clonezilla as the **root** user?

Did you use **Expert Mode** and choose the option to clone to a larger disk (I think it is option -k1)?

Post the output of your **/var/log/messages** file.

---

### Post by ZER01NE1NE on 2010-06-22
OK, I forgot to mention a few things. The old hard drive works fine, I'm just upgrading, and the new one is brand new, like right out of the box. And like I said, Windows and Grub work just fine, so I'm thinking it's a problem with Linux. What I don't understand is, if the kernel can't read the hard drive, then how did the kernel load in the first place? I'll post that stuff you guys asked for when I get a chance, probably sometime tonight.

---

### Post by Don Barzini on 2010-06-22
> **ZER01NE1NE said:**
> OK, I forgot to mention a few things. The old hard drive works fine, I'm just upgrading, and the new one is brand new, like right out of the box. And like I said, Windows and Grub work just fine, so I'm thinking it's a problem with Linux. What I don't understand is, if the kernel can't read the hard drive, then how did the kernel load in the first place? I'll post that stuff you guys asked for when I get a chance, probably sometime tonight.

Did you remove the old drive and put the new drive on the IDE or SATA channel (you didn't mention your hardware type) the original drive was using after you were done with cloning?

I don't think there was ever a doubt that the original drive still didn't work. You could always redo the disk clone. This time entering a root shell in Clonezilla and do your cloning as root.

Your problem could very well be a "permissioning" problem.

In Clonezilla after initial bootup and choosing language and keymap.... you then choose the option "Enter Shell __ Enter command line prompt"..... then choose option [2] for a command line shell.

You then **MUST** become root (superuser) if you want the job to go smoothly. You simply type at the Clonezilla shell command prompt....

```
sudo su -
```

You will immediately see that the prompt changes to a root prompt (#).

Then you type Clonezilla to enter the program as the root user....

```
clonezilla
```

I'm willing to bet that if you mounted the ext4 partition on that new drive, the permissions on the system directories will be all wrong.

---

### Post by foxmulder881 on 2010-06-22
Not that it helps you, but when upgrading hard drives, I always perform a fresh install of all OS's. Windows is often not too fussy, but Linux can be tricky to get configured in the same manner as prior to the upgrade.

Clone disks/applications are fine for data cloning and transfers but more often and not operating systems.

Just speaking from experience of course.

---

### Post by ZER01NE1NE on 2010-06-22
Both hard drives are SATA. Whenever I'm finished cloning, I always unplug the old one to make sure I'm booting from the new one. The old one always works and the new one never does. I used fsck and it didn't find any errors, the filesystems are fine. I've re-cloned this disk at least 5 times, and never once has it worked properly. I'm trying again, as root. I'll post the results of /var/log/messages when this is done.

---

### Post by Don Barzini on 2010-06-22
> **ZER01NE1NE said:**
> Both hard drives are SATA. Whenever I'm finished cloning, I always unplug the old one to make sure I'm booting from the new one. The old one always works and the new one never does.

You also need to change around the SATA data cables so that the new drive is attached to the same (or original) channel as the old drive was previously attached.

---

### Post by pytheas22 on 2010-06-23
> OK, I forgot to mention a few things. The old hard drive works fine, I'm just upgrading, and the new one is brand new, like right out of the box. And like I said, Windows and Grub work just fine, so I'm thinking it's a problem with Linux. What I don't understand is, if the kernel can't read the hard drive, then how did the kernel load in the first place? I'll post that stuff you guys asked for when I get a chance, probably sometime tonight.

If you have disk corruption, this could still happen.  The part of your hard drive where your Windows and grub files are stored could be fine, but the data on your Linux root partition might be corrupted.  I would still recommend running fsck on the Linux partition just to check.

It might also be useful to see exactly which kinds of error messages you get when Linux fails to boot properly.  If it complains about stuff like input/output errors or failure to mount file systems, your data is probably corrupted and/or you have disk hardware issues.

---

