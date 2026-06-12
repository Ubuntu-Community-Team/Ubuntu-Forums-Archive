---
title: "Anyone else having this glitch?"
date: 2010-06-28
forum: Installation &amp; Upgrades
---

### Post by RJARRRPCGP on 2010-06-28
Updating fails to complete with a fresh Ubuntu 10.04 install! This means security updates failed!

I get an error when Update Manager is updating and found out in the details that an update failed, because a process locked a file! 

I wasn't even running anything else! 

It caused Update Manager to report broken packages! 

Strangely, Windows never had an issue with a process tying up a file when I run an update from a fresh install, when I make sure to run only the essentials!

---

### Post by Paddy Landau on 2010-06-29
I've not seen this before.

[LIST]
[*]Did you install while connected via Ethernet to the Internet? That sometimes helps.
[*]After the fresh install, reboot before you run updates.
[*]After running updates, reboot and check for any further updates.
[/LIST]
Sorry, I don't know what else to suggest.

---

### Post by Rubi1200 on 2010-06-29
What is the output of /var/log/dpkg.log for the relevant time period?

You could try running this:

```
sudo dpkg --configure -a
```

and see if the problem is resolved.

---

### Post by paparozoumis on 2010-06-29
> **RJARRRPCGP said:**
> Updating fails to complete with a fresh Ubuntu 10.04 install! This means security updates failed!

I get an error when Update Manager is updating and found out in the details that an update failed, because a process locked a file! 



Can you paste the message you get while updating?
Any detail as of what file is locked?

---

### Post by RJARRRPCGP on 2010-06-29
> **Paddy Landau said:**
> I've not seen this before.

[LIST]
[*]Did you install while connected via Ethernet to the Internet? That sometimes helps.
[*]After the fresh install, reboot before you run updates.
[*]After running updates, reboot and check for any further updates.
[/LIST]
Sorry, I don't know what else to suggest.

Yes. I'm connected with Cat5e. And I rebooted.

---

### Post by RJARRRPCGP on 2010-06-29
> **paparozoumis said:**
> Can you paste the message you get while updating?
Any detail as of what file is locked?

I dunno, because I just reformatted not long ago. Sorry.

I'm fine now, On June 27, 2010, I wiped my Barracuda 7200.12 HDD, repartitioned, reformatted and reinstalled Lucid Lynx. (partly, because my HDD seemed to be hanging and checked the beginning region of my Barracuda 7200.12 for bad sectors with MHDD) Then afterwards, the updates went fine. 

Then I installed the RT kernel, 2.6.33.4, from the bojo42 PPA.

---

