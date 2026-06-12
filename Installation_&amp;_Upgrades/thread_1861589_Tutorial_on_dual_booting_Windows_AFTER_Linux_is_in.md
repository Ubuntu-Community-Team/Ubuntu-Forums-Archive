---
title: "Tutorial on dual booting Windows AFTER Linux is installed first..."
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by travlemon on 2011-10-15
Hello!

Lately I've been making tutorials for what I feel to be common Linux problems that can be easily solved, but may be difficult for a new user to find the right instructions.  I'm still quite new to Linux, but I've been learning a lot, just by being a user that has to mess with things all the time.  I say that because it's important to understand that I am natively a Windows expert, not a Linux expert, and to keep that in mind when viewing my tutorials.

ANYWAY, there is what seems to be a popular tutorial out on the internet that addresses the topic of:  **Dual booting Windows XP with Linux on a computer where XP is already installed**.  The article is located here: [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

I found a way to accomplish this that's incredibly easy, easier than the confusing things I read in this article.  The easy parts are resizing partitions to make space for XP as necessary.  

The harder part is reinstalling Grub.  Also, the article mentions that because the XP installation recognizes the first existing Linux paritition as drive C:, that XP will have to call its own partition drive D: (or whatever drive letter is available, because the Linux partition now exists as drive C:).

I found incredibly easy ways to take care of these:

1. _The Drive C:_ issue:  When you're resizing partitions to make unallocated space for XP, simply create an NTFS partition where you'd want XP installed.  In the XP installation screen, it'll see it as drive C:.  Simple!! I'd recommend this over letting XP setup drive D: as the system drive.

2. _Reinstalling  Grub:_ for anybody who isn't too savvy with the grub stuff, there's a great alternative.  Use the Boot Repair CD boot into either 32-bit or 64-bit mode (depends on your processor).  Then simply choose the options to reinstall grub and unhide the menu.  Done!

I found these 2 things to be extremely useful and it worked perfectly for me. 

Anyway, my reason for this post is to see if people would like to see a tutorial on this.  I think it'd be a huge step above having to run grub commands, especially for newer users.  

Opinions??  (or perhaps I'm a little late on actually finding these methods and there might already be a tutorial out there)

---

### Post by travlemon on 2011-11-16
Well, I ended up making this tutorial.  I know Windows XP is a bit obsolete, but it still seemed like a worthy topic to tackle.  So here it is, for anyone who needs it:

**How to install Windows XP to dual boot with Linux, when Linux was installed first:**
[http://www.youtube.com/watch?v=7-Zs5eyxbFo](http://www.youtube.com/watch?v=7-Zs5eyxbFo)

I hope this becomes of great use to anyone who needs it!  Feel free to respond with comments/feedback or leave directly on the video's YouTube page.

---

