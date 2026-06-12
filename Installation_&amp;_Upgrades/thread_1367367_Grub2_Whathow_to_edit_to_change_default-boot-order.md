---
title: "Grub2: What/how to edit to change default-boot-order?"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by cookdav on 2009-12-29
The title says it all.  This is for Kubuntu 9.10.

What file do I edit, to make one of the OTHER OSes the
default one to boot, in the new grub2 sub-system?

e.g. if I want Windows or some other Linux distro to
be the default OS to boot?

[I tried adding the old (grub-1) 'savedefault' keyword into
one of the existing entries, but that was even worse
and totally broke that entry from being usable, with a syntax error
when you try to invoke it.]

TIA...

---

### Post by cookdav on 2009-12-29
Found an answer myself, in another thread.

Supposedly, the solution is to run the cmd:

sudo grub-set-default 8

[or whatever # of entry is that you want, if not #8]

But, that doesn't work for me.  It runs, but has no effect.
And, it failed for a bunch of others, too.

So, my WORKAROUND is to edit the file '/boot/grub/grub.cfg',
(which says in it, NOT to edit it!) and change the value
of 0 near the top to my desired relative entry #, zero-based)

No doubt, I'll have to tweak this, anytime some update brings
us a new kernel or whatever, but at least it's a start.

(Sigh.  "Pioneers are the people with arrows sticking out of their *sses.")

Needless to say, I'm not too fond of Grub2 yet. :P


EDIT: The final answer might be here:

[http://ubuntuforums.org/showpost.php?p=8218331&postcount=14](http://ubuntuforums.org/showpost.php?p=8218331&postcount=14)

but I'm too lazy right now to care about trying that.

---

### Post by phillw on 2009-12-29
Now you've found that posting, book-mark it - In drs's sig is the font of knowledge of Grub2 - a lot of it written by his good self.

Should you find yourself in a situation where win or ubuntu vanish from your boot list after updates / re-installs --> [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)  is the place to head.

Phill.

---

### Post by efflandt on 2009-12-29
You are not supposed to tamper with /boot/grub/grub.cfg

The correct way to change grub defaults is to edit **/etc/default/grub** or see files in **/etc/grub.d**

For example in /etc/default/grub commenting out this 0 line and adding a line with *saved* would boot the last grub selection that successfully booted.  Then if you are running Windows for awhile it will boot to Windows and if you select Linux, the next time it would boot to that Linux without touching anything.

#GRUB_DEFAULT=0
GRUB_DEFAULT=saved

Or you could fill in a number instead of saved, if you wanted a specific default.

If you want to change grub menu colors, edit /etc/grub.d/05_debian_theme

---

### Post by oldfred on 2009-12-29
Another way in  **/etc/default/grub**:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

**GRUB_DEFAULT="xxxx"** An exact menu entry, including the quotation symbols, may also be used. In this case, location in the menu will not matter. Example: **GRUB_DEFAULT="Ubuntu, Linux 2.6.31-9-generic"**

or

find windows entry like this - [COLOR=DarkRed]Windows Vista (on /dev/sda1)[/COLOR]  - in grub.cfg and copy to grub_default
gedit /boot/grub/grub.cfg
and copy here
gksudo gedit /etc/default/grub
GRUB_DEFAULT="[COLOR=DarkRed]Windows Vista (on /dev/sda1)[/COLOR]"

---

### Post by Elep.Repu on 2010-01-17
I followed [http://3.ly/yXa](http://3.ly/yXa)
and it didn't work. None of these have worked for me.

My cfg file is as follows: [http://paste.ubuntu.com/358204/](http://paste.ubuntu.com/358204/)
My default file is: [http://paste.ubuntu.com/358205/](http://paste.ubuntu.com/358205/)
Nobody said whether or not to allow it to write the menu.lst file (which it prompts for if it's not there).
I've tried with it there and with it not there. Have rebooted many times.

Thanks for Grub 2.

---

### Post by oldfred on 2010-01-17
It does not look like your ran

sudo update-grub

as it says whenever you edit the grub file to get it to rewrite the grub.cfg file. Grub.cfg still says default = 0.

---

### Post by Leppie on 2010-01-17
> **Elep.Repu said:**
> Nobody said whether or not to allow it to write the menu.lst file (which it prompts for if it's not there).
I've tried with it there and with it not there. Have rebooted many times.
there's no menu.lst in grub2, this is the configuration file for grub legacy.

as oldfred said, run update-grub to regenerate the grub.cfg

---

### Post by Elep.Repu on 2010-01-18
Actually I did run sudo update-grub.
Every time.

And yes, when running sudo update-grub it asks you if you would like to create the menu.lst file.
If you say yes, it doesn't ask you to create another one.
if you delete it and retry, it will ask you again.

---

### Post by Leppie on 2010-01-18
> **Elep.Repu said:**
> Actually I did run sudo update-grub.
Every time.

And yes, when running sudo update-grub it asks you if you would like to create the menu.lst file.
If you say yes, it doesn't ask you to create another one.
if you delete it and retry, it will ask you again.
the grub.cfg you posted shows that the modifications have not been applied.

if update-grub prompts you about menu.lst, you are actually still using grub legacy.

---

### Post by Elep.Repu on 2010-01-18
> **Leppie said:**
> the grub.cfg you posted shows that the modifications have not been applied.

if update-grub prompts you about menu.lst, you are actually still using grub legacy.

Default in 9.10 ubuntu is a 1.97 beta I believe. Figured same settings applied since I was seeing the same setup as GRUB2. (And that Startupmanager and grub editors weren't working).

Remade the menu.lst with update-grub (just now, with right GRUB_DEFAULT)
menu.lst is [http://paste.ubuntu.com/358591/](http://paste.ubuntu.com/358591/)

Looking closely I see no windows option within menu.lst.
Chainloads into GRUB2, (When booting Windows is shown at bottom).
Same default config as I've shown before. But it creates this menu.lst file on sudo grub-update.
What's the deal here?

---

### Post by oldfred on 2010-01-18
If you do an inplace upgrade from 9.04 you still have grub legacy (0.97). If you did a new install of Kamic you have grub2. Unless you followed commands to reinstall and installed the old version.

Grub version
grub-install -v

---

### Post by Elep.Repu on 2010-01-18
grub-install (GNU GRUB 0.97)

Used grub-set-default 8 (nothing changed) [http://3.ly/wDOl](http://3.ly/wDOl)
sudo apt-get install grub2
kept local version
worked.

---

### Post by Leppie on 2010-01-18
> **Elep.Repu said:**
> Default in 9.10 ubuntu is a 1.97 beta I believe. Figured same settings applied since I was seeing the same setup as GRUB2. (And that Startupmanager and grub editors weren't working).

Remade the menu.lst with update-grub (just now, with right GRUB_DEFAULT)
menu.lst is [http://paste.ubuntu.com/358591/](http://paste.ubuntu.com/358591/)
grub v. 1.97 is grub2, like grub v. 0.97 is grub 1 or better grub legacy
grub2 doesn't use menu.lst (like grub legacy) but grub.cfg

---

