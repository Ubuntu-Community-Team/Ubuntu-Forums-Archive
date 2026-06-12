---
title: "Ubuntu 12.04 Read-Only file systems, cannot login"
date: 2012-06-12
forum: Installation &amp; Upgrades
---

### Post by alhazzaa on 2012-06-12
Hello there, 

I was facing a problem with my Ubuntu 12.04 of not being able to login after an update for about two days i've searched everywhere but nothing i've read could solve it. And i've fixed it finally so i thought i should inform people facing the same thing about how to solve it!

) This could be for you if you've:
- Changed your account's password prior the update.
- Have an encrypted home directory. 

) Symptoms:
-When you type my password to login on the GUI it flashed a black screen then comes back again to the login screen.

-When you recovery login on root all files couldn't be modified and all what it says is "Read-Only filesystem".

- When you try to modify files such as passwd file it would say Read-Only files system.

- You cannot change the problematic account's password even when your're root (says Locked read-only file system)

- When you login Ctrl+Alt+F3 all you see in your home directory is two files 1) Access-Your-Private-Data.desktop and a README file. 

- Remounting the partition doesn't work and when you do (dmesg) you get "re-mounted. opts errors=remount-ro" 



====================================
Solution:

Login from your Guest Session account and then from the top right click on "Guest Session" then click on "User Accounts" > Click "Unlock" type in the current password to unlock it. Then click on the *** to change the password and then change it to the password that has been recently changed (the password that has been used to lock the home directory in the first place)

Login again using that account and it should work.  


Regards,
Alhazzaa (This is my first thread so i might have placed it in the wrong place)

---

### Post by allang on 2013-03-27
great post  i came across the problem which says "read-only filesystem" when i was writing code  thank you very much

---

