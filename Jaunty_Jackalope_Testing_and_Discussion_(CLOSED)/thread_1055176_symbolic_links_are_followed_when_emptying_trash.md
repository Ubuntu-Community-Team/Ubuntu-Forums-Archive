---
title: "symbolic links are followed when emptying trash"
date: 2009-01-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by billyShears on 2009-01-30
I've moved a symbolic link to my pictures folder to trash, and after emptying trash all the files inside the pictures folder has been deleted.
I'm running alpha 3, does this happen on a fully updated jaunty install?
Of course be careful if you want to test it ;)

---

### Post by Gina on 2009-01-30
Goodness gracious me!!  YES it does!  I created a test folder on my desktop and another within it plus a sym link to the test folder.  Then moved link to trash and emptied trash.  The test folder is still there but the folder within it is gone!!  :( :(

You've found a serious bug there which I confirm.  Have you reported it on Launchpad?

---

### Post by billyShears on 2009-01-30
there was a bug like this in hardy a year ago: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/188361]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/188361")

I have not reported it, I don't have a launchpad account so I would prefer that someone else report it. :)

---

### Post by chrisccoulson on 2009-01-30
I vaguely remember this happening in the Hardy cycle too

---

### Post by marmuta on 2009-01-30
Uh-oh, that could explain some of the ext4 issues too.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781/comments/15](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781/comments/15)

---

### Post by Gina on 2009-01-30
OK -  I'll report the present bug.

---

### Post by tawmas on 2009-01-30
> **Gina said:**
> OK -  I'll report the present bug.

Doh, I had the report written and ready to be submitted, when I noticed this note... Are you done already?

**EDIT**: I posted it. It's [323317]("https://bugs.edge.launchpad.net/ubuntu/+source/nautilus/+bug/323317"). If you managed to also submit your in the meanwhile, please let me know so I can mark mine as duplicate and confirm your. I'm going to dinner now, will be back in 1 hour or so...

---

### Post by taavikko on 2009-01-30
Were not able to reproduce on ext4. 32bit

---

### Post by Gina on 2009-01-30
Oh dear - great minds etc...  Yes - I've posted it [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/323321]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/323321")

I think your post is better :)

---

### Post by tawmas on 2009-01-30
> **taavikko said:**
> Were not able to reproduce on ext4. 32bit

Looks like the link must be an absolute link, not a relative one. I'm going to add this piece of information to the bug report.

I'm on ext4 as well, though 64 bit. Can you please retry with an absolute link?

> **Gina said:**
> Oh dear - great minds etc...  Yes - I've posted it [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/323321]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/323321")

I think your post is better :)

:-) Thanks! I'm confirming yours nonetheless, as I feel that confirming my own bug would be bad etiquette.

---

### Post by taavikko on 2009-01-30
> **tawmas said:**
> Looks like the link must be an absolute link, not a relative one. I'm going to add this piece of information to the bug report.

I'm on ext4 as well, though 64 bit. Can you please retry with an absolute link?



Sorry no dice here, unable to reproduce. Tried few times with different setups, but target remained in test folders, after links were moved to trash.

But Like Pedro said on the bug, that this ugly *** raised it's ugly head once more...

---

### Post by gspat on 2009-01-30
I can confirm this also... using ext3.

Also...

move symlink to trash > empty trash > folder inside folder is gone!

delete symlink (bypass trash) > folder stays???

---

### Post by Gina on 2009-01-30
Ah right - not ext4 problem then.

---

### Post by plun on 2009-01-30
Thanks all for the "heads up" with this   !!!

Patches coming directly....:D

[http://bugzilla.gnome.org/show_bug.cgi?id=512144](http://bugzilla.gnome.org/show_bug.cgi?id=512144)


Don't touch the Trash.....;)

---

### Post by Gina on 2009-01-30
Great :)

---

### Post by gspat on 2009-01-30
> **plun said:**
> Don't touch the Trash.....;)

My son would love this! :)

---

### Post by MacUntu on 2009-01-30
EXT4 is also affected.

---

### Post by inportb on 2009-01-30
... but only on Gnome?

---

### Post by MacUntu on 2009-01-30
> **inportb said:**
> ... but only on Gnome?

Seems to be a bug in GVFS, so yes.

---

### Post by Xgen on 2009-01-30
I always use the 'Delete' command that bypasses trash in nautilus...it doesn't seem to be affected.

---

### Post by ronacc on 2009-01-30
> **Xgen said:**
> I always use the 'Delete' command that bypasses trash in nautilus...it doesn't seem to be affected.

I'll just say I'm with you and refrain from launching into a diatribe against the whole concept of a trash can .

---

### Post by marmuta on 2009-01-31
Wow, this has got to be a new Ubuntu record for the fastest bug fix. Amazing, did it just take only 3 hours from the bug report to the repos? :KS
>   Launchpad Janitor  wrote 6 hours ago:  (permalink)

This bug was fixed in the package gvfs - 1.1.4-0ubuntu3

---

### Post by BwackNinja on 2009-01-31
Hehe, yay! So this must've been my problem...

---

### Post by Paddy Landau on 2009-01-31
> **tawmas said:**
> Looks like the link must be an absolute link, not a relative one.
Please explain the difference between an absolute link and a relative link. (Is this anything to do with a hard link or a symbolic link? I'm familiar with the difference between a hard link and a symbolic link, and I know that the ln command won't create a hard link of a directory.)

---

### Post by billyShears on 2009-01-31
thanks to Gina and tawmas for the report on launchpad! It was impressive to see how fast it has been fixed.

> **Paddy Landau said:**
> Please explain the difference between an absolute link and a relative link. (Is this anything to do with a hard link or a symbolic link? I'm familiar with the difference between a hard link and a symbolic link, and I know that the ln command won't create a hard link of a directory.)

i think an absolute link points to an absolute path (for example /home/user/documents) while a relative link point to a path relative to the position of the link (for example "documents", and that link need to be placed in /home/user, if you move it it won't work anymore, that's because relative links were not affected by this bug I suppose, once moved to trash they became broken)

---

### Post by tawmas on 2009-01-31
> **Paddy Landau said:**
> Please explain the difference between an absolute link and a relative link. (Is this anything to do with a hard link or a symbolic link? I'm familiar with the difference between a hard link and a symbolic link, and I know that the ln command won't create a hard link of a directory.)

They're both symbolic links, the only difference is in the way you create them. Say that you're in /home/tawmas/example and want to create a symbolic link to /home/tawmas/target, the first command below gives you a relative link and the second one an absolute link:

```
ln -s ../target
ln -s /home/tawmas/target
```


EDIT: A couple seconds too late! :-)

---

### Post by Paddy Landau on 2009-01-31
Thank you billyShears and tawmas; it's much clearer now.

---

