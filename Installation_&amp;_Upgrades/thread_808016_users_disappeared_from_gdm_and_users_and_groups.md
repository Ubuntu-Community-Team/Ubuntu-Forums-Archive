---
title: "users disappeared from gdm and users and groups"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by bjb1959 on 2008-05-26
I recently upgraded from gutsy to heron and most everything worked fine but what I can't figure out is my list of users that I created using "users and groups" settings manager are no longer visible in either "users and groups" or as options in gdm. They exist in /etc/groups, /etc/shadow, /etc/passwd, /etc/gshadow files but they don't show up as options to edit or delete in "users and groups" nor do they show up as options in gdm. I can still log in using the username and password on each. any idea how to get them to show up again?

[IMG]http://bartburroughs.hopto.org/users.png[/IMG]

---

### Post by sisco311 on 2008-05-26
First you need to click on the Unlock button in Users and Groups.

---

### Post by bjb1959 on 2008-05-28
> **sisco311 said:**
> First you need to click on the Unlock button in Users and Groups.

This doesn't work, I can unlock it but can't see any users but root. also have a new problem. I created a new user to use instead of my old user because it had become extremely slow and now when I go to users-admin the unlock button is not active and I can't add any new users or add my new user to any groups.

---

### Post by sisco311 on 2008-05-28
> **bjb1959 said:**
> This doesn't work, I can unlock it but can't see any users but root. also have a new problem. I created a new user to use instead of my old user because it had become extremely slow and now when I go to users-admin the unlock button is not active and I can't add any new users or add my new user to any groups.

Log in as your old user and add the new user to the admin group.
```
sudo addgroup *new-user-name-here* admin
```

---

### Post by bjb1959 on 2008-05-29
> **sisco311 said:**
> Log in as your old user and add the new user to the admin group.
```
sudo addgroup *new-user-name-here* admin
```

I fixed the user-admin problem by creating a launcher on the panel. it will work that way but not if I use the link in the menu for some reason. If I use that link the unlock button is grey. If I use the launcher I created on the panel it works fine.  The other 4 users are still missing from the list though so that is still a problem. If I try to add those users again it tells me they already exist but they aren't listed there or in the gdm list. I can log in gdm using the user name and password for those accounts but they just don't show up on the list. So they exist just not visible in gdm or users and groups.

---

### Post by A1Dox on 2010-02-28
[Note] I realise this is an old post that I'm replying to, but it came up in a slightly different search to the one I used to find the thread I originally posted to. So, I'm leaving this post, in the hope it helps somebody else using the search terms that found this thread but not the other. [/note]

I've just fixed a similar problem on a Karmic machine here. The users all showed up in the GDM login screen user list, but only the root user was shown in the user-admin dialog. At the risk of being accused of cross-posting, the full details are in [this post]("http://ubuntuforums.org/showpost.php?p=8896924&postcount=11") ;)

Hope it helps.

Regards
Dox

---

