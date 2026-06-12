---
title: "Unable to boot into Ubuntu 14.04, Grub2 menu only, boot-repair pastebin"
date: 2022-04-26
forum: Installation &amp; Upgrades
---

### Post by urbi44 on 2022-04-26
I would like your help to solve my problem of my pc that boots on the Grub2 screen.

I used boot-repair 64-bit flashed on a USB drive to debug this problem, but I'm not able to understand its output report. I read in the documentation of boot-repair that I can ask for help in this forum ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)). 

This is the pastebin: [http://paste.ubuntu.com/p/46RsHbzQ6T](http://paste.ubuntu.com/p/46RsHbzQ6T).

My pc has the following characteristics (running hostnamectl on a Terminal):Icon name: computer-desktop
Chassis: desktop
Boot ID: accd8c31624a4af1a066a5d697a42ac9
Operating System: Ubuntu 14.04.5 LTS
Kernel: Linux 4.4.0-142-generic
Architecture: x86_64

I don't know if it is important, but:
1) boot-repair does not show the "Recommended Repair" button (first button), but only the "Create a BootInfo summary" one (second button).
2) when launching boot-repair from a Terminal inside the OS of boot-repair flashed on the USB drive, I get the following warning related to DBus (that I saw also in my Ubuntu when it was still working):
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290345&stc=1[/IMG]

I can provide additional information if needed.


Could you help me to solve this problem, please?

Thank you very much,
Regards,
Luca Urbinati

---

### Post by oldfred on 2022-04-26
Please do not post screen shots or photos in line. Just attach.
Easy to attach screen shots with Forum's advanced editor and paperclip icon.

14.04  EOL - End of Life April 2019 

I am surprised Boot-Repair runs, it only is for current versions.
You need to backup your data, list of installed apps and anything else unique and install 20.04 or 22.04.

---

### Post by ubfan1 on 2022-04-26
Your 14.04 is really out of date 4.4.0-223 is the kernel my ESM 14.04 is using.  Extended Security Maintenance (ESM) for 14.04 ends in a few days, so you might be able to update that way if you join, but really, a more current release should be used.  There was some header change for the kernel at about 141 or 142, maybe that's affecting you?  I think it involved the HDMI sound, but HDMI sound was dead from the start of 4.4 until another header fix was made on the i915_component.h file.  The Intel Compute Stick I run 14.04 on  only had 1GB memory, so lubuntu would be the best ...buntu choice.  Debian 11 works fine, and for really lowest mem usage, use Antix.

---

### Post by ActionParsnip on 2022-04-26
I suggest you wipe the system off then do a clean install of Jammy(Ubuntu 22.04). This is LTS and supported for 5 years. You can restore your user data using your backups.

---

### Post by urbi44 on 2022-04-26
Thank you all for the answers.

Since I have some old programs that require Ubuntu 14.04 necessarily, updating to another OS at the moment is not possible.
Given that, is there a way to solve the current issue keeping Ubuntu 14.04? Is it possible to solve my problem?

Could you also tell me how to backup my disk in this situation where I can't boot into the current OS?

Thank you all

---

### Post by ubfan1 on 2022-04-26
Check out [https://ubuntu.com/blog/ua-services-deployed-from-the-command-line-with-ua-client](https://ubuntu.com/blog/ua-services-deployed-from-the-command-line-with-ua-client)
ESM ends this April, so don't wait long.  Free for a limited number of machines.

---

