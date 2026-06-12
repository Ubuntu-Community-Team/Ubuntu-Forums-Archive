---
title: "ubuntu 15.04 starting in version 219 emergency mode!"
date: 2015-10-24
forum: Installation &amp; Upgrades
---

### Post by avishek_arora on 2015-10-24
after updating ubuntu to 15.04 after some days i got this error message. 
my ubuntu is booting in emergency mode on the boot screen it says. 

```
starting version 219
welcome to emergence mode! After logging in , type "journalctl -xb" to view 
system logs, "systemctl reboot" to reboot, "systemctl default" or ^D to 
try again to boot into default mode
root@mydesktop:~#

```

it gives me root access to the terminal and when i try several command like sudo apt-get update i found that it's didn't able to connect to the internet.
when i use command systemctl default i got the graphical login screen then i enter my credentials and after some time it goes back to the terminal and says  
"Error getting authority: Error initializing authority: could not connect: no such file or directory ( g-io-error-quark, 1)
hangup"

i don't want to install a fresh copy of ubuntu. i have access to all my file via root terminal but graphical interface is not working i don't know why.
please suggest me a way to fix this problem without installing a fresh copy of ubuntu.

---

### Post by dino99 on 2015-10-24
when you have done the installation, your user & password have been set by yourself. You also get administrative rights via 'sudo'
So you might login with your user; but xauthority complaint, meaning the installation has not been made as expected.
You can get a newer .Xauthority file if you delete the actual one : > sudo rm ~/.Xauthority (copy/paste that command into a terminal)
On the next login the deleted file is recreated by the system

---

### Post by avishek_arora on 2015-10-24
it did follow what you said and gave command sudo rm ~/.Xauthority
it's says 
```

rm: canot remove /root/.Xauthority: No such file or directory

```

any other suggestions ??

---

### Post by Dennis N on 2015-10-24
Is this .Xauthority file you are planning to remove in your home directory? Using sudo with ~/ is apparently being interpreted as root user's home directory. I suggest not using this shortcut notation. Instead (suppose your user name is avishek) try first without sudo: 

```
rm /home/avishek/.Xauthority
```

and if that fails (probably meaning you don't own it), try it again with sudo in front.

[I]Info:
The /root directory is the home directory of the root account. It is also referred to as the root user's home directory (and not as the root directory). 
[/I]

---

### Post by avishek_arora on 2015-10-24
i also did replaced it with my home directory path. still it says No such file or directory.

---

### Post by Dennis N on 2015-10-24
Have you verified that it is really missing?

cd to your home folder, run this command and check the output (my output shown):

```
[dmn@Sydney ~]$ ls -la .Xauthority
-rw------- 1 dmn users 51 Oct 24 11:38 .Xauthority

```

If it is missing, dino99 says it will be recreated on next login. If he is wrong, you need to find out how to generate a new one.

---

