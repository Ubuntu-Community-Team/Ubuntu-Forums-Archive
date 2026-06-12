---
title: "booting Ubuntu studio 7.10 GUI?"
date: 2008-06-21
forum: Installation &amp; Upgrades
---

### Post by ragebunny on 2008-06-21
Hey i just installed Ubuntu studio using Virtual pc 2007. The problem i have is that it doesn't seem to boot into the gnome interface.

Please could someone lend a hand. Maybe a Solution or even what you think might be happening.

I have installed Ubuntu studio 7.04 and it works fine, i even got the mouse working with a little help. But i haven't got a clue how to boot the GUI instead of teh command line.

thanks for you help.

---

### Post by Partyboi2 on 2008-06-21
Are you getting any error messages? What part is it stopping at? If you are able to get to a terminal (Ctrl+Alt+F2) check to see if you have the ubuntustudio-desktop package installed
```
dpkg -l ubuntustudio-desktop
```

---

### Post by ragebunny on 2008-06-22
Thanks for you help.

as i read your post i realised that i have been trying the comand 

'sudo apt-get install ubuntu-desktop' 

when in fact i should be using 'ubuntustudio-desktop'

SO i used the new command and it started to install, but then virual pc went and crashed mid install..... Now when i try to run the cimmand again im getting this error:

'E: dpkg was interrupted, you must manually run 'dpkg -- configure -a' to correct the problem.'

When i try to run this command i get an error saying that dpkg requires superuser privilege, does this mean i neeed to use the admin acount? how do i do that?

thanks again for your help.

---

### Post by ragebunny on 2008-06-22
Well i've managed to do that, but it just doesn't seem to be working. when running the cammand using sudo it gets as far as 'starting up launch-pad intergration 0.1.15 and just stops. 

im gonna go ahead and re install and see if that changes anything. Any more help will still be welcome.

Thanks.

---

### Post by Partyboi2 on 2008-06-23
There should be a stage in the install process that allows you to choose some of the packages, make sure you choose ubuntustudio-desktop.

---

### Post by ragebunny on 2008-06-23
Thanks a lot for you help. I managed to install ubuntu studio 8.04 under virtual box instead of using virtual pc. I must have screwed up the install of the desktop but its all ok now.

Thanks again for the help.

---

