---
title: "replace fedora - keep home partition?"
date: 2005-09-13
forum: Installation &amp; Upgrades
---

### Post by cgofftn on 2005-09-13
Hello,

I am using Ubuntu on a dual-boot Ubuntu/WinXP laptop with no problems.  I did a clean Ubuntu install on this machine.

I would like to replace a current Fedora4 installation on my desktop machine with Ubuntu, but I want to keep my existing 'home' partition.  I have a large amount of data there I want to keep.  How do I go about doing this?

I tried this before, but I could not get to the Ubuntu Gnome desktop after login.  I wonder if this is because the Fedora Gnome desktop configuration files remained in my home directory?

Any help, but, especially step-by-step instructions, would be appreciated.  Thanks in advance.

Curt Goff

---

### Post by xy77 on 2005-09-13
If you configured /etc/fstab to use your old home partition as /home, it should be fine.

Try backing up the ~/.gnome* folders to somewhere else and launch gnome to see if it works. You will have to reconfigure it if course.

Try it and let us know if it worked.

- David (xy77)

---

### Post by cgofftn on 2005-09-14
I have gone through the installation process with no problems.  However, when I try to log into Gnome I get an error message that a couple of hidden gnome directories can't be created in my /home/'user' folder because 'permission denied'.

Similarly, when I log into the 'failsafe terminal' which should be my user directory I get a 'permission denied' message.  I have to use sudo 'command' to execute any commands.

Apparently there is a permissions issue with my /home/'user' folder.  Does anyone know the correct command to fis this?

Thanks.

Curt Goff

---

### Post by bsussman on 2005-09-14
it is very possible that your uid (the numeric user id ) is different in ubuntu from fedora.

test this by:

 ```
> id
``` 

in both systems, or by grepping your user name out of /etc/passwd - look at the 3rd field (uid and 4th - gid)

If this is so, I should think you might want to change your uid in ubuntu - since it is the newer system on your pc and therefore there might be fewer files that are going to be at issue.

This can be done in kuser (what's the gnome user manager?) and then you will need to make sure all the files in your home are properly marked:

 ```
> cd ~yername
``` 

MAKE SURE YOU ARE IN YOUR HOME DIR

 ```
> sudo chown -R yername:yergroupname .* *
``` 

(should get everything)

boot both distributions and check by:

 ```
> touch ~/nonexistentfilename
> rm ~/nonexistentfilename
``` 

and

 ```
> ls -lan | less
``` 

n = print numerics not names for gid/uid

there are prolly gooey ways to do this - Krusader is your friend in kde, but I could do the above at the command prompt in about 2 minutes, plus boot time;)

AND DO check the doc on all the above commands - trust nobody that gives you commandline syntax, unless you UNDERSTAND the impact of every option and parameter. I might have made a mistake. I might have said sumpin like 'rm -rf *'(DONT DO THIS AT HOME KIDS!).

---

### Post by cgofftn on 2005-09-14
SUCCESS!

I fixed the 'permission denied' problem by using the command:

sudo chown -R 'user' /home/'user'

I then logged into Gnome, but only got as far as displaying the desktop background before I got an error message about Gconf.

I exited 'X' and logged into the 'failsafe terminal'.  Out of habit I ran apt-get update and apt-get upgrade.  There were about 99 packages  that hadn't been upgraded due to an unmet dependency.  After taking care of this I rebooted.

I logged into Gnome again and this time got basically a white desktop with no icons.  So once again into the 'failsafe terminal' and I deleted the ~/.gconf and ~/.gconfd directories.  I logged into Gnome again and this time got the Ubuntu Gnome desktop.

COOL!

So, I have upgraded from Fedora4 to Ubuntu 5.04 AND kept all the data in my 'home' partition.  Everything is there and working.  I just have to tweak my preferences and I'll be good to go.

Thanks to everyone who replied.  Searching the forum messages also provide ideas on how to proceed.

Curt Goff

---

### Post by epedersen on 2005-10-07
Have you had any success with accessing emails, or the like, after you upgraded?  My brother-in-law is interested in moving over to Ubuntu, but would be loath to lose his Netscape emails.  (Or is it Evolution?)

---

