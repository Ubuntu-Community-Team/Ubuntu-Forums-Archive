---
title: "failure to boot up, please help"
date: 2010-12-16
forum: Installation &amp; Upgrades
---

### Post by Chazz44able on 2010-12-16
HI, thanks in advance for your help, I've got a problem at boot up  on my Laptop (HP Compaq 670b). I dual boot Windows XP and Ubuntu 10.04 Lucid lynx. I recently re-installed Ubuntu and repartitioned my hard drive. Everything was working fine to begin with, as I'd only been using Ubuntu. As soon as I booted up in Windows (a few days later) it showed the windows XP blue screen and ran a disk check, then appeared to start fine. After a while a notice came up on the desktop saying: "new software successfully installed, restart now?" I clicked restart later and when I did then later reboot in order to go into Ubuntu, just before it entered the GRUB it came up with the message:
"Non-System disk or disk error
replace and strike any key when ready".
When I then press enter it runs a load of commands and then comes up with the message:
"no module name found
aborted. Press any key to exit".
When I then press enter again it comes up with the first message again.
I've now booted from a live CD to do this, so please help!
Thanks a lot for your time

---

### Post by Tweedle on 2010-12-16
if u are able to, boot into the ubuntu thats already install, goto a terminal and run "grub-install /dev/sda" then run "grub-update"

not sure if this will fix it, but it sounds like you mbr has bad info and it should be replaced. i think this will install grub into your mbr and then update it to show ubuntu and windows. then you should see grub and the options to goto windows or ubuntu.

im not 100% sure on this, you should wait to see if someone else can collaborate on this, i the mean time, look for UBCD 5 and burn it. it is your BEST FRIEND :D from there u can boot your computer, even if u can't other wise. as long as you have destroyed the OS you wanna use.

good luck and never give up.

Tweedle

---

### Post by Chazz44able on 2010-12-16
I can't boot into anything at all, the only way I can do anything is to boot using a live CD

---

### Post by Akavashi on 2010-12-16
As you have a Live CD already, I think that [[COLOR="Red"]this post[/COLOR]]("http://ubuntuforums.org/showpost.php?p=9884063&postcount=1") will come in handy. :P
Good luck!

---

### Post by Tweedle on 2010-12-16
sweet! i guess i should have read it better, you can follow those instructions and be on your way. :D

---

### Post by Chazz44able on 2010-12-16
I'm not entirely convinced it's a grub problem

---

### Post by Akavashi on 2010-12-16
Hmmm... This might be similar to your problem, in which it is a Grub2 bug :/
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/551721]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/551721")
Have a read through it, and see if it matches your problem, and then add yourself to the list if it is.

Oh and one person suggested that BURG (Brand-new Universal loadeR) be a fix.
[http://code.google.com/p/burg/wiki/InstallUbuntu]("http://code.google.com/p/burg/wiki/InstallUbuntu")

---

### Post by Chazz44able on 2010-12-17
okay, thanks, I'll try that this evening... can I install that from a Live CD?

---

### Post by Akavashi on 2010-12-17
Fingers crossed, but I think you should be able to add the BURG repository and then install it within the LiveCD (Or maybe try a LiveUSB preferably, if you can).
Then you would just follow the steps from the [BURG Install]("http://code.google.com/p/burg/wiki/InstallUbuntu") website as above

---

### Post by Chazz44able on 2010-12-18
okay, I've tried to use Burg, but I can't save the sources list after I have added in the extra two lines, as I don't have permission. I've tried to change the permission of the folder, but it says that as I'm not the owner, I cant.

---

### Post by Chazz44able on 2010-12-18
don't bother answering that, I was just being an idiot... I did gedit /etc/apt/sources.list I then realized I needed to be root, so just added sudo to the start

---

### Post by Chazz44able on 2010-12-18
okay then, I couldn't do the BURG install from the LiveCD, as I any changes are only saved on the Live CD's temporary files. I suppose using CHroot privileges may have worked, but I didn't try that. Instead I decided that I'd uninstall and re-install the GRUB2, which worked well for the first and second boot - first to Ubuntu, second to Windows _ but when I attempted to re-boot into Ubuntu again, it didn't show the grub... I've now re-installed the GRUB2 for a second time and am going to try to do the BERG install now.

---

### Post by Akavashi on 2010-12-18
Awesome! Fingers crossed that you can manage to get it installed properly.
And if you're really keen, you can theme BURG up to look all perty like :P
Good luck once again!

Oh! And don't forget to post back here if it works, then you can mark the thread as solved so other users can find the answer ^^

---

### Post by Chazz44able on 2010-12-22
It seems to be working fine and consistently in Ubuntu, I haven't tried booting into XP yet, as I have no need to and don't want to have to do it again... I've changed the boot theme, but what do you mean by customising it? - sorry for the late update.

---

### Post by Akavashi on 2010-12-23
Downloading the themes that are in the following list:
[http://code.google.com/p/burg/downloads/list]("http://code.google.com/p/burg/downloads/list")
Or if you're savvy enough, you can write your own (This is what I would mean by customising; although, I never said anything about customising, except for putting on a theme).

---

