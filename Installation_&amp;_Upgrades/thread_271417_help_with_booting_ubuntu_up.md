---
title: "help with booting ubuntu up"
date: 2006-10-04
forum: Installation &amp; Upgrades
---

### Post by fox3 on 2006-10-04
hi just succesfully installed ubuntu fine.. i boot it up using grub and a text field comes up with loads of things, then it says username and pass so i log in and it says something like enter a command..

something like bash:command

and type a command <command> like that?

any ideas please help me thank you alot

add me on msn [email]jordan_fox271@hotmail.co.uk[/email] if you wanna speak there

---

### Post by whizbaby on 2006-10-04
Err, what exactly did you install? Server version? 
BTW a command prompt in terminal is (after logging in) normally

username@name_of_machine:~$>

If it doesn't look like this you probably didn't reach a usable state of the system.

---

### Post by fox3 on 2006-10-05
> **whizbaby said:**
> Err, what exactly did you install? Server version? 
BTW a command prompt in terminal is (after logging in) normally

username@name_of_machine:~$>

If it doesn't look like this you probably didn't reach a usable state of the system.


yes it does look something like this, all i want to do is get onto the actual linux how do i do this?

---

### Post by fox3 on 2006-10-05
it actually says username@ubuntu

please help i am really confused

when i go to my computer on windows, there is only 1 drive which is the c i dont see nothing for linux is this normal?

---

### Post by whizbaby on 2006-10-05
I asked about the server install because if so you wouldn"t have X (graphical interface) installed. Check if it is by typing
which startx
if it returns empty you don't have X and need to install. If it gives a path type
sudo /etc/init.d/gdm start
(if not directed automatically hit ctrl-alt-F7 to get to the graphics login)
If it doesn't start you have a problem with your graphics driver.
To install X

sudo apt-get install ubuntu-desktop

> **fox3 said:**
> when i go to my computer on windows, there is only 1 drive which is the c i dont see nothing for linux is this normal?

Windoze tries to ignore that other OS exist, so don't worry (there are some progs that you can download to see your linux)

---

