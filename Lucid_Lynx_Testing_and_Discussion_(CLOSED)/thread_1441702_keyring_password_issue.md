---
title: "keyring password issue"
date: 2010-03-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by forcecore on 2010-03-29
is that some temporary bug or what but every time i boot keyring asks password for wifi, it should not because i have auto login and unsafe storage for wifi.

---

### Post by forcecore on 2010-03-29
has anyone had this type issues currently or it was just temporary glitch?

---

### Post by mirach on 2010-03-30
> **forcecore said:**
> has anyone had this type issues currently or it was just temporary glitch?

After installing follow this sequence:

1. Set up the wireless connections making sure to check the box that says "Available to All Users".
2. Reboot.
3. Last of all enable auto login.

I don't know if the reboot in between is needed or not but I always do the three steps above in that order and I never get the keyring thing anymore.

---

### Post by garvinrick4 on 2010-03-30
Keyrings
   
     1. Open up your Home Folder by clicking Places>Home Folder
     2. Press CTRL-H (or click View>Show Hidden Files)
     3. Find a folder called .gnome2 (it has a period at the beginning of the name) and open it by double clicking on it
     4. In side of the .gnome2 folder, there is another folder called keyrings.  Open it up.
     5. Delete any files you find within the keyrings folder
     6. Restart the computer
   
  After you restart and login (if you&#8217;re automatically logging in) you&#8217;ll probably be asked to enter your wireless networks WPA/WEP encryption key.  After you type that password in, the keyring manager will appear to let you know that it would like to handle the storage of that password and lock it away with a new keyring password.  The box looks like this:
   
  Instead of typing in a new password, leave both boxes completely empty and click Create.
   
  You&#8217;ll then be asked if you know what the hell you&#8217;re doing:
   
  Go ahead and click Use Unsafe Storage.
   
  WARNING: Doing this creates a new file in your ~/.gnome2/keyrings/ folder called default.keyring and it will now house passwords IN CLEAR TEXT and not in an encrypted form.  So it is imperative that you are certain no untrustworthy persons can access your user account (either physically or by remote) or they will be able to easily open and read this file and obtain many passwords (for things such as FTP accounts, SSH, e-mail accounts, etc).  Proceed with caution.
   
  From here on all keyring stored passwords you enter will not safeguarded behind a master password or encryption.  Whether or not you want to do this is entirely up to you.  I personally have had enough of the keyring manager and consider it kind of annoying.  But as I said before, you may have certain environmental factors that make having a master password over the rest of your passwords a good idea.  Keep in mind that the keyring password manager has absolutely nothing to do with your administrative/root privilages password that has to be entered any time you want to apply updates, or add/remove software.  You will still have to type your account password in for these actions, and that is something I am quite comfortable with.

---

### Post by forcecore on 2010-03-31
Looks liks it was some sort of glitch because first time i created password with unsafe storage then after restart file was encrypted, now it worked and it is plain text now. I always use unsafe storage for wifi.

---

