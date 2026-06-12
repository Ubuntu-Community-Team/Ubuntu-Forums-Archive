---
title: "login to xubuntu impossible"
date: 2009-11-28
forum: Installation &amp; Upgrades
---

### Post by azertyh on 2009-11-28
hi,
i installed xubuntu thursday, on dual-boot with windows xp. installed correctly.

i logged yesterday and i cant acces to xubuntu. it's not a wrong password because there is not the message "authentification failure". it's just that the window login re-asks the password.

search and ask solution on france ubuntu forum. they said to change the password by mode recovery mode and changing the password by passwd username. i did it. xubuntu opened. reboot xubuntu for being sure. and no, the window login re-asks me again and again the new password. reboot, mode recovery, change password, reboot and no success.

i re-installed xubuntu yesterday. set a very simple password : aaaaaaaa. but no success.

i re-installed this afternoon and tick on "connect automatically". i acceded to xubuntu without typing the password. reboot and xubuntu asks the password??? i type the password and no success.

what happens? and what to do?

remark : i didnt type a wrong password because the message "authentification failure" didnt appear.

---

### Post by azertyh on 2009-12-04
i found that some users had this problem. i found also that if the user set the screen resolution higher than the default, he cannot connect to the desktop at the next boot. i remember that after re-installation, i set always the screen resolution. so, i re-installed xubuntu yesterday, i didnt set the resolution, and i can connect and re-connect to the desktop now.

perhaps this information can help someone to resolve this "bug".

in case of &#8230;, how can i set the resolution on recovery mode? i found that the command is xrandr, can i use this command on recovery mode?

---

### Post by azertyh on 2009-12-11
hi,

i find how to login to the desktop.

at the login screen, open a terminal, go to the folder /home/user/.config/xfce4/xfconf/xfce-perchannel-xml, open the file displays.xml, change the resolution in this file to the default resolution, save and close the file.

log on and clap your hands :D

it's a temporarily solution but it works.

---

### Post by alexandr.imzailov on 2009-12-12
Cause of the problem a bug?
Thank you for temporary solution.

---

### Post by Carranor on 2009-12-16
Dear all,

I am new to linux, but the following solution helped me. I found out that when I changed screen resolution after Xubuntu install, it will ask me for PW and login after restart and then I can never log into the desktop.

I managed to reach desktop by logging in via "safe mode" or what ever it's called in Linux and then type startx. Voila!

After that I enabled chose session in startup. Now I am able to log in after restart by selecting the session I created. It's not a pretty solution, but it works for now.

Edit, oops, I see that the topic already was solved, my bad sorry.

---

