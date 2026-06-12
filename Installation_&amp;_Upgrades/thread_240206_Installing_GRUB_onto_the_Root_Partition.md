---
title: "Installing GRUB onto the Root Partition?"
date: 2006-08-20
forum: Installation &amp; Upgrades
---

### Post by luvr on 2006-08-20
When I installed Ubuntu 6.06, I was surprised that it didn't ask me where I wanted to install GRUB--e.g., on the Master Boot Record, or on the boot block of the Root (or Boot) partition. Ubuntu just overwrote my Master Boot Record without asking.

Now, I have a separate GRUB partition that gets booted through the Master Boot Record, and I prefer to keep it that way. Not a big deal, really, since I can easily reinstall the loader for this partition into the MBR (which is exactly what I did).

I'm just wondering if I overlooked the option to select the location for the GRUB boot loader, or if it is really missing? And, if it *is* missing, then was that done on purpose? (I can understand that the option may be confusing to quite a few users, who may never have heard about a *"Master Boot Record,"* and I don't want to imply that it *should* be present--I'm just a bit surprised that I didn't see it.)

---

### Post by linuxnewbie946 on 2006-08-20
> **luvr said:**
> When I installed Ubuntu 6.06, I was surprised that it didn't ask me where I wanted to install GRUB--e.g., on the Master Boot Record, or on the boot block of the Root (or Boot) partition. Ubuntu just overwrote my Master Boot Record without asking.

Now, I have a separate GRUB partition that gets booted through the Master Boot Record, and I prefer to keep it that way. Not a big deal, really, since I can easily reinstall the loader for this partition into the MBR (which is exactly what I did).

I'm just wondering if I overlooked the option to select the location for the GRUB boot loader, or if it is really missing? And, if it *is* missing, then was that done on purpose? (I can understand that the option may be confusing to quite a few users, who may never have heard about a *"Master Boot Record,"* and I don't want to imply that it *should* be present--I'm just a bit surprised that I didn't see it.)

The installation cd doesn't ask you where to install it because it sees another os and thinks, "Hey, I know what to do, I'll install grub to the MBR!"

---

### Post by luvr on 2006-08-21
> **linuxnewbie946 said:**
> The installation cd doesn't ask you where to install it because it sees another os and thinks, "Hey, I know what to do, I'll install grub to the MBR!"
Hehe... Feels somewhat *"backwards"* to me... I would expect it to *"know what to do,"* and to install GRUB into the MBR, if it did **not** see another OS--since that would mean that there isn't any boot mechanism installed yet.

*My* logic would be, to make it think *"Hey, there's an other OS installed here already; I'd better go and ask the user if I should keep the existing boot infrastructure, or if I should overwrite it with my own GRUB bootloader!"*

But, as I said in my original post, it's no big deal, really.

---

### Post by luvr on 2006-08-31
Just discovered that the Ubuntu **Alternate** disc allows you to choose where the GRUB boot loader will go.

**Now** I understand why the standard install won't ask the user any questions about it; many non-technical users will likely get scared away when they get asked if it's *"OK to install the GRUB boot loader onto the Master Boot Record (Yes/No)?"*

Anyone who **does** understand the question, and *wants* to answer it, can simply install Ubuntu from the **Alternate** disc... Great idea, come to think of it!

---

### Post by luvr on 2007-05-30
I did an Ubuntu 7.04 install yesterday, and discovered an **Advanced** button on the last (seventh) screen of install prompts. When I clicked that, a window appeared that allowed me to specify where I wanted to install the GRUB boot loader--the default is **(hd0)** (i.e., the Master Boot Record of the first hard disk).

Don't know if earlier Ubuntu releases included this option, but I find this really neat!

---

### Post by hellmet on 2007-05-30
Hey.. thanks for that useful tip.. Never knew that !! Ubuntu has hidden this for the sake of newbies!!

---

### Post by Fay on 2007-08-01
Hi 

I was reading these posts and was wondering if anyone came across the option where you can choose to install grub into the ubuntu partition without having to explicitly state which partition it is. 

eg in kickstart of redhat u say bootloader --location=partition and it will automatically detect the redhat root partition and install it there.

Would be great if anyone had any feed back on this.

Thanks

---

