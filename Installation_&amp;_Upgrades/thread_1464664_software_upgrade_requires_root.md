---
title: "software upgrade requires root?"
date: 2010-04-28
forum: Installation &amp; Upgrades
---

### Post by holzpusher on 2010-04-28
I would like to install new software using the Ubuntu Software Center, but when I try, it asks for the root password. I didn't create any root ID because people told me it's a security risk. Why is it asking for root access? I don't know the password!

---

### Post by mkvnmtr on 2010-04-28
If you installed the system type your password.

---

### Post by Dayofswords on 2010-04-28
its the password you made when you installed it

---

### Post by oldfred on 2010-04-28
It is your password. You are the administrator so it will ask for your passwork. Or if doing anything from the command line you have to preface it with sudo and then it will ask for your password.

[http://xkcd.com/149/](http://xkcd.com/149/)

---

### Post by holzpusher on 2010-04-30
Thanks but I tried that, it doesn"t work. Further investigation reveals that the "main" ID I use is no longer in the sudoers file. I don't know how that happened, I certainly didn't remove it. I may now be SOL since I don't have any other ID with permissions to add to the sudoers file.

---

### Post by holzpusher on 2010-04-30
> **oldfred said:**
> It is your password. You are the administrator so it will ask for your passwork. Or if doing anything from the command line you have to preface it with sudo and then it will ask for your password.

[http://xkcd.com/149/](http://xkcd.com/149/)


Thanks fo rthe suggestion but I already tried that. Further investigation reveals that the "main" ID I use is no longer in the sudoers file. I don't know how that happened, I certainly didn't remove it. I may now be up the creek without a paddle since I don't have any other ID with permissions to add me back into the sudoers file.

---

### Post by oldfred on 2010-04-30
This site has lots of good info:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by P4man on 2010-04-30
I think this is the link oldfred wanted to post:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

explains how to fix sudo.

---

### Post by holzpusher on 2010-05-01
Thanks for all the help, I'm a sudoer once again!

---

