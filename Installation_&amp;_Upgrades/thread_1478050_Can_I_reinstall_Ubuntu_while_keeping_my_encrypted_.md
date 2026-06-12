---
title: "Can I reinstall Ubuntu while keeping my encrypted /home partition?"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by kramer65 on 2010-05-09
Hello,

Since a couple of days my Ubuntu pc [behaves strange]("http://ubuntuforums.org/showthread.php?t=1476703"). My applications menu doesn't open anymore, which makes Ubuntu fairly useless. 

So I decided I want to do a clean install while keeping my /home partition. The problem is that my home partition is encrypted. Would this cause trouble when I reinstall Ubuntu?

---

### Post by lemming465 on 2010-05-10
Reinstalling with an existing encrypted home partition is probably beyond the capability of the live desktop CD's.  It should be feasible from the alternate install CD's, if you have backed up your encryption keys first.

Is your home partition fully encrypted at the disk level, e.g. with LUKS (which would have required using an alternate install CD), or is it the more typical ecryptfs setup you get from doing a live desktop install and clicking the radio button for an encrypted home directory?

It's probably easier to repair the existing install.

---

### Post by brantlymurphy on 2010-05-27
Hello,
   So, same issue. Basically need to decrypt and (I have the key) mount pre existing encrypted /home/userhere (9.10 upgrading to 10.04). Simple issue If I had prior encryptfs experience; and lacking that. Need fix ASAP(production sys.) Any help?

---

### Post by verderben on 2010-07-07
If you haven't fixed your problem yet:

[B]Make a backup :) of /home

write down your encryption key:[/B]

```
ecryptfs-unwrap-passphrase $HOME/wrapped-passphrase
```

and then install a new ubuntu (using same username and pass)

and then overwrite the new /home with your backup

hopefully it works

more information:
[http://www.linux-mag.com/id/7568/1/]("http://www.linux-mag.com/id/7568/1/")

[http://ubuntuforums.org/showthread.php?t=1463392]("http://ubuntuforums.org/showthread.php?t=1463392")

> Re: reinstall and save separate encrypted home partition
I did some testing. I set up a clean install of Ubuntu 9.10 with a encrypted home in a separate partition. I put a few test files in home. Then installed Ubuntu 10.4 over the top of it. I selected the same partition for '/' and formated it. I selected the same partition as '/home' but did not format that one. I then used the same user name and password. The option for encrypting '/home' was already selected and grayed out so it could not be unselected. After install, home was readable and ready to go. I did not have to do anything else. 

There is lots of things that could make it so it would not work, so be sure to back up your files before you try it. Also note that I had home set up as a separate partition so if you did not manually set up your computer that way, this will not work. However, there may be some other way to do it.

Let us know if you have tried a something similar.

---

