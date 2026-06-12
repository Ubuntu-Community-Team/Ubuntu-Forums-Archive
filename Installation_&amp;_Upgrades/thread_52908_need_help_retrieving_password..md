---
title: "need help retrieving password."
date: 2005-07-29
forum: Installation &amp; Upgrades
---

### Post by Omnios on 2005-07-29
Hi I gave a friend a Ubuntu cd a few months back and he could not getting going becuase he had a murcery vidie card. Anyways he realy wants to try Ubuntu so he ripped out the video card and is using the onboard video chip. Unfortunatly he has seemed to forgoten the user name and password from all those months ago. 

 Is there anyways of retrieving the username and password? Personaly I think he is going to have to reinstall it but would be nice if it can be retrieved.

---

### Post by phen on 2005-07-29
as linux is a real multiuser system, retrieving of a password will be like in hacker movies....

i think you really have to reinstall... but there is the possibility of using the single user runlevel. don't know how to get into it - sorry. maybe search for it. it should be possible to boot into i think...

cheers,

kai

---

### Post by AgenT on 2005-07-29
WARNING: This is all from memory and could be a little incorrect. Others may be able to fill in the gaps. And when you need to type a command, that means in a terminal or console (and without the double, or " ", quotes)...

You should be able to easily change the password. Well, maybe not easy (guess that depends if you find this easy or not). What do you need to change exactly? The administrator user's username and password or just an ordinary user? And do you have the username/password for a user that has administration rights? If so just login as an administrator and execute the command "ls /home/" to find out the username. Then change the password for that user using "usermod -p <your new password> <username>" (without the < >). If you cannot login into the system with administration rights...

Your best bet would be just to use a LiveCD of some kind (not sure if Ubuntu's LiveCD would be the best for this, but you could try it). With this, to find out the username will be easy. Just do an "ls /home/" as mentioned above. Your LiveCD should have you as root or something that at least has read access to everything.

If you cannot figure out the password after having the username, you could use chroot. chroot is amazing and hopefully works properly on the Ubuntu LiveCD (since Ubuntu likes to use sudo instead of root). You would first have to figure out (easily done) what the root partition of you installation is (/dev/hda1 if all you have is Ubuntu installed, that is the default) and type "chroot /dev/hda1". Now you are hopefully in the system and have administration rights. Just follow the instructions above about using usermod. After you are done, make sure to exit (either using "exit" or "quit", not sure which) properly from the chmod and properly shutdown (by using the LiveCD's shutdown command) the computer.

---

### Post by trigg on 2005-07-29
[QUOTE=Omnios]Hi I gave a friend a Ubuntu cd a few months back and he could not getting going becuase he had a murcery vidie card. Anyways he realy wants to try Ubuntu so he ripped out the video card and is using the onboard video chip. Unfortunatly he has seemed to forgoten the user name and password from all those months ago. 

 Is there anyways of retrieving the username and password? Personaly I think he is going to have to reinstall it but would be nice if it can be retrieved.[/QUOTE]

Getting the password isn't easy, but changing the password is.  

Step 1:  Get a live-cd - the Ubuntu Live-CD or any number of other distributions . . . shouldn't really matter

Step 2: Boot the Live-CD

Step 3:  Get root console shell open (usually just open  up a terminal window and type )

```

su -

```

Step 4: Find out which partition the root ("/") and home ("/home") directories are located
 
```

cfdisk /dev/hda

```

 (could be hde or hdg or whatever your HD is)  if you don't have cfdisk, just use fdisk and the command "p" will print the partition table


Step 5:  (We will assume that the Ubuntu linux root partition is on /dev/hda2 and the home directory is on /dev/hda3) 

```

mkdir /mnt/ubuntu
mount /dev/hda2 /mnt/ubuntu
mount /dev/hda3 /mnt/ubuntu/home
chroot /mnt/ubuntu /bin/bash
ls /home       #(this will list the directories which correspond to usernames)
passwd user  #(HERE IS WHERE YOU SET THE PASSWORD FOR THE USER YOU WANT!)
exit
umount /mnt/ubuntu/home /mnt/ubuntu

```

okay, now your password is reset

You should be able to reboot and use your new password.  No reinstall needed.

---

### Post by BanskuZ on 2005-07-29
Boot linux in single mode. (add "single" in grub)

Then in console:
passwd username

And then of course, halt to shutdown.

---

