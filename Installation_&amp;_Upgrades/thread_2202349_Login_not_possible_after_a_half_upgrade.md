---
title: "Login not possible after a half upgrade"
date: 2014-01-28
forum: Installation &amp; Upgrades
---

### Post by bjngchn on 2014-01-28
There is a computer with an old encrypted alt-cd version of kubuntu. Tried to upgrade or update things. There were errors, then I followed commands I found on Google search. Things at some point   froze, so computer had to be restarted. Have a bios pw, and then encryption pw. Encryption pw is asked from command line instead of  box created for it.... Encryption pw is typed. Then I get usual login screen for user accounts. When I login I get this error (so nothing can be done except shutting it down): ============================================================================================================================================================= Warning: Cannot open ConsoleKit session: Unable to open session: The permission of the setuid helper is not correct.  ============================================================================================================================================================= What now. Questions: Is there a way to login normally? Is there a way to login as root and type commands somewhere to fix things? Is there a way to save files under , say, desktop directory of a user? =========== I suspect I will have to format everything, but there must be a way to save files; or ithis not possible because of encryption?  Maybe I will have to boot from a CD but I don't have the  identical copy of the old system installed on the computer. Have newer CD only.=================== Another thing: I can't seem to be able to change BIOS contents permanently. Boot priority order is like this: 1 . internal optical drive 2.Floppy drive 3. Internal HD drive 4. Network 5. USBFlash === Which one do I use? It seems to be stuck at the first option(optical). Isn't it supposed to be 3. I can go to 3, but when click right and left arrows I see it is again at 1.  ..Also if I decide boot from live CD, do I need to change Bios first? Exactly in what order I insert CD, enter bios, ..etc? Will I be ble to recover files ? =============== Thanks a lotin advance. Hopefully I gave enough info already.

---

### Post by bjngchn on 2014-01-28
Before this problem, sometimes I was getting dark screen just after first pw...but this was not a serious problem. Also it starts with "no video mode activated" and this was not serious either.

---

### Post by bjngchn on 2014-01-28
Accidentally managed to login as root. it still gives errors, but I can at least run ls command. If there is a few GB's of files can I rescue them?  I can't see which files are important just by looking at filenames.=====================At another forum people say this command works, but it didn't work for me. ============================= sudo dpkg --configure -a ============== When I type this I get this: unable to access dpkg status area: Read-only file system.

---

