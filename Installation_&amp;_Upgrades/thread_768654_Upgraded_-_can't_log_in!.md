---
title: "Upgraded - can't log in!"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by visctrix on 2008-04-26
Having done a completely fresh install of Gutsy (and getting rid of Windows), this time I thought I'd upgrade the simplest way - from Update Manager.

Now I can't log in as visctrix (although I can log in using my girlfriend's account).

I've tried to reset my password at the root shell prompt in recovery mode, but that had no effect. Is this something to do with my /home being on a separate partition?

Edit - no, because when I log in as my girlfriend I can see home and the visctrix desktop etc...
 
TIA

---

### Post by ibutho on 2008-04-26
Can you login to the command line as the user visctrix (at the login screen do CTRL-ALT-F1 and login to the terminal).

---

### Post by visctrix on 2008-04-26
Yes I can...

During the upgrade the 'visctrix login:' prompt was flashing up for a while but I couldn't do anything with it.

Now I've logged in in the terminal, do you think I'll be able to log into the main screen?

Just can't remember how to go back to the login screen now... :-)

---

### Post by ibutho on 2008-04-26
You can go back to the login manager by doing CTL-ALT-F7. If you can login as the user visctrix in the command line, try logging into GNOME using the login manager. If that fails, log back into the command line, kill the xerver (sudo /etc/init.d/gdm stop) and then run "startx". If GNOME doesn't run successfully, some error messages will be printed on the screen which will help diagnose the problem. Post those error messages here. If you want to restart the login manager, run "sudo /etc/init.d/gdm start".

---

### Post by visctrix on 2008-04-26
This seems to be working. I couln't log in to Gnome, but killing the xserver and then startx worked - I'm back to my familiar desktop :-)

I have an error message:
> **Failed to run /usr/share/apport/apport-gtk as user root**
Unable to copy the user's Xauthorisation file.

Will I need to do anything else now?

Thanks

---

### Post by ibutho on 2008-04-26
You shouldn't really get that error, so run gnome-terminal and enter
```
sudo chown `whoami`:`whoami` ~/.Xauthority
```

---

### Post by visctrix on 2008-04-26
OK, I've not solved this yet. I rebooted, and still can't login except at the command prompt. Following your instructions worked again and I get the same error message again.

How can I edit the settings to make it work properly in future?

Thanks

---

### Post by visctrix on 2008-04-26
I've tried that command, but I get an error message saying I've entered the wrong password... (I haven't)

---

### Post by visctrix on 2008-04-26
OK, to test the status of my password - 

I'm in Gnome/X after logging in to a terminal, stopping gdm, and then startx as per above instructions

I do seem to be logged in as visctrix

I can't carry out any admin functions: I get effectively the same error as above:
> Failed to run [...] as user root.

Unable to copy the user's Xauthorization file.

---

### Post by visctrix on 2008-04-26
I found [this post]("http://ubuntuforums.org/showthread.php?t=575854") and I did:

```
ls -la .Xaut*
```

I got this result:

> -rw------- 1 root     root     0 2008-04-26 16:57 .Xauthority
-rw------- 2 visctrix visctrix 0 2008-04-26 18:00 .Xauthority-c
-rw------- 2 visctrix visctrix 0 2008-04-26 18:00 .Xauthority-l

I followed the instructions and did:

```
sudo mv .Xauthority .Xauthority_bak
```

Now I get this, and still nothing works:

> -rw------- 1 root     root     0 2008-04-26 16:57 .Xauthority_bak
-rw------- 2 visctrix visctrix 0 2008-04-26 18:00 .Xauthority-c
-rw------- 2 visctrix visctrix 0 2008-04-26 18:00 .Xauthority-l

Still not sure where I'm going with this...

Any more help appreciated :-)

---

### Post by visctrix on 2008-04-26
I seem to have solved this by:
```
sudo dpkg-reconfigure xserver-xorg
```

---

