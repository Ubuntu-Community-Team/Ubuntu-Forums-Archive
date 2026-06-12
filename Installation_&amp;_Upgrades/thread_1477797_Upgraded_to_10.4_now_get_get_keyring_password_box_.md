---
title: "Upgraded to 10.4 now get get keyring password box at boot"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by RichardUK on 2010-05-09
For some reason after upgrading from 9.10 to 10.4 I now at boot get the password box for unlocking the keyring. It does not seem to make any difference to the computer if I put the correct password in, junk or just cancel. Everything still works as it did before. So how do I turn it off, it's not doing anything from what I can see.

---

### Post by lechien73 on 2010-05-09
Did you supply a password for the keyring before? You can disable it by changing the password to blank, but this means that none of your saved passwords will be encrypted - they'll all be stored in plaintext. If you're happy with that, then you can do the following (note that this procedure will delete any saved passwords on your computer):

[LIST=1]
[*]Go to your Home Folder by clicking Places -> Home Folder
[*]Press CTRL-H to view hidden files
[*]Open the folder named .gnome2
[*]Open the folder named keyrings
[*]Delete the files in here, and restart the computer
[*]When prompted for a keyring password, leave both fields blank and click **Create**
[*]You will be given a warning, but click **Use Unsafe Storage**
[/LIST]
The prompt should now vanish when you restart.

If you can remember your keyring password, then you could try the following, which doesn't delete any saved passwords, but still uses unsafe storage:

[LIST=1]
[*]Go to Applications -> Accessories
[*]Click "Passwords and Encryption Keys"
[*]Right Click on "Passwords: default"
[*]Select **Change Password**
[*]Enter your current password into "Old password" and leave the other fields blank
[*]Hit **Change**
[*]Proceed with the **Unsafe Storage** option
[/LIST]

---

### Post by RichardUK on 2010-05-10
Silly question, but if you want protected passwords do you have to live with this dialog box on every boot?

---

### Post by RichardUK on 2010-05-10
Fixed it! :) there was an entry for that ubuntu one thingy that I looked at just once and then ignored it. For some reason after the upgrade it decided that the password was wrong hence the dialog box. ( I think) I just deleted the entry in the "Passwords and Encryption Keys" app and now no dialog box at boot time. :) Thanks lechien73 I never would have found that with out your pointers. :)

---

### Post by lechien73 on 2010-05-11
You're welcome...glad it helped :)

If you get chance, could you click on "Thread Tools" at the top of this topic and set the thread to "Solved"?

Thanks

---

