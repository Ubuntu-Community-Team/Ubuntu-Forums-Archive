---
title: "Boot problem"
date: 2015-10-21
forum: Installation &amp; Upgrades
---

### Post by Geoffray on 2015-10-21
[FONT=arial]Hello,[/FONT][FONT=arial]
[/FONT]
[FONT=arial]I am unable to boot a Toshiba Satellite laptop on which I just installed Ubuntu 14.04.3 LTS.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Here is the URL of my online report:[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial][http://paste.ubuntu.com/12888422/](http://paste.ubuntu.com/12888422/)[/FONT]

---

### Post by james_moore2 on 2015-10-21
I would try to reinstall Ubuntu, I guess leave the MBR where it is as thats what ive read.

---

### Post by Geoffray on 2015-10-21
Hi,

Thank you for the reply. I reinstalled Ubuntu and had no success. I am not sure the MBR line is informative: [http://askubuntu.com/questions/635420/no-boot-loader-is-installed-in-the-mbr-of-dev-sda-is-that-some-pain-to-a-only](http://askubuntu.com/questions/635420/no-boot-loader-is-installed-in-the-mbr-of-dev-sda-is-that-some-pain-to-a-only)

---

### Post by james_moore2 on 2015-10-21
Could you please inform me which Satellite it is as mine is a Toshiba Satellite L755-S5112 and I didn't have any problems.

---

### Post by Geoffray on 2015-10-21
I have a Toshiba Satellite C50DT-N-101.

---

### Post by james_moore2 on 2015-10-21
Well that seems hard to find on the internet.
Are you trying to dual boot?

---

### Post by grahammechanical on 2015-10-21
If we had a machine with a motherboard that had a BIOS boot system then not having the Grub boot loader installed in the MBR of /dev/sda would be the reason why Ubuntu was not loading. But with a motherboard that has a UEFI boot system the message "No boot loader is installed in /dev/sda" is irrelevant as UEFI boot system do things differently. Boot Repair prints that message because it is written to check if there is a boot loader in the MBR for those of us who have BIOS boot systems.

What is important is that there is an efi boot partition containing efi boot files. At the bottom of the Boot Repair report there is this statement.

"Please do not forget to make your BIOS boot on sda1/EFI/Ubuntu/shimx64.efi file." I cannot tell you how to do that as I do not have a UEFI boot system. But It could be what you need to do.

Regards.

---

### Post by Geoffray on 2015-10-21
No, I removed everything and installed Ubuntu.

---

### Post by Geoffray on 2015-10-21
Thank you for the repy grahammechanical. I'll try to find a way to do that...

---

### Post by james_moore2 on 2015-10-21
Did you delete the partition(s)? I would do that except for one then make a 2x your ram linux-swap then put the rest back into the main and format the main into an ex4 primary I believe.

---

### Post by Geoffray on 2015-10-21
I found the solution: I just had to disable the secure boot in the bios before making the installation. Then I made a new installation with the standard configuration and it works.

Thanks for the help!

---

### Post by james_moore2 on 2015-10-21
No problem, should have asked if you did that first.

---

