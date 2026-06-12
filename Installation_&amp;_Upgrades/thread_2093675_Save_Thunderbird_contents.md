---
title: "Save Thunderbird contents"
date: 2012-12-11
forum: Installation &amp; Upgrades
---

### Post by borgward on 2012-12-11
My HDD is failing. How do I save the emails and address book in Thunderbird for new install on new drive. Ubuntu 10.04

In the event the new HDD arrives, is there a way I can transfer my present installation w/all its contents to the new drive? (I have already transferred most of my stuff to a spare drive)

---

### Post by haqking on 2012-12-11
> **borgward said:**
> My HDD is failing. How do I save the emails and address book in Thunderbird for new install on new drive. Ubuntu 10.04

In the event the new HDD arrives, is there a way I can transfer my present installation w/all its contents to the new drive? (I have already transferred most of my stuff to a spare drive)

in your home directory, backup the .thunderbird folder which will be hidden

```
~/.thunderbird
```if it is an old version it may be in the ~./mozilla folder i cant remember when it changed, most recent versions are in ~./thunderbird

All my emails are IMAP acounts so i dont back it up, i just connect back to the accounts and everything is there anyways

---

### Post by SuperFreak on 2012-12-11
Someone may clarify this further, but I believe that emails are located under .Thunderbird/xyz.default/mail in the Home directory where xyz.default could be another combination of letters representing your profile. .Thunderbird is a hidden folder which can be found by pressing CTL-H when in the home directory. I think addresses can be exported from TB and saved on an external drive. Look under tools (open address book first)

edit:beaten to the punch

---

