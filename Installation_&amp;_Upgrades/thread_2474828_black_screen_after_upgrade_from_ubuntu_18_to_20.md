---
title: "black screen after upgrade from ubuntu 18 to 20"
date: 2022-05-09
forum: Installation &amp; Upgrades
---

### Post by evgenysk on 2022-05-09
I tried to upgrade from Ubuntu 18 to 20. Something went wrong. System does not load now. Now there is black screen on startup. Please suggest what to do.
I ran Boot Repair clicked Recommended repair. It did not help. I [COLOR=#333333][FONT=Ubuntu]created a Boot-info[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu] diagnosis:[/FONT][/COLOR]
[https://pastebin.ubuntu.com/p/2pVjvs5tbt/]("https://pastebin.ubuntu.com/p/bmccjjfwZw/")
What commands should I run to repair the system?

---

### Post by ubfan1 on 2022-05-09
From the listing, two things: 1) The EFI partition, sda1, should have the "boot" flag on it, and 2) the ESP's  EFI/Boot/ directory should have a copy of grubx64.efi in it, assuming the rootx64.efi is the copy of shimx64.efi.   Do you see the grub menu at boot, or just a black screen? Ever try the EFI menu (some key at power-up to allow you to select the boot device/OS)?

---

### Post by evgenysk on 2022-05-09
> **ubfan1 said:**
> From the listing, two things: 1) The EFI partition, sda1, should have the "boot" flag on it, and 2) the ESP's  EFI/Boot/ directory should have a copy of grubx64.efi in it, assuming the rootx64.efi is the copy of shimx64.efi.   Do you see the grub menu at boot, or just a black screen? Ever try the EFI menu (some key at power-up to allow you to select the boot device/OS)?

Yes I see grub menu. I choose Ubuntu. Then black screen.
I entered Recovery mode and made package repair. It did not help.
I updated Repair info file above. Could you check it again?

---

### Post by ubfan1 on 2022-05-09
Since the grub menu showed up, the UEFI boot of shimx64.efi/grubx64.efi succeeded -- black screen might be a video problem.  What video hardware do you have?  Can you run a virtual terminal (ctrl+Alt+F3 should pop up vt3, for a login)?  Is the X server (or wayland) running (ps auxww |egrep "X|wayl"  )?  Does the /var/log/Xorg.0.log show any errros (or Xorg.1.log)?

---

### Post by evgenysk on 2022-05-10
> **ubfan1 said:**
> Since the grub menu showed up, the UEFI boot of shimx64.efi/grubx64.efi succeeded -- black screen might be a video problem.  What video hardware do you have?  Can you run a virtual terminal (ctrl+Alt+F3 should pop up vt3, for a login)?  Is the X server (or wayland) running (ps auxww |egrep "X|wayl"  )?  Does the /var/log/Xorg.0.log show any errros (or Xorg.1.log)?

1.Correction to the problem description. System loading ends up with black screen with a cursor at the top of the screen. I will write what ps command returns later.

2.Contents of /var/log/Xorg.0.log are here: [https://pastebin.ubuntu.com/p/xFjm8ZyB8H/](https://pastebin.ubuntu.com/p/xFjm8ZyB8H/) 

3. Video hardware: product: Skylake GT2 [HD Graphics 520], vendor: Intel Corporation. I ran &#8220;sudo lshw -C display&#8221; to get it.

---

### Post by evgenysk on 2022-05-10
Command
ps auxww | egrep "X|wayl"
does not find these processes.

---

### Post by evgenysk on 2022-05-10
ubfan1, thank you for help! You told me that I can open virtual terminal after black screen. It told me that installation was not finished. Then I was able to finish installation.

---

