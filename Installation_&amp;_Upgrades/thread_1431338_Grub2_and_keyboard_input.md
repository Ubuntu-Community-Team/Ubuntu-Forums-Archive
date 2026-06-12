---
title: "Grub2 and keyboard input"
date: 2010-03-16
forum: Installation &amp; Upgrades
---

### Post by Eric1701 on 2010-03-16
I hope this is the right forum to post to as I suspect that it is a Grub2 which would affedt both Mythbuntu and Ubuntu issue and not just a Mythbuntu issue as I can boot into Mythbuntu as described below.

I was using Mythbuntu 8.04 with no problems and then my hard drive crashed so I thought why not install the latest version of which is Mythbuntu 9.10 I did the install and everything seemed to go fine until I rebooted.  

I'm using a PS/2 keyboard.  The Grub2 screen comes up and if I let it time out it will boot fine or if I hit enter it will boot fine but if I want to make another choice like memtest or boot another OS which Grub detected on put on the menu when I hit the arrow key to change my choice it will move down to the next choice but then Grub2 locks up it won't accept anymore keyboard input.  Are there any ideas on how to get Grub2 to fully work.

One thing I tried is I found out how to downgrade / revert to Grub which worked fine I was able to make choice and use the keyboard to navigate the grub menu.  But I would really like to know why Grub2 won't work all the way and if there is a way to fix it.

Thank you for any help or suggestions anyone can supply.
Eric1701

---

### Post by oldfred on 2010-03-16
I had the same problem with old grub when I installed a new motherboard a year ago. It was a BIOS setting on USB keyboard and mouse. My first workaround was scrambling around to quickly switch from USB port to the ps/2 ports and back when I booted.

---

### Post by Eric1701 on 2010-03-16
Thank you [oldfred]("http://ubuntuforums.org/member.php?u=852711") your comment about having to switch from usb to ps/2 when booting put me onto the right track.  however it seems to be the opposite of your situation.  As I am using a PS/2 keyboard.  What I did was go into the BIOS and disabled "USB BIOS Legacy Support"  and that did the trick.  I'm now able to navigate the grub2 menu using the keyboard.  

Thank you so much.

---

