---
title: "Lucid File Sharing is disorganized."
date: 2010-03-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ptn107 on 2010-03-23
Can someone explain why there are different ways to share things...

In Nautilus I can right-click a folder and select properties and click the sharing tab.  That's only after it asks me to install the required packages (samba, libpam-smbpass), log out, and back in (and change my workgroup from the command line to match my windows machines?!).  I also found System -> Preferences -> Personal File Sharing ?  What public files does it share?  It won't even work because "This feature cannot be enabled because the required packages are not installed on your system."  It doesn't tell you that you need to install the apache2.2-bin package.

Why is file sharing so hard?

---

### Post by QLee on 2010-03-23
I see there are zero replies to your questions and observations, so I'll give you a couple of brief ones and some advice.

[QUOTE=ptn107]Can someone explain why there are different ways to share things...[/QUOTE]

Because there are different things to share.

[QUOTE=ptn107]Why is file sharing so hard?[/QUOTE]

I do not think that it is very hard (opinion). I do think it should be difficult enough to do in order to be relatively secure once the sys admin has set it up. Things are done differently than in Windows though.

Remember that at this time, Lucid is still in the beta stage and if people want to avoid problems that they aren't yet able to deal with, they should probably stick with released versions. Although, in this case, the released version would likely be about the same for what you have observed. 

Samba shares (like shared files in Network Neighborhood) need to be configured for sharing in GNU/Linux. And, if you are running a http server, you need to specify which files Apache will share. The fact that you don't understand the difference leads me to speculate that you would be better served using a released version. I don't mean to insult you with that advice, but this question isn't really about Lucid . A search engine might help you to investigate the difference between samba shares and the files your webserver is serving up. Are you even running a webserver?

---

### Post by Robert Citek on 2010-04-06
> **ptn107 said:**
> Why is file sharing so hard?

Thanks for posting.  You are not the only one who thinks this a problem.  The good news is that they're working on fixing this.  Here's the bug report:

[https://bugs.launchpad.net/ubuntu/+source/gnome-user-share/+bug/536766](https://bugs.launchpad.net/ubuntu/+source/gnome-user-share/+bug/536766)

If you need a quick workaround:

[https://bugs.launchpad.net/ubuntu/+source/gnome-user-share/+bug/536766/comments/7](https://bugs.launchpad.net/ubuntu/+source/gnome-user-share/+bug/536766/comments/7)

Again, thanks, and keep posting.

Regards,
- Robert

---

