---
title: "Grub problem following upgrade from 22.04 to 24.04 on a very old laptop"
date: 2024-09-29
forum: Installation &amp; Upgrades
---

### Post by georgesgiralt on 2024-09-29
Hello all
I've an old laptop (Intel Core2 with 4Gib memory, BIOS only, Sata disc but IDE CDROM Writer... ). 
Before upgrading, I had the grub menu displayed on the screen (and I can't remember if I needed something special for this).
After upgrading (which did not finish properly because Thunderbird had an installation problem) the grub menu is not displayed anymore but I can select the default entry by pressing "enter" on the blanl screen. 
I wonder what I should do to get my grub menu back ? 
All help would be appreciated. 
Have a nice and bright day !

---

### Post by Rubi1200 on 2024-09-29
Since it seems you can boot into the install and reach the desktop, let's try this first:

Open a terminal and enter ```
sudo nano /etc/default/grub
```

Change ```
GRUB_TIMEOUT_STYLE=hidden
``` to this ```
GRUB_TIMEOUT_STYLE=menu


```

Also change the timeout to this ```
GRUB_TIMEOUT=5

```
Run ```
sudo update-grub

```

Reboot.

Fixed?

---

### Post by georgesgiralt on 2024-09-29
Can't test it for now, but in the meantime i looked at the backups I had and the default/grub file is identical of the previous one. So either the hidden directive was ignored  in the previous version or ..... 
I'll report back tomorrow. 
Thanks for your answer.

---

### Post by oldfred on 2024-09-29
My old core2 system from 2006 only had 1.5GB of RAM. As long as I did not load more than one larger app like Firefox & several smaller ones like zim & terminal I was ok. Otherwise I got about 2 sec of gray screen as it went to swap. I retired system with 12.04 as last install. Both batteries are dead, so bit of a hassle to boot as I have to reset BIOS clock and keep power on to use system.
As test I tried installing 20.04 and Ubuntu would not even install. Server installs & Kubuntu installed.

I then needed that old laptop for a trip and had 22.04 Kubuntu on an external SSD for UEFI boot. Added old BIOS boot stanza on old HDD and was able to boot SSD. Actually worked bit better. Still tried to not use too much RAM, but when I did swap on SSD was much faster.

Suggest lighter weight flavor for any system that old. Or maybe Kubuntu as mid-weight flavor. And a SSD.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, Xubuntu, Ubuntu MATE, Budgie
Flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors)

---

### Post by georgesgiralt on 2024-09-30
> **oldfred said:**
> My old core2 system from 2006 only had 1.5GB of RAM. As long as I did not load more than one larger app like Firefox & several smaller ones like zim & terminal I was ok. Otherwise I got about 2 sec of gray screen as it went to swap. I retired system with 12.04 as last install. Both batteries are dead, so bit of a hassle to boot as I have to reset BIOS clock and keep power on to use system.
As test I tried installing 20.04 and Ubuntu would not even install. Server installs & Kubuntu installed.

I then needed that old laptop for a trip and had 22.04 Kubuntu on an external SSD for UEFI boot. Added old BIOS boot stanza on old HDD and was able to boot SSD. Actually worked bit better. Still tried to not use too much RAM, but when I did swap on SSD was much faster.

Suggest lighter weight flavor for any system that old. Or maybe Kubuntu as mid-weight flavor. And a SSD.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, Xubuntu, Ubuntu MATE, Budgie
Flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors)
Hello OldFred, Actually this laptop runs very very fine. Even if it is from 2007 and came with Windows Vista ;-) 
A very long time ago someone gave me RAM to reach 4GiB. This changed things a lot. It was slow to boot but once booted, a good machine for surfing.
I use it in the workshop to, essentially, reach Internet to search Google and use VirtualBox and a Windows XP machine to run diagnostic software...
One day the hard disk failed. I then bought a very cheap SSD disk and this made this machine perfectly viable.
I'll test your changes this morning and report back.

---

### Post by georgesgiralt on 2024-09-30
So,  changing to "GRUB_TIMEOUT_STYLE=menu" did the trick. 
Now, I've a question :
How come that the preceding Ubuntu version had the term "hidden" and the menu was visible ? And how come that on another laptop (albeit EFI one) it still has "hiden" and the menu is visible ? 
Anyway, thank you very much for the help. 
Have a nice and bright day !

---

### Post by yancek on 2024-09-30
One possibility would be if the lines you are referring to have a # at the beginning, they are not read.  The first line entry below would hide the menu, the second would not.

> GRUB_TIMEOUT_STYLE=hidden
>  #GRUB_TIMEOUT_STYLE=hidden

---

### Post by georgesgiralt on 2024-09-30
They are not commented out on either computer...

---

### Post by ubfan1 on 2024-09-30
[https://www.gnu.org/software/grub/manual/grub/html_node/Simple-configuration.html#Simple-configuration](https://www.gnu.org/software/grub/manual/grub/html_node/Simple-configuration.html#Simple-configuration)
Certainly not straightforward, and it is not obvious to me why it was set up that way ;^)

---

### Post by Rubi1200 on 2024-09-30
> **georgesgiralt said:**
> So,  changing to "GRUB_TIMEOUT_STYLE=menu" did the trick.

Glad to hear you got this resolved.

Please help others by marking this thread as Solved using the Thread Tools at the top of your first post.

Thanks!

---

