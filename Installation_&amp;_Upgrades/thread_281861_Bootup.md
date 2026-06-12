---
title: "Bootup"
date: 2006-10-21
forum: Installation &amp; Upgrades
---

### Post by dmsn on 2006-10-21
Hey
Also another problem i have.
This always starts when i reboot my computer, how should i do
to fix it?

110/tcp open  pop3
143/tcp open  imap
631/tcp open  ipp
993/tcp open  imaps
995/tcp open  pop3s



Thanks

---

### Post by raul_ on 2006-10-21
It shouldn't? It seems it's opening ports..if want them closed use a firewall. Try firestarter. I think that's what's going on :S

---

### Post by dmsn on 2006-10-22
I use firewall script with iptables and it blocks it for sure.
But i dont want to run alot of services i dont use.
So plese tell me a more correct answer, if you can :p

---

### Post by Original Brownster on 2006-10-22
Hi,
It appears you have installed a mail server component, an MTA like postfix or sendmail etc. as these require these ports open, your answer I believe is looking at inetd 'man inetd' (look at /etc/inetd.conf too) the internet superserver listens on specific ports for services running on your machine' this would be automatically configured for you when package 'x' is installed, so if you install an MTA like postfix it takes care of configuring inetd for you. 
Assuming your not using an MTA (just getting mail from your ISP via pop3) you can un-install the MTA and it (ubuntu) should reconfigure it for you.

HTH

---

### Post by dmsn on 2006-10-22
Its fixed i just did sudo chmod -x imap pop3
;)

---

