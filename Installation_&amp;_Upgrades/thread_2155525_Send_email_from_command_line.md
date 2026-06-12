---
title: "Send email from command line"
date: 2013-06-18
forum: Installation &amp; Upgrades
---

### Post by vjwebb on 2013-06-18
I need to be able to send an email message from a script running via a cron process.  The email will just inform me of the script status.  I already do this kind of thing on a server running an old version of Red Hat.  It uses the mail command.  However, apparently that isn't part of the default install of Ubuntu.

What do I need to install on ubuntu to accomplish this?  This will be the only email that is generated on the computer.

Any help will be greatly appreciated.

V J

---

### Post by SeijiSensei on 2013-06-18
Install the **mailutils** package which provides the "mail" command-line client.

---

### Post by vjwebb on 2013-06-18
> **SeijiSensei said:**
> Install the **mailutils** package which provides the "mail" command-line client.

Thank you.  I will do that.

---

### Post by sanderj on 2013-06-18
Another option: mailsend. See [https://code.google.com/p/mailsend/](https://code.google.com/p/mailsend/)

---

### Post by vjwebb on 2013-06-18
> **sanderj said:**
> Another option: mailsend. See [https://code.google.com/p/mailsend/](https://code.google.com/p/mailsend/)

I think I like this one better and it says that it also works from windows.  I have been looking for something on windows also.

Thank you.

---

