---
title: "Windows XP &amp; Ubuntu Dualboot Problem!"
date: 2006-10-20
forum: Installation &amp; Upgrades
---

### Post by I3roknI3ottle on 2006-10-20
Ok So have my 40gb hardrive setup like this

28GB = Windows
1GB = Linux Swap
4GB = Ubuntu
4GB = Backup

I have Acronis OS Selector installed on this laptop

I installed ubuntu on the 4gb partition thinking I could use Acronis OS Selector to select Ubuntu when I wanted to use it. Little did i remember, when I restarted my computer after installing GRUB boot selector showed up and it shows my Ubuntu installs. 

My question is how can I get back into windows or am I able to use Acronis OS Selector and ditch GRUB? Any Help is Appreciated.

---

### Post by randell6564 on 2006-10-20
> **I3roknI3ottle said:**
> Ok So have my 40gb hardrive setup like this

28GB = Windows
1GB = Linux Swap
4GB = Ubuntu
4GB = Backup

I have Acronis OS Selector installed on this laptop

I installed ubuntu on the 4gb partition thinking I could use Acronis OS Selector to select Ubuntu when I wanted to use it. Little did i remember, when I restarted my computer after installing GRUB boot selector showed up and it shows my Ubuntu installs. 

My question is how can I get back into windows or am I able to use Acronis OS Selector and ditch GRUB? Any Help is Appreciated.
Dont know anything about 'Acronis' but you should have just left Ubuntu to install to the appropriate partition. She would have then recognized Windows, installed GRUB to your MBR and you would have had your dual-boot option!

---

### Post by lloyd_b on 2006-10-20
> I installed ubuntu on the 4gb partition thinking I could use Acronis OS Selector to select Ubuntu when I wanted to use it. Little did i remember, when I restarted my computer after installing GRUB boot selector showed up and it shows my Ubuntu installs.

My question is how can I get back into windows or am I able to use Acronis OS Selector and ditch GRUB? Any Help is Appreciated.

Personally, I would suggest using GRUB and ditching the Acronis.  However, since I've never used Acronis, I'm not in a position to judge it's merits vs. GRUB.

At any rate: To add XP to GRUB:

edit /boot/grub/menu.lst, adding the following (at the end of the file would be easiest):

Title       Windows XP
root        (hd0,0)
makeactive
chainloader +1

Then, run "grub-install /dev/hda"

Reboot, and "Windows XP" should appear at the bottom of the list.

To tell the truth, I'm a little surprised that it's not already there - generally the GRUB installer detects Windows and automatically adds an entry for it...

Lloyd B

---

### Post by I3roknI3ottle on 2006-10-20
how do i edit grub, i've never really had any experience with it as all my linux installs were by themselves.

---

### Post by hearnden on 2006-10-20
You edit your grub boot options by editing the file /boot/grub/menu.lst.  In Ubuntu, look for that file, and edit it with whatever editor you like to use in Ubuntu.  gedit, emacs, terminal and nano, up to you. lloyd_b's instructions should work just fine.

---

### Post by Herman on 2006-10-20
Hello I3roknI3ottle, 
> how do i edit grub, i've never really had any experience with it as all my linux installs were by themselves.I agree with the above posters. lloyd_b's instructions should be all you need.
 
I hope you will like Grub. Grub is the best bootloader in the world, but some people still don't know how to use it. Actually, it's much more than just a bootloader. You will be more likely to appreciate it if you can find out all about it, so here's a webpage about all the things you can do with Grub. [Click Here.]("http://users.bigpond.net.au/hermanzone/p15.htm")
Enjoy Grub and don't be afraid to experiment a little with it, Grub can be a lot of fun, 
Regards, Herman :D

---

### Post by I3roknI3ottle on 2006-10-20
figured this out, that grub page was a great tut.

i dumped os selector, i only used because i was dualbooting windows xp & osx86 and that was the easiest/problem free boot loader for the it.

---

