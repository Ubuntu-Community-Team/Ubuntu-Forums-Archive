---
title: "Create live USB with persistence"
date: 2019-12-11
forum: Installation &amp; Upgrades
---

### Post by sab12345 on 2019-12-11
I just created an Ubuntu 19.1 live USB flash drive, using Rufus in Windows and ubuntu-19.10-desktop-amd64.iso, and the USB drive has no persistence. If I change the time zone from UTC to EST, it does not persist to the next session, which reverts back to UTC. What do I need to do to create a live USB drive that has persistence?

---

### Post by sudodus on 2019-12-12
@sab12345,

It depends on the operating system, where you create the drive (Ubuntu, another linux distro, Windows or MacOS). Rufus is a tool for Windows, but you might be able to use the Ubuntu live drive that you have already (although not yet persistent) or some other computer.

The following link to AskUbuntu shows some alternatives,

[How is it easier to make a persistent live drive with Ubuntu 19.10?](https://askubuntu.com/questions/1181854/how-is-it-easier-to-make-a-persistent-live-drive-with-ubuntu-19-10)

---

### Post by coffeecat on 2019-12-12
@sab12345, I've moved your post and the reply from sudodus into a new support thread from the chat thread you posted to, and re-titled it. If you have a support question, please create your own thread.

---

### Post by yancek on 2019-12-12
It should work if you are using  Ubuntu 19.10 and have version 3.7 or newer of Rufus, explained at the link below.  If it still doesn't work, you might post more specifics on what you did and how you did it.

[https://www.linuxuprising.com/2019/08/rufus-creating-persistent-storage-live.html](https://www.linuxuprising.com/2019/08/rufus-creating-persistent-storage-live.html)

---

### Post by sab12345 on 2019-12-12
Problem solved by using a newer version of Rufus, 3.8, and specifying a size for the persistence partition.

---

### Post by sudodus on 2019-12-12
Please be aware the the ext3 file system in the partition for persistence by Rufus is experimental.

Good luck :-)

---

