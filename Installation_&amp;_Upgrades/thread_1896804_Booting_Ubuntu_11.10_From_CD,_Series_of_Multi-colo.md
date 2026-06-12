---
title: "Booting Ubuntu 11.10 From CD, Series of Multi-colored Screens"
date: 2011-12-17
forum: Installation &amp; Upgrades
---

### Post by orange.emilie on 2011-12-17
Hello. I'm a brand new Ubuntu user, or rather, I am trying to be. Let me tell you what I've been through in the last 24 hours, so that my question can be put into context.

I bought an IBM ThinkPad T60 from eBay with Ubuntu 11.10 installed. I was excited to start using Ubuntu. However, the computer came password-protected. I emailed the seller to no avail.

I followed directions on this forum on how to reset the password from the root shell. I came up with the error "authentication token manipulation error." So, I then followed directions on how to delete likewise-open, libpam-sss and libnss-sss. That didn't work. I heard about the mounting/unmounting trick, but I couldn't find detailed instructions and was afraid to do it without knowing what I was doing.

So I decided to do a clean install of Ubuntu 11.10, thinking it would replace my current version. I successfully made a boot CD with the iso file. However, it froze at the "Installation Setup" screen.

I searched the forums for this, and it seemed as though the issue was caused by an "unclean" swap partition. Because I thought that the swap partition would be replaced when installing Ubuntu again, I deleted it.

I re-booted my computer to go through the installation once more. After the screen with the Ubuntu logo with the little dots underneath, now a series of blank, colored screens show up intermittently at intervals of about 3 seconds. Colors include: red, blue, grey, greyscale gradation, etc. Quite beautiful but I am perplexed.

My question: Did I mess up by deleting the swap partition? Does it have anything to do with the gorgeous colors I'm now seeing?

---

### Post by Buntumatic on 2011-12-17
orange.emilie,

welcome to exciting world of Linux!

As I understand your installation attempt wasn't successful. Among other things it means the original install is still intact.
Booting up in single user mode is probably the easiest way to gain full control over your laptop. Have you tried that?

---

### Post by orange.emilie on 2011-12-17
Thank you for your reply. 

I have not tried single-user mode. Should I attempt to reset the password from there?

---

### Post by Buntumatic on 2011-12-17
Yes, single user mode will give you root shell without asking for password. You can add a new user - yourself - from there and after reboot you will be able to log in as yourself. I'm sure there are plenty of tutorials in Google to help you, however if you feel stuck do not hesitate to ask. :)

---

### Post by orange.emilie on 2011-12-17
Well, the plot thickens. Before I read your reply about single-user, I tried the install disc again. This time, I got 2/3 the way through the installation before it crashed, but not before it deleted my partitions. Now when I boot up my computer there is only a blinking text cursor.

I'm assuming I deleted the original OS.

Oh brother. I am going to try to make a new CD & re-try the installation. I guess I should have waited before giving up on the first OS. :/

---

### Post by Buntumatic on 2011-12-18
orange.emilie,

the problems you describe imply you may have a hardware problem. RAM is the first suspect, there is a memory check application in install CD, I believe. Running it may be a good idea.
FWIW, if you only deleted - bot didn't format - your partitions it's relatively easy to restore with testdisk utility.

---

### Post by orange.emilie on 2011-12-18
Buntumatic,

I'm going to be getting another Ubuntu install disc in a couple of days. The one I tried earlier now fails whenever I try to boot with it, saying there's an error with the disc.

So, once I get the new disc I will check the memory as you suggested. And thanks for letting me know about the partitions. Once I'm able to download the TestDisk utility I'll give that a try.

Thanks again for your advice. :)

---

