---
title: "Upgraded from Mandriva but..."
date: 2005-10-30
forum: Installation &amp; Upgrades
---

### Post by mikec on 2005-10-30
I'm not very experienced with Linux, but have spent some time trying to work with Mandriva. Had a lot of problems getting Samba to work. Anyway I've installed Ubuntu and it seems much better. However, I've got two questions that are probably really obvious, but I can't find the answers:

1. What is the default root password?
2. Bash in Mandriva supports the DOS type cd.. to move up a directory. What is the equivalent for Ubutu as this doesn't work.

:confused:

---

### Post by Joey French on 2005-10-30
If you moved from Mandriva, know this: Ubuntu uses "sudo", which means "superuser do", to access root priveledges. Don't type "su root" or anything, just "sudo", command, it will ask for the password you gave it when you set up the initial account during install. Is that where you are having trouble? I moved here from Mandriva, myself.

You should be able to cd through directories in the shell. Sounds strange. Do you mean you can't "cd" through directories?

---

### Post by mikec on 2005-10-30
I don't remember specifying a root password during installation. I can boot the machine in the debug type mode (without GNOME) and it boots up as root without needing a password. However, I can't move up a directory to get out of the root home directory. I tried cd.., but it doesn't do anything.

If I boot up normally and access bash through a terminal from GNOME I'm logged on in a user account and if I type su it asks for a password. What does sudo do?

---

### Post by Joey French on 2005-10-30
Gives temporary root priviledge. Sort of kicks you out after you do what you gotta do. Safeguard, I guess.

---

### Post by mikec on 2005-10-30
Okay, I'll try it.

How about the other question, how do I move up a directory?

---

### Post by derrick1985 on 2005-10-30
Like Joey said, Ubuntu doesn't use root by default, it uses sudo. The password for sudo is the one you gave the first user when installing. IF you want to, you can get root working in ubuntu using one of two commands:

sudo su

Gives you root privileges until you close the terminal.

sudo passwd root

Gives root user a password. Now, you can login to the root account in GDM.

Also, to go up a directory, the command is cd .. (notice the space between cd and ..)

Cheers, and happy Ubuntu'ing. Any more q's, don't hesitate. This forum is great for anybody, new and experiences linux users.

Derrick

---

### Post by cwf on 2005-10-30
I too wonder why 'cd..' didn't move me up a directory.  I learned that the only way to move up is to actually cd to that directory.

So in your case you want to go to the folder above /home/<user>   So you would type 'cd /home'.  Or to move to the root directory...'cd /'

Hope that helps.

CWF

EDIT:  derrick1985 answered the question as I was typing this up.  And he did a much better job I might add.  Oh well...I'm just a noob tryin to help out another noob!

---

### Post by mikec on 2005-10-30
Thanks for the help. I wasn't putting a space between cd and .., now I have it works fine.

Also I've successfully used sudo and I can set a root password etc... 
Isn't this a bit of a security loop hole if any user can become root?

---

### Post by derrick1985 on 2005-10-30
[QUOTE=cwf] EDIT:  derrick1985 answered the question as I was typing this up.  And he did a much better job I might add.  Oh well...I'm just a noob tryin to help out another noob![/QUOTE]

lol, sorry about that.

---

### Post by mikec on 2005-10-30
They are useful sorting out problems so quickly is a great help.:smile:

---

### Post by Joey French on 2005-10-31
> Isn't this a bit of a security loop hole if any user can become root?

Well, not really, because they will always have to give a password. So, in order to do any root tasks, they will have to sudo, and if they don't have the password, they can do nothing.

---

