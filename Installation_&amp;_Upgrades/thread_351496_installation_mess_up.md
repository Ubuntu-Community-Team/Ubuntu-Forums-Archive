---
title: "installation mess up"
date: 2007-02-02
forum: Installation &amp; Upgrades
---

### Post by kanyez on 2007-02-02
i was installing unbuntu and pressed cancel by mistake then when i tryd to go back to windows i got a disk read error since my computer is new and under warenty i called emachines they were able to get it rebooted but it still kinda looks like unbuntu i mean its windows but with unbuntu feel and its missing programs that come with the computer so i rebooted it two more times and it still has a unbuntu feel ?i jus want my windows back im scared if a reboot cd cant fix it then i did something serious ?

---

### Post by empthollow on 2007-02-02
the easiest way to fix it is to got through the ubuntu install on a second partition.  If that is not an option, you could try to get an actual windows cd, boot from the cd and then press c (i think) for command prompt.  type "fixmbr" and that should fix the boot sector and make windows work again.

---

### Post by dryder on 2007-02-02
Use the XP install disk, let it go until given the option to R (Repair) existing installation.

At the prompt. if unsure of avaialable commands type help.

Otherwise just type fxmbr and it will reboot.

David

---

### Post by kanyez on 2007-02-02
how do i do fxmbr step by step please?

---

### Post by empthollow on 2007-02-03
i can't remember exactly step by step but i'll give it a shot.
1. put cd in and wait till is asks you for a response
2. press r for recovery mode (you should now see a black screen possibly w/ login)
3. if you do not see a black screen possibly w/ login, there should be an option like manual or command mode
4. after logging in you will see "c:\"
5. type "help" here and you will see a list of commands or programs if you will
6. type "fixmbr" or maybe it is "fxmbr" or maybe it depends on the version of windows either way you can see the correct command in the "help" section
7. type "reboot" or "restart" or "exit" - sorry i can't remember, the idea is to restart the system and you should be back up

---

