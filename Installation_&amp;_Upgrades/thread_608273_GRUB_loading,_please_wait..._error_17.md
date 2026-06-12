---
title: "GRUB loading, please wait... error 17"
date: 2007-11-09
forum: Installation &amp; Upgrades
---

### Post by j12 on 2007-11-09
I have windows vista on my laptop and i wanted ubuntu 7.10 on it so i partitioned the 80gb hdd into a 10gb and a 70gb, and i set up a dual boot. So i install ubuntu onto the 10gb partition successfully. But after a while needed those 10gb's back so i went into windows vista and i formated the 10gb partition just as storate. Yes windows gave me the little warning, "this partition contains data that may be recognized by other operating systems". So i formatted and have a 70gb and a 10gb hard drive both in windows vista. Then i try to restart and i get the GRUB loading, please wait.....error 17 message. Before, i was able to choose between booting up vista or ubuntu. And when i formatted the 10gb partition i expected to just automatically boot into vista when i turn on the computer. But now i get the error message. I kinda need to get back into vista because i have a lot of homework etc. saved on there.

---

### Post by Laserbeast on 2007-11-09
Boot a Windows disk into recovery mode, and do "fixmbr". That will reset the bootloader and boot right into Vista.

---

### Post by j12 on 2007-11-09
how do i boot into recovery mode with with the vista dvd?

---

### Post by Laserbeast on 2007-11-09
> **j12 said:**
> how do i boot into recovery mode with with the vista dvd?

Here's something I found online. I haven't used Vista yet so this isn't my advice:

> Use Vista's Start-up Repair utility.

1. Boot from Vista DVD
2. Loads files - select English.
3. Select repair option
4. Will search for Vista installation
5. Follow through on prompts
6. May have to do repair function more than once.

Though, if you can get yourself to a command prompt from the disk, I think "fixmbr" should do the trick unless they changed the command.

---

### Post by j12 on 2007-11-09
When i used the vista command prompt. it says 'fixmbr' is no recognized as an internal or external command, operable program or batch file. I do have a windows xp cd, will that work if i put it in and do the fixmbr thing.

---

### Post by Laserbeast on 2007-11-09
> **j12 said:**
> When i used the vista command prompt. it says 'fixmbr' is no recognized as an internal or external command, operable program or batch file. I do have a windows xp cd, will that work if i put it in and do the fixmbr thing.

Yes, XP will work for sure.

Check this out:
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)

---

### Post by confused57 on 2007-11-09
> **j12 said:**
> When i used the vista command prompt. it says 'fixmbr' is no recognized as an internal or external command, operable program or batch file. I do have a windows xp cd, will that work if i put it in and do the fixmbr thing.
You can also use the bootrec.exe utility on your Vista install DVD:
[http://support.microsoft.com/kb/927392/en-us](http://support.microsoft.com/kb/927392/en-us)

---

### Post by 1337455 10534 on 2007-11-10
I got the infamous Err 17 *installing* Feisty on an XP dual. Heh.

---

