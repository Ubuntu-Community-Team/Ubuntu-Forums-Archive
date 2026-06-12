---
title: "Does ubuntu started asking you for password to mount drives?"
date: 2010-03-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-03-20
when i want to mount one of my ntfs partition the first time it asks for password and it's possible that after some time he might ask again does it happen to you too and how can i stop it?

thanks in advance.

---

### Post by timosha on 2010-03-20
Same here since the updates this morning. It is now the same behavior as in Karmic.

---

### Post by jrothwell97 on 2010-03-20
This behaviour is not new. However, you can change it by going to System/Administration/Users and Groups, and in the User Privileges tab of the "Advanced Settings" dialogue, enabling "mount user-space file systems".

I think. Good luck!

---

### Post by aviramof on 2010-03-21
i already did but again because i use auto login and i don't enter password when i restart my ubuntu this password request appear this hall auto login password request is a serious bug and that matter need to be address once and for all.

---

### Post by timosha on 2010-03-21
I login with a password and have "mount user-space file systems" activated. This doesn't change anything. Nautilus keep asking for a password when mounting a NTFS or EXT4 disk.

---

### Post by mc4man on 2010-03-21
The need to now have to  auth. mounting internal filesystems comes from the latest update to udisks. Changelog pretty much explains why - 

>  * Drop debian/local/ubuntu.pkla again: This will be provided by a new  policykit-desktop-permissions package.



---

### Post by Dilutu on 2010-03-21
Yeah same thing here.Except "users-admin" ,"User Privileges" shows a blank window....I' waiting for an update.

---

### Post by mc4man on 2010-03-21
> is there a bug filed for it already?

It is not a bug (yet), it was an intentional change (removing the .pkla

---

### Post by aviramof on 2010-03-21
yeah well it's very uncomftarble that i need to enter password to mount my own drives and i'm hopping that they would disalbe it soon.

---

### Post by goat69 on 2010-03-21
[FONT=Arial][SIZE=2]Try this. Save a copy of this  in case it doesn't work.[/SIZE][/FONT][FONT=Arial][SIZE=2]
/usr/share/polkit-1/actions/org.freedesktop.udisks.policy[/SIZE][/FONT][FONT=Arial][SIZE=2]

Run:[/SIZE][/FONT][FONT=Arial][SIZE=2]
 gksudo gedit /usr/share/polkit-1/actions/org.freedesktop.udisks.policy

[/SIZE][/FONT]  [FONT=Arial][SIZE=2]Find:
 [/SIZE][/FONT][FONT=Arial][SIZE=2]<action id="org.freedesktop.udisks.filesystem-mount-system-internal"> 
[/SIZE][/FONT] [FONT=Arial][SIZE=2]
Look down a few lines under "default" and change "auth_admin" to "yes" like this.
 [/SIZE][/FONT][FONT=Arial][SIZE=2]<allow_active>yes</allow_active> 
[/SIZE][/FONT] [SIZE=2][FONT=Arial]
Save and try it.
[/FONT] 



[/SIZE]

---

### Post by aviramof on 2010-03-21
thank you very much it's working but i'm hopping i want have to do this every time i install ubuntu in the future.:)

Thread is solved for now any way.

---

### Post by goat69 on 2010-03-21
I found this awhile ago in another thread for 9.10.  Thanks to him/her for it.  For karmic the path is different, "/usr/share/polkit-1/actions/org.freedesktop.devicekit.disks.policy."  
One of the things I keep on hand when playing with different installs and the break/fix  cycle.

---

### Post by Dilutu on 2010-03-21
Does not work for me .I get this error:
"Not Authorized: Remote Exception invoking org.freedesktop.PolicyKit1.Authority.CheckAuthorization() on /org/freedesktop/PolicyKit1/Authority at name org.freedesktop.PolicyKit1: org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.udisks.filesystem-mount-system-internal is not registered"
   Edit: works now, turned out I also had to change defaults filesystem-mount to "yes"!

---

### Post by VMC on 2010-03-21
> **goat69 said:**
> [FONT=Arial][SIZE=2]Try this. Save a copy of this  in case it doesn't work.[/SIZE][/FONT][FONT=Arial][SIZE=2]
/usr/share/polkit-1/actions/org.freedesktop.udisks.policy[/SIZE][/FONT][FONT=Arial][SIZE=2]

Run:[/SIZE][/FONT][FONT=Arial][SIZE=2]
 gksudo gedit /usr/share/polkit-1/actions/org.freedesktop.udisks.policy

[/SIZE][/FONT]  [FONT=Arial][SIZE=2]Find:
 [/SIZE][/FONT][FONT=Arial][SIZE=2]<action id="org.freedesktop.udisks.filesystem-mount-system-internal"> 
[/SIZE][/FONT] [FONT=Arial][SIZE=2]
Look down a few lines under "default" and change "auth_admin" to "yes" like this.
 [/SIZE][/FONT][FONT=Arial][SIZE=2]<allow_active>yes</allow_active> 
[/SIZE][/FONT] [SIZE=2][FONT=Arial]
Save and try it.
[/FONT] 

[/SIZE]

Thanks. that worked, **but** I compared that file "org.freedesktop.udisks.policy", to my last install, dated Mar18th and they are identical.

Even though this works something else is being done that we need to even mess with that file.

---

### Post by mc4man on 2010-03-21
I would just wait and see what package replaces "org.freedesktop.UDisks.pkla" ( where this was controlled.
Hopefully it will allow control of more auth.'s like in the past.

If you really must have then while editing the action directly works, probably better to just restore the .pkla

(previously in karmic beta/rc I'd suggested editing the actions, have since decided that there, (karmic), when possible a .pkla is better for several reasons. (have a couple in karmic

To restore
(create the file

```
gksu gedit /var/lib/polkit-1/localauthority/10-vendor.d/org.freedesktop.UDisks.pkla
```

paste this in and save

```
[No password required for admins]
Identity=unix-group:admin
Action=org.freedesktop.udisks.filesystem-*;org.freedesktop.udisks.change-system-internal
ResultActive=yes

```

---

### Post by goat69 on 2010-03-21
[I]> **VMC said:**
> Thanks. that worked, **but** I compared that file "org.freedesktop.udisks.policy", to my last install, dated Mar18th and they are identical.

Even though this works something else is being done that we need to even mess with that file.[/I] 

That sounds about right.  I believe I had to start entering a password to mount other drives after I did updates this weekend.  But I could be wrong.  

Thread that also discussed this.  [http://ubuntuforums.org/showthread.php?t=1308528&highlight=password+partition+karmic&page=2](http://ubuntuforums.org/showthread.php?t=1308528&highlight=password+partition+karmic&page=2)

---

### Post by mc4man on 2010-03-22
And here is the new package (the reason for removing the .pkla the other day.

Haven't updated yet to test..

> policykit-desktop-privileges (0.1) lucid; urgency=low

  * Initial release. (LP: #455694)
 -- Martin Pitt < [email]martin.pitt@ubuntu.com[/email]>   Wed, 17 Mar 2010 09:50:07 +0100

Edit: atm (or not ?) this seems to be a non user adjustable deal (to some extent

The current installed new .pkla

> [Mounting, checking, etc. of internal drives]
Identity=unix-group:admin
Action=org.freedesktop.udisks.filesystem-*;org.freedesktop.udisks.drive-ata-smart*
ResultActive=yes

[Change CPU Frequency scaling]
Identity=unix-group:admin
Action=org.gnome.cpufreqselector
ResultActive=yes

[Setting the clock]
Identity=unix-group:admin
Action=org.gnome.clockapplet.mechanism.*
ResultActive=yes

---

