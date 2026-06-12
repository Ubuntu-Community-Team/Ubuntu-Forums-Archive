---
title: "encryted /home directory on netbook"
date: 2010-03-18
forum: Installation &amp; Upgrades
---

### Post by rockhoppe7 on 2010-03-18
Hi,

How can I tell whether my /home directory is encrypted on my new netbook?

When I ran the karmic UNR installation program I chose the option "require a password to log in and decrypt your home directory", but I can't see any evidence that /home is encrypted.

When I'm logged in with my password, I can obviously see all my documents normally.  I want to check that encryption is working before copying my sensitive documents onto this machine.

Help gratefully received - thanks

---

### Post by uRock on 2010-03-18
Run this command in a terminal ```
ecryptfs-unwrap-passphrase
``` and if you have encryption it will let you know. If you don't have it, then check out the encrypted private folder set up on [this page]("http://bodhizazen.net/Tutorials/Ecryptfs/").

---

### Post by uRock on 2010-03-18
I personally use the private folder. It is much easier to set up and recover should you have to reinstall(provided there is a /home partition).

---

### Post by rockhoppe7 on 2010-03-18
Hi, thanks for your response.
When I ran ecryptfs-unwrap-passphrase, I was prompted for a 'passphrase' so I put in my login password.  This produced a 32-digit passphrase - the same one that was generated when I first installed.  Does this mean that my /home directory is encrypted?

Thanks

---

### Post by uRock on 2010-03-18
> **rockhoppe7 said:**
> Hi, thanks for your response.
When I ran ecryptfs-unwrap-passphrase, I was prompted for a 'passphrase' so I put in my login password.  This produced a 32-digit passphrase - the same one that was generated when I first installed.  Does this mean that my /home directory is encrypted?

Thanks

Sure does. Be sure to record that. If you were to throw in the LiveCD it will not be able to open your home folder nor show the actual size of the files within it.

Glad I could help,
Ronnie

---

### Post by rockhoppe7 on 2010-03-18
Thanks, that's great.
In your second post you say you prefer to use the private folder, because it's easier to set up and recover - could you explain about that, please, and point to some instructions?

---

### Post by uRock on 2010-03-18
> **rockhoppe7 said:**
> Thanks, that's great.
In your second post you say you prefer to use the private folder, because it's easier to set up and recover - could you explain about that, please, and point to some instructions?

The private folder is easier to set up within a non-encrypted partition. Once logged in there would be a Private within the Home folder along with Music and such and you can drop data into the folder which would encrypt the folder so that it can't be seen when someone else is logged in, if you have multiple accounts, and if someone uses any other means to mount the hard drive, then they will not be able to see the folder.
 To see more o how to do the private folder go to this link, which is written by one of the forum's admins. [http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/)

---

### Post by rockhoppe7 on 2010-03-18
Thanks, I'll check it out.
Really appreciate your help on this - and such speed! Amazing. Thanks
Best wishes, rockhoppe7

---

### Post by Berable on 2010-03-28
Guys, I have a big problem

After solve a problem with .ICEauthority file a can't access my private data because...
I forgot my passphase.... :frown:

There're a file named Access_Your_Private_Data.desktop and when I execute this I asked for my passphrase 

Many music, movies, source codes, documents..... I'm afraid...

This issue can be fixed? Or I will cry forever ...  :-({|=

---

