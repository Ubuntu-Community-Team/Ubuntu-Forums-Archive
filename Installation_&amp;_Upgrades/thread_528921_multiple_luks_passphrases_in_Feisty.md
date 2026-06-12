---
title: "multiple luks passphrases in Feisty"
date: 2007-08-18
forum: Installation &amp; Upgrades
---

### Post by snaildarter on 2007-08-18
Hello.  I have installed fully encrypted (except /boot) Feisty to my laptop successfully.  I used the instructions at 

[https://help.ubuntu.com/community/FeistyEncryptedRootWithInstaller]("https://help.ubuntu.com/community/FeistyEncryptedRootWithInstaller")

Unfortunately, when booting, it always asks for me to "Enter Luks Passphrase" twice.  At first I thought this was because I had both the swap partition and the / partition encrypted, so I reinstalled using only / and a swap file.  No change.  I then tried to install using the LVM method, found at 

[https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto?highlight=%28encryptedfilesystem%29]("https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto?highlight=%28encryptedfilesystem%29")

But either I'm too stupid to follow those instructions, or they're wrong.

Can anyone tell me if it is possible to install a fully encrypted Feisty (except /boot) and only have to enter a passphrase once?  If so, how?  I've searched the Ubuntu forums and Googled it and can't find an answer.  If someone helps me with this, I will gladly contribute back to the community with a hopefully clear guide to installing an encrypted Ubuntu OS for Newbies.

Much thanks

---

### Post by snaildarter on 2007-08-20
I should probably have asked this question in a different way.  Why, when I've only got one encrypted partition (/), do I still have to enter the LUKS passphrase twice?  If someone can explain that to me, perhaps I can figure out how to fix it myself.

Thank you!

---

### Post by snaildarter on 2007-08-22
I've apparently asked a pretty hard question.  Could anyone please suggest a different forum I could post to for the answer?  It would be much appreciated.

---

### Post by snaildarter on 2007-09-04
Anyone?

---

