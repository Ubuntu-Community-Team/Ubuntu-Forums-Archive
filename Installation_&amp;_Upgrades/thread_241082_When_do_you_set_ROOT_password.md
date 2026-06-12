---
title: "When do you set ROOT password?"
date: 2006-08-21
forum: Installation &amp; Upgrades
---

### Post by ChantCd_com on 2006-08-21
I just installed Ubuntu 6.06.1 LTS (Server disk)
I opted to install to HD, NOT to install the LAMP server.

I went through the whole install, including where it asked me for a user "besides root" to login as.

But it never once asked me for a Root password!

How do I set the root password now?

Matthew

---

### Post by BitTorrentBuddha on 2006-08-21
```
sudo -s -H
passwd
```
But because of using sudo you shouldn't need a root password.

---

### Post by Tomosaur on 2006-08-21
Sudo is a security feature so that you don't need to create a root account / password.

---

### Post by BitTorrentBuddha on 2006-08-21
On an opposite note, how do I unset my root password lol? Accidentally set it when trying that out.

---

### Post by ChantCd_com on 2006-08-21
Thanks for the help -- I managed to find another thread with a link to a place where you can set the root password.

I don't like strange quirks like "no root password." 
I'm too used to having a root password -- as for security, I'll have to just use a real good password.

Matthew

---

### Post by VK2XCI on 2006-08-21
> **ChantCd_com said:**
> Thanks for the help -- I managed to find another thread with a link to a place where you can set the root password.

I don't like strange quirks like "no root password." 
I'm too used to having a root password -- as for security, I'll have to just use a real good password.

Matthew

If there is one thing that I DONT like about Ubuntu it's this strange "no root account" **feature**. Specially no root user graphical login. I got used to it in Mandrake and old habits are hard to break. It's bad enough that Windows treats me like an idiot without Linux doing it too :p 

Only thing that stops me going back to Mandriva is the .deb packaging system. I could neve go back to .rpm, even with yum.

 Now I may be missing something here and there may be a way to do it, like starting X from console while logged in as root.?

---

### Post by BitTorrentBuddha on 2006-08-21
[color=red]ILL-ADVISED, USE AT YOUR OWN RISK[/color] 

To enable graphical root login, go to System -> Administration -> Login Window and select the Security tab. From there enable "Allow local system administrator login."

---

### Post by aysiu on 2006-08-21
I don't see how the *sudo* model is "treating you like an idiot." It's just different from the root model, and I think it's preferable.

For the reasons as to why, read this:
[http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)

For a better and more convenient way to make root changes graphically than logging in as root:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

Have an open mind. I've used both the root/user model and the *sudo* model, and I much prefer the *sudo* model now, even though it took some getting used to.

---

