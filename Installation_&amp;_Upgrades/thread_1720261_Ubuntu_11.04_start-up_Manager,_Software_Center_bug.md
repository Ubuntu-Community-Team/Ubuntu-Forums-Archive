---
title: "Ubuntu 11.04 start-up Manager, Software Center bugs."
date: 2011-04-03
forum: Installation &amp; Upgrades
---

### Post by hari_home on 2011-04-03
I upgraded from 10.10 to 11.04 Beta using
sudo update-manager -d
I used Startup-Manager to change the boot default to the last item
on the list.

I noticed that it was always booting to the first item on the list.

As an experiment, I chose one item before last. Now it boots to the last
item on the list.

I noticed that grub boot menu shows latest linux kernel as first followed by
the recovery version, then there is a sub-menu for previous versions (there were 2 in my case if I choose the previous versions. After that there is memtest and another memtest (serial) and finally the Win 7.

I noticed that the StartUp-Manager does not show the sub-menu. It shows all the 7 menus. I think this is a bug in StartUp-Manager in 11.04.

Also, I downloaded dropbox .deb and tried to install with Software Center.
It gave me an error. However, 
sudo dpkg -i nautilus-dropbox_0.6.7_i386.deb

did the job.

I had to the same with skype install.

Software Center did install what were in its list. I tried vlc and emacs.
T=I checked the file permissions of ~/.cache/software-center
No problems there.

Hope this helps some one install and also find the fix.

---

### Post by gooby2 on 2011-04-06
Same thing with the start-up entries, but only since installing 11.04.38.8, was ok with 11.04.38.7 and 10.10 before that.
Removed 11.04.38.7 with janitor (Ubuntu Tweak won't install) but entries are still there in startup manager.

---

### Post by loopingz on 2011-05-04
As for startup manager, your post helped me understand. Sure it would need an update, but at the moment if you understand the trick it is quite easy.
At startup count the line number of what you want to set as default system.
Check that line number in Startup manager even if it says it is linked to something else. It just works.
If the line number in startup manager is bigger than total line number at boot then first line will be the default.
I believe the startup manager devs knows the issue, but maybe there is a way to contact them?

---

### Post by Kasual on 2011-05-10
I can also confirm this but what I first noticed was that the startup manager didn't perform the post configuration tasks like it normally does when you close it.  If you select anything other than the last item in the list then it will perform the post configuration tasks and let you know that you have selected a valid entry even if it isn't exactly what you might think you are selecting.

---

### Post by sabatorious on 2011-11-19
Thanks for the solution - I simply counted to the right line item (there were a bunch of extra lines in the selection box for Startup Manager) and bingo.  Thanks again, this was driving me nuts.

---

