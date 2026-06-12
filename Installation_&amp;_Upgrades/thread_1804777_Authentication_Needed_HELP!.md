---
title: "Authentication Needed: HELP!"
date: 2011-07-15
forum: Installation &amp; Upgrades
---

### Post by Partian on 2011-07-15
Hey guys,
I keep on having to enter my password
each and everytime I am wanting to install an application/program
and it is starting to get abit irritating.

I am Administrator, I am the ONLY user.

ANy help would be GREAT!

Thanks,
Ryan Williams

---

### Post by Grenage on 2011-07-15
Greetings,

You're asked for a password so that it can temporarily escalate your permissions, and that's normal.  If it didn't ask for your password, it would be because you were logged in as a root user - this would be incredibly bad.  Experienced users won't even log in as root; it protects you from yourself and others.

The reason Windows XP was such a hell-spawn of viruses and malware was that nearly everyone ran it as a local administrator.

---

### Post by Partian on 2011-07-15
> **Grenage said:**
> Greetings,

You're asked for a password so that it can temporarily escalate your permissions, and that's normal.  If it didn't ask for your password, it would be because you were logged in as a root user - this would be incredibly bad.  Experienced users won't even log in as root; it protects you from yourself and others.

The reason Windows XP was such a hell-spawn of viruses and malware was that nearly everyone ran it as a local administrator.

SO this means that I can't disable it?
also, I have this 'key lock' thing that always pops up whenever I enter a password for a website, could I disable this also?

---

### Post by haqking on 2011-07-15
this question must get asked once a day in these forums.

Yes you can disable it by giving yourself a blank password which is BAD.

That means any code or malware has the opporttunity to run with admin privelege without you confirming it is ok.

IF you really want to do it then look up blank passwords, and the sudoers file  etc.

[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

like i said, this is not a good idea, whether you are the only user or not, it is not about users so much, more about code,scripts,processes,applications,malware etc being able to execute without you confirming it.

Would you leave your house front door open because you are the only person who lives there ? ;-)

---

### Post by Partian on 2011-07-15
> **haqking said:**
> this question must get asked once a day in these forums.

Yes you can disable it by giving yourself a blank password which is
BAD.
Yeah, I understand truely however, it gets annoying at times, when I try and do a speed download.

> **haqking said:**
> 
Would you leave your house front door open because you are the only person who lives there ? ;-)


An expression used not so much nowadays, but it is a powerful one.

But thanks for the link and the thought.
I will think about it abit more.

---

### Post by Grenage on 2011-07-15
> **Partian said:**
> SO this means that I can't disable it?
also, I have this 'key lock' thing that always pops up whenever I enter a password for a website, could I disable this also?

If you configure the machine so that you enter a password when the computer starts up (login screen), then the keyring shouldn't ask for a password.  As for the rest, as haqking also mentioned, you can set it so that there's no password, but expect no sympathy if you end up with a toasted machine.

---

