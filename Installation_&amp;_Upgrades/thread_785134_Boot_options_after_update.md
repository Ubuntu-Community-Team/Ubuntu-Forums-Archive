---
title: "Boot options after update"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by stokerw on 2008-05-07
Hi, My upgrade to 8.04 has gone well, but I'm mystified by the boot options on my dual boot laptop.
I seem to have two sets of ubuntu options (in addition to the recovery mode and windows options).
One is labeled Ubuntu 8.04, kernel 2.6.24-generic
The other is Ubuntu 8.04, kernel 2.6.16-generic
They both seem to boot equally well. Should I be concerned to remove one of the options - If so which one, and how how I do it?

Thanks, Stoker Wilson.

---

### Post by Herman on 2008-05-07
:) Hello stokerw,
You don't need to be concerned about the extra boot options, that's perfectly normal. When we receive a new kernel in an update, the new kernel will be added to the top of the list, and that's the best one to boot.
Just for safety though, they still leave your old kernels in your system and move the entries for booting them further down the list. They do that just in case there's ever something wrong with a new kernel and it doesn't work in your computer or something like that. In that case you can try booting with your older kernel and your computer should boot okay.

If you think it's messy or your list gets too long, you can place 'hash' marks before the start of the line, see this link for more information,  [Hide titles in the GRUB Menu]("http://users.bigpond.net.au/hermanzone/p15.htm#hide_items").- tidy up, comment out extra entries you'll never use.

Regards, Herman :)

EDIT: The file that controls your GRUB menu is your /boot/grub/menu.lst file in case you don't already know, and you can open it in a terminal and edit it. I am not sure if you are new so I just thought I had better explain that just in case. If you are new then possibly this link might be a good place to start, [Orientation]("http://users.bigpond.net.au/hermanzone/p15.htm#orientation"). - a guided tour of some of the most important files needed for booting Linux.

---

### Post by PCWizKid on 2008-05-07
[IMG]http://bp2.blogger.com/_ofqWS815dOE/SCCXZNH8XHI/AAAAAAAAAls/9jptnKJUWIg/s320/hardy_splash.jpg[/IMG]
Hi, I have similar boot options aswell, they are fine and as expected, I finally toke the plunge and upgraded my Ubuntu 7.10 - Gutsy Gibbon to 8.04 LTS, I recorded the steps and captured it for anyone that would like to see exactly what was involved in doing the upgrade.  [Take a look here]("http://pcwizkid.blogspot.com/2008/05/ubuntu-804-hardy-heron-upgrade.html").

Cheers
[PCWizKid]("http://PCWizKidsTechTalk.com")

---

### Post by stokerw on 2008-05-07
Hi, Many thanks for that helpful reply.
Yes I am new, and just building up my expertise. So much is quite different from Windows.
Your a :KS
Stoker.

---

