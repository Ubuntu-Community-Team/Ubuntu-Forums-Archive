---
title: "Thunderbird and Firefox Unusably Slow - Maverick"
date: 2010-10-23
forum: Installation &amp; Upgrades
---

### Post by dvdram on 2010-10-23
Hi,

I've just upgraded my laptop, and one of the desktop workstations, to Kubuntu 10.10 (using the package manager in both cases). The laptop is fine, almost everything works as it should, but on the desktop, both Thunderbird and Firefox have become unusable.

Launching Firefox, nothing appears to be happening, but after about 5 minutes I get 'Warning: Unresponsive Script.' The script in question is /usr/lib/firefox-3.6.11/components/nsContentPrefService.js:829

Thunderbird does a similar thing, although it takes a lot longer, and it refers to a different script - unfortunately I don't have 10 minutes to find out which one, but I believe it had 'security' in the name.

I tried removing and reinstalling both programs, but no luck there. What I have noticed is that, having enabled the root account, I can use Firefox (haven't tried Thunderbird, but I assume the same would apply) without a problem in that. With that in mind, two things I think might be relevant: /home is an NFS share, and normal users are authenticated via LDAP. I can't imagine how that might affect things - it never used to before 10.10 - but the only other difference I can think of between root and a normal user is that it's a permissions issue, in which case I'd think a lot more people, and the laptop, would have been affected. Oh, I also tried renaming ~/.mozilla and ~/.thunderbird, but that didn't help either.

Any help, pointers, suggestions, would be greatly appreciated!

Thanks,

Alex

---

### Post by SeijiSensei on 2010-10-23
Try turning off IPv6 DNS resolution; it substantially improved my performance in both applications.

In Firefox, type "about:config" into the address bar.  Agree to violate your warranty (What warranty? Do I get my money back?).  Type "ipv6" into the Filter bar on the next screen, and you'll see the entry to disable IPv6 DNS resolution.  The default is "false" meaning it's not disabled.  Double-click the entry to switch it to "true", then close the tab and see if Firefox works more quickly.

In Thunderbird, you use Edit > Preferences > Advanced > Config Editor, then follow the same procedure as used for Firefox.

---

### Post by dvdram on 2010-10-24
Thanks for your suggestion!

I tried to change the settings, but after 40+ minutes of waiting for Firefox to respond, I had to give up.

I've noticed something else though - OpenOffice, which I used for the first time today since upgrading to 10.10,  is also extremely slow to start, taking almost 5 minutes! The only other apps I've used, rekonq, Konsole and aMSN, all work fine.

Once again, trying OpenOffice under the root account, it starts as quickly as I'd expect, which seems to add credibility to my idea that either LDAP or the NFS /home directory is to blame here. How, though, I have no idea!

---

### Post by go4linux on 2010-10-26
Hi, I found your thread yesterday while I was trying to solve a similar problem. Since apparently I solved mine, I thought it might be interesting for you to look at it:

[http://ubuntuforums.org/showthread.php?t=1605475](http://ubuntuforums.org/showthread.php?t=1605475)

Hope it helps

---

### Post by dvdram on 2010-10-28
Hi,

Thank you! I did look in messages, but didn't notice the lockd errors buried amongst all the other things on my todo list! They were there though, and the problem is now sorted.

Thanks again,

Alex

---

