---
title: "No encryption option after clean install of 11.04"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by Dada Maheshvarananda on 2011-05-05
After installing 11.04, adding the public keys of friends to the Passwords and Encryption Keys and generating a new public key. However there is no encryption option when right clicking a file, nor is there any user interface for Seahorse or GNU Privacy Guard. When I try to open an encrypted file, I get the error message, "There is no application installed for PGP/MIME-encrypted message header files".

---

### Post by Dada Maheshvarananda on 2011-05-05
> **Dada Maheshvarananda said:**
> After installing 11.04, adding the public keys of friends to the Passwords and Encryption Keys and generating a new public key. However there is no encryption option when right clicking a file, nor is there any user interface for Seahorse or GNU Privacy Guard. When I try to open an encrypted file, I get the error message, "There is no application installed for PGP/MIME-encrypted message header files".

If I type 'seahorse' in Terminal, what opens is Passwords and Encryption Keys, without any option to encrypt or decrypt with the keys.:confused:

---

### Post by Dada Maheshvarananda on 2011-05-09
> **Dada Maheshvarananda said:**
> If I type 'seahorse' in Terminal, what opens is Passwords and Encryption Keys, without any option to encrypt or decrypt with the keys.:confused:

SOLVED: In terminal, type: 'sudo apt-get install gpa'

Then type: 'gpa'

---

### Post by rwh on 2011-07-06
Actually, I think what you really want is the seahorse-plugins package, AKA "Decrypt File" in the Ubuntu Software Centre.  This gives you an "Encrypt..." option in the right-click menu in Nautilus, and integrates with the keys you have stored on your system (managed by seahorse, AKA "Passwords and Encryption Keys".

---

