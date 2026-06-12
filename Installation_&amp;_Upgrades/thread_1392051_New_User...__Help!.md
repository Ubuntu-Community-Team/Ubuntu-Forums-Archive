---
title: "New User...  Help!"
date: 2010-01-27
forum: Installation &amp; Upgrades
---

### Post by ccrawford57 on 2010-01-27
I loaded 9.10 on an old dell laptop last week and everything worked fine.    I did learn that the HD was failing so I purchased a new one...  160GB.     I booted up again off the USB "ubootin" and was able to get to the GUI and install Ubuntu.   Now, when I reboot, I keep getting GRUB and when I choose an option, I get the error message:
 
error: no such device: 8b811ee8-6650-4c  etc.....
 
I believe the number refers to my HD, but I am not certain.   The BIOS is set up to boot from the HD if the USB is not present.     I've tried reloading at least 5 times.  Also, reformatted the drive and reloaded just to be sure
 
Do I have another bad HD?    What am I doing wrong.

---

### Post by Jonasan Cope on 2010-01-30
hey dude,

tried to reply to your message, might have worked, might not - the reply that is - forum is not co-operating. tried email contact link as well. with this post as well you might just get this fix for your grub problem.

enjoy linux mate.

[QUOTE=ccrawford57]hello.... I saw your post on updating the grub cnfg file. my grub keeps inserting a line that looks for a floppy drive, and I am unable to boot without editing that line every time I boot. I ran update grub, but no luck. Can you tell me how I permanently update the grub config to remove this line?[/QUOTE]

yeah ok i can help you there. exctly the same as the issue i had.

fairly simple fix but it took me a while to work out.

there may be a more elegant way but this works.

when you run update-grub, the program rechecks your system and rewrites the grub.cfg file. what you need to do is force grub to see your own custom list of entries - so you can take out the floppy disk check line.

update-grub runs through a series of executable files in the /etc/grub.d/ directory to build the new grub.cfg file. each of these executable files gets grub to check kernels and boot possibilities in your system - and compile a new file.

we need to alter the last of these files - "40_custom".

first off open a terminal and open gedit with super-user (admin) privileges to edit the 40_custom file

         sudo gedit /etc/grub.d/40_custom

enter your system password when requested to have sudo access.

now open another terminal and enter

        gedit /boot/grub/grub.cfg

copy all the text in the grub.cfg file and paste it all below the header in 40_custom file.

next job is to scan down this 40_custom document, checking in the text for the linux boot entries that are causing you problems and deleting the lines that are referencing the floppy drive - just as you do at the grub terminal to get your system to boot.

once you've removed each line referencing the floppy drive which dosnt exist you then need to save the 40_custom file and then close the editors.

we now have to make the 40_custom file executable. go back to a terminal and type

      sudo chmod +x /etc/grub.d/40_custom

type your admin password if asked for it. now update-grub will see your custom file. problem is its also going to write its own boot entries as usual - leaving you with the same problem. grub can be stopped from doing this by making the other files in the /etc/grub.d/ non-executable - meaning update-grub only works with your 40_custom file. bring up a file browser window and navigate to the /etc/grub.d/ directory. you should see 7 files. Ignore the readme and 40_custom - we are going to make all the other files non-executable.

so, in the terminal type the following

     sudo chmod -x /etc/grub.d/00_header

press the 'up' cursor to bring up the last command entered in the terminal, scroll back and change the 00_header to each of the other 4 file names respectively, pressing enter each time - i.e. same command for 05_debian_theme, 10_linux, 20_memtest86+, 30_os-prober.  i.e.

     sudo chmod -x /etc/grub.d/05_debian_theme
     etc....

you can now run the grub update program..

     sudo update-grub

and this should have just copied the 40_custom file we edited back into the grub.cfg file, and given us clean boot options without the floppy disk search.

check by using the terminal to

    gedit /boot/grub/grub.cfg

make sure this worked properly and that the floppy search lines have been removed.

now reboot your system and everything should boot automatically.

i hope.

could probably have just told you what to do quicker and easier than that, but maybe that gives you some idea of what you did and why - better to understand a little i think.

let me know if it works for you, and feel free to ask any questions if this is not clear.

cheers, jonasan



----------


also a point of note on that failing HDD. did palmpiset come up and tell you that you had many many bad sectors - re-allocated secotrs - somewhere around 65 000 of them?? if so it may have been a bug in that program which has been giving lots of people that message when they first install 9.10. from what i can gather serching others experience - this happened to me - it seems that if the number is high like 65000 then it is almost definately a bug and nothing wrong at all. its an unrealistically high number you see, and really if you had a problem it would be reading out somewhere below or around 1000 for a really bad problem and dieing HDD. so maybe your other HDD was actually ok?

but im not sure as i'm not a a developer just a user,  so i cant be certain - someone else might know better.

anyway, hope the grub fix works.  cheers, jonasan.

---

### Post by coldraven on 2010-01-30
Palimpsest says that I have 26 million Uncorrectable errors!
Strange 'cos the machine works fine! :p

---

