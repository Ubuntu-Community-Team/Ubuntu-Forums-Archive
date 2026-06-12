---
title: "Password failure after new install"
date: 2014-02-23
forum: Installation &amp; Upgrades
---

### Post by pcal on 2014-02-23
Hi guys,

Just spent hours helping my Dad with system problems. He had a motherboard failure that resulted in a new PC. The HDD from the old machine got swapped into the new machine in the hope of getting it working. It sort of did, but ran into regular crash and freeze problems.

I booted his new machine from a live 12.04.4 USB and discovered most of the HDD was empty (ie he didn't use a whole lot of space!). So, I shrunk the root partition, and created a new partition for /home. From the live session, copied the entire /home folder into the newly created and formatted partition, and reinstalled v12.04.4 into the root partition. It is an Ubuntu only machine - so no windoze to worry about...

From the install wizard we set the mount point for the /home partition, created his user account with the same username and password that had existed originally, and selected the option to not ask for the password on boot, but just go directly to the desktop.

After a great deal of watching nothing much happen, the installation was complete. However, not only does the login screen still ask for his password, but it won't accept it when he enters it. He can log in with the Guest session - and the system seems to be working OK - but can't access any of his files etc from that environment.

Can anyone suggest why his password is failing to be recognised? He has already tried all the upper/lower case variations and typos that he can conceive of to no avail...
More importantly, are there any words of wisdom that may restore access to his user account?

Thanks in anticipation,

Pcal

---

### Post by steeldriver on 2014-02-23
It's probably to do with the ownership of the copied /home files - just creating a user with the same *name* as before doesn't guarantee that the numeric UIDs used by the filesystem get sorted out

Try logging in at one of the CLI virtual teminals (Ctrl-Alt-F1 thru F6) and then reporting back with the output of

```
ls -al /home
```

---

### Post by lets on 2014-02-24
Hi steeldriver
I have proceeded as above and the output was as follows I hope I type it in correctly.

user@user-desktop:~$ ls -al /home
total 64
drwxr-xr-x  5   root  root     4096   Feb  24  08:03.
drwxr-xr-x 24  root  root     4096   Feb  23   21:36..
drwxr-xr-x 46  user  user   36864   Feb  24   21:17 user
drwx------  2  root  root   16384   Feb  23   18:33 Lost+found
drwx------  4  root  root     4096   Feb  23  19:01.Trash-0

Hope this helps! Can you tell me how to exit the tty screen without shutting down the computer?
Thanks
lets

---

### Post by Bucky Ball on 2014-02-24
Yes, well it's not as easy as simply copying the info and calling the partition /home. Try [THIS]("http://www.psychocats.net/ubuntu/separatehome#makepartition"), [THIS]("http://www.maketecheasier.com/move-home-folder-ubuntu/") and the many clues [HERE]("https://duckduckgo.com/?q=move+%2Fhome+to+partition+ubuntu").

When you say you copied all the data from the /home directory to the new partition, did you also copy the hidden files and folders? 

A much easier way of going about this is to leave the /home directory exactly where it is, copy your personal data to another partition called whatever you like, as you have done, delete what is in the original /home and create symlinks in the original /home partition to the copied folders on the new partition. Easy. It goes like this:

Create a symlink:
[http://www.herikstad.net/2009/07/creating-symlink-in-ubuntu.html](http://www.herikstad.net/2009/07/creating-symlink-in-ubuntu.html)

```
ln -s 'location to link to' 'name of symlink'
```

So, consequently, you may have something like this:

```
ln -s /media/newpartition/Video /home/user/Video
```

This will create a symlink inside the old /home directory to the folder /Video on the new partition. You need to edit with your own user and paths, naturally.

This way, all your hidden folders/files, which are all your config settings and other settings to do with your installed apps and setup, remain where the system knows they are and your personal data is off the / partition.

---

### Post by steeldriver on 2014-02-24
> **lets said:**
> 
Hope this helps! Can you tell me how to exit the tty screen without shutting down the computer?


Key combo Ctrl-Alt-F7 should get you back to the GUI screen

Your directory ownership looks OK btw so like Bucky Ball says we would need to dig deeper (possibly into the copied "dot files") to find the issue

---

### Post by pcal on 2014-02-24
Thanks for the helpful advice offered for Dad's problem. I will note the alternative methods suggested and look into them if ever I need to perform this operation again... but as the re-partition and format has already been done in this case it is too late to consider alternatives.

If I have inadvertently failed to copy any files (not sure that is the case - but if I have) then that is a separate problem I'll need to sort out later.

As I understand it, since we have done a complete fresh installation in the root partition, even if there were files missing in the /home partition, the installation wizard should have recreated them. The issue isn't that user files are missing, but rather that the system won't boot into the user account at all. The fact that Dad was able to log into the tty screen as he was asked to do, proves to my mind that both his username and password were correctly entered into the new installation.

So, if his credentials work at the tty screen login, why do the same credentials not work to log into the user account? And why are the credentials being sought at all when the system was told to go directly to the desktop on boot?

Unfortunately, Dad's place is about an hours drive from here and I can only get down there intermittently. He is proficient with Firefox, Thunderbird, Gimp and the like, but the underlying OS is still deep black magic to at least some extent (it is only marginally less deep for me!). His motivation to solve the problem is intense, but please keep any suggestions at beginner level.

Thanks in anticipation.

---

### Post by Bucky Ball on 2014-02-24
What happens when he logs into a terminal? Is it a blinking cursor? If so, try:
```

sudo service lightdm start
```

That might get us to a desktop for further sniffing.

---

### Post by lets on 2014-02-24
the result was.

[sudo] password for user:
start: Job is already running: lightdm
lets

---

### Post by pcal on 2014-02-24
> **Bucky Ball said:**
> 
That might get us to a desktop for further sniffing.

I believe that the Guest account still logs in ok, so a desktop with guest access rights at least is available...

---

### Post by lets on 2014-02-24
yes that is correct
lets

---

### Post by Bucky Ball on 2014-02-24
> **pcal said:**
> I believe that the Guest account still logs in ok, so a desktop with guest access rights at least is available...

I'm aware of this, but the guest account will probably have limited permissions and it may not be possible to do much to fix the problem using a guest account. More desirable to get in with admin level permissions. The guest probably won't have them. ;)

---

### Post by pcal on 2014-02-26
> **Bucky Ball said:**
> What happens when he logs into a terminal? Is it a blinking cursor? If so, try:
```

sudo service lightdm start
```

> **lets said:**
> the result was.

[sudo] password for user:
start: Job is already running: lightdm
lets

Are there any other options to get the user desktop open?

---

### Post by Bucky Ball on 2014-02-26
```
sudo service lightdm stop
```

... and then try the other command again?

```
sudo service lightdm start
```

---

### Post by lets on 2014-02-26
followed above and on start
"lightdm start/running, process 2068"

it then went to the login page of the desktop but still would not accept the password requested!

lets

---

### Post by steeldriver on 2014-02-26
I can't remember whether it's you or the OP (pcal) who was originally using auto-login - that may be a factor

Basically if GUI login is not working but CLI login (at one of the Ctrl-Alt-F*n* virtual terminals) is, then that means there's nothing wrong with your password but something is preventing your desktop session from starting. In cases where you've copied an old home dir the first thing to check is that the ownership of the home dir and all its contents corresponds to the 'new' user. If you checked the top level home dir and that's OK, then also check

```
ls -l ~/.{ICE,X}authority
```

(after logging in at Ctrl-Alt-F1 as before). Next would be to check disk space.

---

### Post by lets on 2014-02-26
followed above

"-rw------- 1 root root  135630 Feb 23 17:08 /home/user/.ICEauthority
-rw------- 1 root root          0  Feb 23 17:30  /home/user/.Xauthority"

this is the result
lets

---

### Post by steeldriver on 2014-02-26
OK so try

```
sudo chown $USER:$USER ~/.{ICE,X}authority
```

Then switch back to tty7 (Ctrl-Alt-F7) and try again logging in to the GUI

---

### Post by pcal on 2014-02-26
Recognising that I'm not the expert here, would it be helpful to create a new user account? 

sudo adduser username

(substituting username for some new account name)

This would potentially create a new working login so dad could at least start using his new computer, albeit with a new username. It may also cast some light onto the cause of the issue (ie. if the new account suffers the same problem, then the issue had nothing to do with the copied /home folder. )

Worst case : If the new account works and the old one never does, then at least the user files from the old account can still be copied into the new account and the ownership issues sorted out.

---

### Post by lets on 2014-02-26
still will not accept password!
lets

---

