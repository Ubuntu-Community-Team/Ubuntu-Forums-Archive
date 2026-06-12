---
title: "Netflix Player (Ubuntu 10.10)"
date: 2010-11-03
forum: Installation &amp; Upgrades
---

### Post by Andrew.McCoy on 2010-11-03
Does anyone know if there is a way to get the Netflix player installed from the Ubuntu Software Center if at all?

---

### Post by uRock on 2010-11-03
It would require Microsoft's Silverlight, but I would love to see it in Linux.

---

### Post by Andrew.McCoy on 2010-11-03
I figured it was simply a dream. :-P thanks.

---

### Post by monokrome on 2010-12-22
Novell has an implementation of SilverLight for Linux called Moonlight that supports everything that NetFlix would need to work on Linux, but Netflix has made some bad bad programming choices in their code. This has caused them to be in a state where it will be a lot more changes than it should be to get NetFlix running on Linux, and I think there are some issues with their licensing and Linux.

So, Silverlight isn't the issue. Netflix is.

---

### Post by chaser24 on 2010-12-24
DRM is the issue.  Netflix is using Microsoft's PlayReady DRM likely under pressure from content providers.  Regardless of why, Microsoft will not license the use of the DRM for Linux Desktops, although they have allowed it for set-top boxes such as Boxee and Roku.

So neither Silverlight or Netflix (exclusively) is the issue.  It's the use of Microsoft's DRM stack and their refusal to license it for Linux Desktop use.

The only way I've been able to get it to work is using a VirtualBox VM running WinXP.  I personally haven't had any major performance issues with my implementation.

---

### Post by emarkay on 2011-01-24
What, no one's got this yet? "sudo apt-get install libplayready"  :popcorn: Hey, it's only bits, I am sure it'll happen soon. 

Anyway,  there went 3 hours in trying to investigate why one can't get Netflix strams on a Ubuntu PC. It is up to Microsoft to allow the PlayReady DRM to work in Llinux.  Other than using XP in a VM it's not possible as of now on any app using any Linux.
[I]
"Netflix streams in a browser using Microsoft’s Silverlight plugin, essentially a beefed-up version of the Flash player with Microsoft’s PlayReady Digital Rights Management. An open-source version of Silverlight is available for Linux called Moonlight which is developed by Novell in collaboration with Microsoft. Microsoft even acknowledges Silverlight support for Linux through the use of Moonlight. However, the major difference between Silverlight and Moonlight is the PlayReady DRM. Without the DRM, Netflix movies won’t stream.

Moonlight’s project site lists PlayReady a feature, but the status is unsupported meaning that Microsoft has not yet licensed PlayReady for third-party use. Since Netflix relies on external resources to provide its streaming capabilities, the onus lies on Microsoft to release their DRM library for third-party use."[/I]

[http://geekshuiliving.com/2010/05/10/netflix-on-linux-why-this-is-advantageous-for-everyone/](http://geekshuiliving.com/2010/05/10/netflix-on-linux-why-this-is-advantageous-for-everyone/)

Also see:
[http://www.techrepublic.com/blog/opensource/the-netflix-linux-conjecture-how-netflix-snubs-the-linux-community/1745](http://www.techrepublic.com/blog/opensource/the-netflix-linux-conjecture-how-netflix-snubs-the-linux-community/1745)
[http://www.thedrmblog.com/](http://www.thedrmblog.com/)
[http://forums.silverlight.net/forums/t/94992.aspx](http://forums.silverlight.net/forums/t/94992.aspx)

---

### Post by presence1960 on 2011-01-24
> **Andrew.McCoy said:**
> Does anyone know if there is a way to get the Netflix player installed from the Ubuntu Software Center if at all?

Netflix software is not compatible with linux, at least for now.

---

