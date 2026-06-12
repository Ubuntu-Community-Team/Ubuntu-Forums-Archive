---
title: "strange user behavior after upgrade"
date: 2005-10-17
forum: Installation &amp; Upgrades
---

### Post by ackattack on 2005-10-17
I did a fresh (reformat) i386 install on and AMD64 system from the CD... during the "expert" install I set up both the root password and a default user (I used "shadow passwords")

Now, no programs which require root priviliges will run.  Example, synaptic asks for the root password and then does nothing.  From a terminal, running "sudo apt-get" asks for the password and then does nothing.  

The only way I can get anything administrative to run is from a command line root shell, which still works (i.e. "su" still works, and running programs from within the "su" works fine, but "sudo ...." doesn't)

I'm guessing something about my default user account is set wrong, but I'm too much of a newbie to figure it out.  I just want it to work like before!

---

### Post by dakira on 2005-10-17
Hi,

this is happened to me, too when I used expert install. I think the problem is that usually root is deactivated. But not if you use expert install. Also if you do that the sudoers file is not correct.

You have to do the following:
```

sudo
users-admin &
```
to open the users and group manager. No create a group called "admin" and add yourself to this group. When your done close the users-admin.

Go back to the shell and set your favourite editor and add a missing line to the sudoers file.
```

# assuming you are still root
# the next line picks the editor, use what you want
export EDITOR=/usr/bin/gedit
visudo
```

At the end of the file add this line:
```
%admin  ALL=(ALL) ALL
```

That's it.

---

### Post by ackattack on 2005-10-17
[QUOTE=dakira]Hi,

this is happened to me, too when I used expert install. I think the problem is that usually root is deactivated. But not if you use expert install. Also if you do that the sudoers file is not correct.
[/QUOTE]

Thanks.  I just reinstalled using the normal (non-expert) and everything is now fine.  But it seems like the expert install is a bit farked.  I need to figure out how to send a bug report...

---

### Post by dakira on 2005-10-18
[QUOTE=ackattack]Thanks.  I just reinstalled using the normal (non-expert) and everything is now fine.  But it seems like the expert install is a bit farked.  I need to figure out how to send a bug report...[/QUOTE]

I'll send that bug report. The problem is exactly what I described above. In expert mode the root user is not deactivated (maybe on purpose) and the user you create during installation is not added to the sudoers file. I also have the feeling that some automatic configuration scripts (i.e. for X) don't work as smoothly as in non-expert install.

---

### Post by Bill Statler on 2005-10-18
I see the same bug with a slightly different cause. I installed Hoary in "expert" mode a few months ago, and the root user was active. Today I upgraded to Breezy using aptitude and the (mounted) DVD ISO file. It went fairly smoothly but I am in the same situation as ackattack: no sudo, no root login, but su does work.

Thanks for the explanation, dakira -- I'd be really stuck now without it.

---

### Post by Bill Statler on 2005-10-19
Okay, I got things fixed but with a few differences from what dakira suggested above. I couldn't edit users/groups with users-admin because I couldn't use sudo to start it.  (Starting with su doesn't seem to work.)  I also couldn't use gedit from su to edit sudoers.

Here's what does seem to work:

Go to a text-only login by pressing ctrl-alt-F1, and login as root.

OR

Open a terminal window, type "su -", and login with root's password.

The sudoers file must be edited using "visudo".  But first, tell visudo what editor to use, otherwise you'll probably get vi, and this is not the time to learn vi.  Type this:

```
export EDITOR=nano
visudo
```

You'll now be editing sudoers using nano.  At the bottom of the file, add a line to give yourself permission to use sudo:

```
myusername   ALL=(ALL) ALL
```

Exit and save.

If you're in the ctrl-alt-F1 terminal window, type "logout", then hit ctrl-alt-F7 to return to your GNOME session.

That ought to fix things so that you (at least) can use sudo.  Now, if you want, you can do like dakira suggested and run users-admin, make yourself an admin group, put all your trusted users in it, and then re-edit the sodoers file to give the entire group sudo rights.

---

### Post by dakira on 2005-10-19
Okay, I forgot that it's not possible to use sudo when sudo is the problem and doesn't work ;) stupid me.

Anyway.. if you do it your way then when you're done you should do what I suggest above. Add a group "admins" and add yourself to that group). After you did that remove the line from sudoers with your username and replace it with the %admins... I suggested above.

After that you are back to what it should be like in ubuntu. Now if you want another user to be able to "sudo" you only have to add him to the group admins.

---

### Post by yamadatroy on 2006-01-11
I am so glad that I found this post.  I was having the same problems after installing Ubuntu 5.10 using expert mode.  I had to install using expert mode because DMA does not seem to load properly in Ubuntu by default so the regular install kept failing. ([http://ubuntuforums.org/archive/index.php/t-81600.html)](http://ubuntuforums.org/archive/index.php/t-81600.html)).
Thanks for help with the sudo problem. :)

---

