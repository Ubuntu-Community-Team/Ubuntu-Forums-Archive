---
title: "[SOLVED] Added new user, opened pandoras box."
date: 2008-07-03
forum: Installation &amp; Upgrades
---

### Post by AlexBellisBrown on 2008-07-03
First let me explain, i WAS running a perfect bugless Ubuntu system, im the only user. Now, i like to use google earth a lot. But its a pain in the *bum* to keep turning off compiz when i want to use it. So i decided to add a new user, free of compiz. So, i added a new user, but now ive changed my mind, i want to delete it, so, hence ive got myself into this bug. ( [https://bugs.launchpad.net/ubuntu/+source/xubuntu-meta/+bug/194496](https://bugs.launchpad.net/ubuntu/+source/xubuntu-meta/+bug/194496)) Now, i cannot delete the account, and having the account is causing me serious problems with my Avant Window Navigator, it keeps freezing. Now, ive tried to delete the account using Sudo Userdel (username) (or something like that, dont worry, i did it right, just cant remember) BUT!!! Now i cant use Sudo (or Sudo Su) because im no longer the only user. So as u see im quite boxed in. So, what do you recommend? Log in as root? Edit from that? Thanks in advance! :)

---

### Post by jnw222 on 2008-07-03
use root it has a free sledgehammer for the pc

---

### Post by jnw222 on 2008-07-03
what version do u use

---

### Post by AlexBellisBrown on 2008-07-04
I use Hardy Heron. :)

---

### Post by rogier.de.groot on 2008-07-04
I'm sorry, but what you're saying sounds completely ridiculus.
You not being the only user doesn't affect sudo; wether or not you're a member of the 'admin' group does.
A user account is just a bunch of settings and files/directories; it can't affect AWN like you describe.
You probably can't login as root, as that account is disabled by default.
BTW, you're never the only user, check /etc/passwd it'll list quite a lot of other user accounts.

Could you please post the contents of:
/etc/passwd
/etc/group(s)
/etc/sudoers

---

### Post by AlexBellisBrown on 2008-07-04
alex@alex-laptop:~$ sudo su
[sudo] password for alex: 
alex is not in the sudoers file.  This incident will be reported.
alex@alex-laptop:~$ 


Go figure, i cant do sudo. And this all started when i added a new user. I ONLY wish to delete the new user someday.

---

### Post by AlexBellisBrown on 2008-07-04
> **rogier.de.groot said:**
> 

Could you please post the contents of:
/etc/passwd
/etc/group(s)
/etc/sudoers

These do not exist.:popcorn:

---

### Post by SkonesMickLoud on 2008-07-04
Try CompizSwitch:

[http://ubuntuforums.org/showthread.php?t=662926](http://ubuntuforums.org/showthread.php?t=662926)

> **AlexBellisBrown said:**
> These do not exist.:popcorn:

Heh, they better, else there's no way that you're logged in.  Look at them by doing "sudo gedit xxx".  Note that "/etc/sudoers" must be edited by visudo.

You could also log into your normal account, go to System >> Admin >> Users and Groups.  Click on "Unlock".  Click on the user you want to allow to sudo, then "Properties".  Click the "User Priveledges" tab.  Check the box marked "Administer the system". OK.  Close.  Log out.  Login.  Try to sudo.

---

### Post by AlexBellisBrown on 2008-07-04
Ok, will do, but that still doesnt solve my problem of deleting the account i created... any ideas?

---

### Post by SkonesMickLoud on 2008-07-04
> **AlexBellisBrown said:**
> Ok, will do, but that still doesnt solve my problem of deleting the account i created... any ideas?

In the Users And Groups screen I mentioned earlier, unlock it, click on the user you want to delete and hit "Delete".

Please let us know, and mark this thread as solved if it works.

---

### Post by AlexBellisBrown on 2008-07-04
Ahhh, Does nobody read my first post? Im blocked in thanks to [https://bugs.launchpad.net/ubuntu/+s...ta/+bug/194496](https://bugs.launchpad.net/ubuntu/+s...ta/+bug/194496) that bug!! I need some other way of deleting the account.

EDIT; The page i linked to isnt working, anyway, the bug is that when you click Unlock, It doesnt, and it gives this error message; Could not authenticate, and unexpected error occurred.

---

### Post by AlexBellisBrown on 2008-07-04
> **AlexBellisBrown said:**
> Ahhh, Does nobody read my first post? Im blocked in thanks to [https://bugs.launchpad.net/ubuntu/+s...ta/+bug/194496](https://bugs.launchpad.net/ubuntu/+s...ta/+bug/194496) that bug!! I need some other way of deleting the account.

EDIT; The page i linked to isnt working, anyway, the bug is that when you click Unlock, It doesnt, and it gives this error message; Could not authenticate, and unexpected error occurred.

Found the bug... [https://bugs.launchpad.net/ubuntu/+source/xubuntu-meta/+bug/194496](https://bugs.launchpad.net/ubuntu/+source/xubuntu-meta/+bug/194496)

Anyone?:confused::confused::confused::confused:

---

### Post by SkonesMickLoud on 2008-07-04
In a terminal:

```
sudo userdel -r <username>
```

Down in the comments of the bug report you linked:

```
sudo aptitude install policykit-gnome
```

has been listed as a fix to a non-working unlock button.

---

### Post by AlexBellisBrown on 2008-07-04
I say again, I now find Sudo unusable

[sudo] password for alex: 
alex is not in the sudoers file.  This incident will be reported.

---

### Post by SkonesMickLoud on 2008-07-04
> **AlexBellisBrown said:**
> I say again, I now find Sudo unusable

[sudo] password for alex: 
alex is not in the sudoers file.  This incident will be reported.

Sorry, I missed where you said you can't sudo, last night was a long night...

Try this:

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by AlexBellisBrown on 2008-07-04
Thanks :) Im sure itll work once i do that, it all sounds right. But unfortunatly a little thing called work is calling, so ill have to do it tonight, ill let you know how it goes, and thankyou very much!! :)

---

### Post by AlexBellisBrown on 2008-07-04
SkonesMickLoud, I wish i could thank you twice and buy you a beer, everything now works, i succsessfully edited the files, regained my Sudo capabilities, and deleted the account, thus solving the problem, also i should point out, to add/remove users, you must "unlock" it. This can only be done if you have Sudo capabilities, thus the error message, hence once i got sudo working, i could easily delete the account via that method. Thanks again to everyone, im marking this solved! :):):)

---

