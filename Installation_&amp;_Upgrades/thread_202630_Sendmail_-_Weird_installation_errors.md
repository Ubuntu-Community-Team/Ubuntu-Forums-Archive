---
title: "Sendmail - Weird installation errors?"
date: 2006-06-23
forum: Installation &amp; Upgrades
---

### Post by mafitzpatrick on 2006-06-23
Hi folks,

I've installed sendmail for use with php development.  After install (using synaptic) it works instantly and is able to send emails.  However, on re-starting the computer it gets as far as "Starting basic networking..." then throws out the following errors (not copied verbatim):

[INDENT]rm Cannot remove /etc/mail/sendmail.cf read only filesystem.

/usr/share/sendmail/update_auth line 98 - Cannot create temp file for here document

Do (or words to that effect) /etc/init.d/sendmail reload
[/INDENT]

After restart sendmail no longer works.  Doing what is suggested in the bottom line achieves nothing (just sits waiting in terminal until Ctrl-C). Changing file permissions on the files mentioned does not help anything.

Any suggestions? Other people seem to get this working out of the box.

---

### Post by x-64 on 2006-06-26
Have a look here:

[https://launchpad.net/distros/ubuntu/+source/sendmail/+bug/43752]("https://launchpad.net/distros/ubuntu/+source/sendmail/+bug/43752")

Looks as though there's a fatal bug either in sendmail or ubuntu. The best option as far as I can see is to use postfix instead, it's far more secure anyway and I haven't encountered any problems with it.

Hope this helps.

---

### Post by mafitzpatrick on 2006-06-28
Guess I'll remember to look at launchpad next time before I post "UH?" questions!

Thanks for your help x-64, much appreciated.


Interestingly - why doesn't the link to the "Ubuntu bug tracker" on the top right point to [Ubuntu]("https://launchpad.net/distros/ubuntu") itself, or better yet [the bug tracker]("https://launchpad.net/distros/ubuntu/+bugs"). [The launchpad base (malone)]("https://launchpad.net/malone") is a bit confusing - I would never have found the Ubuntu bit without your linK!

---

