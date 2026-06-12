---
title: "broken path try to update"
date: 2012-09-27
forum: Installation &amp; Upgrades
---

### Post by vsalunkhej on 2012-09-27
root@vikas:~# update-exim4.conf
Command 'update-exim4.conf' is available in '/usr/sbin/update-exim4.conf'
The command could not be located because '/usr/sbin' is not included in the PATH environment variable.
This is most likely caused by the lack of administrative privileges associated with your user account.
update-exim4.conf: command not found

---

### Post by drmrgd on 2012-09-27
Odd that /usr/sbin would not be in your PATH environment.  Logged in as root (sudo -i), would you mind posting the output of:

```
echo $PATH
```

As a test, if you don't see /usr/sbin in that string, try adding it to see if that helps:

```
export PATH=$PATH:/usr/sbin
```

That will only be a temporary solution, and will revert back once you log out and log back in or start a new shell.  If it's truly missing you can add that path permanently.  I'm just curious as to whether it's really missing or not, and if so, does adding it fix the problem.

---

### Post by grahammechanical on 2012-09-27
Quote

> This is most likely caused by the lack of administrative privileges associated with your user account.

Run the command again and this time run it as:

```
sudo update-exim4.conf
```

And do enter your password when requested.

---

### Post by vsalunkhej on 2012-09-28
Thanks 
I follow the following command as for your direction
echo $PATH
export PATH=$PATH:/usr/sbin
sudo update-exim4.conf
 I think that command is run but when i restart  the commputer  and try to update(sudo update-exim4.conf), same message is comming.

---

### Post by drmrgd on 2012-09-28
Yes, the 'export' command I gave is only good for 1 session.  I wanted to see the results of echo $PATH first to be sure the path was no included in your environment, and then test adding the path to your environment to see if it fixed it.  I think I can safely assume based on the script working when you ran the 'export...' command that for some weird reason /usr/sbin is not in Root's $PATH.

To make the change persistent, we'll need to just permanently modify your $PATH variable.  Since this is a system resource path, without knowing what true Linux sysadmin dogma is, I would add that path to /etc/environment.  In most cases, the new path is not like this and most people will just add it to their .bashrc file.  I've also never modified Root's $PATH.  So, if any expert finds this method less than ideal, please do correct me.

At any rate, start a root shell as you did:

```
sudo -i
```

Then modify the file /etc/environment by adding the following to the existing string:

```
/usr/sbin
```

Be sure to separate the new entry from the others with a colon (:).  So if you add it as the first element in that string, it would be:

```
PATH="/usr/sbin:/usr/local......"
```

If you add it at the end, it would be:

```
PATH="...../usr/games:/usr/sbin"
```

You may have one other change to make.  I'm a bit surprised that this has not come up with a non-root user on your system.  However, you may need to modify the /etc/sudoers file as well.  In there you should see a line like this:

```
Defaults        secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
```

This is the default system PATH, and if you use an initial shell (as in sudo -i), the system should reset many of the environment 
variables, using only what's in this file as the default.  That means that if /usr/sbin is not in that string, even though you added it to /etc/environment, when you run 'sudo -i' you will not be able to see the new location in your PATH.  So, /usr/sbin will need to be added to that string as well.

This still all begs the question of why this location is not in your default system environment?  To me that's very strange as this is a very standard location for binary files on all Linux systems.  Also, here's a little more documentation on Environment Variables that you might find handy:

[https://help.ubuntu.com/community/EnvironmentVariables](https://help.ubuntu.com/community/EnvironmentVariables)

---

