---
title: "Authenticating the upgrade failed"
date: 2007-09-25
forum: Installation &amp; Upgrades
---

### Post by Im_Original on 2007-09-25
Hello everyone, 

I have been trying to update from edgy to feisty, but have problems. 

When I open the update manager from the terminal, I get this:

    me@mycomputer:~$ gksu "update-manager -c"
    warning: could not initiate dbus

The upgrade manager opens, when I click the button to upgrade, the update manager starts to download the files, but the progress bar goes nowhere. The terminal shows this:

    extracting '/tmp/tmpiCypuP/feisty.tar.gz'
    authenticate '/tmp/tmpiCypuP/feisty.tar.gz' against '/tmp/tmpiCypuP/feisty.tar.gz.gpg' 
    exception from gpg: GnuPG exited non-zero, with code 131072

And the update manager shows a warning box:

    Authentication failed

    Authenticating the upgrade failed. There may be a problem with the network or with the 
    server. 

I know that there is no problem with my network connection, the internet runs fine.  So it seems to be a problem with the servers, but it's been like this all day,  but that's a long time for servers to be down. So I have a few questions, and confusions that I was hoping someone could help me with,  please.

-What's the dbus? It didn't initiate, does this affect the update?
-Is there any other way to check if the servers are working? I would like to  try and verify whether or not that is the problem.  I could ping them if I knew the address, but I don't, and I don't know how to find it. 
-according to the output on the terminal, the update manager does something with '/tmp/tmpiCypuP/feisty.tar.gz.gpg' .   I looked for it, it's not there on my computer. Is it looking on the server?


Thanks alot

---

### Post by Im_Original on 2007-09-26
Anybody? Upgrading isn't essential at this point, but I would like to know what's going on. 

Thanks

---

### Post by Lesterchakyn on 2007-10-23
As weird as this may sound, I think it goes with the gpg personal keys not being created before the update.

I just ran gpg (no arguments), and it created the personal keys.

After that, I could run the upgrade with no problems.

---

### Post by Xoanan on 2007-10-23
How do you run gpg btw?

---

### Post by RedNikon on 2007-12-09
I had the same issue, after typing in ```
gpg
``` and then running the updater it all worked just fine.

---

