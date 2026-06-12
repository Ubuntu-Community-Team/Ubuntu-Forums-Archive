---
title: "Fetchmail stale lock files"
date: 2018-03-04
forum: MINT
---

### Post by netsense on 2018-03-04
Hi all

I've been running the same mail configuration for years now: fetchmail  to download from my various POP accounts, dovecot to provide IMAP  services, and thunderbird as an IMAP client (plus Bluemail on my Android  device, although that's more recent). It's all on a single machine, running Linux-Mint 18.3.

In the past month, I've been getting periods where no mail is coming in,  and running fetchmail from the command line returns "removing stale  lock file" and then the emails arrive.

Does anyone know why fetchmail would hang like this, and what I can do about it?

Thanks in advance.
Edwin

---

### Post by HermanAB on 2018-03-05
That is 'normal'.  You have to improve your script to handle the errors!

---

### Post by coffeecat on 2018-03-05
*Thread moved to **MINT** sub-forum.*

---

