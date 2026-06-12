---
title: "Unable to sudo upgrade or update"
date: 2024-01-30
forum: Installation &amp; Upgrades
---

### Post by jctech2025 on 2024-01-30
Hi All,

I recently installed Ubuntu on my Windows 10 machine in Virtual box.  The install went through fine as I didn't see any errors.  I got to the login screen and logged in.  I went to run sudo apt get upgrade and apt get update, and got the following error:

"user is not in the sudoer group, access is denied"?  I have never seen this before, I am rusty on Ubuntu at the moment but did I miss something?

Thanks

---

### Post by #&amp;thj^% on 2024-01-30
Just add your user to that group:
```
su -
usermod -a -G sudo vboxuser
```

If "su -" don't work use "sudo -s"
Shown here:
```
su -
Password: 
su: Authentication failure
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> sudo -s
[sudo] password for me: 
root@me-on-zfs:/home/me# 

```

---

### Post by jctech2025 on 2024-01-30
Ok I will try that when I get home and update.  I'm working on setting up a Ubuntu, and Backtrack that I can go back and forth between.  Got get this stable first.

---

### Post by jctech2025 on 2024-02-06
Ok, I tried the above.  I was able to use sudo - and it logged me into root.  Once into root, I tried the usermod command and got no errors.  I ended up running all the updates while in root with no issues.  As soon as I went back to the regular user that I was trying to add I tried to run updates again and got: "could not open lock file - permission denied", somewhat paraphrased.  Thoughts?

---

### Post by ActionParsnip on 2024-02-06
Did you prefix the command with sudo? If so then I suggest a reboot of the VM if possible. If the issue persists then we can unlock the lock file.

---

### Post by jctech2025 on 2024-02-06
I did prefix with sudo.  I also did a reboot but I can reboot again.  I know I didn't see any error when trying to add the user.  If the reboot doesn't work how do we unlock the lock file?  Thanks.

---

### Post by ActionParsnip on 2024-02-07
> **jctech2025 said:**
> I did prefix with sudo.  I also did a reboot but I can reboot again.  I know I didn't see any error when trying to add the user.  If the reboot doesn't work how do we unlock the lock file?  Thanks.
```
 
sudo fuser -vki /var/lib/dpkg/lock
sudo dpkg --configure -a

```
Should do it

---

### Post by jctech2025 on 2024-02-07
Ok thanks I will try that and update.

---

### Post by corradoventu on 2024-02-08
Check if you have 'sudo' group ```
groups
```

---

### Post by jctech2025 on 2024-02-12
There we go.  I was able to run sudo apt-get update after running the lock file fix.

---

