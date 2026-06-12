---
title: "Username &amp; Password?"
date: 2006-10-21
forum: Installation &amp; Upgrades
---

### Post by Forgott3n on 2006-10-21
Ok.

I just finished my brand new install of Ubuntu 6.06 and during the install it asked for a username, which I made "root". It also asked for the name of the computer which was "ubuntu-desktop" and the name of the person (first name, last name business) was "Justin".

Now, I restarted and up comes the login screen. I enter in "root" and then my password. I get this: "The system administrator is not allowed to login from this screen."

What do I do?

---

### Post by taurus on 2006-10-21
Big mistake!!!  There is already a root account and it's disable so if you make a username as root during the installing process, you can't log in!!!  Why didn't you call it justin instead of root?  You have a few options.  Boot into recover mode from GRUB and change the username of that account from root to justin or whatever you want to call it.  Or boot into LiveCD, mount your harddrive where / is, and make the change.  Or reinstall and this time, create an account with username anything else except root!!!

---

### Post by dbd on 2006-10-21
I'm amazed that the installer allowed you to make your username "root". When logged in as root you have permissions to do anything, and the vast majority of the time you do not want these permissions, it is very dangerous and things can easily go very wrong. 

You want your normal user to be called something else (justin would be a good idea), so what you want to do is add a new user. I'm not sure if this will work, but its worth trying before reinstalling.

First To do this reboot your computer, then at the grub menu choose "single-user mode"
once that has booted use this command:
> sudo adduser justin
(replace justin with whatever you want your username to be)
then reboot with the command
> sudo init 6
and you should be able to log in as justin with no problems

For more info about the root user see here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Good luck :)

---

### Post by Forgott3n on 2006-10-21
Ahh nutters. I heard of linux using root as administrator, so I wanted to make use of the lingo, learn and use the terminology. I figured, "Well since I will be the admin, lets make my username root".

Sounds like I'm going to change it via GRUB. Any instructions on how to proceed? The computer is way to slow to reinstall.. That took too long.


Thank you for your time.

[EDIT] Ahh that kind sir just posted a possible solution. Lets see if I can do that.

---

### Post by Forgott3n on 2006-10-21
Ahh bad news, there is no "single-user-mode" in my GRUB boot, I have the memtest, ubuntu, and ubuntu recovery mode.

I tried the GRUB command line, that didn't work.

How would you go about changing/adding the login info on the live cd?

---

### Post by sitedesign on 2006-10-21
recovery mode is the same as single user mode.

---

### Post by taurus on 2006-10-21
If you look at my reply, it said recovery mode!!!

---

### Post by Forgott3n on 2006-10-21
Beautiful!

I was able to create a new user from the recorvery mode and login perfectly.

Thanks everyone.


Perhaps this goes to show that the developers should restrict the user 'root' from being created... Because people like me, the newbs, will break it :)

---

### Post by Alfredo Garzon Zamora on 2006-11-04
If I dissable the recovery mode from the grup menu, how can I acces it to uncomment those lines??

---

### Post by taurus on 2006-11-04
> **Alfredo Garzon Zamora said:**
> If I dissable the recovery mode from the grup menu, how can I acces it to uncomment those lines??
You would need to use the LiveCD to boot from it.  Then mount your harddrive where / is and edit menu.lst on your harddrive...

---

### Post by Alfredo Garzon Zamora on 2006-11-05
thanks a lot, In my languaje "Gracias"

---

### Post by taurus on 2006-11-05
> **Alfredo Garzon Zamora said:**
> thanks a lot, In my languaje "Gracias"
You're welcome (and in my language, "You're welcome!").  :mrgreen:

---

