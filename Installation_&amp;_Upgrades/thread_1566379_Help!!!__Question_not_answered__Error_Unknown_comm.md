---
title: "Help!!!  Question not answered:  Error Unknown command 'keystatus'"
date: 2010-09-02
forum: Installation &amp; Upgrades
---

### Post by seldin on 2010-09-02
I saw 2 users asking the same question, but no one has answered that post...

I am posting this because it is also happening to me.

I've installed (through Wubi) Ubuntu 10.04, after rebooting,  I've got this error, waiting a couple seconds, Ubuntu started normally. This message now repeats whenever I start Ubuntu.

[B]Error: unknown command, keystatus

[/B]I always get this message when I boot to Ubuntu. How can I get rid of this message and fix this issue.

Thank you,

[EMAIL="larryTAKEOUT@seldin.net"]larryTAKEOUT@seldin.net[/EMAIL]

---

### Post by lechien73 on 2010-09-02
The problem may be elsewhere in your startup. The error regarding keystatus is probably harmless. As the Grub manual states:

> Checking key modifier status is *only supported on some platforms*.If invoked without any options, the keystatus command returns true if and *only if checking key modifier status is supported*.

There is a link [here]("https://help.ubuntu.com/community/Grub2"), which deals with Grub2. Search for 'wubi' in the document, it gives specific details which can be changed for wubi users.

---

### Post by lechien73 on 2010-09-02
Actually, after further investigation, I may have responded a little hastily :oops:

Since 'keystatus' is not supported on your system, the following becomes true:

> During boot, the system will check the SHIFT key status. If it cannot determine the key status, a short delay will enable the user to display the menu by pressing the ESC key.

I haven't tested this, but if pressing ESC during this delay brings up the Grub menu, then a solution to the problem would likely be:

From a terminal window, type:

```
sudo nano /etc/grub.d/30_osprober
```

Scroll down to the line, which says:

```
if sleep$verbose --interruptible 3 ; then
```

It's line 46 in my copy - press CTRL+C in nano to see your current position. It may also read:

```
if sleep$verbose --interruptible ${GRUB_HIDDEN_TIMEOUT} ; then
```

Change it to:

```
if sleep$verbose --interruptible 0 ; then
```

Press CTRL+X to save the file, and then run:

```
sudo update-grub
```

To commit the changes. I haven't tested this, but based on my understanding of the code and the logic involved, this should remove the delay after the failure to detect the Shift key status.

---

### Post by seldin on 2010-09-02
I am trying to save new version of file and it's not allowing me to do.

I then tried doing su
  to log in as super user.

I tried doing chmod 777 filename
  and it said operation not permitted.

So how do I write to this file

Thank you,

---

### Post by seldin on 2010-09-02
Lechan,


I needed to add one change to your suggestion. This worked great !!!
( basically, I removed any mention to keystatus and set timeout = 0;

Thank you,

- Larry



From:
=======================   begin  ================
if [ \${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep$verbose --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
======================= end ======================

To:

=======================   begin  ================
if [ \${timeout} != -1 ]; then
      set timeout=0
fi
======================= end ======================

---

