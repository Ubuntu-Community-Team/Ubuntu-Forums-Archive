---
title: "Automating some tasks..."
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by fifo_thekid on 2008-05-27
Hi all
I've little experience with Linux
But I really like Kubuntu
I used it to install Oracle 11g using a very complicated guide
After finishing it, I had millions of problems
But now, I could solve everything
The problem is, every time I restart the computer there are a lot of things that I need to type again and again
I really wish that those can be done automatically
I will start with the first one:
Notes: My username if fifo, and the other username which is used for Oracle is called oracle.

1- Setting The Display Parameter:

```

fifo@AHMED3:~$ export DISPLAY=:0.0
fifo@AHMED3:~$ xhost +
access control disabled, clients can connect from any host
fifo@AHMED3:~$ sudo su -
[sudo] password for fifo:
root@AHMED3:~# export DISPLAY=:0.0
root@AHMED3:~# xhost +
access control disabled, clients can connect from any host
root@AHMED3:~# su - oracle
Your account has expired; please contact your system administrator
su: User account has expired
(Ignored)
oracle@AHMED3:~$ export DISPLAY=:0.0
oracle@AHMED3:~$ xhost +
access control disabled, clients can connect from any host
oracle@AHMED3:~$

```

Any method for automating those steps on startup?

Thank you...

---

### Post by IgnorantGuru on 2008-05-27
I don't have time to go into detail right now, but to automate commands you enter them in to a script (a text file that has "#!/bin/bash" on the first line and is executable).  If you want a script to run at startup as root, you can add it to the /etc/init.d startup scripts using a certain procedure.  Check out a howto on adding init.d scripts in Ubuntu.

---

### Post by fifo_thekid on 2008-05-27
thank you for your reply
but the step 
```
sudo su -
```
asks for a password
how can i add that into the script?!!

and what if i want to double click on the script and after that it executes the command and then instead of exiting is just gives me the command prompt?

---

### Post by IgnorantGuru on 2008-05-27
Hi,  I don't believe I'm the best person to answer your question because I'm not familiar with oracle and I'm not that familiar with the details of exporting X displays.  But I'll see if I can point you in the right direction.

My understanding is that the user logged into KDE or gnome owns the X display, and can allow other users to access it using the xhost + command.  The other users just need to set their DISPLAY environment variable to tell X what display they want.

So if fifo owns the X display, only fifo needs to execute xhost +, I would think.  So it looks to me like you have some extraneous commands in there. You might want to see if you can narrow it down to just what is required.

 	
> but the step
sudo su -
asks for a password
how can i add that into the script?!!

If the script is run by root, it will not ask for a password.

I would think a script like this would do what you did:

```

#!/bin/bash
# run this script as root

# these commands are run as fifo
su fifo -c export DISPLAY=:0.0
su fifo -c xhost +

# these commands are run as root
export DISPLAY=:0.0
xhost +

# these commands are run as oracle

su oracle -c export DISPLAY=:0.0
su oracle -c xhost +

```

You can save that script to a text file 'myscript' then run it with
```
sudo bash myscript
```

But I'm not sure why you would want root to set the DISPLAY variable, or why you would want root or oracle to execute xhost +.  Doesn't make sense to me but like I said I'm not that familiar with it.

It looks to me like only oracle needs to variable set, and only fifo needs to execute xhost +.

```
su fifo -c xhost +
su oracle -c export DISPLAY=:0.0
```

You might try that and see it if accomplishes your purpose.

> and what if i want to double click on the script and after that it executes the command and then instead of exiting is just gives me the command prompt?

When you create the shortcut to the script, or add it to the menu, in the application settings you can set 'open in terminal'.  If the last command in the script is sudo su - then you should be left in a (root) terminal (providing you set the script to run as root).  Not sure you would want to do that though - what exactly are you trying to do?

It sounds like you may just want a script which starts oracle for you.  Have you searched the web for a good way to do that?

If you provide each step of what you're doing (beyond just setting the DISPLAY variables) I or someone else might be able to direct you.

You might also look through this...
[http://www.google.com/search?q=setting+up+oracle+on+ubuntu](http://www.google.com/search?q=setting+up+oracle+on+ubuntu)

And this shows an init.d script for starting oracle (at the end)...

Installing Oracle 11g on Ubuntu 8.04 LTS (Hardy Heron)
[http://www.pythian.com/blogs/968/installing-oracle-11g-on-ubuntu-804-lts-hardy-heron](http://www.pythian.com/blogs/968/installing-oracle-11g-on-ubuntu-804-lts-hardy-heron)

---

### Post by fifo_thekid on 2008-05-28
I tried typing this in the console:
```

su fifo -c xhost +
su oracle -c export DISPLAY=:0.0

```

and it worked, when i make a bash file and execute it, i don't get errors but when i switch to oracle using:
```
su - oracle
```
and execute
```
xclock
```
i get the error:
> Error: Can't open display:

all what i want to do is to save the DISPLAY parameter for the oracle account permanently, and disable access control permanently

thank you

---

### Post by IgnorantGuru on 2008-05-28
I noticed this in the oracle install guide:

"If you happen to be using Ubuntu on the Desktop as well, go to System -> Administration -> Login Window, select the Security tab and uncheck the box next to “Deny TCP connections to the Xserver”. You will have to restart your Xserver for this change to take effect."
[http://www.pythian.com/blogs/968/installing-oracle-11g-on-ubuntu-804-lts-hardy-heron](http://www.pythian.com/blogs/968/installing-oracle-11g-on-ubuntu-804-lts-hardy-heron)

Maybe that will take care of the xhost +.  Then you should be able to start oracle with a wrapper script:

```

#!/bin/bash
export DISPLAY=:0.0
xclock

```

run the script as oracle:
```
su oracle -c bash myscript
```

Or you can make a menu entry or application shortcut to the script, and in the settings select "run as user... oracle".

If you want xclock started at system startup, add an init.d script similar to the one used in the guide.  See this section:  "Also, a startup script might be useful, right? Create a file called /etc/init.d/oracledb and put this into it:"

You could also try adding DISPLAY=:0.0  to /etc/environment  but that is not generally done.  AFAIK it is customary in Debian/Ubuntu to use wrapper scripts for the env variables.

---

### Post by fifo_thekid on 2008-05-28
> I noticed this in the oracle install guide:

"If you happen to be using Ubuntu on the Desktop as well, go to System -> Administration -> Login Window, select the Security tab and uncheck the box next to “Deny TCP connections to the Xserver”. You will have to restart your Xserver for this change to take effect."
[http://www.pythian.com/blogs/968/ins...ts-hardy-heron](http://www.pythian.com/blogs/968/ins...ts-hardy-heron)

I don't have this menu under Kubuntu, it's available in Ubuntu only:confused:

---

### Post by fifo_thekid on 2008-05-30
The question now is:
1- How can I make the DISPLAY variable for each user set automatically upon startup
2-How can I get rid off typing xhost +, notice that i'm using Kubuntu so I don't have the choice 'Deny TCP connections to the Xserver'

---

