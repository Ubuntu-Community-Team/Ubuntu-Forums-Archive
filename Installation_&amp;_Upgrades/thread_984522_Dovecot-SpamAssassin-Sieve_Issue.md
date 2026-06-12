---
title: "Dovecot-SpamAssassin-Sieve Issue"
date: 2008-11-16
forum: Installation &amp; Upgrades
---

### Post by Phatzer on 2008-11-16
Hey guys,

I'm fairly new to working with linux in general and after reading guides and tutorials, I have my web/mail server working as intended, all apart from one little problem that is.

I decided today to enhance my email filtering from just using postgrey to using postgrey with spamassassin. Great, that was painless, however then I thought to myself "in for a penny, in for a pound", and so I though I'll stick Sieve in there too, so that it can shift email with 'X-Spam-Flag: YES' mail to my junk folder.

Well, after a few hours I've got nowhere. I've followed all guides, and this is what I have done...

- Added the cmusieve plugin to dovecot.conf (it exists in the plugin dir, I've checked)
- Made sure dovecot was set up for delivery in my postfix master.conf
- Added the mailbox and virtual transport lines for dovecot, and mailbox command for dovecot delivery to my postfix main.conf
- Added the .dovecot.sieve file to my mail home directory and told it what to do with email

Now, as far as I'm aware, Sieve then compiles the .dovecot.sieve file to .dovecot.sievec? Well this isn't happening, and I'm getting no errors anywhere, which is really annoying.

I've shifted the .dovecot.sieve file up and down a few directories in my mail directories, but no avail. I am getting "Warning: Killed with signal 15" quite often though if that's of any help.

There were a couple of commands that a few sites suggested, but none of them were found, unless you guys can suggest any.

Please tell me where I'm going wrong!

---

### Post by Phatzer on 2008-11-17
Managed to solve the issue, it was simply that my home directory was not set correctly, I had an extra $ in the path further down in the dovecot.conf file, oops!

---

