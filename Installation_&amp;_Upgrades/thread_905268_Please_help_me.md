---
title: "Please help me"
date: 2008-08-30
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2008-08-30
I have installed an Bea aquaLogic server, then sudo chmod 777 -R on the installation directory.
Then I restard my computer I am geting the following error message.
User's $HOME/.drmc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions.User's $Home directory should be must be owned by user and not writable by other users.
I think because of it I can't go to the internet.
tks

---

### Post by arkara on 2008-08-30
```
chmod 644 ~/.drmc 
```

---

### Post by BiggoCharley on 2008-09-28
After an upgrade to Hardy I am getting exactly the same error message on start-up. When I try to change permissions to 644 this is what I get:
chmod: cannot access `/home/charley/.drmc': No such file or directory"
charley@ubuntu3:~$ 
When I search for the file it is there and it is owned by me and is in the home directory.  What gives?   Any ideas?

---

### Post by WWSmith36 on 2008-09-28
Try this please
```
sudo chown [username] $HOME/.dmrc
sudo chmod 644 $home/.dmrc
```

---

### Post by BiggoCharley on 2008-09-28
Thanks for the response.
I tried the following with the results shown:
charley@ubuntu3:~$ sudo chown charley $HOME/.dmrc
[sudo] password for charley: 
charley@ubuntu3:~$ sudo chmod 644 $home/.dmrc
chmod: cannot access `/.dmrc': No such file or directory
charley@ubuntu3:~$ sudo chmod 644 $home/charley/.dmrc
chmod: cannot access `/charley/.dmrc': No such file or directory
charley@ubuntu3:~$ 
But as I said earlier --the file is there in the /home/charley directory. (No "HOME" --in caps --directory that I can find.

---

### Post by WWSmith36 on 2008-09-28
sorry

sudo chmod 644 $HOME/.dmrc

---

### Post by BiggoCharley on 2008-09-28
I tried again.  Here is what the terminal screen looked like after I entered the command:
charley@ubuntu3:~$ sudo chown charley $HOME/.dmrc
[sudo] password for charley: 
charley@ubuntu3:~$ 

I then rebooted and the same error message came up on the login screen.

I really appreciate your taking the time on this.

---

### Post by BiggoCharley on 2008-09-28
Forgot to mentiion that I also tried this:
"charley@ubuntu3:~$ sudo chmod 644 $HOME/.dmrc
[sudo] password for charley: 
charley@ubuntu3:~$" --with the same results.

---

