---
title: "How to acces my private data ???"
date: 2016-01-18
forum: MINT
---

### Post by alex295 on 2016-01-18
Hi everybody ! I have recovered /home with folder alex that have 2 files : Access-Your-Private-Data.desktop , and README.txt . I don't know where to put the file Access-Your-Private-Data.desktop  in such a way that i can acces all files on folders : Downloads , Documents , Music , Pictures , Settings & Hidden Programs Files . Do you know how to resurrect /home partition and to see these files in these folders ??? Please help!  :|

---

### Post by ajgreeny on 2016-01-18
I assume you have been using an encrypted /home or perhaps full disk encryption, in which case I also assume that the Access-Your-Private-Data.desktop file is a shortcut to the dialog which appears asking for the encryption passphrase.

What do you see if you double click that Access-Your-Private-Data.desktop file?
Do you know the encryption passphrase?

If not, I'm afraid you are unlikely to get any of your data back; that is the whole point of encryption, ie, that it is impossible to retrieve without the passphrase.

It is, therefore, essential to have good backups of everything if using encryption, as all data will be lost with no password, and even with a password could be lost if the encrypted partition becomes corrupt in some way.

---

### Post by alex295 on 2016-01-20
If i open file Access-Your-Private-Data.desktop from recovered /home partition i get the error mesage : Could not display "/media/alex/E - Toshiba/ho/R...ess-Your-Private-Data.desktop". The location is not a folder. If i put this file on current /home user folder and after that i open it my /home partition it will be destroyed . Maybe i placed this Access-Your-Private-Data.desktop in a wrong place and after that i opened it and my Linux get crush . Please i wanna know how to ressurect my lost /home partition or ressurect the recovered /home partition . Where i have to place this file to ressurect/populate my actual home partition ? I will do anything to access my private data ! Please , help me , please !

---

### Post by Rob Sayer on 2016-01-20
The only thing I can find is here:

[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

... under "Recovering Your Mount Passphrase".  But if you don't have the file they mention, or your pass phrase, you're out of luck.  As mentioned, this is what encryption is for.

---

### Post by alex295 on 2016-01-24
Thanks !

---

