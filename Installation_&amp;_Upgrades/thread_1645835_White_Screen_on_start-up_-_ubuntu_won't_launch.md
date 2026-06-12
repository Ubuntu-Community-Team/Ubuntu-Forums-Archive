---
title: "White Screen on start-up - ubuntu won't launch"
date: 2010-12-15
forum: Installation &amp; Upgrades
---

### Post by guntu on 2010-12-15
Hi,

I have been running Ubuntu 10.04 Lucid not on a separate disc partition but installed right on my Windows (7) partition. Everything was working fine until yesterday.

I restarted my computer and then the system was scanning the disc then suddenly after the disc check, the computer restarted and when it was supposed to launch Ubuntu, the screen went completely white.

I tried restarting again, I manage to get to where I choose to boot with Windows 7 or Ubuntu. I choose Ubuntu and the same happens again: white screen. 
It doesn't go any further than this and the only thing the computer can do is boot with Windows 7.

Has anyone had the same problem? Any idea how to fix it?

Also, is there a way I can access my files (saved in Ubunutu) from Windows? If I can manage to copy these files then I don't mind reformatting the whole disc. 

I appreciate anyone's help, thanks!

---

### Post by sikander3786 on 2010-12-15
Is Windows 7 still working fine?

And was Ubuntu installed inside Windows using the Wubi installer or this is a proper dual-boot setup?

You can access the files by mounting your Ubuntu partition/Wubi folder under a Live Ubuntu CD/USB but the issue you are facing might be fixable. Instead of going for a re-install, please provide us with more details.

---

### Post by bcbc on 2010-12-15
This thread likely contains a fix [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

It also has a link to a tool you can use to retrieve your Ubuntu data from Windows (ext2read).

---

### Post by guntu on 2010-12-15
> **sikander3786 said:**
> Is Windows 7 still working fine?

And was Ubuntu installed inside Windows using the Wubi installer or this is a proper dual-boot setup?

You can access the files by mounting your Ubuntu partition/Wubi folder under a Live Ubuntu CD/USB but the issue you are facing might be fixable. Instead of going for a re-install, please provide us with more details.


Hi, thanks for the response. 

Yes, Windows 7 is still working fine.

I installed Ubuntu inside Windows ( I'm assuming using Wubi installer?  I downloaded it from the Ubuntu page [http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)).  But for sure it's not a proper dual-boot setup. 

I'll give it a try tonight using a Live Ubuntu CD/USB to try en recover my files, then move onto the fix from the other post (above) and see if I can fix it. 

Would you recommend that I do a proper dual-boot set-up? Would this save me future problems? 

Thanks again!

---

### Post by sikander3786 on 2010-12-15
The link that bcbc posted will definitely take you out of troubles. See problem # 2 there.

There is a section named Permanent Fix on that thread. Once you fix and are able to boot your Wubi install, apply the fixes mentioned there and it might be more stable.

A proper dual-boot is always recommended if you intend to use Ubuntu as a production OS. The creator of Wubi says that it was meant just to easily test Linux and not a long term solution ;-)

Feel free to ask if you want a dual boot setup. There are many of us here who can help you.

A proper dual boot is a bit faster and lot more stable than Wubi one.

---

### Post by guntu on 2010-12-16
Thanks again for the help [sikander3786]("http://ubuntuforums.org/member.php?u=806649")  & [bcbc]("http://ubuntuforums.org/member.php?u=946783")! 

I downloaded Ubuntu 10.04 last night and burned it in a disc. I'm going to use it to recover my files first and then I'm definitely going to do a proper dual-boot set-up this weekend. :p

---

