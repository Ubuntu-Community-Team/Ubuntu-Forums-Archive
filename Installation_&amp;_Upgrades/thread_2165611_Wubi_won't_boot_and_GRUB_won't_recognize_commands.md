---
title: "Wubi won't boot and GRUB won't recognize commands"
date: 2013-08-05
forum: Installation &amp; Upgrades
---

### Post by XKRh8WA on 2013-08-05
I don't know much about Ubuntu, but I installed the Windows Wubi several months ago for work.  It's been working well all summer and I ported much work to it, but three days ago I hit the GRUB shell.  I haven't been able to boot since.

I've been chasing the issue all over.  At this point, all I know for sure is that I still have my root.disk.  In particular, I've been trying to follow these instructions:
[http://calamari.wordpress.com/2009/12/01/fixing-a-broken-wubi-grub-after-ubuntu-updates/](http://calamari.wordpress.com/2009/12/01/fixing-a-broken-wubi-grub-after-ubuntu-updates/)

This site says to do the following:

```
[COLOR=#666666][FONT=Arial]sh:grub> linux /boot/vmlinuz-(Your version of the kernel) root=/dev/(Your Windows partition) loop=/ubuntu/disks/root.disk ro
[/FONT][/COLOR][COLOR=#666666][FONT=Arial]
sh:grub> initrd /boot/initrd.img-(Your version of the kernel)[/FONT][/COLOR]

[COLOR=#666666][FONT=Arial]sh:grub> boot
[/FONT][/COLOR]
```
But, since I can't seem to find my kernel version or partition name, I've been trying to use these tips:
[http://answers.oreilly.com/topic/44-how-to-discover-boot-parameters-from-the-grub-command-shell/](http://answers.oreilly.com/topic/44-how-to-discover-boot-parameters-from-the-grub-command-shell/)

However, I'm facing these roadblocks:
- The GRUB shell keeps returning "unknown command root", "unknown command kernel", etc. whenever I try to use these commands.  (i.e. root (hd0,0))
- The only partitions listed are 'hd0', 'hd0,msdos1', 'hd0,msdos2', 'hd0,msdos3'.
- TAB auto-completion won't fill in vmlinuz-...
- Using commands such as 'root=(hd0,0)' will execute without any response.  I have no way of knowing if anything was actually set.  I get no feedback, and they don't seem to have helped yet.

If I'm using outdated GRUB commands, what would be the new commands for fixing this issue?  

All help is greatly appreciated.  I have too much work on Wubi at this point to afford to lose it.

Thank you.

---

### Post by TheFu on 2013-08-05
Which Ubuntu? What version?
Does your system have UEFI?
Does your system use GPT disks?

I don't know anything about WUBI - never used it myself - normally, I'd suggest **Boot Repair** and that you run the **Ubuntu Boot Info** script. Google will find both.

---

### Post by Jonathan Precise on 2013-08-05
[SIZE=4]Welcome to Ubuntu forums, [/SIZE][COLOR=#000000][SIZE=4]XKRh8WA![/SIZE][/COLOR][HR][/HR][COLOR=#000000]Before I can solve your issue, I need a little bit more of information:[/COLOR][COLOR=#000000]

(If you remember,) Which ubuntu version did you install?
To which disk and partition did you install wubi to?
(I doubt this is possible, but) does your system have GPT disks?

If you can't answer the last question, don't worry! ;)

Please reply when you have the required information.[/COLOR]

---

### Post by XKRh8WA on 2013-08-05
To Jonathan and TheFu,

I'm using Ubuntu 12.04 Precise Pangolin LTS.  I do not have UEFI.  I have Master Boot Record and not GPT disks.  Also, I have no way to use the Ubuntu Boot Info script since I cannot get into Ubuntu at all.  I only have access to the GRUB prompt.

Let me know if there's any more information I should provide.

---

### Post by TheFu on 2013-08-05
Can you boot a LiveCD or from a USB flash drive? If so, then you can install bootinfo or just download the script and run it to generate the data.  However, since you are using WUBI, I don&#8217;t know if that data is important at all. Perhaps not at all .

---

### Post by papibe on 2013-08-05
Thread moved to **Installation & Upgrades** as requested by OP.

---

### Post by bcbc on 2013-08-05
See [Ubuntu 12.04 (Wubi) not starting - root.disk corrupted]("http://askubuntu.com/q/228709/14916")

---

### Post by Jonathan Precise on 2013-08-07
> **XKRh8WA said:**
> To Jonathan and TheFu,

I'm using Ubuntu 12.04 Precise Pangolin LTS.  I do not have UEFI.  I have Master Boot Record and not GPT disks.

Well XKRh8WA, looks like I have all the information I need, except one...

Do you remember to which drive you installed Wubi (or in other words, where is the root.disk file)?


> **XKRh8WA said:**
> Also, I have no way to use the Ubuntu Boot Info script since I cannot get into Ubuntu at all.  I only have access to the GRUB prompt.

Let me know if there's any more information I should provide.

Unfortunately, the ubuntu boot info script will not detect wubi installs. It can only detect normal (non-wubi) installs.:(

[HR][/HR]If you ever get your problem fixed, either copy the files you can't possibly lose to your windows partition.

I also recommend doing a full install as wubi can break more easily.:(

If you ever make a full install and have problems with grub, go to  [http://sourceforge.net/projects/linux-secure/files/linux-secure-13.04-32bit.iso/download](http://sourceforge.net/projects/linux-secure/files/linux-secure-13.04-32bit.iso/download). Let the file download, and then [burn it to a DVD]("http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows"). Run a _**full system backup**_. Restart your computer **_with the disk inside_** You should see ubuntu load. Then click try ubuntu. In  the dash search for boot-repair. Start boot repair, and run a recommended repair. Restart your computer, and take the disk out when prompted. Done!

---

### Post by XKRh8WA on 2013-08-09
I followed these instructions and performed the disk check.  Afterwards, the "date modified" property of root.disk seems to have been updated, so I think the disk check did something.  However, I'm still being dropped into the GRUB.

---

### Post by bcbc on 2013-08-09
These are the commands to boot a Wubi install from a grub prompt. It will likely give you some error message (probably when loop mounting the disk) because otherwise you wouldn't be stuck at the grub prompt in the first place. 

```
search -s -f -n /ubuntu/disks/root.disk
probe --set=diskuuid -u $root
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /vmlinuz root=UUID=$diskuuid loop=/ubuntu/disks/root.disk ro quiet splash
initrd /initrd.img
boot
```

If that didn't work, and the root.disk exists and is its normal size (between 5 and 30 GB), and you've run chkdsk as you say, then you could try fsck'ing the disk. For this you'll need to boot an Ubuntu Live CD and mount the partition containing the root.disk. Basic instructions here: [http://askubuntu.com/a/118419/14916](http://askubuntu.com/a/118419/14916) (that post also contains a link to a tool that gives readonly access to the root.disk from Windows)

---

