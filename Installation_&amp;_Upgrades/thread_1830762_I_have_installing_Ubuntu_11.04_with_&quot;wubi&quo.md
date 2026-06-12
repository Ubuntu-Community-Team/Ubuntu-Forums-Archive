---
title: "I have installing Ubuntu 11.04 with &quot;wubi&quot; in Windows 7"
date: 2011-08-22
forum: Installation &amp; Upgrades
---

### Post by spi_ on 2011-08-22
[I]hello,
apology for my English..
I have installing Ubuntu 11.04 with "wubi" in Windows 7, but I want to installing in a different hard disk and I try for uninstalling with " Add remove Programs " and with wubi?(Ubuntu) uninstaller but it is not possible, after that I removes "folder" Ubuntu from hard disk and I installed in the other hard disk, but now in boot screen I see :
Windows 7
Ubuntu
Ubuntu
if I select the third Ubuntu I see "Cannot load"...
the questions is:
1) how full uninstalling Ubuntu?
2) where I found "boot" file to I removes the one Ubuntu?
I wait for your answer...
thanks a lot....[/I]

---

### Post by Mark Phelps on 2011-08-22
One of the main reasons I do NOT use Wubi is that is has a nasty habit of NOT being able to clean up after itself.

What you can do to remove it manually, is the following:
1) Remove the "file" that Wubi installed.
2) Install EasyBCD from NeoSmart Technologies.
3) Use the Edit Boot Menu option of EasyBCD to remove any entries for Ubuntu.
4) Save the edited menu.

Now, it is gone.

---

### Post by spi_ on 2011-08-24
> **Mark Phelps said:**
> One of the main reasons I do NOT use Wubi is that is has a nasty habit of NOT being able to clean up after itself.

What you can do to remove it manually, is the following:
1) Remove the "file" that Wubi installed.
2) Install EasyBCD from NeoSmart Technologies.
3) Use the Edit Boot Menu option of EasyBCD to remove any entries for Ubuntu.
4) Save the edited menu.

Now, it is gone.

thanks a lot Mark...
another question:
hello,
apology again for my English...
There are  security transactions; There are firewall, antivirus, antispam for Ubuntu linux?
how do I install the "Google Talk"? how can I "Chat" with my gmail account?
I wait for your answer...
thanks a lot...

---

### Post by Mark Phelps on 2011-08-24
> **spi_ said:**
> thanks a lot Mark...
another question:
hello,
apology again for my English...
There are  security transactions; There are firewall, antivirus, antispam for Ubuntu linux?
how do I install the "Google Talk"? how can I "Chat" with my gmail account?
I wait for your answer...
thanks a lot...

OK, since different problems tend to be entirely unrelated, and different "experts" tend to respond to different questions -- it's generally a bad idea to lump all your questions into one post.  It gets to be too long and complicated -- and folks quit reading it.

In terms of security, while it is possible for Linux systems to get viruses, that happens so rarely that it is a waste of time trying to install AV products in Linux.

As to your other questions, it would be best to start a new thread -- one for each question.

---

