---
title: "How to delete windows vista(loader) on boot menu?"
date: 2011-10-11
forum: Installation &amp; Upgrades
---

### Post by zeuso0 on 2011-10-11
Hi,

I bought a netbook with windows 7 installed.
then I partitioned a 20G D:drive from C:drive and installed ubuntu netbook remix 10.10 in it, alongside with win7

However, too many options exists in my grub menu list !

```
xxx@ubuntu:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-30-generic
Found initrd image: /boot/initrd.img-2.6.35-30-generic
Found Windows Vista (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done
```

Where the heck windows vista come from?? I never had Vista before.
and HOW TO remove windows vista (loader) and windows 7 (loader) from menu list ?

---

### Post by Quackers on 2011-10-11
The Vista entry is likely to boot the Windows recovery partition. I would just put up with it, personally.
If you remove Windows 7 entry you won't be able to boot Windows!

---

### Post by zeuso0 on 2011-10-11
> The Vista entry is likely to boot the Windows recovery partition. I would just put up with it, personally.
If you remove Windows 7 entry you won't be able to boot Windows!But the thing is: the grub menu came up after I selected "ubuntu netbook". 
so it's like, when restarting, the first menu asks me to choose "windows 7" or "ubuntu",  once I selected "ubuntu", it then came up with a second menu list which is the menu I showed in my first message.

Any ideas?

---

### Post by garvinrick4 on 2011-10-11
#The Vista partition is as Quackers states Vista is just how linux reads that partition does
not mean Vista is installed.
#You would have to run this and post it. All else will be a quess.
[Boot Info Script | Download Boot Info Script software for free at SourceForge.net]("http://sourceforge.net/projects/bootinfoscript/")

---

### Post by Quackers on 2011-10-11
So where does the first menu come from and what's on it?
Does it look similar to the second menu?

---

### Post by garvinrick4 on 2011-10-11
> So where does the first menu come from and what's on it?
Does it look similar to the second menu?I am wondering if a WUBI install is still left in BCD of Windows or something WUBI
going on here. 2 grub menu's just seems like something left hanging around from wubi. What do you think Quackers?

---

### Post by Quackers on 2011-10-11
Yes, or maybe EasyBCD is involved, perhaps.

---

### Post by zeuso0 on 2011-10-11
> **garvinrick4 said:**
> #The Vista partition is as Quackers states Vista is just how linux reads that partition does
not mean Vista is installed.
#You would have to run this and post it. All else will be a quess.
[Boot Info Script | Download Boot Info Script software for free at SourceForge.net]("http://sourceforge.net/projects/bootinfoscript/")

Thanks for the reply.
Here is what I got after running the script:
```
xxx@ubuntu:~/Desktop$ sh boot_info_script.sh 

boot_info_script version: 0.60        [17 May 2011]


"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.

[: 326: busybox awk: unexpected operator
boot_info_script.sh: 353: Syntax error: "(" unexpected (expecting "fi")

```

So what does this unsuccessful result mean?

---

### Post by Quackers on 2011-10-11
Try installing gawk first via synaptic package manager.

---

### Post by zeuso0 on 2011-10-11
> **Quackers said:**
> So where does the first menu come from and what's on it?
Does it look similar to the second menu?

```
The first menu: windows 7 and ubuntu netbook, two options.

if windows 7 chosen, then goes to win 7 desktop
if ubuntu netbook chosen, then goes to the 2nd menu, which has: 
ubuntu with linux 2.6.32-30 generic
ubuntu with linux 2.6.32-30 generic safe mode
windows vista (loader)
windows 7 (loader)

```

The reason why this is important to me is that I once mis-clicked on "windows vista (loader)", and it brought me into grub rescue prompt and it took me the whole lot of time to get out. 

So I want to remove the "vista" option real badly
Could you guys help?

---

### Post by bcbc on 2011-10-11
You installed with Wubi. The second menu is the standard Ubuntu menu (and that has detected windows and windows recovery... in the upcoming 11.10 release windows entries will be suppressed on Wubi installs). 

Since you should only be booting Ubuntu from this menu (which comes at the top) you can just ignore the other entries. There's no easy way to prevent this menu showing.

Installing a regular dual boot will get rid of the first (windows boot manager) menu, and then all you'll see is the grub menu - and so you'll need the windows entry to boot windows.

---

### Post by Quackers on 2011-10-11
Do you have a previous wubi installation?
Have you installed EasyBCD in Windows?
Did you install gawk and re-run the boot script?

EDIT  see above post :-)

---

### Post by zeuso0 on 2011-10-11
> **Quackers said:**
> Try installing gawk first via synaptic package manager.

OK, I have installed gawk.
It seems to me  that the result is the same.
```
xxx@ubuntu:~/Downloads/boot_info_script060$ sh boot_info_script.sh 

boot_info_script version: 0.60        [17 May 2011]

boot_info_script.sh: 353: Syntax error: "(" unexpected (expecting "fi")
```

I previous installed wubi but I have formated the whole drive and reinstalled wubi.

---

### Post by Quackers on 2011-10-11
Did you see bcbc's post? post #11

---

### Post by zeuso0 on 2011-10-11
Yes, I see. If there is no easy way then I'll just leave it along.
Hopefully the new versions will be optimized on these things.

Thanks for all the replies.

---

