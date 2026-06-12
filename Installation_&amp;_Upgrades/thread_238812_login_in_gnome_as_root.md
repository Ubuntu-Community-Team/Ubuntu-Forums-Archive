---
title: "login in gnome as root"
date: 2006-08-18
forum: Installation &amp; Upgrades
---

### Post by a133x on 2006-08-18
I would like to login in gnome as root user, but my root user and pass does not work at the login screen. Is there a way to make it work because I am constantly anoyed to enter the password all the time and I cant even do certain things like writing to a usb stick because I dont have wirte permission. If I would be root than I could do all this things.

---

### Post by BitTorrentBuddha on 2006-08-18
Doing so is a very bad idea and is disabled by design. I believe there's a way to enable it, but it is highly recommended not to, have you tried instead using sudo or sudo -s -H?

---

### Post by a133x on 2006-08-18
Yes, thats what I am doing all the time, but I am limited all the time to things that I can do from the terminal. I know it is not recommended to login as root but I will take my chances, I have run many linux os's from root for a long period of time and no harm was done. If anyone knows how I could login as root I would greatly apriciate it. Thank you for the reply BTB

---

### Post by BitTorrentBuddha on 2006-08-18
If you truly insist on logging in as root and you understand what you're about to do, you can enable it by going under System -> Administration -> Login Window under the Security tab enable "Allow local system administration login"

---

### Post by givré on 2006-08-18
Be carfull dude,
You're going to reject the secure linux model for the unsecure windows model, are you sure you really want that.

---

### Post by a133x on 2006-08-18
> **givré said:**
> Be carfull dude,
You're going to reject the secure linux model for the unsecure windows model, are you sure you really want that.


Ok, very true, I solved the problem that botherd me most so I whont change to the unsecure mode :), but thank you very much for telling me this, maybe I will need it in the future.

---

### Post by Izzy25 on 2006-08-19
is there any way to open file in the File System without them being read only im always trying to configure files and theyre read only so theres no way to save them im trying to setup up my printer and have to add some lines to a file in /etc but i cant save the file heres the error message [http://i42.photobucket.com/albums/e315/Izzy25323/error.jpg]("http://i42.photobucket.com/albums/e315/Izzy25323/error.jpg")

---

### Post by Izzy25 on 2006-08-19
nvmd i got my printer working i installed the printer in root login i guess ill be having to swith between root and my username to make changes or is there a way i can get all those priviliges?

---

### Post by Niloc on 2006-08-19
Excuse me butting in but I am a complete newby both to Linux and this forum. Can someone tell me what or who is a 'root'! I am trying to mount my memory stick and it keeps telling me that 'only root can do that' where is root?

---

### Post by Izzy25 on 2006-08-19
i am a newbie to but from what i know root is the admin wich gets total control to login as a root you have to set a password first by running this in terminal
> sudo passwd root
(your own password first...)
(root password...
(root password again...)

and then you do this to enable root in login 
> System -> Administration -> Login Window under the Security tab enable "Allow local system administration login"

ive read that it is not recommende or not safe to run in root but i did it to install my printer and then logged back on as my username and my printer works good in my account so i would suggest to install what you need then move verything back to how it was. 

you can try this or get some info from a more advanced user i barely have about 40 hrs workin on linux but this worked for me so maybe you can try it

---

### Post by givré on 2006-08-19
Yeah that's not really safe, and you can do everything you want from command line if you want to edit file with root access. It's as easier as
```
sudo gedit /<name of the file>
```
and remember that TAB for autocompletation is your friend.

There is also a way to be able to edit file with root access from nautilus. with nautilus-action. But last time that i try it, automatix was able to add that. Have a look there [www.getautomatix.com](www.getautomatix.com)

---

