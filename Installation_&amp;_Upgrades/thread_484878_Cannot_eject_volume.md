---
title: "Cannot eject volume"
date: 2007-06-26
forum: Installation &amp; Upgrades
---

### Post by parthamage on 2007-06-26
I just upgraded from 6.10 to 7.04.  I keep having a small window pop up that has a message which reads, "Cannot eject volume".  It does not have a program name in the title bar, and only has an "OK" button.   This has nothing to do with any CD or DVD program I am currently running; I don't have anything loaded into the drives, and I still get the error message.  Any ideas?
Charles

---

### Post by parthamage on 2007-06-27
Looked in my event log, and found this repeated ad nauseum
Jun 27 12:10:39 charles-desktop kernel: [11397.936000] ide: failed opcode was: unknown
Jun 27 12:10:39 charles-desktop kernel: [11398.136000] hdc: status error: status=0x58 { DriveReady SeekComplete DataRequest }

Please Help!

---

### Post by luvr on 2007-06-28
[Feisty usb stick Cannot eject volume.]("https://bugs.launchpad.net/ubuntu/+bug/99538/comments/10") Does that help, maybe?

---

### Post by Pumalite on 2007-06-28
It's a known bug of 7.04. But if you click in 'OK', it ejects it anyway.

---

### Post by parthamage on 2007-06-28
I tried moving the file in the suggested fix, but it says I don't have permission.  It says that "root" is the owner, and I can't access the permissions in the properties.

As to just hitting OK, I know that works, but the window continually popping up, particularly when I am playing Neverwinter Nights, is extremely annoying.

---

### Post by altgrrr on 2007-07-05
> **Pumalite said:**
> It's a known bug of 7.04. But if you click in 'OK', it ejects it anyway.

You might be right in that it ejects anyway but the ecternal drive "restarts" and is mounted again right after, annoying the crap out of me ;D  anyone found a solution?

---

### Post by luvr on 2007-07-09
> **parthamage said:**
> I tried moving the file in the suggested fix, but it says I don't have permission.  It says that "root" is the owner
Yes, you will have to *"become root"* in order to move the file. If you are using the command-line interface, just precede whatever command that you want to execute, with **"sudo"**--e.g.,
```
sudo mv *fromfile* *tofile*
```

If you want to do it via the graphical user interface, then you can hit **<Alt>+<F2>** to call up the *"Run Application"* window, and type the following command into its input field:
```
gksudo nautilus
```
That will open a file browser window under the control of root. Now navigate to the appropriate folder and move the file.
**WARNING:** Since this browser window runs under the control of root, you shouldn't leave it open any longer than strictly necessary. As root, you have the power to do anything and everything to your system, including destroying it. If you're not careful, you may even make your **own** data files inaccessible to yourself!

---

### Post by parthamage on 2007-11-05
I'm back.  Problem has resurfaced under Gutsy with a vengeance.  And the fix posted to this thread won't work, as the file I was supposed to move does not exist.  It is getting extremely annoying.  None of my drives are USB; none of my drives are external.  I just have an internal CD-RW, and and an internal DVD-ROM.  I would rather not have to crack open my case and unplug them; I need my optical drives from time to time!.

HELP!

---

