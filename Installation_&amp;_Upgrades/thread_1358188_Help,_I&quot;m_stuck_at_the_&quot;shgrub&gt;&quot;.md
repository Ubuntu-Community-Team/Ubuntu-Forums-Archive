---
title: "Help, I&quot;m stuck at the &quot;sh:grub&gt;&quot; prompt"
date: 2009-12-18
forum: Installation &amp; Upgrades
---

### Post by bamim2 on 2009-12-18
I've managed to hose up my system. When I try to boot, it crashes to shell with a "sh:grub>" prompt & the kernel doesn't load. Is there a way to boot up from here or rescue this installation somehow (with a CD or something)?

---

### Post by renkinjutsu on 2009-12-18
Assuming you have Grub2

> **Gordon Hopper said:**
> I think "file not found" refers to the grub.cfg file. Please post the output of "set" at the grub rescue prompt. Does the "prefix" look correct? You can change the prefix at the grub prompt with, for example

set prefix=(hd0,1)/boot/grub

Use the ls command to find the correct path. (Search works only if the search module is loaded). After the prefix is set correctly, then:

insmod normal
normal

will bring up the grub menu.

If that works, then the final step is to save the environment permanently. I don't know how to do that yet. (I'm having the same issue).

then, when you're booted into ubuntu:

> **Zaur Nasibov said:**
> You have to reinstall grup-common and grub-pc packages.

These solutions were posted on [launchpad]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/355359")

---

### Post by darkod on 2009-12-18
First of all, did you install wubi and not full ubuntu? This error is common for wubi, not so much for ubuntu. If you installed wubi inside windows, the procedure is different.

---

### Post by bamim2 on 2009-12-18
Thank you to all who tried to help me on this. I messed it up too badly & had to reinstall.

---

### Post by bamim2 on 2009-12-31
Well, I did it to myself again! I can't boot into Ubuntu again.

How would I know that it's Wubi? Or how would I have known (since I can't boot that OS anymore)? 

I did install it from within Windows XP, but it doesn't run from inside of Windows or anything. When the PC boots up, Grub stops Windows loading & asks if I want to boot to Windows or Ubuntu. Unfortunately if I choose Ubuntu now it drops me at that prompt. 

I tried "insmod normal", "normal" & that didn't work. Is there something else I can try? 

I'm on the PC right now booted to Windows (of course). I really need to get this fixed pretty soon or I'm going to have to remove & reinstall the Ubuntu OS. I really don't want to spend my New Years Eve (tonight) installing Linux. Again. 

Any suggestions (that relate to this) or explanations would be greatly appreciated. 

============
"I didn't want to do this. What I really wanted to be was .... a lumberjack.... Ohhhh, I am a lumberjack & I'm ok...." :guitar:

---

### Post by darkod on 2009-12-31
If you install it from within windows, it's wubi and not ubuntu. I guess it's not grub stopping the windows boot but that's the windows bootloader asking you if you want to boot windows or the virtual ubuntu, wubi.
When it stops to ask you, notice what does it say above the menu, if it doesn't say Grub 1.97 then it's not grub.
This sh:grub problem has been around for wubi. I would recommend using full ubuntu, on its own partition and its own filesystem. Wubi is running sort of virtual ubuntu inside windows and can create issues.

---

### Post by bamim2 on 2009-12-31
Can Ubuntu make it's own partition on my hard drive without messing with the Windows file system that's already there?

---

### Post by garvinrick4 on 2009-12-31
When you deleted WuBi install the first time you left the wubi that attaches itself to
dos4grub. If you go to command line in Windows if it is Vista or 7 and type "bcdedit"
without the qoutes you will see it. I am sorry I see you have XP. That I do not know
but look in your Windows boot manager and see if there is on entrie that has a WUBI
in it. When you delete UBUNTU Wubi from your system using Add and Remove programs
in Windows it sometimes leaves itself attached to Windows dos4grub menu. WUBI is to
be deleted from system with the uninstall in its Window folder. It is worth checking but
it is a good possibility. If it is it has to be deleted from boot manager, google it. I have
not worked with XP and Wubi just the new bcd in Vista and 7.

You know if you used Wubi if you did not partition your drive for Linux. Wubi will be right
next to Users in C: drive in Windows.

---

### Post by g4b000 on 2010-01-04
> **darkod said:**
> First of all, did you install wubi and not full ubuntu? This error is common for wubi, not so much for ubuntu. If you installed wubi inside windows, the procedure is different.

Can you please show me the procedure for the installation inside windows? I get the grub 1.97~beta4 shell prompt after a kernel image update.

sh:grub> ls
(loop0) (hd0) (hd0,2) (hd0,1)

sh:grub> set
?=16
color_highlight=
color_normal=
loop=loop0
pager=
prefix=(hd0,2)/boot/grub
root=loop0
show_panic_message=false

sh:grub> insmod normal
sh:grub> normal
error: unknown command 'normal'


How can I boot inside my ubuntu remix? Is it possible to store a wubi installation into a phisical partition or I need to reinstall?

Thanks a lot
g4b0

---

