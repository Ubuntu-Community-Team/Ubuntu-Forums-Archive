---
title: "Update Manager back to its old ways?"
date: 2009-10-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jblackhall on 2009-10-13
When I updated to the Karmic beta, I was really pleased with how Update Manager was working.  I didn't have to enter in my password before checking for updates and nice little window came up saying that it was "Updating Cache".  Once the updates were listed, I could click on "Install Updates" and enter my password and it would open a new notification saying it's "Applying changes".

Now when I open Update Manager, I have to enter a password before checking for updates and the little window that pops up is the same as the one in Jaunty saying it's "Downloading File 33/48".  When I click on Install, it states that it's "Downloading Package Files 1/42".

Where did my sleek Update Manager go?  Is it coming back for the 9.10 release??

---

### Post by kansasnoob on 2009-10-13
I noticed the same thing. I guess I don't really care how it works as long as it works.

Then again I seldom use it:)

On my work machine I always run apt-get update && apt-get upgrade before I begin working.

---

### Post by PRGUY85 on 2009-10-13
Preferred the previous way it was working without password checking for updates.

---

### Post by ikt on 2009-10-13
I do wish the old update manager would come back. Time to report a bug/wishlist?

Does it have to do with apt daemon crashing a lot?

---

### Post by 23meg on 2009-10-13
Looks like it has to do with this (emphasis mine):

> update-manager (1:0.126.1) karmic; urgency=low

  * DistUpgrade/DistUpgradeView.py:
    - log exceptions from pm.DoInstall() into main.log.
      this helps identifiying Dpkg::Pre-Invoke problems
  * DistUpgrade/DistUpgradeCache.py:
    - fix sandbox upgrade mode
  * DistUpgrade/DistUpgrade.cfg:
    - hint for mysql-server upgrade (LP: #413789)
  * UpdateManager/backend/__init__.py:
    - **change order of backends to: synaptic, aptdaemon**

 -- Michael Vogt <michael.vogt@ubuntu.com>  Mon, 12 Oct 2009 18:30:55 +0200


---

### Post by FuturePilot on 2009-10-13
I was about to ask this same question.

> **23meg said:**
> Looks like it has to do with this (emphasis mine):
I saw that in the changelog too, but that doesn't explain why it was done. Is there a particular reason for that change?

---

### Post by null_pointer_us on 2009-10-13
Searching [https://bugs.edge.launchpad.net/ubuntu](https://bugs.edge.launchpad.net/ubuntu) for aptdaemon reveals some critical/high priority bugs. Maybe someone who's interested can find an answer?

---

### Post by jblackhall on 2009-10-13
Maybe this? [https://bugs.launchpad.net/ubuntu/karmic/+source/policykit-1-gnome/+bug/445303](https://bugs.launchpad.net/ubuntu/karmic/+source/policykit-1-gnome/+bug/445303)

I mainly just want the language and animation of the notifications on the old version.  I don't care so much about when I need to enter my password.

---

### Post by vrkalak on 2009-10-13
Patience, guys!!

Remember, that at the moment, Karmic 9.10 is going through a metamorphosis.
Even the main Ubuntu page says, that Ubuntu Karmic is in Beta ... some things may not work from the start.  
I had an update glitch this past Sunday, but the Daily Builds worked, after they fixed that bug.

Give them until the Final Release is out, to work out all the update/upgrade bugs.

Not long now . . . until the Final Release of Ubuntu Karmic Koala 9.10  Yay!!

---

### Post by hanzomon4 on 2009-10-14
So no policy-kit?

---

### Post by emarkay on 2009-10-14
I like it now and the way it was - the amount of files also shows which (relatively) repos are "slow".. A single bar of just "X of Y"  Is just useless in comparison.

---

### Post by autocrosser on 2009-10-14
I agree--I like the "old" way & want it to stay that way......I like knowing what it is doing--not hidden the micro$oft way.......

---

### Post by Merk42 on 2009-10-14
> **autocrosser said:**
> I agree--I like the "old" way & want it to stay that way......I like knowing what it is doing--not hidden the micro$oft way.......

Can we have that **and** the ability to check for updates without a password?

---

### Post by coldReactive on 2009-10-14
> **Merk42 said:**
> Can we have that **and** the ability to check for updates without a password?

Options are always good, indeed.

---

### Post by dadedo123 on 2009-10-14
I get many errors in my update-manager, they better fix it. hehe.  I have to clear my cache, and change the server everytime I want to update, it gets very annoying!

---

### Post by ikt on 2009-10-14
> **dadedo123 said:**
> I get many errors in my update-manager, they better fix it. hehe.  I have to clear my cache, and change the server everytime I want to update, it gets very annoying!

Submitted a bug?

[http://screencasts.ubuntu.com/2009/09/16/Reporting_Bugs](http://screencasts.ubuntu.com/2009/09/16/Reporting_Bugs)

---

### Post by dadedo123 on 2009-10-14
> **ikt said:**
> Submitted a bug?

[http://screencasts.ubuntu.com/2009/09/16/Reporting_Bugs](http://screencasts.ubuntu.com/2009/09/16/Reporting_Bugs)

I don't really know how update manager works, I've always had problems with it, with all the releases I used. :p

> W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) jaunty Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures were invalid: BADSIG EF4186FE247510BE Launchpad PPA for Ubuntu Mozilla Daily Build Team

---

### Post by andrewabc on 2009-10-14
I preferred Jaunty way.
Although only needing password to install (instead of checking for updates) was much better.

---

### Post by philinux on 2009-10-14
[https://bugs.launchpad.net/ubuntu/+source/aptdaemon/+bug/448810](https://bugs.launchpad.net/ubuntu/+source/aptdaemon/+bug/448810)

See comment 16.

---

### Post by FuturePilot on 2009-10-14
> **philinux said:**
> [https://bugs.launchpad.net/ubuntu/+source/aptdaemon/+bug/448810](https://bugs.launchpad.net/ubuntu/+source/aptdaemon/+bug/448810)

See comment 16.

Ah, that explains it.

---

