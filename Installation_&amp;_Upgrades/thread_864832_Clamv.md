---
title: "Clamv"
date: 2008-07-20
forum: Installation &amp; Upgrades
---

### Post by krsnavan on 2008-07-20
Has following questions on CLAMV?

1.Whether CLAMV has GUI interface?

2..Whether i can clean Windows Viruses,Spyware,Worms using that?
3.How to update the latest Signature files of CLAMV.

Vanna

---

### Post by Canis familiaris on 2008-07-20
1. It has ClamTk for GNOME. Klam for KDE.
You can install either of GUI by:
Applications->Add/Remove
Search for ClamAV and install

2. Yes it detects Windows viruses too.

3. ```
sudo freshclam
```

You do not need an antivirus, spyware remover in Linux. The only case you need Antivirus is when you share data with you friends and you care thatyou do not carry Windows viruses to their PC.

---

### Post by krsnavan on 2008-07-20
WIndows infected with lot of worms and spywares?

whethere i can mount a windows hdd and clean the files?

vanna

---

### Post by Canis familiaris on 2008-07-20
> **krsnavan said:**
> WIndows infected with lot of worms and spywares?

whethere i can mount a windows hdd and clean the files?

vanna
Could you post the output of:

```
sudo fdisk -l

```

---

### Post by Kevbert on 2008-07-20
If you're particularly interested in removing windows spyware (on Windows I assume) you should take a look at [[COLOR="Red"]Spybot[/COLOR]]("http://www.safer-networking.org/en/index.html").  It's free as in Ubuntu and runs in Windows.

---

### Post by Kevbert on 2008-07-20
Here's the [[COLOR="Red"]post[/COLOR]]("http://www.ubuntugeek.com/howto-install-clam-antivirus-with-gtk-frontend-gui.html") on how to install a GUI for ClamAv (in Linux).  It will only find Windows/DOS viruses.  To manually update virus signatures you need to use sudo clamtk from the terminal command line.  Once you've done this you can go to Help, Update Signatures in the ClamAv window.

---

### Post by wandalalakers on 2008-07-20
I've been using kubuntu, clamav and the klamav gui.  klamav said that I had an email phishing problem in thunderbird and said that I needed to quarantine an email.  Well, I told it to quarantine and klamavthe ended up deleting my entire thunderbird inbox.
I have backups of my email but I just thought that one email would have been deleted instead of my whole inbox.
Here is my klamav error and I've also attached a print screen.

email.phishing.dbldom-124
I would figure if this is true, there is only one email that's causing my problem.  Maybe it's a false positive.
I also normally report any phishing emails that I receive and delete them.
I recreated my email account so maybe this error won't come up again.  I'm rescanning after recreating my inbox to see if the error occurs again.
Well, after the 2nd scan, klamav didnt' report the email.phishing.dbldom-124 error anymore.

---

