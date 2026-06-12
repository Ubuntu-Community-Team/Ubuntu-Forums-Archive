---
title: "Ubuntu 10.04 sudo issues"
date: 2010-08-24
forum: Installation &amp; Upgrades
---

### Post by Legendman3 on 2010-08-24
Hey yesterday I was messing around with the terminal then I decided to sudo chmond -R myname the etc folder in ./ now when I use sudo for anything I get:

sudo: /etc/sudoers is owned by uid 1000, should be 0
sudo: no valid sudoers sources found, quitting

Halp! this is bad....:sad:

---

### Post by ajgreeny on 2010-08-24
Oh boy, what a mix up you got into!  What on earth were you trying to do?

If I assume your command was chmod (not chmond) I am surprised you ended up in that situation, as chmod is normally used for permissions, not ownership, which is chown.  Are you sure you did not get the command you show above wrong; did you use chmod or chown?

If you can be certain of the command you used last time, (should be in ~/.bash_history in your home folder) you may be able to change it back to where it should be with ```
sudo  chown -R root
```though I have to admit that it may end up with other problems that are not solved.

This, I think gives you a warning not to use terminal commands of that sort without knowing exactly what they will do, and not to play with permissions in file system folders.

EDIT:

I have just realised that you can not do that as you can't use sudo any more, so you will need to go into recovery mode at startup, and use the terminal to m,ake those changes with the cli.

---

### Post by Legendman3 on 2010-08-24
Yes thats the command in the little cammand thing can you give me some steps on how to undo it in recovery mode?

---

### Post by ajgreeny on 2010-08-24
> **Legendman3 said:**
> Yes thats the command in the little cammand thing can you give me some steps on how to undo it in recovery mode?
Sorry, but what is the command?  I am still a bit uncertain what command you actually ran in the terminal, and from which system or home folder you were running the terminal to get you to where you are now.

I don't want to make things worse than they are at the moment!

---

### Post by Legendman3 on 2010-08-24
The command was sudo chown -R jacob etc i did it from the ./ folder

---

### Post by ajgreeny on 2010-08-25
You could try recovery mode and running the command ```
chown -R root
```but that will mean that your home folder is also owned by root, not you, so after that, but still in recovery mode try ```
chown  -R jacob:jacob /home/jacob
```which should return ownership of you home folder/partition back to you.  Now reboot, and hopefully - -?

All this assumes you user name is jacob; change it if that is wrong.

If none of that works, then I think I would give up, backup all my personal home files on an external disk using the live CD, and simply reinstall; it's so quick to do and may save a great deal of time and hassle.

---

### Post by Legendman3 on 2010-08-25
When i select recovery mode in grub it comes up with a list what do i press so i can type the commands in?

---

### Post by spjackson on 2010-08-25
> **Legendman3 said:**
> When i select recovery mode in grub it comes up with a list what do i press so i can type the commands in?
It's "Drop to root shell prompt" or words to that effect, if I recall correctly.

---

### Post by ajgreeny on 2010-08-25
Yes, that's the one you need.

---

### Post by Legendman3 on 2010-08-25
Ok now that thats done its saying everytime i do a sudo it says "sudo: must be setuid root" Then I type in "setuid root" then it says "The program 'setuid' is currently not installed.  You can install it by typing: sudo apt-get install super" I then type "sudo apt-get install super". Then it says "sudo: must be setuid root". WTF? can i do sudo apt get in the recovery mode?

---

### Post by spjackson on 2010-08-25
> **Legendman3 said:**
> Ok now that thats done its saying everytime i do a sudo it says "sudo: must be setuid root" Then I type in "setuid root" then it says "The program 'setuid' is currently not installed.  You can install it by typing: sudo apt-get install super" I then type "sudo apt-get install super". Then it says "sudo: must be setuid root". WTF? can i do sudo apt get in the recovery mode?
Eeek! Earlier postings suggested that the problem was file ownership in /etc and subdirectories. This new error suggests that the fault is more widespread.
```
$ ls -l /usr/bin/sudo
-rwsr-xr-x 2 root root 148024 2010-06-18 22:07 /usr/bin/sudo
```You should see the file owned by root, group root and permissions as above. The 's' in the permissions is setuid. You set the setuid bit as follows:
```
$ chmod u+s /usr/bin/sudo
``` but you can only do that if you are the file owner. Changing file ownership automatically unsets the setuid bit. You will be able to fix this in recovery mode as before. However, in your shoes I would be concerned about what else is broken, and I'd seriously consider a re-install.

In order to use apt-get in recovery mode, you'd need to choose "Drop to root shell prompt with networking" (or similar).

---

### Post by ajgreeny on 2010-08-26
As I said in one of my recent posts to you, I think there will be no end of file ownership and permission problems following your original command, so I really think now is the time to backup everything and cut your losses and re-install.

It only takes about 20 mins to install, and then not too long to get your configuration back, so if I think about the time and heartache you have already suffered, I say go for it and put the whole saga down to a learning experience.

I imagine you won't do that again in a hurry!

---

### Post by Legendman3 on 2010-08-26
Actually I dont have much to loose anyways. well except my bookmarks but oh well ill find them back... ok this can be marked solved now just gotta find the install cd...

---

### Post by ajgreeny on 2010-08-26
You can still save your files plus all bookmarks etc etc by copying your home folder, including all hidden files and folders, to a USB drive.  After installing again, just copy them all back to your new home.

---

