---
title: "Root or sudo login"
date: 2006-02-20
forum: Installation &amp; Upgrades
---

### Post by Cth on 2006-02-20
Hello, I need to log in as root. in Ubuntu 5.10 Gnome. I read the HELp but not sure what it is telling me to do because I am very new to linux.

I would like to move files from my USB key to my etc/ppp/peers folder.
It is telling me to drop dead no way.

Anyone have a easy way to do this?**__**

Thanks..

Chris..:confused:

---

### Post by el3ktro on 2006-02-20
You can execute any command in the terminal as root by typing "sudo", e.g. when you want to copy some files you could type something like

sudo cp /media/usbstick /etc/ppp/peers

This will take the files from the USB stick and copy it to the destination dir with root permissions. You'll be asked for a password, and you have to enter YOUR password, root itself doesn't have a password.

Tom

---

### Post by Jedeye on 2006-02-20
Im just going to break down el3ktro's post for ya:

**sudo** - gives you root privileges
**cp **- copy paste command
**/media/usbstick** - location of usb drive
**/etc/ppp/peers** - location where usb drive content will be pasted to

if the command does not work for you go to /media/ and see if there is a different folder name in there that would be your usb drive.

you may have known all of this but figured it would hurt to post it anyway. Good luck!

---

### Post by jsestri2 on 2006-02-20
i hate to play the devil, but you could tell him how to set the root password...

sudo passwd root

its obviously not a great idea to run a lot as root, but every now and again typing sudo every command gets old.

---

### Post by taurus on 2006-02-20
Just do you know, you better know what you are doing when you log in as root directly because it will not tell you to drop dead no way.  Instead, you will find out you have a one sick machine (can't boot; can't log in, etc.) if you put in a wrong command...  ;)

---

### Post by Cth on 2006-02-20
Thanks Guys.

  I got it

\\:D/

---

