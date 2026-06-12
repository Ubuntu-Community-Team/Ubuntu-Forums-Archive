---
title: "Encrypted Install Questions"
date: 2011-05-21
forum: Installation &amp; Upgrades
---

### Post by User4 on 2011-05-21
I would like to install Ubuntu onto a laptop to handle all of my personal files etc. Ideally I would like to put the whole installation onto an encrypted partition, but I not not have a lot of experience with Linux and I have a few questions: -

[LIST=1]
[*]How difficult is it to install Ubuntu on an encrypted partition?

[*]Can this be done from the standard installation disc?

[*]What are the usual problems?

[*]What would you expect the start-up times to be like if it were a ~50GB partition with a typical laptop core i3 processor?
[/LIST]

Is there anything else I should know?

Thank you

---

### Post by Dutch70 on 2011-05-22
I'm no expert in this area, but I'll answer the best I can & maybe someone will add to it.

1. It's not difficult at all. IIRC the installer will give you the option.
2. Yes
3. The only one I can think of is if you're system gets botched somehow, it will be difficult at best for someone to help you recover your files. 
4. Roughly 30-40sec.

You're swap partition will be encrypted also. Not that it's a problem. 

Anyone want to add to this???

---

### Post by User4 on 2011-05-22
Thank you Dutch, that's really helpful.

What do you mean by botched? - some kind of hard drive failure?

Can anyone else think of any reasons not to do this?

---

### Post by mseney on 2011-05-22
My experience with the latest release (Natty 11.04):

Only Encrypt /home - ubuntu-11.04-desktop ISO Image
Fully Encrypt      - ubuntu-11.04-alternate ISO Image

The problem that can arise is if you forget your encryption passphrase, you will never be able to access the contents of the drive. When a drive isn't encrypted and the Operating System becomes unusable, you can still plug the hard disk into another running machine or use a Live CD/DVD to access the files. This also means if someone gets ahold of your Laptop they have full access to your files. Personally, I would encrypt everything. Just make sure you never forget the passphrase. ;)

---

### Post by User4 on 2011-05-22
Thank you mseney.

I agree with you there, the fully encrypt option would have been much better.
Unfortunately I have installed using the 'encrypt /home' option.

How can I go about uninstalling ubuntu? - is this easy to do?
Where can I get hold of the alternate ISO image?

---

### Post by superdad0128 on 2012-01-07
i also have a question...? support still available?

---

