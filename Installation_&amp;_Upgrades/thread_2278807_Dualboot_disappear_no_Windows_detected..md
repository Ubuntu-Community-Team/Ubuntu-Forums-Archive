---
title: "Dualboot disappear no Windows detected."
date: 2015-05-19
forum: Installation &amp; Upgrades
---

### Post by nwind on 2015-05-19
Hi all,
i had installed ubuntu yesterday beside Windows 7, I downloaded ubuntu from official site and created bootable USB, when I restarted my computer and launched installation from USB no system had been detected on my computer by ubuntu installation. So i did not care About it because i know that Windows 7 is there so i followed instructions and I finish installation of ubuntu. Now when I turn on my computer there is no chance to choose between Ubuntu and Windows 7. My computer Log me directly into ubuntu and it is behaving like there is not any other operating system. Could you please help me how to fix my problem and get the table between chosing operating system after i turn my computer on? Or Could you please help me how to get into Windows after i turn my computer on? Thank you.

---

### Post by ajgreeny on 2015-05-19
> **nwind said:**
> Hi all,
i had installed ubuntu yesterday beside Windows 7, I downloaded ubuntu from official site and created bootable USB, when I restarted my computer and launched installation from USB no system had been detected on my computer by ubuntu installation. [COLOR=#ff0000]So i did not care About it because i know that Windows 7 is there so i followed instructions and I finish installation of ubuntu.[/COLOR] Now when I turn on my computer there is no chance to choose between Ubuntu and Windows 7. My computer Log me directly into ubuntu and it is behaving like there is not any other operating system. Could you please help me how to fix my problem and get the table between chosing operating system after i turn my computer on? Or Could you please help me how to get into Windows after i turn my computer on? Thank you.
The part I show in red above worries me and I think you really should have cared about it, as I fear you may have overwritten your Windows OS.

We need much more info about exactly what you did when installing in order to be able to help you, but for the moment stop using the installed Ubuntu, boot to your live system, open a terminal with Ctrl+Alt+T  and run command ```
sudo parted -l
```which will show us the partitions on your computer.

You could also run Boot-Repair from the live USB (see my signature), but at this stage do not accept the default repair, just run the script to get a report and show us the pastebin URL.

---

### Post by DeadlyOats on 2015-05-19
Actually, it might could be an MS Windows Update.  There is a Microsoft Windows Update, that for whatever reason breaks the boot loader, so that Windows don't show up, unless you make MS Windows' boot loader your loader of choice.  I'm one of them people that reads the details of every MS update, because MS is always trying to put something in there that borks your system somehow.

This is [one of the updates]("https://support.microsoft.com/en-us/kb/3033929") that I did not install, and it's the one that breaks your boot loader.  So, if you installed this update on your Windows 7, then it might be the problem you're having.

I'm not really technically proficient, but if one of you Linux gurus knows what's going on with this, maybe you could tell the Linux people to figure out a fix for Microsoft's shenanigans?

---

### Post by Malik_Rumi on 2015-05-19
Well, I'm no linux guru either, and I am on Windows 8.1, but I just had a windows update that gave me a big red screen about unauthorized boot signatures. All I had to do was go back into Windows bios and disable uefi again.

---

### Post by ajgreeny on 2015-05-19
> **Malik_Rumi said:**
> Well, I'm no linux guru either, and I am on Windows 8.1, but I just had a windows update that gave me a big red screen about unauthorized boot signatures. [COLOR=#ff0000]All I had to do was go back into Windows bios and disable uefi again.[/COLOR]
I presume the change you mention shown in red in your post was only temporary, or you will not be able to boot Windows any more.  Maybe you meant that you just turned off secure-boot, not UEFI?

Perhaps I have missed your point totally, but I do not run Windows any more; have no need for it, so I could easily be unaware of required actions in this situation

---

### Post by Malik_Rumi on 2015-05-19
I was just throwing my two cents in in case it helped. And you're right, it was secure boot, not uefi. I can get into Windows. In fact, that's all I'm getting into now, but that is the topic of a separate thread. This thing with the red screen was several days ago.

---

