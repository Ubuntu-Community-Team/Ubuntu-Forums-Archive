---
title: "Unable to boot Ubuntu 15.10 (Mate) DVD"
date: 2016-03-26
forum: Installation &amp; Upgrades
---

### Post by Shannon_Stephens on 2016-03-26
I'm having trouble booting Ubuntu 15.10 (Mate) DVD.  When I boot from the DVD I get a plain Grub2 boot screen where I can chose:  Try Live, Install Ubuntu, Check Media.  Regardless of which one I pick I get the same results.  The screen goes black & then the about 10 sec. later the PC reboots.  I'm not a complete noob but I've never ran into this issue before.  I know in the past you could change your graphic boot options but they are no longer on the boot DVD.  Here are my system specs just in case.

AMD Athlon X4 750K Quad Core 3.4 GHz
16 GB RAM
Radeon R9 270 2GB

If anyone can offer help I would appreciate it.

---

### Post by Shannon_Stephens on 2016-03-26
I have determined the issue lies with videocard.  I used my DVD and was able to install onto a VirtualBox VM without issue.  Anyone have suggestions?

---

### Post by yancek on 2016-03-26
Try adding the nomodeset option on boot as explained in the link below.

[http://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu](http://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu)

---

### Post by Bucky Ball on 2016-03-27
Using nomodeset, as suggested above, but the link above doesn't apply to you as it shows how to add nomodeset to the grub kernel line at boot on an already installed system.

Boot from the install media and when you get to the purple screen with the little icon down the bottom, hit a key (from memory it's any key but feel free to correct me anybody). At the next screen, 'Try Ubuntu', etc, hit F6. That will bring up some options. In there you will find 'nomodeset'. Choose that and continue. Any luck?

---

### Post by Shannon_Stephens on 2016-03-27
Thanks for the suggestion Bucky.  However the problem is I don't get a normal Ubuntu Boot screen.  This is the boot screen I get:

[IMG]http://i.imgur.com/tshD0hf.png[/IMG]

After this no matter what option I select it just reboots.  I never get to the purple screen.

---

### Post by Bucky Ball on 2016-03-27
Ah. In that case, the link provided earlier, or something like it, might work.

Highlight 'Try Ubuntu' and hit 'e'. That should take you to another page. On that page, look for the kernel line that ends in 'quiet splash'. Add 'nomodeset' after a space at then end. This:

> quiet splash nomodeset

Follow instructions at the bottom of the page to save the change and continue. Get any further?

I am presuming you are going to the kernel line when you hit 'e'.

(PS: Please attach large pics rather than inserting them in your posts. 'Adv Reply' or 'Go Advanced' and use the paperclip icon. Large pics are not good for those (potential helpers) with slow connections and/or vision issues. Thanks.)

---

