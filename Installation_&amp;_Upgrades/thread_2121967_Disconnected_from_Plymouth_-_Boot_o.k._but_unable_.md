---
title: "Disconnected from Plymouth - Boot o.k. but unable to login user"
date: 2013-03-03
forum: Installation &amp; Upgrades
---

### Post by Loerie on 2013-03-03
A new error (after some updates) does not allow me to log into the Ubuntu user/partition.

The system boots properly through GRUB, but instead of signing into the linux partition/ user, a black screen appears for a fraction of a second and I am back to the user login screen.

The same happens when logging into 'Guest'

The error message is very brief and appears to say:


> stopping anac(h)ronistic cron
[some other message which is too fast to read]
Starting the Winbind daemon winbind
saned disabled: edit etc/default/saned
mountall: Disconnected from Plymouth

... then back to the user log-in screen.

Many thanks

The password is correct.

Ubuntu Version:
3.2.0-38 pae (12.04-1)

---

### Post by MAFoElffen on 2013-03-04
That may be one of two problems, either a problem with the password or .Xuthority getting zapped.

If you can press <cntrl><alt><F2> and get to a virtual console session and is doesn't let you loggin then do Part 1. If it does let you log in Go do Part 2.

Part 1-
If at the Grub Menu, press the "e" key... Go down to recovery and select the menu item "root"...

With care, mount the root with read/write:
```

mount -o rw, remount /

```
Then see how your username is when it was installed:
```

ls /home

```
Then using the same spelling and case, replace "user_name" in the following command with your user name:
```

userpwd user_name

```
Enter in your password and confirm when it asked you.

Then reboot:
```

shutdown -r now

```

Part 2-
Follow Part 1 just to get to the root prompt, then:
```

ls /home    # Remember your user name like above's instructions
cd /home/user_name    # substituting your user name
rm .Xuthority
touch .Xauthority
chmod 600 .Xauthority
shutdown -r now

```

---

### Post by Loerie on 2013-03-06
**[COLOR=#ff0000]Updated response on 3/7/13:[/COLOR]**

Am able to go to the root prompt and the user-name directory and then tried to execute your Part 2; but commands could not be executed and returned the following error messages:

> rm: cannot remove '.Xauthority': no such file or directory

> touch: cannot touch '.Xauthority': read-only file system

> chmod: cannot access '.Xauthority': no such file or directory

How do I create this 'Xauthority' which seems to be elusive?


--------------------------------------------------------------------------------------------------------

Response of 3/6/13

I have tried...:

> If you can press <cntrl><alt><F2> and get to a virtual console session

I can, but "login incorrect" is the response.

Is this the usual username and password? If yes, I tried <cntrl><alt><F2>
 on a working partition and it also tells me 'login incorrect"; that's why I am asking.


Part 1-

at GRUB, I pressed "e" and this popped up:


> recordfail
insmod gzio
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --  ....


I added > mount -o rw, remount /  after set root=

then pressed F10

Still unable to login.

I must have done the wrong thing, so what is the right thing to do?

I am new and your patience is appreciated.

---

### Post by Loerie on 2013-03-15
Anyone?

---

### Post by grg3 on 2013-03-21
Make sure the disk is not full! That will give this error. Login at console and do df to see if that is the problem.

---

### Post by Loerie on 2013-03-24
Thanks grg3.

df shows that the disk is far from full.

Thinking back, 2 things happened prior to the problem.
There was an update and I killed Zeitgeist. The next bootup did not allow me to log in to the partition in question.

As I sucessfully killed Zeitgeist at another computer without a problem, it might be possible that the update has something to do with it.

I can use the other partion without a problem (which is what I am doing now). 

If there is no way to fix the missing .xauthority issue in order to log in to the other partition again (as mentioned above), perhaps I should start a new post: How to recover the data from the other, encrypted partition?

Your response is much appreciated.

---

