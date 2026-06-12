---
title: "Is this a bug in 21.10 ?"
date: 2021-11-17
forum: Installation &amp; Upgrades
---

### Post by janne-m-boman on 2021-11-17
Hello
not sure if this is a bug.. I'm trying out 21.10. in Virtualbox. I choose "install ubuntu" in the welcome screen (the one that says try ubuntu / install ubuntu).
It seems like that somewhere in between choosing the keyboard layout and first login screen the keyboard layout does not stay the same. Or maybe between choosing the keyboard layout and specifying the password. 

Because in the screen where you specify the username and pass, it's using the wrong keyboard layout.
I tested by typing "this is a question mark > ?" in the name field, and it's outputting "this is a question mark > _", clearly using the wrong keyboard layout despite me specifying the correct one just before.
I guess this leads to me specifying a password with a wrong keyboard layout, and then again in the login screen, failing to log in.

Link to some screenshots:
[https://drive.google.com/drive/folders/10cPHyZ50p8qHeVSvhXKy-YzUgqZBoTWy?usp=sharing](https://drive.google.com/drive/folders/10cPHyZ50p8qHeVSvhXKy-YzUgqZBoTWy?usp=sharing)

What do you think?
[IMG]https://drive.google.com/file/d/10YyL6yU6ItiqOd3pLEQB-gEjK8cmbCha/view?usp=sharing[/IMG]
[IMG]https://drive.google.com/file/d/10YyL6yU6ItiqOd3pLEQB-gEjK8cmbCha/view?usp=sharing[/IMG]

---

### Post by sudodus on 2021-11-17
I suggest that you try Ubuntu 20.04.3 LTS. It is more debugged and polished, and has a much longer life (supported until April 2025 while 21.10 is only supported for 9 months. And I know that 20.04.3 LTS is well tested in VirtualBox, it should work out of the box. See also [this link](https://askubuntu.com/questions/1018033/ubuntu-development-version-how-to-participate-or-how-to-get-a-smooth-ride).

You can start by testing it live, 'Try Ubuntu', and install from there if you wish. When starting the live session you can also set the language and check that it works before starting the installer.

[hr][/hr]
After getting familiar with Ubuntu 20.04.3 LTS you can 'Try Ubuntu' again with 21.10 and maybe succeed, maybe fail, but in a more informed way. I don't know how it works in VirtualBox, but if you are lucky, someone who knows will see this and share the experience with you.

---

### Post by janne-m-boman on 2021-11-17
Thanks. I've been using the LTS for some time now. I was just taking 21.10 around the block to see what's new, so this is not critical. But having a potential bug affecting password hmm.. "consistency" just feels like a big hole in the ground :D

---

