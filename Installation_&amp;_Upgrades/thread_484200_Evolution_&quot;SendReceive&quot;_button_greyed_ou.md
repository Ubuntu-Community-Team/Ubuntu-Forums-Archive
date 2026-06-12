---
title: "Evolution &quot;Send/Receive&quot; button greyed out - can't send or recieve email"
date: 2007-06-25
forum: Installation &amp; Upgrades
---

### Post by bumpkin on 2007-06-25
I just upgraded from Dapper to Feisty by installing from CD. Before I did so I tar'd up my home directory to later move to the new install. 

I now have the new install working but evolution's "send/receive" button is greyed out. I have checked the account information and even successfully used the "authentication" buttons for out-going and in-coming mail servers which checks for authentication types available from the server.

I can see my email that I copied into the "mail" dir. I have tried to send but the email goes to the "outbox".

Any suggestions?

---

### Post by bapoumba on 2007-06-25
Hello :)

Just a guess: may be going from dapper to feisty was a big jump as far as conf files (which  you copied from dapper, am I right?).

Did you try to set up evolution from freshly installed feisty? Did it work? The idea being that if you got backups, you just delete the .evolution from your /home, or the files you unpacked, and see if the send/receive buttons are back.

I'll have to look around which files you have to copy to get your mails back (and I'm interesting in knowing, as I backup my mails from evolution, but I never had to restore them...).

---

### Post by bumpkin on 2007-06-25
Fixed the problem. 

Default setting is to work off-line which greys out the buttons.  Select File -> work on-line allows you to use the send/receive button.

---

### Post by bapoumba on 2007-06-26
> **bumpkin said:**
> Fixed the problem. 

Default setting is to work off-line which greys out the buttons.  Select File -> work on-line allows you to use the send/receive button.
Glad to see you found the way to fix this (and sorry, it must have been the same for me here, I just do not remember).

---

### Post by merelyme2 on 2008-05-13
> **bumpkin said:**
> Fixed the problem. 

Default setting is to work off-line which greys out the buttons.  Select File -> work on-line allows you to use the send/receive button.

Just thought I would add that this happened to me after upgrading to 8.04 and the default setting was enabled to **work [B]online**[/B],but the send/receive was still greyed out. To fix this, I set it to **work offline,** then closed out of evolution, restarted it, then set option back to **work online**. I could then send and receive e-mail and the link was no longer greyed out.

merelyme2

---

### Post by eternalnoob on 2008-06-04
Just a minor clarification
I don't think work offline is the default setting. I think the restore from backup is the thing that sets it to work offline. 
The same thing happened to me when I installed Hardy.
send/receive was working OK
I restored my evolution backup from Gutsy and the send/receive button was greyed out.
I stared at that greyed out button for 3 days until I came across this thread. Thanks guys

---

### Post by GreenLinux@R on 2008-06-13
I appreciated it too. It fixed my same problem. Thanks.

---

### Post by ericartman on 2008-06-28
OK for me it wasn't an upgrade but rather a recent update to my evolution program that left it in "work offline" mode thanks for the fix.

Cart

---

### Post by mrajdl on 2008-07-03
Same happened to me after upgrading to 64 bit ubuntu,  I feel stupid for overlooking the work offline.  Thanks.

---

