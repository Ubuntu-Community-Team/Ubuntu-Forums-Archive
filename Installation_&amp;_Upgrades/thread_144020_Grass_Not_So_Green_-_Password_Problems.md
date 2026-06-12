---
title: "Grass Not So Green - Password Problems"
date: 2006-03-13
forum: Installation &amp; Upgrades
---

### Post by Jose Catre-Vandis on 2006-03-13
Took the plunge, installed Ubuntu!

Used the Expert setting, which asked for a root password, and then a username and password. All of these delivered.

Boots into Ubuntu fine, and can login with username/password.

However trying to do anything "administrative" things don't go so well. 

e.g. System > Administration > Networking asks me for a password.

Have tried all three variants, the "root" password, the "user" password (which I can log in with) and blank. No success with any of these.

Similarly when trying to use a sudo command (e.g. apt-get) in terminal, I get my user is not in the sudoers file and is being reported.

Checked question.dat in /var, which tells me of a root password mismatch? and no sign of a password for user.

Where have I gone wrong, or what do I need to do to fix this? Seems a shame to fall at the first hurdle! :(

---

### Post by kaamos on 2006-03-13
Did you have a specific reason to choose expert install?

---

### Post by Jose Catre-Vandis on 2006-03-13
wanted to avoid overwriting data on my one but many partitioned disk, in order to keep files and XP

---

### Post by kaamos on 2006-03-13
The normal install has manual partitioning as well, so I suggest you do that. I don't know how well the expert install and root account works with ubuntus sudo-centered model.

---

### Post by engla on 2006-03-13
I have absolutely no knowledge about expert mode install.

But it sounds like you created a root user and a "user" user with different passwords, and that the user is not in the sudoers file by default.

That means you have to add the user to the sudoers file yourself.
I don't know too much about that, but you basically type
su
<type in the root password>
visudo <or anything else needed to setup sudo>

---

### Post by richbeales on 2006-03-13
to make sudo work, add the following to /etc/sudoers

i.e.
su
<enter root password>
pico /etc/sudoers

add the line:
myusername   ALL=(ALL) ALL

to the end of the file, replacing myusername with your own username.  I'm not saying this is the best or most secure way of doing things, but it works for me!

---

### Post by aysiu on 2006-03-13
Don't do an expert install unless you're an expert.

Intermediate and beginner users should do a normal install.

---

### Post by Jose Catre-Vandis on 2006-03-13
Thanks to engla and richbeales.

Can do the edit in terminal window, but how to save the sudoers file?

OK found the asnwer to this

[http://www.ubuntuforums.org/showthread.php?t=143461&highlight=sudoers+save](http://www.ubuntuforums.org/showthread.php?t=143461&highlight=sudoers+save)

---

### Post by Jose Catre-Vandis on 2006-03-13
[QUOTE=kaamos]The normal install has manual partitioning as well, so I suggest you do that. I don't know how well the expert install and root account works with ubuntus sudo-centered model.[/QUOTE]

Thanks for the advice Kaamos, might well have to try this!:)

---

### Post by Jose Catre-Vandis on 2006-03-13
[QUOTE=richbeales]to make sudo work, add the following to /etc/sudoers

i.e.
su
<enter root password>
pico /etc/sudoers

add the line:
myusername   ALL=(ALL) ALL

to the end of the file, replacing myusername with your own username.  I'm not saying this is the best or most secure way of doing things, but it works for me![/QUOTE]

Great got it working, so it appears at present no need to "go back" and reinstall "standard". What impact on security does this have, if any?

---

### Post by Jose Catre-Vandis on 2006-03-20
Now moved onto Dapper Flight 5

Slowly getting configured :)

---

