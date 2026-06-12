---
title: "Having problems logging in to administrator account"
date: 2011-11-18
forum: Installation &amp; Upgrades
---

### Post by Raptor434 on 2011-11-18
Im running ubuntu 11.10 and i went to take the password off of my admin account and now it wont log in to that account it just kicks me back to the log in screen. ive tried deleting the xauthority file but i get an error saying it isnt found. when i log in using the tty1 it gives me an error saying there is a missing key... any help is appreciated!

---

### Post by MAFoElffen on 2011-11-19
> **Raptor434 said:**
> Im running ubuntu 11.10 and i went to take the password off of my admin account and now it wont log in to that account it just kicks me back to the log in screen. ive tried deleting the xauthority file but i get an error saying it isnt found. when i log in using the tty1 it gives me an error saying there is a missing key... any help is appreciated!
This is a little touchy security-wise... Whatever was the first user in the installer was an admin account. The root password was assigned the same- such as if you try to log onto a text console or TTY sessions.  You can set additional users as admin accounts... You can change the root password and there is "a way" into a root prompt to fix the broken password...

- Boot.
- Hold down the shift key to bring up the Grub Menu.
- At the grub menu, select a Recovery mode boot option.
- At the recovery mode menu, select the last option, "Drop to Root Prompt"
- You'll be dropped down to the root prompt. At this point, as root, be careful what you ask for...
```

ls /home

```And you should see the  user folders of your install. That way you can see the spelling of the user account you want to reset the password for (Example "raptor")

Then using our example, do
```

passwd raptor

```After entering a valid password* twice... it will finish.

-type "exit" and <enter> to exit out of the root shell.

That will reset the password...

Note-  
* I know that the admin utility "passwd" will not accept null or blank as a valid password... but you can do it manually, with a little trickery.  I know a few different ways to create a working account with a blank password. Pam and DM's (desktop managers with their graphical login screens) are both configured by default not to accept a blank/null password. As with above, there's ways around that...

The way I'll mention is the easiest and fastest. 
- After you have the account created, with a password  (will be required)
- Press <cntrl><alt><F2> and get to a TTY session 
- Log in as "root" (You have to be in a root prompt to lock and edit this file)
- Enter the password
- Open /etc/shadow to edit with your favorite editor (nano, vi, vim, emacs etc.)
- Look for the user account line...
example-- rapter:[COLOR=Black][COLOR=Red]$1$5druSp26$nVpXn5EVk73sWzZlhLuXNB1[/COLOR]:13996:0:99999:7:::[/COLOR]
- Replace the highlighted text, which will be between the colons / after the user account name, with the text "U6aMy0wojraho".
example-- rapter:[COLOR=Red]U6aMy0wojraho[/COLOR]:13996:0:99999:7:::

This way the password ends up "functionally" as blank, but is not null. That way it gets past the failsafe's built in to prevent a null password from being used.

The other way is to create the account, which from the desktop applet requires you to have a valid password. Drop down to a root prompt to delete the password all together for that user. But then you have to reconfigure pam -and- the desktop manager (KDE, GDM, LXDE, etc) separately to be able accept a null password.  That method takes longer and is more work, but once done, creating subsequent (hopefully non-admin) accounts, that can have a blank password easier. If you want to do it that way, just tell me and I'll provide instructions.

Again, I'll give my disclaimer that a blank or null password for an admin or root is a security risk, but if you are set on that, there's several safe ways to open that hole.

---

### Post by Raptor434 on 2011-11-19
i tried what you said and it gave me an error saying Authentication token manipulation error  then  it says password unchanged

---

### Post by MAFoElffen on 2011-11-19
> **Raptor434 said:**
> i tried what you said and it gave me an error saying Authentication token manipulation error  then  it says password unchanged
That error says the password files don't match... Please read the whole post before starting.

Look at this file --> /etc/passwd.  Make sure that user account is in there.

Then do 
```

pwconv

```That will recreate the shadow file from the users in the passwd file.

Or you could manually edit /etc/shadow and make sure the users match the user accounts of /etc/passwd. (They are different formats and do different things) 

The popular plan would be to backup the shadow file. Then recreate the shadow using pwconv. At that point, you could probably reset the password using passwd or manually edit the shadow file on that user's password with what I gave you...

If that doesn't work, check the permissions on the passwd file and make sure it has permission 2377. If this file doesn't have the right permissions and access rights, it will also throw that error.
```

ls -l /etc/passwd

```Your output should be similar to this
```

-rw-r--r-- 1 root root 2377 2011-08-19 14:38 /etc/passwd

```If it isn't go root, then reset with
```

chmod 2377 /etc/passwd                      

```

---

