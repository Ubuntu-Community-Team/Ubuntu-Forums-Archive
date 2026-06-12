---
title: "dual booting to ubuntu"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by sprightlyone on 2008-05-29
hi:confused:
  i`ve reposted under new title
 normal boot mode freezes on splash screen
if i let the boot selection boot to recovery mode i get a menu
"boot to normal mode"
boot to root shell prompt which is root@ubuntubrutus :/# cursor
ifix fix x server
boot to normal mode srarts loading ACPImodule =OK
                         starting ACPI module =OK
cursor then stalls on next line
the prompt option seems to be the path to take ???but to what next to fix problem
frozen load @splash screenis where it all stops
thanks lyle

---

### Post by Vadi on 2008-05-29
Try pressing Ctrl+D in recovery... does it go on?

---

### Post by sprightlyone on 2008-05-29
Hi
  Ctrl+D doesn`t seem to do anything 
 but did get the following once when exiting the recovery-mode menu under starting ACPI module =OK
next line [8948439.1366941]EEEK! page mapcount {page}went negative![-1]
 E89c.GZ 097217] page PFN=0
 any ideas on this error ?????:confused:
can i get a prompt+the command  to manually start UBUNTU from OS selection screen ???
 or use prompt in recovery mode screen to go somewhere?????
 i seem to have all the pieces but can`t lay them out inthe order necessary to boot the system  
thanks

---

### Post by Vadi on 2008-05-29
Try booting with the kernel option "acpi=off". I don't know where to type that in though.

---

### Post by zvacet on 2008-05-29
> Try booting with the kernel option "acpi=off". I don't know where to type that in though.

Instructions are [here.]("https://help.ubuntu.com/community/BootOptions#head-fd6993472b20e64d715ae8f44a496dc2cf9f7cbd")

---

### Post by sprightlyone on 2008-05-30
hi 
  tried all  the suggestions /options still can`t seem to solve the problems 
 can`t seem to find this "boot/grub/menu.lst "everyone refers to can`t get to it from any prompts that i can access 
  this is not going anywhere @the moment 
  any more ideas???????? :confused:
thanks lyle

---

