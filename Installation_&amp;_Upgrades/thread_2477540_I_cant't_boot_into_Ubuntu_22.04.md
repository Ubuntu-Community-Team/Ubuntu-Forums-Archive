---
title: "I cant't boot into Ubuntu 22.04"
date: 2022-07-29
forum: Installation &amp; Upgrades
---

### Post by punkuj on 2022-07-29
Hello, I am unable to boot into my Ubuntu 22.04, previously some of my hard disk space was dirty(Windows also stated this) so i ran "fsck /dev/sda2" and after this whenever i am trying to boot into my laptop it prompts me 5 messages which are "Failed to start user login management" so i ran  boot repair and it gives this "Please enable a repository containing the [grub-efi] packages in the software sources of unknown Linux distribution (sda2). Then try again." message.
Here is the pastebin link [https://paste.ubuntu.com/p/dqDkGWzcXc/](https://paste.ubuntu.com/p/dqDkGWzcXc/)
Thank you very much.

---

### Post by tea for one on 2022-07-29
[COLOR="#0000FF"]Line 49[/COLOR] - OS#1:   unknown Linux distribution on sda2

That comment is unusual, can you confirm which distro is installed?

---

### Post by yancek on 2022-07-29
Line 84 of boot repair indicates there is no /etc/fstab file which is  major problem for booting.  You have/had a UEFI install as both windows and ubuntu are shown on partition sda1.  Are you booting with UEFI enabled in the BIIS firmware?  Can you post the contents of the /etc/apt/sources.list file?

---

### Post by punkuj on 2022-07-29
I am really sorry, I just re-installed ubuntu and it seems to be working fine by now. Thank you very much

---

### Post by punkuj on 2022-07-29
It's Ubuntu 22.04.
I just re-installed it from the same usb drive.

---

### Post by Impavidus on 2022-07-29
> **punkuj said:**
> I am really sorry, I just re-installed ubuntu and it seems to be working fine by now. Thank you very much

Probably best. By the looks of it, there was filesystem damage all over the place. A new install is the best way to deal with that. If it happens again, consider the possibility that it's a hardware problem.

---

### Post by punkuj on 2022-07-30
Thank you very much for helping me out.

---

