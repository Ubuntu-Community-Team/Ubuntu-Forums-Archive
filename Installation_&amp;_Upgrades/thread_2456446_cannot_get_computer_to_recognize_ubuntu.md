---
title: "cannot get computer to recognize ubuntu"
date: 2021-01-11
forum: Installation &amp; Upgrades
---

### Post by knaber on 2021-01-11
Hi,
I'm trying to install ubuntu.  At first I installed it alongside windows but after it successfully installed and I restarted I couldn't get back into Ubuntu.  Then I decided to install it overtop of Windows and after it seemed to install correctly when it restarts it gives me a no operating system found.  I ran repair boot and here is my link:  [http://paste.ubuntu.com/p/2KrH3J6yqV/](http://paste.ubuntu.com/p/2KrH3J6yqV/)  .  After I ran repair and restarted it still didn't find the OS.
I really don't know where to go from here.  Ideally I'd like to install any version of Ubuntu and then create a windows VM from inside Ubuntu.  
My computer is quite old and the BIOS doesn't have many options but it is set to boot UEFI although it has the option for auto or BIOS i believe.  Other than that there doesn't seem to be many options.  I can't add a boot location as far as i can see.  Sorry if none of that makes sense, I'm just learning.
Thanks, Kerry

---

### Post by CelticWarrior on 2021-01-11
Welcome.

Line 80: [COLOR=#000000]Please [/COLOR][COLOR=#AA22FF]**do**[/COLOR][COLOR=#000000] not forget to make your UEFI firmware boot on the Ubuntu [/COLOR][COLOR=#666666]20[/COLOR][COLOR=#000000].04.1 LTS entry [/COLOR][COLOR=#666666]([/COLOR][COLOR=#000000]sda1/EFI/ubuntu/shimx64.efi file[/COLOR][COLOR=#666666])[/COLOR][COLOR=#000000] !

UEFI settings > Boot menu. In the OS selection make sure it shows "Ubuntu". That should be it.[/COLOR]

---

### Post by knaber on 2021-01-11
yes, can you tell me how i can change my UEFI settings? Is this in Ubuntu?

---

### Post by CelticWarrior on 2021-01-11
UEFI settings is what you probably think as "BIOS settings" but actually isn't because if you found "UEFI" references in your firmware then it's UEFI, not BIOS. UEFI replaced the old BIOS a long time ago. All consumer grade computers have UEFI instead of BIOS at least since 2012!

---

### Post by knaber on 2021-01-11
Ok sounds good but I do not see a way to add anything to my UEFI.  I don't see a way to add a picture of my bios either so i included a link of what mine looks like that i found online:

[https://forums.lenovo.com/t5/Enterprise-Client-Management/M710Q-BIOS-Legacy-PXE/m-p/3748091](https://forums.lenovo.com/t5/Enterprise-Client-Management/M710Q-BIOS-Legacy-PXE/m-p/3748091)

 My primary boot gives one option HDD1: P0: WDC WB.... 

Any advice would be greatly appreciated

---

