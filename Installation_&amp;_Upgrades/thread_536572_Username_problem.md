---
title: "Username problem"
date: 2007-08-27
forum: Installation &amp; Upgrades
---

### Post by GeoffSmith on 2007-08-27
About a year ago I set up a sytem for a small business using Ubuntu 6.06 LTS as the server and Windows XP on the client PCs.  The server is set up as a Windows Domain Controller using SAMBA.  Up till now things have been running rather smoothly but recently one user has been unable to write her roaming profile back to the server when she logs off.

After a long and tedious fault-finding process I discovered that the problem is related to the users Linux username !!!

When I first created the system I set the Linux usernames to firstname.lastname and then created the SAMBA usernames to be the same.   During my faultfinding I deleted and then recreated the Linux username but, alas, I got the following error message:

[COLOR="Red"]Please set a valid user name consisting of a lower case letter followed by lower case letters and numbers.[/COLOR] 

I assume that some update in the past year has broken my system making the existing Linux usernames invalid. 

If I create the username without a dot and then create a corresponding SAMBA username the user is able to log on and off the Windows domain and have their roaming profile copy back and forth as it should.

Basically the fix is simple - delete and recreate the users (there are only about 10 of them).  However, this will mean that the users now have different Windows logons to what their Email addresses are (and I can't change those without a great deal of angst).  This is bound to lead to all sorts of frivolous problems as the users are simple creatures and are used to their current names.

My question is - what is the best way to allow the users to log onto the Windows domain with their existing usernames?  Any suggestions will be appreciated.

---

### Post by kidders on 2007-08-29
Hi there,

The only place I can find a reference to the error message you mentioned is gnome-related. I hope you're not running *that* on a server! Afaik, the username restriction it describes has never existed in Linux ... so it probably never will. :confused:

Samba, most mail servers, and many other apps are capable of creating mappings between internal usernames and the underlying Linux accounts. This allows you to to do things like map Geoff.Smith@yourdomain, gsmith@yourdomain, god@yourdomain, etc. all to the same Linux account on the server. Similarly, YOURDOMAIN\Administrator is typically mapped to Linux PDCs' local root accounts. Essentially, there is very often no reason why network clients need even *have* local user accounts on a mail/samba server ... let alone be aware of what the usernames are.

Despite both of these notes:[LIST]
[*]Creating Linux usernames that don't start with a lower case alphabetic character, or that contain anything other than US English alphanumeric characters in the ASCII character set is a bad idea, and can lead to problems.
[*]Administrators of small networks can find it awkward not to have consistently named one-to-one mappings between Linux accounts and samba/mail users. So, just because things don't *have* to be set up that way doesn't mean it isn't quite acceptable.[/LIST]Anyhow, to cut to the chase, those Linux accounts with the problematic characters in their names should never have been created, but now that they have been, I would suggest...[LIST]
[*]Remove gnome. Graphical applications have no place on a server.
[*]If you want to, you can (technically) continue using your current account naming convention, although I wouldn't advise it, personally.
[*]If you want to switch to a new naming scheme, you can do so transparently by teaching samba & your mail server to map "apparent" usernames to "real" ones.[/LIST]On most setups like yours I configure, I tend to opt for usernames of the form "gsmith" or "smithg", simply because they're quick to type, when logging into things. On top of that, I tend to create mappings for email purposes, so gsmith@mydomain and geoff.smith@mydomain both work.

Sorry for being so long-winded, but I hope that helps a little. The important thing to note is that what gnome considers a valid username and what Linux considers a valid username are not necessarily the same thing. One matters ... the other doesn't. Similarly, one is open to arbitrary changes in the future ... the other isn't.

---

