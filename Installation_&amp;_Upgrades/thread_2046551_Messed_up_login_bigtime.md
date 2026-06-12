---
title: "Messed up login bigtime"
date: 2012-08-23
forum: Installation &amp; Upgrades
---

### Post by Lloydb39 on 2012-08-23
1. Built a new machine
2. installed hard drive from another machinewith Ubuntu 11.10 on it.
3. Plugged in wireless adapter from same old machine.
Everything worked fine, then:
A. Updated to 12.04
B. Installed Samba and tried to join my Windows network
Now: Never could share because I didn't know the network password and now my new machine will NOT let me login. I have a loop. The screen goes black, prints a message I don't have time to see and goes back to login. I can log in as guest, but can't really do anything. (I can make changes in user accounts because it accepts my password as administrator so I know the password is right.)
I could reinstall but I would like to fix this. Anybody?

---

### Post by drmrgd on 2012-08-23
If, while at the login screen, you press 'Ctrl+Alt+F1", you can enter TTY1.  At that point you'll be asked for login credentials.  When you try to log in with the admin account (I guess the main account), do you get any error messages?  That might be a way to see what the error is in order to troubleshoot the problem.

---

### Post by Lloydb39 on 2012-08-23
Thanks. I just tried that, and it says the login is incorrect. (I also didn't know how to get out of TTY so I rebooted). In the meantime I uninstalled Samba to see if that would help. It didn't.I logged in as guest, went to terminal and did ls -l /home, which I read on another thread. It said no such directory!?

---

### Post by darkod on 2012-08-23
Are you sure you are trying with the correct username and password? The user can't simply disappear.

Was your /home maybe a separate partition on another disk? So when you moved this disk to the new machine, the /home partition remained in the old machine.

Don't forget, linux is case sensitive with everything, usernames, passwords, files, etc. Not only with password like windows usually is. You need to type the username exactly as it is too.

---

### Post by Lloydb39 on 2012-08-23
Thanks. My username is just my first name and it is what shows on the top of the screen when I switch users. It is also the only one besides guest. and the password is the one I've always used. The 1 TB hard drive is a single partition. I'm wondering if the fact that I used this drive and wireless adapter in another machine to access the network previously, is there a config file somewhere that maybe got confused because of the new motherboard? Just a wild guess...Is there a way to reset passwords?
Another thread talked about looking at .xsession log but I can't find one. Totally baffled.

---

### Post by darkod on 2012-08-23
The network shouldn't have anything to do with it, it doesn't even let you log in.
The swap of hardware also should not affect it, maybe it will want to install some driver once it's up and running, but I would expect that it lets you log in at least.

If you are absolutely sure you are using the correct credentials, I don't know what might be the problem.

---

### Post by Lloydb39 on 2012-08-23
Update: From TTY I typed username and password all in lower case and it took. But now what? I'm still in TTY (and guess I can leave by typing "exit")?

---

### Post by darkod on 2012-08-23
You can reboot with:
sudo reboot

Also starting the GUI should be like:
start x

but never tried that. :)

---

### Post by Lloydb39 on 2012-08-23
Well, went to gui and it still would not accept password. So back to terminal, it took password and I rebooted from there. Came back up with normal screen but STILL won't take password. Just for the hell of it I did ls -l /home and got:
dr -xr -xr -x 32 username username 4096
which is Greek to me

---

### Post by darkod on 2012-08-23
When you log in in terminal, it should enter in your Home folder by default. If you try:
ls

does it list the content of your Home folder?

Very strange. I'm no expert on permissions, but I don't see any w in the result of ls -l /home so it looks like you don't have write permission for your own Home folder. But I'm not sure if I'm reading that correctly.

---

### Post by Lloydb39 on 2012-08-23
It is missing the "w" which another thread says is critical, but doesn't explain how to fix it. (I appreciate your patient attempts to help.)

---

### Post by Lloydb39 on 2012-08-23
It is missing the "w" and another thread says this is critical but it does not tell how to fix it. Another proposed solution is to remove the .xautority and .xsession-errors file but I'm a little hesitant to do that yet. thanks for your patience.

---

### Post by steeldriver on 2012-08-23
Yes your home dir needs to be writeable by its owner (you) in order for an X session to start

Since you can log in at the virtual terminal AND you appear to be the owner, you should be able to fix that without sudo / root privileges, i.e.

```
chmod u+w /home/username
```If you still can't get a graphical login after doing that, check the ownership and permissions on your .Xauthority file

```
ls -l ~/.Xauthority
```and make sure that is also owner by you and writeable - it should be 

```
-rw------- 1 *username* *username*
```

You can remove ~/.Xauthority safely (it will be regenerated when you successfully login) if it is messed up

---

### Post by drmrgd on 2012-08-23
> **steeldriver said:**
> Yes your home dir needs to be writeable by its owner (you) in order for an X session to start

Since you can log in at the virtual terminal AND you appear to be the owner, you should be able to fix that without sudo / root privileges, i.e.

```
chmod u+w /home/username
```If you still can't get a graphical login after doing that, check the ownership and permissions on your .Xauthority file

```
ls -l ~/.Xauthority
```and make sure that is also owner by you and writeable - it should be 

```
-rw------- 1 *username* *username*
```You can remove ~/.Xauthority safely (it will be regenerated when you successfully login) if it is messed up

+1 to this!  

It looks like somehow you locked yourself out of your /home directory and this is causing all kinds of grief.  

I also wanted to follow up to say that if you want to switch back to the graphical TTY (i.e. the one with the graphical login screen you had before) without rebooting, you can use 'Ctrl+Alt+F7'.  There are usually 7 TTYs available to you, and (so F1 - F7 will work), and F7 is the usual graphical one running X.  Sorry to not be more clear on that!

---

### Post by Lloydb39 on 2012-08-23
The code I got back was -r-r-r
so I removed xauthority, rebooted.
At login I got Could not update ICEauthority file...
still locked out of my computer

---

### Post by drmrgd on 2012-08-23
The permissions for that might be incorrect as well, although I'm surprised that Steeldriver's first command didn't fix it.  You can try fixing that with:

```
sudo chmod 600 $HOME/.ICEauthority
```

Maybe to help see what's going on, can you post the output of:

```
ls -la $HOME
```

That will help to make to see if there are any other owner and permissions issues.

---

### Post by Lloydb39 on 2012-08-23
Additional ifo: finally got to see the error message screen. it says I have "broken pipe" and it couldn't write bytes -- whatever that means

---

### Post by Lloydb39 on 2012-08-23
ls -la $HOME showed a long list, at the top of which was drwxr for my username, which should be a good thing....

---

### Post by Lloydb39 on 2012-08-23
Houston, we have liftoff. I did a sudo reboot after that last chmod and my original screen came back, apparently all intact. It didn't even ask for a password. Thanks guys. You're the best.):P

---

### Post by Lloydb39 on 2012-08-23
Whoops. Spoke too soon. It looks good but it will do nothing. Ubuntu One crashed, Firefox is running, it says, but doesn't work. I cant save any text documents (I was going to save the system log) and so I have a screen I can do nothing with.... geez

---

### Post by drmrgd on 2012-08-23
We did a chmod to .ICEauthority, but it might also require a chgrp too.  That's sort of why I wanted to see a full list to be sure that the users and groups were correct on those files.  

If you do an ls -l $HOME/.ICEauthority and the group is not correct (let's assume that your group is the same as your username, which is often the case on home systems), you'll just need to run:

```
chgrp <username> $HOME/.ICEauthority
```

and that should fix it.  Also double check the other files - especially the hidden configuration files like ~/.mozilla for Firefox to be sure the user and group is correct for those.

---

### Post by steeldriver on 2012-08-23
drmrgd would there be any harm if the OP just hits the whole dir recursively with chown?

```
sudo chown -R *username*:*username */home/*username*
```I don't recommend changing permissions recursively but ownership within $HOME should be unambiguous I think?

---

### Post by drmrgd on 2012-08-23
I was thinking the same thing at first and almost posted that solution .  Just to be sure, I double checked my own /home director on this VM I have at work.  There were a few root owned files and directories in there.  I think they're innocuous and might even be specific to my setup or to this VM, but I wasn't sure.  So, that's why I suggested the long route.  Also, I thought I could catch something if I saw the permissions on the OP's whole /home folder, but we're still lacking that data.

To be honest, maybe a recursive chmod is the way to go.  I'll bet the stuff I have owned by root in my home dir is specific to my set up.

---

### Post by Lloydb39 on 2012-08-23
Guys, I appreciate it. I finally threw in the towel and installed 12.04 64-bit version, which has an added benefit of letting me use all 8 gigs of memory, as I understand it. It is still running but no hiccups so far. Anyway, I learned a lot from your answers. (I'm a bit concerned that Ubuntu "recommended" the 32-bit version, but we'll see....)

---

### Post by drmrgd on 2012-08-23
OH!  Heh, I didn't realize that you were having those memory issues from the other thread.  I totally forgot about that.  So, yeah, in that case a reinstall would be most beneficial.  Hope this works a little better for you!

---

