---
title: "Help Error Message!!!"
date: 2008-10-05
forum: Installation &amp; Upgrades
---

### Post by ZepFloyd on 2008-10-05
So burned the iso file onto a cd, went to boot it, loads up...i choose to just run ubuntu from the disk so nothing is installed/changed. well it starts showing the load screen with the orange block going back in forth. after a couple minutes i start getting these error messages:

Buffer I/O error on device fd0 logical block 0


there were numbers in front of that message, which would change...but the same message every couple seconds....unless i didnt wait long enough...what seems to be the problem?

i am running vista 64...pretty sure i d-loaded and burned the 64 bit file...any ideas?

thanks

---

### Post by JAS510 on 2008-10-05
i had the same message, but that was when i loaded the 32bit version.  i had to reburn the iso file at a slower speed as well. 

give that a shot and see what happens.

---

### Post by ZepFloyd on 2008-10-05
> **JAS510 said:**
> i had the same message, but that was when i loaded the 32bit version.  i had to reburn the iso file at a slower speed as well. 

give that a shot and see what happens.

burned it at 8x and it still did the same thing....anyone else help me out here? thanks

---

### Post by ZepFloyd on 2008-10-05
i just tried wubi to see if that would work...i got some other error message after the load screen for that as well. i dont know if my bios settings on my comp are screwing it up or what.


any help is appreciated

---

### Post by JAS510 on 2008-10-05
yeah after a full night of troubleshooting my system.  I'm back to the same level as you.

---

### Post by ZepFloyd on 2008-10-05
so hopefully someone can help me out...getting none in the chat.

trying to boot ubuntu from the disk...it boots up to the menu i choose to boot from disk orange load screen goes...then i get an error message just like this thread talks about [http://ubuntuforums.org/showthread.php?t=438923](http://ubuntuforums.org/showthread.php?t=438923)

in the chat a few people said to add floppy=off or acpi=off in the boot line in the F6 menu...i did that and still no luck

CAN ANYONE HELP ME OUT?????

running vista 64 bit, 4 GB ram, 320 GB HD, gigabyte ep45-ds3r mobo

any help is appreciated

---

### Post by Pumalite on 2008-10-05
What is your CPU?

---

### Post by cariboo on 2008-10-05
The kernel is looking for your floppy drive. If it really bothers you disable the floppy drive in the bios and you shouldn't have any problems.

Jim

---

### Post by ZepFloyd on 2008-10-05
> **Pumalite said:**
> What is your CPU?

intel core 2 duo E8400

---

### Post by cariboo on 2008-10-05
Have you tried disabling the floppy drive in your bios?

I answered this post before realizing that you posted the same question in the 64bit forum, You should double post. I'll asks the mods to close one of the threads

Jim

---

### Post by Sef on 2008-10-05
Merged.  Double Posting.  Please post a question only once in Ubuntu Forums.

---

### Post by ZepFloyd on 2008-10-05
> **cariboo907 said:**
> Have you tried disabling the floppy drive in your bios?

I answered this post before realizing that you posted the same question in the 64bit forum, You should double post. I'll asks the mods to close one of the threads

Jim

oh sorry, will remember from now on.

i havent tried disabling the floppy from my bios...people in chat said i could disable it by just typing floppy=off at the end of the bootline in the F6 menu in ubuntu

---

### Post by ZepFloyd on 2008-10-05
just checked...floppy was already disabled when i went into my bios

any other ideas?

---

### Post by Sef on 2008-10-06
> burned it at 8x and it still did the same thing....anyone else help me out here? thanks

Burn it at 4x or slower.

---

### Post by ZepFloyd on 2008-10-06
> **Sef said:**
> Burn it at 4x or slower.

i'll try it...right now i am d-loading the beta for the new version..see if that works.

---

### Post by ZepFloyd on 2008-10-06
I GOT IT TO WORK!!!

so i d-loaded the newest beta version...i opened up the .rar file...saw the wubi installer was in there. i went let me try this route so i dont have to burn a disc..open it up...it says hit ESC to go to menu..i'm like ok...then i selected install by some other way...forget the word...it wasnt the first option. everything installed correctly...i think it even partitioned itself 

granted might be buggy..but final release coming out end of month..think i can live with that. also its installed...i guess i could always uninstall if i dont like

thanks for all the help

EDIT: maybe wubi isnt installed per se but yea i'll mess around see if i wanna keep.

---

