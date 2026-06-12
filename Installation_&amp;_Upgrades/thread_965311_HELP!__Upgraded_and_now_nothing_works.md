---
title: "HELP!  Upgraded and now nothing works"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by Sk8Save on 2008-10-31
I installed 8.04 from CD and finally got issues working (had wireless connectivity problems, but solved them).  I used the upgrade manager to go from kernel -16 to -21 (plus a whole host of other upgrades).  Now, when I boot up, I log in just fine.  I try to access the network manager, but it gives me an error that I am not allowed to access that.  I was before.

When I start Firefox, the dial appears and spins for a few moments, and then returns to the cursor.  Nothing starts.  I tried going back to the -16 kernel (it's still offered in the dual-boot menu), but the same thing happens.

I am a real Linux and Ubuntu newbie.  Can anyone tell me where I went wrong and how to fix it?

Also, one more question...how does one log in as a superuser ('root').  When I try to log in from the main login screen as root, it says this is not where root logs in.

Thanks in advance!

---

### Post by Peter09 on 2008-10-31
In Ubuntu you normally user the prefix 

```
sudo <then a command>
```
to gain administrator access. You can do ```
sudo su
``` do get a more permanent access but this is not normally done.

The first thing I suggest to sort your problems is to ensure that you are fully upto date with your system, in a terminal type-

```
sudo apt-get update
sudo apt-get upgrade
``` 

see if doing this helps.

---

### Post by Dumdideldum on 2008-10-31
In Ubuntu, there is no such option to login as root. Login as your main user, then type in sudo su - provide it with the password of your user.

Then you have root powers.
To execute root commands, always put:
sudo 
in front of the command.

For instance:
sudo ls /root

The network settings should ask you about a password to enter so that you gain root powers or a Button "Unlock" to get root powers.
So that's the ordinary behavior of Ubuntu.

The Firefox issue:
Very hard to tell, you could try a:
sudo apt-get --reinstall install firefox

---

