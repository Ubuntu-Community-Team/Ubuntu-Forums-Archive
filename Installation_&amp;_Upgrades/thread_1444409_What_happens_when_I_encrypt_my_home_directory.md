---
title: "What happens when I encrypt my home directory?"
date: 2010-04-01
forum: Installation &amp; Upgrades
---

### Post by leneflower on 2010-04-01
I'm just trying to migrate to Ubuntu 10 Beta from Gentoo. One option in the installer intrigued me. It said something like (from memory) "Use password to log in and decrypt my home directory". 

What happens behind the scenes when I choose this? (How) can I enable this later on? (I didn't activate it because I wanted to migrate my Gentoo user's home as painless as possible.) (Yes, it was completely painless, thanks for asking :-) )

Greets, Lene

---

### Post by foldingstock on 2010-04-01
Hello Lene, 

It is possible to encrypt the home directory after the install, but it is not as easy as clicking the radio button during the installation. When you encrypt it, essentially, there is a script the "decrypts and mounts" your home directory when you log in, and umounts it when you log out, putting it back in an "encrypted" state. 

For information on how to set this up, please check out the [Ubuntu wiki page.]("https://wiki.ubuntu.com/EncryptedPrivateDirectory")

The easiest way for you to go about encrypting your home directory after install would be something along the lines of: 

- Move everything in '/home/$USER' to another file, something like '/home/backup'
- Setup '/home/$USER' as an encrypted directory
- Log out and back in so the '/home/$USER' encrypted directory is mounted
- Move the files back into the newly-encrypted directory

Short of that, you may wish to setup an encrypted directory inside your home directory. This would allow you to still encrypted files you want hidden, but you wouldn't have to move anything around to set it up. Something like '/home/$USER/private' or similar.

---

