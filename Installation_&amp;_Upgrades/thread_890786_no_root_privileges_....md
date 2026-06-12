---
title: "no root privileges ..."
date: 2008-08-15
forum: Installation &amp; Upgrades
---

### Post by Bucky Ball on 2008-08-15
I have just installed Ubuntu Studio Hardy on my desktop and had a few problems logging in. Refer to this solved post below for detials:

[HTML]http://ubuntuforums.org/showthread.php?t=890707[/HTML]

Now I am in (posting from the machine in question) and exploring the new desktop set up. Trouble is, I have no root priveleges to anything. Try to open nautilus and this is the result;

```
gksudo nautilus
Failed to run nautilus as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.
```

The beat goes on. All ideas appreciated ... :)

---

### Post by tamoneya on 2008-08-15
it seems as if you arent in the sudoers file but lets just give it a test:```
sudo nano ~/test.txt
```
If you still get an error you should restart and boot into recovery mode (hit escape at the grub prompt and select recovery).

Then follow this guide to modify sudoers.  It is best if you make a backup.

[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

The other thing you should check is to make sure you are in the admin group.

EDIT: now that I think about it it is probably best if you do the admin group stuff first.  So run the test,  go to recovery mode, check admin group, check sudoers.

---

### Post by Pumalite on 2008-08-15
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Bucky Ball on 2008-08-15
```
$ visudo
visudo: /etc/sudoers: Permission denied
$ sudo visudo
[sudo] password for ustudio: 
ustudio is not in the sudoers file.  This incident will be reported.
$ 
```

That&#347; about the size of it so far. Note how I have just got ´$´ and not ´root@user´ first. (?) This does not seem normal.

---

### Post by tamoneya on 2008-08-15
have you logged in through recovery mode (single user mode).  If you do this you will automatically be root.

---

### Post by Bucky Ball on 2008-08-15
> **tamoneya said:**
> have you logged in through recovery mode (single user mode).  If you do this you will automatically be root.

Yep, gave that a go and looked at the instructions but not really sure what I should be doing in there. Ran ´visudo´ as suggested but not sure how to edit that file to make any difference, apart from unhash passwords so no-one requires one, and I don´t want to do that.

Oddly, it shows root@ustudio on the way out of there and that is what is missing from my terminal when I am logged into ustudio desktop. Hmm. I am confused ....

---

### Post by Bucky Ball on 2008-08-15
Okay, latest update ...

I have been booting into the recovery kernel, going to a terminal shell and plugging in;

```
visudo
```

It show me the file but won´t let me edit it. I am wanting to try adding;

```
ustudio ALL=(ALL) ALL
```

under the line that says;

```
root ALL=(ALL) ALL
```

... an idea from this page ...

[HTML]http://www.pendrivelinux.com/2007/10/05/how-to-add-a-user-to-the-sudoers-list/[/HTML]

I seem to be getting somewhere but can´t edit that file ... :confused:

---

