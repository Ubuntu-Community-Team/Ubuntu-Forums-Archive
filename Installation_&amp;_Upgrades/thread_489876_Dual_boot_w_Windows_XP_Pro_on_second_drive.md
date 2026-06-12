---
title: "Dual boot w/ Windows XP Pro on second drive"
date: 2007-07-01
forum: Installation &amp; Upgrades
---

### Post by ciscoookid on 2007-07-01
Hi all,

I recently stumbled upon a version of Windows XP Pro on a torrent site, downloaded it, burned the iso, and was putting it in and rebooting, when I realized, I really don't want my computer to be as messed up as it was when I tried to have a dual boot before. 

ANYWAY, my question is how can I install Windows on my second hard drive and edit my GRUB loader to show up with them both? I looked at another post similar to this, but I couldn't understand half of it. 

Can anybody help me, in simple terms?

Thanks

---

### Post by mikewhatever on 2007-07-01
Are you asking for help with pirated software? My advice, do not install it. Its against the law, and such stuff is usually full of spyware and viruses.

---

### Post by ciscoookid on 2007-07-01
It's not really pirated, it's just a copy of it that comes with the cd key. I was gonna do it with Vista, but I know that they're cracking down on pirated versions.

---

### Post by skar0059 on 2007-07-02
First, I do not see how that is not piracy.  But I do not understand your situation.

Read here.  It is very simple.  Edit your /boot/grub/menu.lst, the details of how to edit it are as follows.

[http://icculus.org/~lucasw/Linux/Linux%20and%20XP%20Bootloading.html](http://icculus.org/~lucasw/Linux/Linux%20and%20XP%20Bootloading.html)

---

### Post by ciscoookid on 2007-07-02
So.. In that article it didn't end up working. Is it even possible to do this? When I type in this:

 sudo gedit /boot/grub/grub.conf

nothing happens. Gedit opens up, but it's a blank document. How do I get this to work?

..And yes, I know it's a pirated copy, I just didn't want everyone dismissing me as a moron. But it's already out there.. And I installed it on my other machine and it worked fine. The CD key worked and it installs.

---

### Post by logos34 on 2007-07-02
No, it's

[B]
sudo gedit /boot/grub/menu.lst
[/B]
Or better yet
[B]
gksudo gedit /boot/grub/menu.lst[/B]

You know, if you have a 64-bit processor you can download a free (and perfectly legal) trial version of Windows XP Pro x64.

---

### Post by ciscoookid on 2007-07-02
Well, I edited the  /boot/grub/menu.lst, putting in the lines from that site in at the bottom, and it worked perfectly. But it still boots to Ubuntu by default, whereas when I had Windows on my second drive, it would give me the list of operating systems to boot. How can I set it back to that? I can choose which one I want to boot, of course, but I'd prefer seeing the list instead of having to hit escape right when it boots up.

---

### Post by logos34 on 2007-07-02
comment out hiddenmenu and change the timeout

**timeout  5**  (or however many secs)

**#hiddenmenu**

---

