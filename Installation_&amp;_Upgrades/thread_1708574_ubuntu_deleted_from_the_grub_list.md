---
title: "ubuntu deleted from the grub list"
date: 2011-03-16
forum: Installation &amp; Upgrades
---

### Post by jogonjr on 2011-03-16
I used grub customizer to delete the extra ubuntu entries on the grub after an update but when i restarted what was left was just windows and mac. Is there any way to put it back?:confused:

---

### Post by RDeeKoi on 2011-03-16
Bear with me, this is my first reply/post.

The actual grub.cfg file is located in /boot/grub/grub.cfg

The .cfg file is just a script that displays the entries you see in your grub menu on boot.

You can just edit that file (using any editor) and add the Ubuntu menuentry line back.  If you don't want to edit that file, you can probably run /usr/sbin/grub-mkconfig to re-generate the .cfg file.

---

### Post by jogonjr on 2011-03-17
thanks but how can i edit that file? i cannot see the ubuntu drive from windows. can it be done if i boot to the ubuntu disk?

---

### Post by RDeeKoi on 2011-03-17
Sorry, I just assumed you were in Ubuntu.
Not sure booting from the live CD will work.

Found this thread from a couple months ago: [http://ubuntuforums.org/showthread.php?t=1378212](http://ubuntuforums.org/showthread.php?t=1378212)

You might be able to use that software within your windows environment.

---

### Post by sikander3786 on 2011-03-17
Instead of doing anything fancy, the easiest solution is to re-install Grub. The simple way takes just 2 commands or if that is not successful, you might need to chroot and purge your Grub which might take a bit more.

In order to let us see the problems and give you exact commands to follow, we need you to boot an Ubuntu Live CD/USB and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

While posting, click the # icon in post menu and paste your text in between the generated [code] tags for readability purposes as this will be a long output.

---

