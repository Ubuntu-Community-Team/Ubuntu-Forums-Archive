---
title: "Nautilus ssh keeps prompting for password"
date: 2010-02-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Pollox on 2010-02-20
I use Nautilus' "connect to server" function to ssh into a server, and store the password in my keyring so it doesn't prompt me for a password every time.  This was working fine up until a few days ago, but now every time I connect or even navigate to a new folder, a window pops up saying "OpenSSH" at the top and prompting for my password again.  Anyone else experiencing this issue?

---

### Post by Toe on 2010-02-20
I've seen the same kind of behaviour appear for samba shares.
Previously the password was stored forever, now I have to enter it every time I access a share.
Started a few days ago. I think I recall that there was a gnome-keyring update. Could this be related?

---

### Post by cariboo on 2010-02-21
I use public/private keys to connect to my server via ssh. Nautilus asked for my pass-phrase the first time I connected, and hasn't asked since. I see nothing in the keyring about it though.

---

### Post by sonicb00m on 2010-02-22
i foudn this problem in the past if i didn't use a URL with a username in it.

ie. [email]username@server.com[/email]

If the username was the same as the user name I was logged in with in Ubuntu it worked ok.

---

### Post by Pollox on 2010-02-23
> **cariboo907 said:**
> I use public/private keys to connect to my server via ssh. Nautilus asked for my pass-phrase the first time I connected, and hasn't asked since. I see nothing in the keyring about it though.

Using public/private keys fixed this issue for me.  Thanks.

---

