---
title: "how to install a driver which is a shell script (.run) file?"
date: 2008-07-05
forum: Installation &amp; Upgrades
---

### Post by sonaural on 2008-07-05
the driver for my ati graphics card on the system didn't work (it actually made the graphics worse) so i went to the website and downloaded the right driver but the system can't read the language the driver is in (compressed?).

it has a .run ending and in the properties it's called a shell script file

---

### Post by sdennie on 2008-07-05
If you are sure you trust the file, you should be able to install it with:

```

sudo sh name_of_the_file.run

```

---

### Post by sonaural on 2008-07-05
it asked me for my sudo password?  i've actually never used sudo before.  i tried my administrator pass and it didn't work.

---

### Post by sdennie on 2008-07-05
The sudo password should be the same as your login password if you are the only user on the machine.  You won't see the password being displayed as you type it but, it should work.

---

### Post by falcon61102 on 2008-07-05
Use the your user password that you logged into Ubuntu with.  It's just like when you get the GUI window asking if you are sure you want to proceed because it's an administrator task.

---

### Post by sonaural on 2008-07-05
so i got the password thing to work, i'd typed it in twice when i saw no characters appear.  the message i got , however, said "can't open ati the driver"

as i said, i've never used sudo.  is it possible i need to install it?

---

### Post by falcon61102 on 2008-07-05
No you don't need to install sudo... the command sudo is basically telling Ubuntu that you plan on running things as an administrator.  The sudo command worked.  What didn't work was your driver.  Is that the correct driver version for the hardware you have?

---

### Post by BLTicklemonster on 2008-07-05
Where is the driver right now? Desktop?

cd /home/yourname/Desktop

sudo sh filename.run


(you know what I do? When I get one of those files with names like "ati-4.566.8_oh_whoo_dee_doo-megamonster.run I just right click and rename the danged things to "ati.run" and be done with it. God all mighty I hate those stinking long names!!!)

---

### Post by sonaural on 2008-07-06
yes.  i'm 100% sure of what kind of graphics card i havfe.  i had someone show me how to open a terminal that would ask the computer what specific card is installed.

i've heard that ati has very poor linux compatability.  oh well...

---

### Post by sonaural on 2008-07-06
the driver is on the desktop,
how do i insert the paragraph break between
cd /home/yourname/Desktop
and
sudo sh filename.run
without activating the first command line?  when i tried just the first command line it claimed no such file or directory.

also is there supposed to be a character space between cd and /home/? i tried both and both turned up the no such file objection.  i guess the answer to my first question would solve this.

---

### Post by BLTicklemonster on 2008-07-06
```
cd /home/yournamehere/Desktop
```

```
sudo sh filename.bin
```

copy and paste into terminal one at a time. use arrow key to move cursor to text you need to retype, retype, and go for it. yes, there's a space between cd and /home


Or, have you tried using the restricted drivers?

Applications, add/remove, at top, Show: All Available Applications

then scroll down to Ubuntu Restricted Drivers

Perhaps that will be an easier way?

---

