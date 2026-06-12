---
title: "Luks issue with Karmic"
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by nunki on 2009-10-10
I just upgraded to Karmic and everything went fine. However, when I boot up now, I am no longer prompted for my passphrase for my two luks encrypted drives. One of the drives contains /home, the other is just storage. The boot hangs, and nothing happens. On a whim, I wondered if it was stuck at the prompt, but I just couldn't see it. I typed my passphrase into a blank screen and viola, the boot sequence finished.

Has anyone else experienced this? All the data for my drives seems to be intact and accessible. Somehow, Im not seeing any prompts. Any suggestions would be appreciated.

---

### Post by mannheim on 2009-10-10
Somewhere else here there's a thread complaining that there are no longer any error messages shown during boot now. Perhaps this is another symptom of the same problem.

Under Jaunty, were things set up so that you were prompted for the encryption key during usplash? And under Karmic, when you typed in the password "blind", was that during the (new) usplash -- i.e. the bare white ubuntu logo on a simple black background?

---

### Post by nunki on 2009-10-10
Yes, in Jaunty I would be prompted during the usplash. Now, the white logo appears...then fades. Until I type the password in "blind" the boot sequence never finishes.

---

### Post by nunki on 2009-10-10
It appears that this was a bug [43049]("https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/430496"). However, I seem to have the updated version of cryptsetup. Hoping someone else has had and solved this issue.

[update]
It looks like usplash and libusplash were updated today. Unfortunately this did not fix the problem.

---

### Post by nunki on 2009-10-11
bump

---

### Post by discordian on 2009-10-11
nunki: It might be best to disable the splash image until the problem is fixed. You'll be able to see the question then, altough the boot screen will look less pretty. 
This also suggests that this is a bug with usplash and not with cryptsetup; but i admit that, since turning of the splash image is one of my first things to do after installing any distro that features one, i haven't invested much time in finding the bug.

If you're using grub2, see this [howto](http://www.ubuntugeek.com/startup-manager-change-settings-in-grub-grub2-and-usplash.html), or, if you're still running grub v. 1, simply edit /boot/grub/menu.lst and remove the strings "quiet" and "splash" from the line(s) starting with "linux /vmlinuz [...]"

discordian

---

### Post by nunki on 2009-10-11
> **discordian said:**
> nunki: It might be best to disable the splash image until the problem is fixed. You'll be able to see the question then, altough the boot screen will look less pretty. 
This also suggests that this is a bug with usplash and not with cryptsetup; but i admit that, since turning of the splash image is one of my first things to do after installing any distro that features one, i haven't invested much time in finding the bug.

If you're using grub2, see this [howto](http://www.ubuntugeek.com/startup-manager-change-settings-in-grub-grub2-and-usplash.html), or, if you're still running grub v. 1, simply edit /boot/grub/menu.lst and remove the strings "quiet" and "splash" from the line(s) starting with "linux /vmlinuz [...]"

discordian

Ok I followed the howto and disabled the usplash for now. I can see the prompt now. This will have to do until someone is able to figure out what the bug is. Thanks for the tip.

---

