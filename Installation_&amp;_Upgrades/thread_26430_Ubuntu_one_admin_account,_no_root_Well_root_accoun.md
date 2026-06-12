---
title: "Ubuntu: one admin account, no root? Well root account exists."
date: 2005-04-12
forum: Installation &amp; Upgrades
---

### Post by Kosmotron on 2005-04-12
What did I do wrong? :) On Warty, it "disabled" root account and sudo worked. On Hoary, root account is enabled by default and sudo isn't working on my "user" account. Thanks in advance.

---

### Post by lao_V on 2005-04-13
Can you tell us what's in your sudoers file? And, does your 'user' belong to the admin group?

---

### Post by marsopia on 2005-04-13
Same happens to me. I instlled Hoary in expert mode, and I ,surprisly, been asked for an Admin passws. I went trough all installation and now I have no access to Synaptyc, for example, usign my user passwd. 

What must I do?

I read something like this on Hoarys development forum, but now is closed...

how can I fix this problem? Where is the sudoers file allocated?

Mariano

---

### Post by Kosmotron on 2005-04-13
[QUOTE=lao_V]Can you tell us what's in your sudoers file? And, does your 'user' belong to the admin group?[/QUOTE]

Without commented lines:

[FONT=Courier New]Defaults        !lecture,tty_tickets,!fqdn
root    ALL=(ALL) ALL[/FONT]

And no, the user does not belong to admin group.

---

### Post by dusu on 2005-04-13
Hi Kosmotron,
for what concerns your sudoers file, it should look like :
```
# User privilege specification
root    ALL=(ALL) ALL

# Added by Ubuntu installer
Kosmotron ALL=(ALL) ALL

```
(if your user name is Kosmotron, of course).

---

### Post by Kosmotron on 2005-04-13
I sort of figured out :)

But how come I'm reading from various places that Hoary should by default install like Warty, with root disabled and sudo-ready? Is it officially different from Warty or just "this probably goes with Hoary too, haven't tried" sort of thing? And was all that Hoary basically did (regarding this subject) was add the admin user to sudoers file and passwd -l root?

---

### Post by traderjb on 2005-04-22
Forgive me, but I too am having similar problems.  As a newbie to Ubuntu and Linux, I am not all familiar with this sudoer file.  Where can I find it?  I wish to get on the internet, but first need to setup the networking.  But to do this, I get a dialog box asking for my password.  I had just installed Ubuntu and not once was I asked for some sort of administrative password.  Please help me, I don't wish to go back to Windows XP!

---

