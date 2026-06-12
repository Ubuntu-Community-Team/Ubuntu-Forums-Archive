---
title: "Ubunto 10.10 installation problem"
date: 2010-11-06
forum: Installation &amp; Upgrades
---

### Post by SGR 1806-20 on 2010-11-06
Hi, 

i am using windows since i first get my pc but itz day-2-day demands and vulnerabilities make to turn to linux but for some other things i do need window yet :P
last time kubuntu was on my machine along with window 7 (through wubi) but then i uninstall that kubuntu ,coz i want to use ubunto.i've got my ubuntu 10.10 cd, so i just sat infront of my pc, inserted the disc and it was a happy installation as it usually does with wubi but when i restart my pc and go for ubuntu OS , there show up a kubunto screen, which has a title like ubuntu login and there in username field , thats not my username dat i've choose for my ubuntu but it is my pc-name from win7.well i try to log-in with the user i 'd made during installation but it didnot let me logged-in :( i try again n again even through consol but no hope.then i go back to win and uninstall wubi and get install again ubunto but nothing different was there to meet me :( 

so i better think to get advice from you guys as i am new to linux and dont know much about itz setting n stuff.. so any suggestion , sollution broz for my problem :)

i have a core 2 quade Q6600 2.40 Ghz intell processor with 64-bit win 7 ultimate. i am installing 32 bit ver of ubuntu 10.10...!

---

### Post by bcbc on 2010-11-06
> **SGR 1806-20 said:**
> Hi, 

i am using windows since i first get my pc but itz day-2-day demands and vulnerabilities make to turn to linux but for some other things i do need window yet :P
last time kubuntu was on my machine along with window 7 (through wubi) but then i uninstall that kubuntu ,coz i want to use ubunto.i've got my ubuntu 10.10 cd, so i just sat infront of my pc, inserted the disc and it was a happy installation as it usually does with wubi but when i restart my pc and go for ubuntu OS , there show up a kubunto screen, which has a title like ubuntu login and there in username field , thats not my username dat i've choose for my ubuntu but it is my pc-name from win7.well i try to log-in with the user i 'd made during installation but it didnot let me logged-in :( i try again n again even through consol but no hope.then i go back to win and uninstall wubi and get install again ubunto but nothing different was there to meet me :( 

so i better think to get advice from you guys as i am new to linux and dont know much about itz setting n stuff.. so any suggestion , sollution broz for my problem :)

i have a core 2 quade Q6600 2.40 Ghz intell processor with 64-bit win 7 ultimate. i am installing 32 bit ver of ubuntu 10.10...!
The login displayed name is the user name from windows. the user name you selected is the user name wubi uses (e.g. home is /home/<username>
You can change the displayed name after logging in. Just use the password you entered.

e.g. my user account on windows is Admin, my username for ubuntu is bcbc. So the logon screen prompts Admin, but my home is /home/bcbc

If you can't log in still, boot the -recovery mode. (2nd item on grub boot menu). Then drop to a root shell. Find your user name ("ls /home" and then reset the password: "passwd <username>"

---

### Post by SGR 1806-20 on 2010-11-06
tnx for rply bcbc :)
okey. so all i have to do is go to recovery mode and change my password but wouldn't it will ask me for my current password as it is not accepting it as valid login?? and do i have to enter just password for the name that appear at login screen instead of my username for ubunto? meanz for Admin not for bcbc as in ur example? :)

---

### Post by bcbc on 2010-11-06
> **SGR 1806-20 said:**
> tnx for rply bcbc :)
okey. so all i have to do is go to recovery mode and change my password but wouldn't it will ask me for my current password as it is not accepting it as valid login?? and do i have to enter just password for the name that appear at login screen instead of my username for ubunto? meanz for Admin not for bcbc as in ur example? :)

You don't need a password to get root access to your install. The recovery mode gives you full root access.

You should be able to enter the password on the logon screen - ignore the user name displayed and type in the one you entered in the wubi install dialog. If it doesn't work then change the password as I described and try again.

There'll only be one user (that you can log on to) and that will be the user you created with the wubi install - you can't "logon as root" (that's the ubuntu default). 

There's one user - and one password.

---

### Post by SGR 1806-20 on 2010-11-06
thnx bcbc :) i got in my ubunto :) thanx alot dear :)

---

