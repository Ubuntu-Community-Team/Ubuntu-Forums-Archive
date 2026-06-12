---
title: "Mail with error &quot;3 incorrect password attempts&quot; on  after upgrading to 11.10"
date: 2012-01-04
forum: Installation &amp; Upgrades
---

### Post by strfrank on 2012-01-04
Hi,
I have recently upgraded my hp 6710b laptop from 11.04 to 11.10.
This is my developement machine so I have postfix installed as well as truecrypt that mounts my favourite volumes, asking me for the password on gui login.
Every time I enter the truecrypt password (even if the password is correct at first attempt) I receive a mail from the same machine telling:

3 incorrect password attempts ; TTY=unknown ; PWD=/home/xxx ; USER=root ; COMMAND=/usr/bin/truecrypt --core-service


The encrypted partition is mounted and works correctly, but this message is very annoying and didn't happen before.
I've read something about PAM problems, but don't know if this is the case,
Thanks,
Frank

---

### Post by smitty3000 on 2012-12-27
I too have the same problem and this has been going on for years. Whenever I enter my password in truecrypt I get the '3 incorrect password attempts' message when I log in correctly the first time. This is unacceptable as I have my system set to email me when an error occurs. This happens on Ubuntu, Debian, Linux Mint and Sabayon. I too, believe PAM is not the problem. Can it be a truecrypt problem as no other authorization forms cause this? Anybody, please post a remedy to this situation or some other recourse.

---

### Post by Oliver Lau on 2013-02-16
> **smitty3000 said:**
> I too have the same problem and this has been going on for years. Whenever I enter my password in truecrypt I get the '3 incorrect password attempts' message when I log in correctly the first time. This is unacceptable as I have my system set to email me when an error occurs. This happens on Ubuntu, Debian, Linux Mint and Sabayon. ... Anybody, please post a remedy to this situation or some other recourse.

Try this:

I have two options to offer. 

  Option 1: Paste the following code in the /etc/sudoers.

 ```
USERNAME ALL=(ALL) NOPASSWD: /usr/bin/truecrypt
```Option 2: Paste the following code in the /etc/sudoers: 

```
%truecrypt ALL=NOPASSWD: /usr/bin/truecrypt
```And execute as follows:

```
sudo groupadd truecrypt
``````
sudo adduser $USER truecrypt
```   Tested: TrueCrypt 7.1 a released on February 7, 2012
OS: ubuntu 12.04 

Oliver Lau, Einbeck

---

