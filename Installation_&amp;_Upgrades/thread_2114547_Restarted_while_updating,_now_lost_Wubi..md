---
title: "Restarted while updating, now lost Wubi."
date: 2013-02-10
forum: Installation &amp; Upgrades
---

### Post by xerosugar on 2013-02-10
Ubuntu was in the middle of an update when it seemed like it had stopped working. Cancel button was grayed out and the progress  indicator didn't move at all...

I thought I had no other choice but to restart Ubuntu. Thinking that it might pick up the update process from where it was when I got back. So I chose to restart, and when I got to the boot menu, which for me is:

- Windows7
- Ubuntu

I chose Ubuntu, but that didn't load Ubuntu at all. Instead, I was presented with another menu, which was:

- Windows7

(Booting windows is not a problem btw)
So, what are my options? Reinstall Wubi, or fix this mess I've created? If I reinstall Wubi, can I use the root- and swap .disk files from my previous installation?

---

### Post by U202E on 2013-02-10
as far as I know reinstalling is the easiest option, and just backup your settings and documents...

but before trying it: can you access your files from within win7? so that you check the file-system.

---

### Post by bcbc on 2013-02-10
Reinstalling will wipe out the old install completely. If you need to recover data, do that first.

You can use this tool to get readonly access to the root.disk from Windows. It's a bit flaky but it works. [http://ext2read.blogspot.com/](http://ext2read.blogspot.com/)

Or you can boot a live USB/DVD and access the root.disk from there. This is also the method you will likely need if you want to try to fix your problem. If you do, boot the Ubuntu CD and post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and then we can see what's up and I can give you some more instructions.

Note, that reinstalling and using the old root.disk will probably not fix whatever is going on, because everything you use to boot is contained on the root.disk and will likely just get passed over to the new one. 

If you can't be bothered to attempt repairs which may not work ultimately, you can just backup your data and reinstall.

---

### Post by xerosugar on 2013-02-11
Thanks for the tips. I think I'll just reinstall Ubuntu from scratch since I didn't have that much stuff installed. I'll be back if I run into problems!

---

