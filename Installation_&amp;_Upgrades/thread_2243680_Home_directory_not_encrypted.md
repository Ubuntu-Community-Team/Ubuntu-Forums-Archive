---
title: "Home directory not encrypted?"
date: 2014-09-10
forum: Installation &amp; Upgrades
---

### Post by hedden on 2014-09-10
I have set up a dual-booting system on a Dell laptop.  It can boot either Ubuntu 14.04 or Windows 7, using grub as boot manager.
When I installed Ubuntu, I am fairly certain that I asked it to encrypt my home directory.
When I first launched Ubuntu, I remember seeing a message about the encryption not being complete, and giving me several
choices to fix it, including "manual". However, I was experiencing the very slow graphics performance problem described here:
[http://askubuntu.com/questions/450555/very-slow-graphics-performance-after-upgrade-12-04-14-04](http://askubuntu.com/questions/450555/very-slow-graphics-performance-after-upgrade-12-04-14-04)
(I was able to solve the slow performance easily by installing and using gnome-panel and the Metacity window manager:
that's not the issue.) However, before I had solved the graphics performance problem, the system was so painfully slow
that I decided to wait to fix the encryption problem until after I had fixed the graphics problem. Once I had fixed the graphics
problem I was able to log in and use Ubuntu normally. However, the messages about fixing encryption no longer displayed.
I wanted to make sure that I had properly encrypted my home directory and had recorded the passphrase to recover it,
if necessary. I tried typing "encrypt-unwrap-passphrase", but the command is unrecognized.
I am fairly certain that my home directory actually is encrypted, because I created another user, enabled the root account,
and then tried, as root, to cd into my home directory from the other account. There was nothing there except some files
mentioning encryption. Can anyone explain what I should do to ensure that my home directory is properly encrypted,
that I know the passphrase to recover it, and also to ensure that the swap partition is encrypted?
Thanks in advance for any help.

---

### Post by hedden on 2014-09-10
Sorry, everyone. I don't know where I got the "encrypt-unwrap-passphrase" from
(I didn't invent it), but it's not spelled correctly. It should be "ecryptfs-unwrap-passphrase",
that is, with no letter "n" between the initial letters "e" and "c", and with "fs" before the
first hyphen: "ecryptFS-..." instead of "eNcrypt-...". I typed it correctly, and it worked fine.
Tom

---

