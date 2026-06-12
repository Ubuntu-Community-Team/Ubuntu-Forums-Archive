---
title: "GRUB menu not showing after installing Ubuntu 22.04 LTS [Dual Boot]"
date: 2022-05-07
forum: Installation &amp; Upgrades
---

### Post by atinesh2 on 2022-05-07
I have installed **Windows 11** in SSD1 and then installed **Ubuntu 22.04 LTS **in SSD2 but on restart I couldn't see **GRUB menu** which allows me to switch between Windows and Ubuntu. I tried repairing boot configuration using Boot Repair tool.

 ```
$ boot-repair
```

[IMG]https://i.postimg.cc/MTcNmLnr/Screenshot-from-2022-05-07-15-16-20.png[/IMG]

But when I click "Recommended repair" option I am getting the below error.

[IMG]https://i.postimg.cc/FKCwcvHL/Screenshot-from-2022-05-07-15-16-54.png[/IMG]

I have used this tool earlier when I had Ubuntu 18.04 LTS and Windows  10 in my PC and it worked fine, Does anyone have any idea about this  error ?

---

### Post by oldfred on 2022-05-07
You should reinstall Windows in UEFI boot mode to gpt partitioned drive.
Note that change from MBR to gpt will totally erase drive, so have good backups.

Microsoft has required vendors to install in UEFI boot mode to gpt partitioned drives since 2012 and release of Windows 8.
Even Windows 7 before 2012 could be installed in UEFI boot mode, but only with UEFI Secure boot off.

How you boot install media UEFI or BIOS is then how it installs or repairs for both Windows & Ubuntu.

---

### Post by yancek on 2022-05-07
Rather than trying the boot repair option, you would have been better served using the Create BootIInfo Summary option and posting the link you get when it finishes here.  That would give members more details to work with.  Since the message says you have a Legacy/MBR install of windows, you must have a Legacy install of Ubuntu's Grub because a Grub install UEfI will not boot a Legacy windows nor will a Legacy install of Grub boot a windows UEFI install.

---

