---
title: "Login problem after upgrade.."
date: 2011-11-26
forum: Installation &amp; Upgrades
---

### Post by grimslider75 on 2011-11-26
When the login screen appears where I can choose which user to log into, everything appears as it normally would. However, when I choose my user [Kurt], I type in my password and press enter. What happens next is the login box goes away and the screen goes black. After this, a command-line-like interface shows up for a second or two where there is a bunch of text, and then that dissappears. After all of this, the login screen with the login box shows up again. If I try to login again, the same sequence of events occur no matter what.

The session selected it Xubuntu. I can also select Xfce session, but I recieve the same problem. 

I have recently upgraded from 11.04 to 11.10. The upgrade had some problems, such as not being able to complete probably. To remedy this, I ran apt-get update through the recovery console since the system wasn't booting up properly. I also had to manually install the fglrx driver and the lightdm window manager (or whatever it is). 

How can I fix the login problem?

Also, I can login using the guest account without any problems whatsoever. Why?

Thanks in advance.

---

### Post by grimslider75 on 2011-11-27
I Fixed this issue by following instructions from [here]("http://askubuntu.com/questions/46008/cant-log-in-cycles-through-black-screen")

>           
       Try this:
  
[LIST=1]
[*]Boot pc
[*]When presented with login screen press ctrl + alt + f1
[*]Login
[*]Backup your home folder /home/<username> by executing the command ```
sudo mv /home/<username> /home/backup
```
[*]Then recreate your home folder by ```
sudo mkdir /home/<username>
``` and set file permissions by typing ```
sudo chown <username>.<username> /home/<username>
```
[*]go back to graphical login screen (ctrl+alt+f7/f8 depending on your config), or reboot, and try and login.
[/LIST]
  This will determine if the issue is caused by your user profile. if  you are able to login after this, then you can copy over the items and  settings you want from the backup folder.
  Remember that username is case sensitive. so if your username is dave, then don't type Dave or DaVe.. type dave where <username> is specified.
 


---

### Post by sublunary on 2012-02-05
Fantastic.  I spent the last couple of days reading up and trying different solutions, and this one worked for me just presently after a fresh reinstall.  Thanks much.

---

### Post by MASEngr on 2012-02-05
This is not solved, this solution does not work.

```

sudo mv /home/username /home/backup

cannot move, file in use or busy.  

```
(Can't remember the exact error message, I have to reboot into Windows to get help.)

So this doesn't work.  How can you do this with an encrypted volume?

---

### Post by atentik on 2012-02-06
> **grimslider75 said:**
> I Fixed this issue by following instructions from [here]("http://askubuntu.com/questions/46008/cant-log-in-cycles-through-black-screen")

I followed this... though it did not solve my problem, it added another problem. I am able to log on now but it say" ```
Could not update ICEauthority file /home/abcdedg/.ICEauthority"
```
Any idea how I could resolve this?

---

