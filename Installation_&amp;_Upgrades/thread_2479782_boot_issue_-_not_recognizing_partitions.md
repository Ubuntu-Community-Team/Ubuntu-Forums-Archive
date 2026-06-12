---
title: "boot issue - not recognizing partitions"
date: 2022-10-06
forum: Installation &amp; Upgrades
---

### Post by pedroharu on 2022-10-06
Sorry if this is not following any forum etiquette, it's my first time here.

My computer has a partitioned SSD, one partition with Ubuntu and the other with Windows installed.
I was logged in to windows, doing every day stuff, and suddenly the computer restarted. Since then I can't boot it anymore.
The names of both OSs are not even showing in the boot list anymore (they were before). I assume that the SSD is not being recognized.
I've tried installing both Ubuntu and Windows but the installer does not recognize any partition for that. I couldn't find anything useful to change in the BIOS. I also opened my laptop and checked that the SSD is correctly plugged and looks fine.

As explained in help.ubuntu, I ran boot-repair on my computer and this is the diagnosis: [URL="https://pastebin.ubuntu.com/p/RM5yk5ZjgY/"]https://pastebin.ubuntu.com/p/RM5yk5ZjgY/
[/URL]
Thanks for your time. I literally ran out of ideas.

---

### Post by yancek on 2022-10-07
Your boot repair link is broken.  Check it to make sure it is the correct link.

Which version of Ubuntu and which version of windows did you have?
Were these both UEFI installs?  Do you have an option in the BIOS to select boot from EFI file?  If so, what happens?

---

### Post by pedroharu on 2022-10-07
I have Ubuntu 20 and Windows 10 installed on my SSD, however I can't tell if they were UEFI installs.
I checked my BIOS for that option and couldn't find it.

---

### Post by tea for one on 2022-10-07
Line 17 - 0 (zero) OS detected
Line 50 - Internal partitions not visible
Line 66 - This is the live USB (Kingston)

Looks suspiciously like hardware failure.

---

### Post by pedroharu on 2022-10-07
I'm also suspecting of hardware failure, which would be quite odd for my thinkpad. I have it for one year only and it never leaves my desk.
Since I can't rule out the possibility that the link between boot and SSD is broken, I tried boot repair.

So I guess there's no hope here, right?

---

### Post by tea for one on 2022-10-07
Little hope at the moment because the SSD is not appearing in the boot-repair report.
As you were using Windows when it all went pear-shaped, there is always the unusual possibility that Windows has altered a UEFI setting, preventing the internal drive from booting.
Perhaps try a Windows recovery disk?

Have a look at all the UEFI settings to see if anything looks different.
Shot in the dark, really, but strange things often happen..............

---

### Post by pedroharu on 2022-10-07
Thanks for the reply.
I already tried using Windows recovery, with no success.
All the UEFI settings look normal to me. I tried toggling on and off many options and restarting, again no success.

---

