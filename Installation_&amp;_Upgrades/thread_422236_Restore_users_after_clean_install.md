---
title: "Restore users after clean install"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by rdoolen on 2007-04-25
I did a clean install to upgrade from Edgy to Feisty. I have a separate /home. When I did the install I entered the user name and password for one of the accounts. That one seems to work (at least I can login) But the others don't. 

How do I transfer the other accounts?

Thanks

---

### Post by BoneKracker on 2007-04-25
Account information (usernames, userids, passwords, etc.) are not stored in the home directory.

You'll need to create the accounts again.

---

### Post by cantormath on 2007-04-25
> **rdoolen said:**
> I did a clean install to upgrade from Edgy to Feisty. I have a separate /home. When I did the install I entered the user name and password for one of the accounts. That one seems to work (at least I can login) But the others don't. 

How do I transfer the other accounts?

Thanks

maybe I am misunderstanding what you are trying to accomplish here but If you did a clean install, wouldnt the old users be removed?  I would think you would have to create them again.  Are you trying to attach an old home partition to the new install?

---

### Post by BoneKracker on 2007-04-25
> trying to attach an old home partition to the new install

Yeah, that's what he said...
> I have a separate /home
(the operative word being "have")

---

### Post by rdoolen on 2007-04-25
Sorry for not being clear. I have a separate /home partition. I want to then use the user folders on the /home partition. When I did the clen install, I entered one of the login names and its password. If I login with that name , I see the apropriate home folder. I have two more accouts which I want to restore. 

The /home is still intact, all the data is there. I need to be able to setup new accounts that attach to those folders.

Does that make sence?

---

### Post by cantormath on 2007-04-25
> **BoneKracker said:**
> Yeah, that's what he said...

(the operative word being "have")

well you can just piss off ........a separate home partition DOES NOT imply that is an old home partition....but you knew that.

> **rdoolen said:**
> Sorry for not being clear. I have a separate /home partition. I want to then use the user folders on the /home partition. When I did the clen install, I entered one of the login names and its password. If I login with that name , I see the apropriate home folder. I have two more accouts which I want to restore. 

The /home is still intact, all the data is there. I need to be able to setup new accounts that attach to those folders.

Does that make sence?

I understand that you have a separate partition for home, is it your old partition from a previous install or did you just make it separate?  Im sorry, I am just making sure I understand the situation.

---

### Post by rdoolen on 2007-04-25
Its from an Edgy install.

---

### Post by cantormath on 2007-04-25
> **rdoolen said:**
> Its from an Edgy install.

This might be a stupid question, but, have you tried system>administration>users and groups......regarding the users issue?  You can create any users you need to recreate through there and pick the home folder you want for each user.  Dont forget to set the user privs in the User Priv section.

Another recommendation, if you have not, take a look at this tutorial on reattaching your old home to a new install
[http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)

If this is the wrong direction, please let me know.

---

### Post by rdoolen on 2007-04-25
I think Bonekracker was on the right track. The user, groups, etc aren't on the /home. I need to somehow tell the OS about the user folders in the /home. How to do this is what confuses me.  If I try to logon, the username and password aren't recognized.

As you point out, I could add users of the same name. I tried this, but that seemed to confuse things-- I couldn't loging to that account at all, although it did try.

I think I need to copy some files from my orignal /etc to my new /etc (I made A LOT of backups) So, I have the old /etc.

So I guess it comes down to what I need to copy.

---

### Post by cantormath on 2007-04-25
> **rdoolen said:**
> I think Bonekracker was on the right track. The user, groups, etc aren't on the /home. I need to somehow tell the OS about the user folders in the /home. How to do this is what confuses me.  If I try to logon, the username and password aren't recognized.

As you point out, I could add users of the same name. I tried this, but that seemed to confuse things-- I couldn't loging to that account at all, although it did try.

I think I need to copy some files from my orignal /etc to my new /etc (I made A LOT of backups) So, I have the old /etc.

So I guess it comes down to what I need to copy.

as I said, you can do that through System>Administration>users and groups in the menu or you can use the adduser command.  You need to also adjust the privs to allow the new created users to do things......When adding users, I dont think you need to mess with the /etc file at all.........best of luck.

---

### Post by rdoolen on 2007-04-29
Well, I didn't have good luck with adding users.  I tried it but I still couldn't login. So, I copied group  gshadow  passwd  and shadow from my old /etc to my new /etc. Now I can login to all the accounts and they were restored to their old state. I think your way would work but the ID's have to be the same as the old, maybe I was doing something wrong.

Thanks for all the help.

---

