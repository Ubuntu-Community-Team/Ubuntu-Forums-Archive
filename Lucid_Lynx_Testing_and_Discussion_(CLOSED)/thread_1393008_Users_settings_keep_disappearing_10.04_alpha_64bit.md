---
title: "Users settings keep disappearing 10.04 alpha 64bit"
date: 2010-01-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by yedidyah on 2010-01-28
I can't say what happened before the problem started but this is what has been going on.

Suddenly I was unable to do anything in user1 without being prompted for root password.

I restarted (holding shift down during boot up) and booted into the recovery mode and selected root-Drop down into root shell prompt and did the following command:

adduser user1 admin

Information came from:

[http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

Once I established that I went and set a password on root so if I had any more problems I would at least be able to control root from user1 account.

I then opened a user2 account for extra control without having to go to root.

Under the original user1 account I go to System->Administration->Users and Groups then I select user1 account and select "Advanced Settings" under "user privileges" I check-mark all the options and close it all down restart the computer and check it and everything I selected previously is de-selected again. They never stick.

user2 account does NOT have any of these problems but it also does not have access to all the programs and changes I made to user1 account so if I were to use it I would have to figure that out and transfer a bunch of files over.

Any ideas?



[COLOR="White"].[/COLOR]

---

### Post by yedidyah on 2010-01-28
Anyone understand this problem?

---

### Post by overdrank on 2010-01-29
Moved to Lucid Lynx Testing and Discussion

---

### Post by xarte on 2010-01-29
I'm having the same problem. Computer crashed mid-update at one point; also hibernated and crashed. Booted to have no wireless, then discovered that passwords wouldn't work. 

Fixed passwords by adding user to sudoers, logged in as root and changed root password.

I can now use gui users/groups to check user priviledges, but they don't stay checked. For some reason users/groups isn't writing changes.

Could the relevant file be write protected or nonexistant?

---

### Post by yedidyah on 2010-01-29
Okay this is what I had to do to correct this problem and it has worked so far.

I had to add myself (user1) back to the Administration as I previously stated.

Also I went into users and groups under System->Administration and started another user (user2), as I stated.

Under user2 I used the update manager and it updated aproximately 70 packages. 

Then I restarted and finally all the programs that were available to user1 were now available to user2. 

So I went back to users and groups and made it so user2 had access to all of user1's stuff. Then I started migrating all my stuff over. Something strange in that though as some files were completely locked even in user2's environment. Still haven't got access to them.

Once I fully migrated then I went back into users and groups and deleted user1.

Now user2 works better than ever with permissions (except that one file from user1 that is all locked up).

I will post more concerning this issue if anything new comes up.

---

### Post by xarte on 2010-01-29
I rebooted into rescue mode with networking. Once it had made the wired connection, selected repair broken packages.

It now appears to be updating the entire installation with 266 upgraded packages - one hour to go. Hoping this fixes the problem! (especially since it will probably use my remaining download limit....)

---

### Post by yedidyah on 2010-01-30
xarte

Please post how that worked out when you get to it.

Thank you

---

### Post by xarte on 2010-01-30
Sadly the update/repair broken packages has made no change to the lack of persistence of user/group settings and disabled wireless.

I'm creating a new user to see if that works, though it obviously is a less than ideal solution.

I regret that I don't know enough about Linux to be able to troubleshoot on a more fundamental level.

---

