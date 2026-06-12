---
title: "Ubuntu 9.10 No login/password"
date: 2010-04-22
forum: Installation &amp; Upgrades
---

### Post by wetsprocket on 2010-04-22
I installed VM Ware Workstation 6.5 and installed Ubuntu 9.1 from ubuntu-9.10-desktop-i386.iso. It installed without issue but I was never prompted for a username/password. Now I am at the Ubuntu login screen with the option to login as Ubuntu or other... , both of which require a password. Anyone else experience this?

[IMG]http://i82.photobucket.com/albums/j261/tboss888/ubuntu.jpg[/IMG]

---

### Post by coffeecat on 2010-04-22
I am not familiar with VM Ware - I use VirtualBox - but if you install Ubuntu in VM Ware the same way as in Virtual Box, you would have to boot into a live session from the ISO or from a CD. In which case it is impossible to install Ubuntu without setting a password. You will have had to fill in the fields in the window as in the thumbnail attached.

If you managed to install Ubuntu in some other way, please post details. It would be interesting to know.

Anyway, to reset the password, you have to boot into recovery mode and follow the instructions in this link:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

**Edit:** By the way - your screenshot isn't clear enough to read, but the username looks to be different from the default live session 'ubuntu' username. If so, you must have set your username in the screen I have posted, and you couldn't have got past that screen without setting a password. Are you sure you didn't note it down somewhere?

---

### Post by garvinrick4 on 2010-04-22
Just incase you are in a Live CD situation use ubuntu as username and nothing for password just hit enter.

---

### Post by coffeecat on 2010-04-22
> **garvinrick4 said:**
> Just incase you are in a Live CD situation use ubuntu as username and nothing for password just hit enter.

Ah yes. Good point! 

@wetsprocket, if you are in a live session and the system is prompting you to log in as 'ubuntu', you haven't installed Ubuntu yet! But 'ubuntu' and an empty password should do the trick. The live session normally doesn't prompt for a password but sometimes something goes awry and it does.

---

