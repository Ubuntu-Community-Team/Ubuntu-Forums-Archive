---
title: "Changing the machine's name"
date: 2007-03-17
forum: Installation &amp; Upgrades
---

### Post by DRGuy on 2007-03-17
Hi

This seems like it should be an easy question, but I don't want to just jump in and hang myself...  I just installed ubuntu (6.10) on my laptop as a dual boot with Windows XP.  I inadvertently gave the wrong name for the system.  I want it to have the same name as when the Windows partition would be booted.  However I ended up giving it a name of one of my other systems (forgot what I had named this laptop when I was installing ubuntu - thought it had the other machine's name).

Anyway, is changing the name as easy as just editing /etc/hostname and rebooting?  Will the /etc/hosts file regenerate with the new name after the reboot, or do I need to edit that as well?

I also did a grep (from a find) in my home directory and it did find a few files with the uname in it.  For example there seems to be a binary .ICEauthority that "matches", and a .openoffice.org2/lock file (even though I don't have any openoffice application open).  There is also a config file (I guess just a config.log actually) for my only (so far) GTK+ project that has the machine name in it.

Do I need to be concerned about any such files?  Would they either be a "don't care" or tend to take care of themselves?  Any other problems I need to be aware of (and perhaps prepared to resolve)?

Also, is there any reason NOT to have the Windows and the Linux boots not use the same hostname?

Thanks,
--
DRGuy

---

### Post by kidders on 2007-03-17
Hi there,

> **DRGuy said:**
> Anyway, is changing the name as easy as just editing /etc/hostname and rebooting?Yes. Rebooting isn't essential, but it *is* the most straightforward way to ensure that all your applications are aware of the change. As you mentioned, there can sometimes be other changes to make (eg /etc/hosts, if you modified it), or explicit references to your hostname in things like Apache/Postfix configuration files.

> **DRGuy said:**
> Do I need to be concerned about any such files?
In general terms, you shouldn't need to worry about places where _you_ didn't actually type out the old hostname yourself. If you find that you do have to make such changes, you have discovered bugs, imo. You see, the idea behind having an /etc/hostname is that your entire system has a single point of reference, whenever it wants to know what your PC is called. A properly configured Linux box shouldn't need to be told more than once. :-)

> **DRGuy said:**
> Also, is there any reason NOT to have the Windows and the Linux boots not use the same hostname?My instict is to say yes because, conceptually speaking, they are two different machines, in a way. On my network for instance, each OS on multi-boot machines often serves up different services (or the same services, using different authentication databases), or needs to be treated differently in terms of how it accesses the internet, and so on. Distinctions like that are easier to make if such computers use multiple IP addresses, which implies that they have multiple hostnames.

In your case, you may wish to impose internet access restrictions on your box when it's running Windows XP (to stop it drowning in malware), but loosen up any such restrictions when it's running Linux (to avoid annoying yourself).

So, I suppose the short answer is that if you want your dual boot machine to be treated almost as though it were two different computers, you should set two different hostnames. If not, it seems more sensible to re-use the same one.

I hope that helps.

---

### Post by DRGuy on 2007-03-17
Hi Kidders,

Thanks for the reply!  I'm not sure how much it matters about the name when the machine is Linux vs Windows.  I'm just pretty sure it isn't a good idea that it be named the same as one of my other computers.  This laptop isn't really providing any service itself on my network.  Mostly (aside from just getting to my DSL) I just want it to be able to get to one or another of my printers.

Maybe I'll have to rename the Windows side as well (not for any technical reason, just 'cause I'm a nut).  I'd probably call the Linux side Jekyll and the Windows side Hyde.  I have a pair of almost identical IBM towers (purchased cheap when they went off lease at our local high school) that I call Castor and Pollux (the Gemini twins).

Thanks again,
--
DRGuy

---

