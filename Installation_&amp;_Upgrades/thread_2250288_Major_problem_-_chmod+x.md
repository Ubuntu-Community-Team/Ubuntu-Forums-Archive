---
title: "Major problem - chmod+x"
date: 2014-10-27
forum: Installation &amp; Upgrades
---

### Post by mohamed2 on 2014-10-27
First of all, I want to apologize in advance if the solution to this post would take up your time. I changed the permissions of the home directory, I wasn't aware that I was there, and it happened. Every command I do is denied and the GUI is all gone and I guess most of you is familiar with the GUI error when you reboot. I have tried everything..literally.

I accessed the shell through CTRL + F1 but then again, I couldn't even login.
I then went to recovery, and tried to reinstall ubuntu-home after the update but neither of them would work. I even tried to chnage the mirror sites but that made it even worse!
I even tried the best solutions online (even reinstalling the ATI graphic card failed).

Now, I'm trying to install the system again from a bootable USB and it won't let me - it throws a bunch of messages like kernet_init+0xe/0x0... and rest_init+***** (same). 

I'm not even confident that a technician can help..although I am running out time and I will be screwed really soon. My work is on Github (thank god) I will just need to install all dev tools again. Please help me out..

---

### Post by fantab on 2014-10-28
How did you change your permissions? Generally 'chmod+x' is use to make a file executable to undo it you should 'chmod-x'.

---

### Post by mohamed2 on 2014-10-28
I was running commands as specified by Apache to get rid of an error showing on my error.log...one of them is chmod+x, I know that the revert is chmod-x but the moment I used the command, I was no longer able to interact with my console or anything, and when I rebooted, my only option was to go to recovery mode.

I'm trying to apt-get upload, but the mirrors are not being fetched and I'm trying to find a way to go online from the command prompt, I guess this is my last chance..

---

