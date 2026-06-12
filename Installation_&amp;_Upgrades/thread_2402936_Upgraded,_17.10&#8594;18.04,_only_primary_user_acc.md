---
title: "Upgraded, 17.10&#8594;18.04, only primary user account is accessible"
date: 2018-10-05
forum: Installation &amp; Upgrades
---

### Post by john_ladasky on 2018-10-05
Hi there,

The subject line says most of what I need to say.  I have a desktop machine with multiple user accounts which I upgraded from 17.10 to 18.04.  I have only been able to connect my primary account.

I have a separate /home partition on my HDD.  When I upgrade Ubuntu, I have a habit of downloading the ISO, making a bootable DVD, and then trying before installation.  In years past I got burned by accepting the automatic upgrades that are offered in the dialog box.  Obsolete applications could leave pieces of themselves behind, and cause compatibility problems; or, NVidia drivers would not behave; or other things.  I check first, and then if everything appears to be working, I proceed.  I manually reinstall all my apps after the upgrade.

When you install Ubuntu using the DVD and Ubiquity, you only provide the primary account login information.  No secondary account folders are erased, but the login information is wiped.  When I have upgraded in the past (say, from 15.04 or 16.04), after the installation is complete I go to Settings > Details > Users from the primary account desktop, click Add User, and then re-enter the information about each account, including a new temporary password.

This isn't working after my 18.04 upgrade.  I just tried to add a password for an existing secondary account.  When I enter that password, the login screen goes black for about 15 seconds and then kicks me back to the login screen.  The system does not report that the password does not match.  No additional folders were created in /home, so I am confident that I re-typed the account name correctly in Add User.  These symptoms were not changed by cold-starting the machine.

I hope that someone can help me figure this out.  Thanks!

---

### Post by #&amp;thj^% on 2018-10-05
> **john_ladasky said:**
> Hi there,

The subject line says most of what I need to say.  I have a desktop machine with multiple user accounts which I upgraded from 17.10 to 18.04.  I have only been able to connect my primary account.

I have a separate /home partition on my HDD.  When I upgrade Ubuntu, I have a habit of downloading the ISO, making a bootable DVD, and then trying before installation.  In years past I got burned by accepting the automatic upgrades that are offered in the dialog box.  Obsolete applications could leave pieces of themselves behind, and cause compatibility problems; or, NVidia drivers would not behave; or other things.  I check first, and then if everything appears to be working, I proceed.  I manually reinstall all my apps after the upgrade.

When you install Ubuntu using the DVD and Ubiquity, you only provide the primary account login information.  No secondary account folders are erased, but the login information is wiped.  When I have upgraded in the past (say, from 15.04 or 16.04), after the installation is complete I go to Settings > Details > Users from the primary account desktop, click Add User, and then re-enter the information about each account, including a new temporary password.

This isn't working after my 18.04 upgrade.  I just tried to add a password for an existing secondary account.  When I enter that password, the login screen goes black for about 15 seconds and then kicks me back to the login screen.  The system does not report that the password does not match.  No additional folders were created in /home, so I am confident that I re-typed the account name correctly in Add User.  These symptoms were not changed by cold-starting the machine.

I hope that someone can help me figure this out.  Thanks!

I mainly use the terminal for this, maybe give this a try:
To create new user accounts on Ubuntu using the terminal, run the commands below
```

sudo adduser richard  ## Replace richard with the user name desired
```
Again Replace richard with the user account name you wish to add.

When you run the commands above, you will get prompts to enter some more details of the user as well as creating the new user password. When you’re done, type Y for yes to save the information.

And if you want to  Add User to Sudo Admin Privalages

Now that the user account is created, use the commands below to add the user to the sudo program which will allow the user to install / remove packages and well as make some system-wide changes to the server / desktop.
```

sudo usermod -aG sudo richard
```

Again, replace richard with the account name.

This will add the user to the sudo program or group.

After that, the user should be able to run and execute tasks only administrator have access to.

To test  run the commands below as Richard or the newly created user's name.
```

sudo apt update && sudo apt dist-upgrade && sudo apt autoremove
```

The commands above should run without problems… Hope this helps.

---

### Post by john_ladasky on 2018-10-05
> **1fallen said:**
> I mainly use the terminal for this, maybe give this a try:
To create new user accounts on Ubuntu using the terminal, run the commands below
```

sudo adduser richard  ## Replace richard with the user name desired
```
Again Replace richard with the user account name you wish to add.


Just tried this:

```
sudo adduser foo
``` (the account I already tried to add using the GUI)

And Linux replied:

```
adduser: The user 'foo' already exists.
```

I also started looking for other Linux commands which relate to user accounts to see whether I could find other information.  The LAST-LOGINS column in the output of **[FONT=courier new]lslogins[/FONT]** shows a time when I did in fact try to log on as "foo". Would [FONT=courier new]**lslogins**[/FONT] show unsuccessful login attempts?  It looks like I am logging in, but then something is kicking me back out.

---

### Post by #&amp;thj^% on 2018-10-05
> **john_ladasky said:**
>  Would [FONT=courier new]**lslogins**[/FONT] show unsuccessful login attempts?  It looks like I am logging in, but then something is kicking me back out.
Invalid login attempts can be tracked using command "lastb" provided the file /var/log/wtmp is present. 
IE Mine:
```
me on Fri Oct 05 at 09:11 PM in ~ branch: (HEAD) 
>> sudo lastb
me       tty7         :0               Thu Oct  4 20:20 - 20:20  (00:00)
me       tty7         :0               Thu Oct  4 09:04 - 09:04  (00:00)
me       tty7         :0               Thu Oct  4 07:36 - 07:36  (00:00)

btmp begins Thu Oct  4 07:36:03 2018

```
Now a failed login attempt would look like this example:
```
Last login: Sat Apr 21 16:24:24 UTC 2018 on pts/3
Last failed login: Sat Apr 21 17:44:04 UTC 2018 from 185.189.58.212.ptr.cy4n.net on ssh:notty
There was 1 failed login attempt since the last successful login.
```

Note: The accounting system on your computer keeps track of usage user statistics and is kept in the current /var/log/wtmp file. 
This is beginning to sound like a permission problem or a corrupt install. :(

---

### Post by john_ladasky on 2018-10-31
> **1fallen said:**
> 
This is beginning to sound like a permission problem or a corrupt install. :(

Hi 1fallen,

Thanks for trying to help me, sorry for the slow reply.  I have not solved this problem.  In fact, it has now appeared on a second computer in our laboratory!  The symptoms are identical, even though the hardware is quite different.  

I own the primary account, and can log in.  There are two other accounts on the computer.  The other two users could log in until a few days ago.  Now they can't get past the login screen.  After the password is correctly typed, the screen goes black for a few seconds and simply returns to the login screen.

Can anyone understand this problem or suggest a way to troubleshoot it? Thanks!

---

