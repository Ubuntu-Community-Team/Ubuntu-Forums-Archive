---
title: "Update Problems"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by thestig_992 on 2008-05-26
I was updating my Hardy computer on the weekend, and stupidly logged out of my computer and turned it off while the update was still installing. It poped up with an error message saying it would restart the install process when i logged back in, but it didnt. Now im stuck with a low screen resolution, a strange theme, and a large deafault text size, none of which i can change.

Im fairly sure that this is to do with the update on the 24 may (though there were 60mb of updates as i hadnt updated in a while). I was wondering if there was any way to reinstall the updates, or if I can use the 8.04 CD to repair or anything like that...
Thanks in advance...

---

### Post by iaculallad on 2008-05-26
> **thestig_992 said:**
> I was updating my Hardy computer on the weekend, and stupidly logged out of my computer and turned it off while the update was still installing. It poped up with an error message saying it would restart the install process when i logged back in, but it didnt. Now im stuck with a low screen resolution, a strange theme, and a large deafault text size, none of which i can change.

Im fairly sure that this is to do with the update on the 24 may (though there were 60mb of updates as i hadnt updated in a while). I was wondering if there was any way to reinstall the updates, or if I can use the 8.04 CD to repair or anything like that...
Thanks in advance...

Try to logon using the Recovery mode (Press ESC when GRUB is loading at boot time)

Input the commands below into your terminal:

**Code:**

> sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade

---

### Post by thestig_992 on 2008-05-26
Getting into recovery mode doesnt seem to work for me...Pushing escape while grub is loading does nothing. When the menu loads (I have it set up to triple boot XP, 7.10, and 8.04) I dont have any options to do with recovery mode...
It might be something to do with my other issue that im getting around to fix, which is that Im booting off grub from my 7.10 partition, then pointing it at the 8.04 partition.

Also, when i try running those commands in the terminal, the **sudo apt-get -f install** doesnt do anything except check what needs to be installed (which in this case is nothing). Because of this I didnt try runny the other commands, as as far as I can tell they kinda depend on it working...
Thanks for the quick response though

---

### Post by iaculallad on 2008-05-26
Try to follow this [link]("http://sudan.ubuntuforums.com/showthread.php?t=306424") to solve you're broken upgrade.

Same process as above (using the terminal) except you are to use the Ubuntu LiveCD.

---

### Post by thestig_992 on 2008-05-26
sorry about that, I managed to fix my boot file after all to include the recovery mode. Along the way though, I screwed up my hdd order, so couldnt boot. Then i fixed it with grubs options, booted regular modeto test that it worked, and god behold, my desktop was back to normal!

Really sorry for all ur effort, adn thanks very much for ur quick help XD

---

