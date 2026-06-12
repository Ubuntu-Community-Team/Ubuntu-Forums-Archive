---
title: "How do I remove Ubuntu and boot menu"
date: 2016-09-19
forum: Installation &amp; Upgrades
---

### Post by ray42 on 2016-09-19
How do I remove Ubuntu and boot menu so that I can boot normally to Windows?

It is on a laptop on its own partition

---

### Post by ajgreeny on 2016-09-19
You will need to restore the Windows bootloader files first or you may not be able to boot back into windows once Ubuntu has been deleted.

Do you have a BIOS or UEFI machine?

Do you have the DVD for your version of Windows? That will be the easiest way to restore the bootloader.

---

### Post by ray42 on 2016-09-20
Hello ajgreeny

[COLOR=#000000]BIOS, and I might have the DVD. What happens if I do not have the DVD?[/COLOR]

---

### Post by ajgreeny on 2016-09-20
> **ray42 said:**
> Hello ajgreeny

[COLOR=#000000]BIOS, and I might have the DVD. What happens if I do not have the DVD?[/COLOR]
You may be able to get a generic windows BIOS bootloader to work using Boot-repair (in my signature) Advanced option, but it is something I have never needed to do as I do not run Windows of any version any more except XP in a virtual install.

I am not sure if that repair system works on all Windows versions and you may need someone with more knowledge than I have to confirm one way or another but a quick search suggests it can work on all supported Windows versions from Vista to Win-10.

---

### Post by deadflowr on 2016-09-20
> **ray42 said:**
> [COLOR=#000000]BIOS, and I might have the DVD. What happens if I do not have the DVD?[/COLOR]

I think you can create a repair disk to fix windows booting issues:
[https://support.microsoft.com/en-us/help/17423/windows-7-create-system-repair-disc]("https://support.microsoft.com/en-us/help/17423/windows-7-create-system-repair-disc")
Create the repair disk before you nuke Ubuntu.

---

### Post by ray42 on 2016-09-21
Do you think this will work?

[https://www.youtube.com/watch?v=k2OaNH8pBZ0](https://www.youtube.com/watch?v=k2OaNH8pBZ0)

UPDATE: It might be an old link, the software is still current, and IT WORKS! Yah!

---

### Post by ajgreeny on 2016-09-21
> **ray42 said:**
> Do you think this will work?

[https://www.youtube.com/watch?v=k2OaNH8pBZ0](https://www.youtube.com/watch?v=k2OaNH8pBZ0)
Absolutely no idea, but in his case he could have managed simply by installing the new version of Linux Mint over the old one by choosing Something Else in the installation precess.  Actually, I'm not even sure if it was called Something Else back in 2011 when that video was made, so I suspect the info it shows could be out of date; as I don't use Windows I am not sure.

As I understand it you are not replacing Ubuntu with another version but just want the space back for Windows.  I suggest you look in more detail at Boot-repair -Advanced which should be able to solve your Windows bootloader problem.

---

### Post by ray42 on 2016-09-22
Thanks, I haven't actually removed the OS yet. I was making sure I knew how to before hand.

---

### Post by mastablasta on 2016-09-22
windows repair disk is officially supported (by Microsoft) method.
boot-repair is the linux way of doing it easilly.

---

### Post by ray42 on 2016-09-22
[COLOR=#000000]UPDATE: It might be an old link, the software is still current, and IT WORKS! Yah!

thanks everyone for your input[/COLOR]

---

### Post by ajgreeny on 2016-09-23
Great! Please mark as SOLVED from the Thread Tools menu up-top. It is a great help to users searching the forum.

---

