---
title: "&quot;Ubuntu&quot; user's default password (v9.10)"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by Nanded on 2010-05-16
Hi,

I have installed Ubuntu 9.10 on USB drive with persistance (using the USB installer software).
During the installation process, I was not asked for root or superuser password.
Whenever I boot on Ubuntu, I am not asked for any password and land up in desktop environment.
Ideally, I want that, when I boot, I should be prompted/asked to choose a user to login and login to that user.

My understanding is, when I boot now, I land in the user 'ubuntu'. Which is the superuser.
Is there a default password for 'ubuntu' user? what is it?
I tried to change the password for 'ubuntu', via System -> Preferences -> About Me (there is a change password button). It asks to enter existing password and authenticate, but I don't know the existing password.

Please help.

Thanks in advance.

---

### Post by blchinezu on 2010-05-16
let the current password field blank

edit: you can also try to change the password from the terminal

type **passwd** and it will ask for the current password. hit enter without any other input.. if it asks for the new password things are allright.. else it means there actually is a password set

---

### Post by -Jeremy- on 2010-05-16
Very odd... Usually during install you are asked if you want ubuntu to ask for your password or automatically log you in. The fact that you get logged in automatically would suggest you consciously made that choice. Also as far as I know root is always called root so the 'ubuntu' user you log in as is not root.

To change your password just type 'passwd ubuntu' in the terminal and insert your new password.

To let Ubuntu ask for your password instead of automatically logging you in go to:
System > Administration > Login Screen and change the parameters to your liking.

---

### Post by Dubious9 on 2010-12-24
Hello,

I discovered the solutions to this problem: It's a corrupt optical disk/faulty burn.

Details:

I arrived at this thread because I was having a strikingly similar problem. I wanted to install Ubuntu 10.10 Desktop on a dated IBM ThinkPad Model A31 (circa 2002/2004). However different from the original problem of this thread after booting from the optical disk I got a 'funky' looking low resolution screen asking me to pick a language (English) and then a a menu that included (something like): "Try Ubuntu" , "Install Ubuntu" , "Recover Installation", "Test Media" , "Memory Test", "Install Text Mode Ubuntu" and several function key options at the bottom of the screen like F1 Keyboard, F4 Mode, and F6 for options.

After selecting 'Install Ubuntu' I waited an unusually long time for the Ubuntu Desktop to appear. When the Desktop appeared it was at a good resolution, 32-bit color, and purple background. But, I was not given the usual 'Choose Language' , 'Choose Keyboard', 'What's your name/User Name/Name of this Machine/Password/Require Password at login/Login Automatically' etc. Instead I was asked to authenticate: User/Password and nothing I tried worked.

I tried booting from the optical disk and choosing to verify the media. It made it through with no errors. 

I then tried booting from the optical disk again and this time pressing F6 and choosing boot options. None worked. However, when choosing 'nomodeset' the installer crashed part way through the install with plain text on the screen saying I/O error I/O error I/O error I/O error...

This was when I suspected a bad burn.

I tried re-burning at the slowest possible speed with verification...and after this when I booted from the optical disk a choose install ubuntu (no boot options just plain 'install ubuntu') The desktop appeared quickly within a few minutes and I received the proper account setup screen. And I succeeded in installing ubuntu.

---

