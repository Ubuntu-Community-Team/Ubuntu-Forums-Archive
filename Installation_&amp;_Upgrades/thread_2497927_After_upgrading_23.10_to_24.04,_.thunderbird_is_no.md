---
title: "After upgrading 23.10 to 24.04, .thunderbird is not deleted."
date: 2024-05-23
forum: Installation &amp; Upgrades
---

### Post by eduardp2 on 2024-05-23
Hi,
I upgraded 23.10 to 24.04 and I saw that took lots of space.
Then I saw that:
a) Two very heavy thunderbird folders exists. 
~/.thunderbird
and
~/snap/thunderbird

I assume .thunderbird is the DEB version folder and that this is not used anymore, so it can be safely deleted. Is it true?

b) ~/snap/thunderbird takes almost double the space of .thunderbird. On closer examination

~/snap/thunderbird/common/.thunderbird/<somecode>.default/ImapMail/<myIMAPserver>-1.com/
contains two shared.sbd folders:

shared.sbd
shared-1.sbd

while previous .thunderbird folder only contains one of them
shared.sbd

So, the question is... is it safe to delete one of them? Which one?

Thanks,

---

### Post by eduardp2 on 2024-05-24
Ok,

WARNING!!! This is my case... yours can be different! 

IN MY CASE!!! I ended up deleting both dirs, .thunderbird and ~/snap/thunderbird/common/.thunderbird/<somecode>.default/ImapMail/<myIMAPserver>-1.com/shared.sbd and everything looks ok.

WARNING!!! This is my case... yours can be different! 

I have only IMAP accounts, so it didn't have to be a problem If I mistakenly deleted something on the client side. I WOULDN'T HAVE DELETED THE DIRS IF I HAD A POP3 ACCOUNT!!!

BEFORE DELETING ANYTHING i went through the dirs:

~/.thunderbird/<somecode>.default/ImapMail/<myIMAPserver>-1.com/shared.sbd
~/snap/thunderbird/common/.thunderbird/<somecode>.default/ImapMail/<myIMAPserver>-1.com/shared.sbd
~/snap/thunderbird/common/.thunderbird/<somecode>.default/ImapMail/<myIMAPserver>-1.com/shared-1.sbd

and with dolphin I could see that IN MY CASE only shared-1.sbd was being modified today while the others did not have any update in files timestamps since the day I updated from 23.10 to 24.04.

SOLVED (IN MY CASE, NOT NECESSARY IN YOURS, BE CAREFULL!!!)

---

