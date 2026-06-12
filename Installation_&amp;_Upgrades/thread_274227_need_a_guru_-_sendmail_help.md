---
title: "need a guru - sendmail help"
date: 2006-10-09
forum: Installation &amp; Upgrades
---

### Post by davedekker on 2006-10-09
I know its most likely against the rules, but I have been trying to get sendmail configured on my new LAMP server with no luck... any guru's willing to help? I have searched and read about everything I could find... from "its the most complicated thing" to "it works right out of the box"... Please Please Please...

thanks

p.s. trying to get the server so that PHP cripts will send mails for things like signing up on forums I will be hosting


DD

[email]davedekker@gmail.com[/email]

---

### Post by cilynx on 2006-10-09
I know it doesn't really answer the question, but:

Don't use sendmail.  Sendmail is well documented is the largest security hole in all of *NIX.  Pretty much every other mail system in the world (postfix, exim, qmail) have a "sendmail" wrapper script that PHP can work with.  Personally I use Qmail.  DJB may be an ***, but his software is rock solid.

---

### Post by davedekker on 2006-10-10
will the PHP scripts have to be modified? or will it work the same? I'm not sure of the code they use.  

thanks,

DD

[http://www.trialsoftheswitch.com]("http://www.trialsoftheswitch.com")

---

### Post by cilynx on 2006-10-10
Generally, the scripts that come with the various mail packages are drop-in replacements for sendmail.  It is common practice to write PHP and such expecting "sendmail" because it's the standard.  Because of this, the other packages have "sendmail" scripts that act exactly as the real thing would only more secure as it calls the new system backend instead of actually using the atrocity that is sendmail.

In less words:

You will not have to modify the PHP scripts.

---

