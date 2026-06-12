---
title: "sodu: command not found"
date: 2019-04-29
forum: Installation &amp; Upgrades
---

### Post by tofazzal.haque on 2019-04-29
I am new user of ubuntu 18.04. May be, I have changed environment variable. As a new user, I can't understand exactly what's happening. I can't upgrade, install or remove any software from my machine. 

code: 
sudo apt-get upgrade
result: 
sodu: command not found

code: 
sudo apt-get remove playonlinux
result: 
[https://paste.ubuntu.com/p/PFQSvX4r8Q/](https://paste.ubuntu.com/p/PFQSvX4r8Q/)

code: 
echo $PATH
result:
/home/shuvo/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin




Please help me.

---

### Post by TheFu on 2019-04-29
> sodu: command not found

It is spelled "**sudo**" and located .... 
```
$ which sudo
/usr/bin/sudo
```

Details matter. Being inconsistent in the posting above causes confusion. We can't tell what you actually typed.  Best to always copy/paste the text and wrap it in 'code' tags like I've done.

---

### Post by freemedia2018 on 2019-04-29
Just a guess, but you could be having problems due to /home/shuvo/bin being the first thing in your path. If the usual items were first, that might work better.

TheFu suggested you run which sudo ...that sounds like a good idea. It looks from your paste like sudo is working, so maybe it's there and it really was just your typo.

You should also run sudo apt-get update before you run sudo apt-get upgrade.

---

### Post by TheFu on 2019-04-29
What does **/usr/bin/sudo echo $PATH** show?
Every userid has a different environment. Each process inherits the environment from the parent process.  That's the normal way stuff happens.  If you really want to dig deep, you can look under /proc/ at all the currently running processes and the environment for each is shown there.  /proc isn't a real file system, it is mapped into memory to provide appropriate access to the userids with the correct permissions. Normal userids can't see processes for which they aren't the effective userid. Basically, you can see your stuff.

Thrown into that mix is the fact that sudo has specific protections to ignore dangerous environments, which may be enabled or not.  That would be controlled by either the sudo.conf or sudoers files.  The manpage on each has the details.  The entire set of manpages for all the sudo commands and config files is a work of art.  Seriously.  

Screwing around with sudo settings can break things, including sudo.  I've done it a few times.  Got to the point where I had to use a live-boot/install flash drive to hack into my own box to fix/undo the sudoers changes.

---

### Post by sisco311 on 2019-04-30
```
sudo echo $PATH
```will print the current user's path because the parameter expansion is performed before the sudo command is executed.

The output of:
```
sudo env
```
and
```
sudo sudo -V
```would be helpful.

---

### Post by Impavidus on 2019-04-30
> **freemedia2018 said:**
> Just a guess, but you could be having problems due to /home/shuvo/bin being the first thing in your path. If the usual items were first, that might work better.I don't think that's a problem, as long as there's no sudo in /home/shuvo/bin. I've had a /home/user/bin directory for a long time (since before /home/user/.local/bin was made common) and never had any problems. The reason to put the local stuff at the front is to allow it to override the more global stuff.

> **TheFu said:**
> What does **/usr/bin/sudo echo $PATH** show?
That will still show the user's normal PATH. The shell expands $PATH before it runs sudo. To get root's PATH, run```
/usr/bin/sudo -i echo '$PATH'
```

If you use a command starting with sudo and the shell replies that sodu doesn't exist, you must have something funny (a shell function or an alias) replacing sudo with sodu. What do you get from ```
type sudo
```

---

### Post by TheFu on 2019-04-30
Impavidus is correct. My *sudo echo $PATH* won't work and neither will *sudo -i echo $PATH*. The PATH is expanded. Just tested it here.

But the '$PATH' delays the expansion until later.
```
sudo -i echo '$PATH'
```
very interesting.

**sudo -i** will enter root's account, running the root startup based on the shell.  Allow the shell to be entered, then run **echo $PATH**, as root.

the sudo manpage:```

     -E, --preserve-env
                 Indicates to the security policy that the user wishes to preâ
                 serve their existing environment variables.  The security
                 policy may return an error if the user does not have permisâ
                 sion to preserve the environment.
...
     -H, --set-home
                 Request that the security policy set the HOME environment
                 variable to the home directory specified by the target user's
                 password database entry.  Depending on the policy, this may
                 be the default behavior.
...
     -i, --login
                 Run the shell specified by the target user's password dataâ
                 base entry as a login shell.  This means that login-specific
                 resource files such as .profile or .login will be read by the
                 shell.  If a command is specified, it is passed to the shell
                 for execution via the shell's -c option.  If no command is
                 specified, an interactive shell is executed.  sudo attempts
                 to change to that user's home directory before running the
                 shell.  The command is run with an environment similar to the
                 one a user would receive at log in.  The Command environment
                 section in the sudoers(5) manual documents how the -i option
                 affects the environment in which a command is run when the
                 sudoers policy is in use.
...
     Environment variables to be set for the command may also be passed on the
     command line in the form of VAR=value, e.g.
     LD_LIBRARY_PATH=/usr/local/pkg/lib.  Variables passed on the command line
     are subject to restrictions imposed by the security policy plugin.  The
     sudoers policy subjects variables passed on the command line to the same
     restrictions as normal environment variables with one important excepâ
     tion.  If the setenv option is set in sudoers, the command to be run has
     the SETENV tag set or the command matched is ALL, the user may set variâ
     ables that would otherwise be forbidden.  See sudoers(5) for more inforâ
     mation.
...
```
Sorry about some of the funky characters.
Suffice it to say, control of the environment is a key aspect for sudo.

---

