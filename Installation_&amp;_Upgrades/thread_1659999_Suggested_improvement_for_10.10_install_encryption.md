---
title: "Suggested improvement for 10.10 install: encryption passphrase"
date: 2011-01-04
forum: Installation &amp; Upgrades
---

### Post by markling on 2011-01-04
Ubuntu's request for an encryption passphrase on installation could be greatly improved.

After installation, if the option to encrypt the home folder has been checked, Ubuntu prompts: "Record your encryption passphrase".

On running the action there are the following problems:
# When you type a passphrase, your keypresses are not indicated on the screen
# If you make a mistake typing the passphrase, and backspace, there is no way of knowing whether the backspace operation has worked
# The passphrase is typed once and the operation ends. There is no attempt to validate the correct entry of the passphrase by asking for it to be typed twice.

The combination of these shortfalls can be fatal. My last recorded encryption passphrase proved to be incorrect when after a critical failure I was required to enter my encryption passphrase to retrieve my data. It had not been backed up for a while. Ubuntu did not recognise my passphrase. Only after some dogged support from Canonical was the problem resolved.

I've just done a fresh install. I have butter fingers. I inevitably fumbled over the entry of my encryption passphrase. I have absolutely no way of verifying the passphrase I just set. Should Ubuntu ditch another critical failure on me, what do you think the chances are that my passphrase will work?

markling.

---

### Post by markling on 2011-01-10
The thing that caused the failure, btw, was changing my login password.

---

