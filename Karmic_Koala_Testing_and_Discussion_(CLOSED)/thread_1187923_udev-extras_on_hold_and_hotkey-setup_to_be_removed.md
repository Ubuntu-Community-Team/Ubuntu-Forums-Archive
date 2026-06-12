---
title: "udev-extras on hold and hotkey-setup to be removed"
date: 2009-06-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by zika on 2009-06-15
Should I update  with title taken in account ... ? :)
apt-get keeps udev-extras back but does not mention hotkey-setup...
synaptic doesn't bother about udev-extras and suggest to update it but wants hotkey-setup to be removed...
which one is right ... ?

---

### Post by dino99 on 2009-06-15
i've updated without bad surprise !!!
When i've checked for updates, partial upgrade was done, then i've manually accept removal & install: every thing work fine (i'm not on a laptop so i don't know for you)

---

### Post by chrisccoulson on 2009-06-15
It would really help for you to read the changelog, which explains the situation quite clearly:
> udev-extras (20090615+1-1) karmic; urgency=low

  * Update to git 190658b9:
    - Add hid2hci.
    - udev-acl: add sound card input-jack devices.
    - Some bug fixes.
  * Add Conflicts: hotkey-setup, since we have taken over keymap handling now,
    and hotkey-setup only has some old cruft which sometimes even breaks keys.
    (LP: #384511)
  * Add debian/README.source to explain source package structure and how to
    merge to a new upstream snapshot.

 -- Martin Pitt < [email]martin.pitt@ubuntu.com[/email]>   Mon, 15 Jun 2009 08:40:42 +0200

---

### Post by zika on 2009-06-15
> **chrisccoulson said:**
> It would really help for you to read the changelog, which explains the situation quite clearly:It would really help if You've put the URL from which I could "read the changelog, which explains the situation quite clearly:" ... Thank You. I'm sorry for not being properly informed ... I'll try to try harder in the future ...

---

### Post by psyke83 on 2009-06-15
> **zika said:**
> It would really help if You've put the URL from which I could "read the changelog, which explains the situation quite clearly:" ... Thank You. I'm sorry for not being properly informed ... I'll try to try harder in the future ...

It's important to be informed in situations like this - never accept Partial Upgrades without researching beforehand. I believe that users who opt to test alpha releases should know this information (there's no shame in not knowing these things, since we all started from scratch at some point ;)).

[This]("https://lists.ubuntu.com/archives/karmic-changes/") link will be useful for future reference.

---

### Post by zika on 2009-06-15
> **psyke83 said:**
> It's important to be informed in situations like this - never accept Partial Upgrades without researching beforehand. I believe that users who opt to test alpha releases should know this information (there's no shame in not knowing these things, since we all started from scratch at some point ;)).

[This]("https://lists.ubuntu.com/archives/karmic-changes/") link will be useful for future reference.

I'm subscribed to that for some time ... :). Thank You. I am not ashamed being all the time at the "scratch point". The more I learn I realize more how much is there to learn. As You can see I am not ashamed to ask. I was doing research ... and I did not accept partial upgrade (yet) at least in Karmic, one or two glitches in Jaunty ... :) Thank You for great advices ...

edit: it's my mistake: I thought of mailing list listed below and not this place ... Sorry. As I said. I do learn everyday ... :)

---

### Post by castrojo on 2009-06-15
> **zika said:**
> It would really help if You've put the URL from which I could "read the changelog, which explains the situation quite clearly:" ... Thank You. I'm sorry for not being properly informed ... I'll try to try harder in the future ...

It helps to follow this list: [https://lists.ubuntu.com/mailman/listinfo/Karmic-changes](https://lists.ubuntu.com/mailman/listinfo/Karmic-changes)

---

### Post by taavikko on 2009-06-15
also quite handy tool to check the changes:
```
aptitude changelog package
```

---

### Post by psyke83 on 2009-06-15
> **taavikko said:**
> also quite handy tool to check the changes:
```
aptitude changelog package
```

Yes, though the mailing list has the advantage of showing packages that have yet to be built and seeded to the servers. You may catch some important information that way.

---

### Post by taavikko on 2009-06-15
> **psyke83 said:**
> Yes, though the mailing list has the advantage of showing packages that have yet to be built and seeded to the servers. You may catch some important information that way.

Yes, don't dispute the mailing list, "aptitude changelog" tip was meant for those who didn't know the existence of it...

quick way to see changes in a package (once the info is available)

---

### Post by zika on 2009-06-15
> **whiprush said:**
> It helps to follow this list: [https://lists.ubuntu.com/mailman/listinfo/Karmic-changes](https://lists.ubuntu.com/mailman/listinfo/Karmic-changes)
subscribed ... Thanks ... Must admit, it comes in batches and I do not get to read every bit ... :)

edit: @taavikko: **aptitude changelog package** is a great tip, I did not know about that ... Thanks ... I'll have to eplore it, if it is available at the moment of confusion and doubt to upgrade or not to upgrade ...

The problem with *udev-extras*, as it happens most of the times, solved by itself but I have learned lot of stuff ... Thank You all!

---

### Post by Starks on 2009-06-15
> **zika said:**
> It would really help if You've put the URL from which I could "read the changelog, which explains the situation quite clearly:" ... Thank You. I'm sorry for not being properly informed ... I'll try to try harder in the future ...
In Synaptic:

Package > Download Changelog

---

### Post by zika on 2009-06-15
> **Starks said:**
> In Synaptic:

Package > Download Changelog
Great! Thank You.

---

