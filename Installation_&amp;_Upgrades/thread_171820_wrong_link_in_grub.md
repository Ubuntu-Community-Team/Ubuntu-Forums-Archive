---
title: "wrong link in grub"
date: 2006-05-07
forum: Installation &amp; Upgrades
---

### Post by ichigo on 2006-05-07
I've got a problem with grub:
After installing windows I put grub into the mbr again, which worked fine. But after that I noticed that grub refers to an ubuntu installation on hda8, my ubuntu is on hda7. Obviously I can't boot to ubuntu now...
I tried to change the boot/grub/menu.lst using ubuntu live and Knoppix. I mounted hda6 with rw access, but still I couldn't change system files like menu.lst. :( 
Does anybody know how to change those files (for example using ubuntu live etc.)? Or do you know another way to make grub work correctly? (without reinstalling ubuntu)

---

### Post by louis_nichols on 2006-05-07
the easiest way is still to boot your ubuntu installation and sort things after

be careful, because grub will always see partitions with one number lower than linux (for example /dev/hda3 from Linux will be (hd0,2) in grub)

so just boot your grub, select the line about your current Ubuntu and press "e" to edit boot options for that entry

go to the line with root and edit accordingly. You're suggesting it says (hd0,7) so that you have to change to (hd0,6) then press enter to save the change for that session, then "b" to boot

after this you'll be able to boot your ubuntu and edit your menu.lst

edit: typos

---

### Post by ichigo on 2006-05-07
Thx for your help so far! I managed to get into ubuntu with your help! But I wasn't able to log in as root so far. On "sudo -i" it says:

sudo: /etc/sudoers is mode 0644, should be 0440

(here are the two lines from that file:
root	ALL=(ALL) ALL
%admin	ALL=(ALL) ALL

"su root" etc. ask for a password, but none of the paswords I usually use works.
There are many more things that are quite strange, since I manually entered ubuntu. I can't access synaptic (it doesn't even ask for a password). I got an error message saying gstreamer isn't installed or my soundcard isn't configured correctly, but sounds are played perfectly...

---

### Post by louis_nichols on 2006-05-07
well... let's take it one step at a time. Your booting the way I told you has not changed anything of the way your system was booting before, so the culprit is somewhere else.

The contents of the file are what they should. I don't exactly understand why you need to run sudo -i but you can just make the change it requires:

```
sudo chmod 0644 /etc/sudoers
```

---

### Post by ichigo on 2006-05-08
Actually the code you gave me returns the same line as other sudo-commands did - since /etc/sudoers was in the wrong mode. My problem was that I had couldn't go to root mode, as you can see in my old post. 
Hence I wasn't able to change any  system file
I used the recovery mode to get root access and made my modifications there. 
And I suppose you ment 0440 instead of 0644...
Anyway, thankyou for helping me to make ubuntu work again!

---

### Post by louis_nichols on 2006-05-08
[QUOTE=ichigo]Actually the code you gave me returns the same line as other sudo-commands did - since /etc/sudoers was in the wrong mode. My problem was that I had couldn't go to root mode, as you can see in my old post. 
Hence I wasn't able to change any  system file
I used the recovery mode to get root access and made my modifications there. 
And I suppose you ment 0440 instead of 0644...
Anyway, thankyou for helping me to make ubuntu work again![/QUOTE]

You're right, I missread and should have written 0440 in the command. Sorry about that.

Glad it's working again, though. :)

---

