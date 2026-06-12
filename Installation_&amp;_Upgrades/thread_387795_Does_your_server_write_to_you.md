---
title: "Does your server write to you?"
date: 2007-03-18
forum: Installation &amp; Upgrades
---

### Post by Holzmann on 2007-03-18
I remember when I installed Ubuntu 5.10, someone advised me to set up an e-mail client so that the system could e-mail me notification messages, errors, etc. I didn't quite know what the person meant at the time and still have a vague idea.

Do you have your machine set up to send you messages via e-mail when a certain event takes place?

Thanks.

---

### Post by Mr. C. on 2007-03-18
There are numerous system services that can be configured to report on various activity.  These reports can be sent via email.   In addition, some services provide the capability to submit email to the system for delivery.  

The advice someone gave you was to install or configure some program (a client) to read this email.  You may already have dozens of nightly reports sitting in your inbox, waiting to be read.

There are command line and GUI mail programs (aka: MUAs short for Mail User Agents).

You can configure your system to leave mail on the local machine, or have it forwarded to an external email address.

Its all highly configurable, and depends entirely on your needs.

MrC

---

### Post by Holzmann on 2007-03-18
Well, I run Ubuntu Server, so forget the GUI.

If it is advisable to do, I would like my system to "report" certain events to me, critical ones at the least, and I am totally lost on how to do this. How do I select which events get reported and then how they are sent to a place where I can read them.

More detailed advice would be appreciated.

Thanks.

---

### Post by Mr. C. on 2007-03-18
There's no stock answer to your question.  I intentionally used vague terms and generalities only to indicate the possibilities.  Now its up to you to indicate specifically what you are after.

You may desire reports on how well your antivirus / antispam  mail server is performing (but it doesn't sound like you have one).  You may want reports on which files were downloaded from your website.  Or perhaps failed SSH connection attempts.

There are numerous log analysis programs that either mail nightly reports, or can alert you should some service fail.

Its best to approach this first by defining specifically what you are trying to accomplish, and what would satisfy that request.

The first step I would suggest is start looking at and learning about the various logs in /var/log.  Anything of importance will be there.  Start with the logs: messages, syslog, auth.log, and maillog.  As you become familiar with their contents, you may desire to automate some of your routine scanning.

MrC

---

