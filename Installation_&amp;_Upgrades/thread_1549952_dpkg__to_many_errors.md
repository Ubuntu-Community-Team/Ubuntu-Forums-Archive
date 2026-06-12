---
title: "dpkg  to many errors"
date: 2010-08-10
forum: Installation &amp; Upgrades
---

### Post by carpman on 2010-08-10
Hello, ok have issues with an upgrade from 8.04 to latest.

System won't boot so an using livecd and chroot.

I have upgraded to grub2 via chroot but all the time with dpkg i am getting message 'to many errors?

I tried 'dpkg --configure -a' and get the same so did 'dpkg --configure -a --abort-after=99999' this worked in as now it will run to the end and stop without message about to  many errors.

looking at output it has long list of apps all with same reason, ie

[B]dpkg: error processing app name (--configure): dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of [/B]

Now the current issue is that grub is not finding the latest kernel dispute running update-grub. I have solved this in the past by removing all kernels and then installing latest again.

Trouble is can't remove old kernels as keep getting the message from dpkg  about 'to many errors'

any ideas?

cheers

---

### Post by rollin on 2010-08-10
If you want to remove old kernels try using synaptic, select "Installed" under "Status" and search for "linux-image" obviously be careful not to remove the one you want to keep and use the function "Mark for Complete Removal" Also Synaptic has the function under "Edit" to fix broken packages.

If this doesn't work I'd recommend a little homework in plugging your errors directly into Google.

---

### Post by carpman on 2010-08-10
> **rollin said:**
> If you want to remove old kernels try using synaptic, select "Installed" under "Status" and search for "linux-image" obviously be careful not to remove the one you want to keep and use the function "Mark for Complete Removal" Also Synaptic has the function under "Edit" to fix broken packages.

If this doesn't work I'd recommend a little homework in plugging your errors directly into Google.

seems you did not read my post at all :(

I cannnot boot system at all so have to access install via livecd and chroot so not gui?

and yes i have done the google search.

cheers

---

### Post by rollin on 2010-08-10
> **carpman said:**
> seems you did not read my post at all

I cannnot boot system at all so have to access install via livecd and chroot so not gui?

and yes i have done the google search.

cheers

The last line in your post you asked:

> **carpman said:**
> Trouble is can't remove old kernels as keep getting the message from dpkg about 'to many errors' any ideas?

I responded:

> **rollin said:**
> If you want to remove old kernels try using synaptic, select "Installed" under "Status" and search for "linux-image" obviously be careful not to remove the one you want to keep and use the function "Mark for Complete Removal" Also Synaptic has the function under "Edit" to fix broken packages.

Seriously in the back of my thoughts over an hour I tried to figure out what you are doing with your non booting system, trying to achieve, who gave you the advice to attempt to resolve it this way? 

Sorry my post did not help, it's voluntary friendly advice, I'm not an expert and it's not funded. Not really my problem you can't boot or access GUI functions in your current method though, you seem happy with your method so you figure out the GUI access. If not start at the beginning perhaps a post like " Upgrading from 8.04 to 10.04 system won't boot" might work better. All the best I hope someone else can help from experience. Best of luck.

---

### Post by carpman on 2010-08-11
Thanks for replies.

I have two problems, one is it not booting at all not even gue this is due to upgrade installing kernel 2.6.32-24 but grub does not find new kernel and so tries to load previous kernel which does not load.

I just had this same issue on another system and removing kernels via livecd and chroot worked fine.

Now this system is more complicated as i am getting the dpkg 'to many errors' message which prevents me un-installing kernels.

What this means is firstly i have to deal with the dpkg issue, i have searched the forums and google for a solution as explained in first post.


looks like i might have to do a reinstall.

cheers

---

### Post by rollin on 2010-08-11
Cool. I read your last post a little slower and a few more times LOL ;) So you're using 10.04 and then when you upgrade to the 2.6.32-24 kernel grub stops working and you can't boot...

Maybe some info on these posts might help [http://ubuntuforums.org/showthread.php?p=9650542#post9650542](http://ubuntuforums.org/showthread.php?p=9650542#post9650542) [http://ubuntuforums.org/showthread.php?p=9650701#post9650701](http://ubuntuforums.org/showthread.php?p=9650701#post9650701)

Keep chucking out information, like what hardware are you using? I'll do my best to help. Good luck :)

---

### Post by carpman on 2010-08-12
Thanks for reply, sorry both those deal with duel boot wubi, this ubuntu only install on old packard bell c3.

I know how to deal with the grub issue as had same issue on another pc, to fix it i need to uninstall all kernels and reinstall latest, this worked a treat on the other pc.

Now as i can't boot into system at all i need to boot with livecd and then chroot into the install. Once done i should be able to uninstall all kernels with apt-get remove ......  but this fails with the dpkg to many error message, as does most anything i do relating to apt-get.

As i posted in OP this seems to related to dependency issue a but i know of no way to force the resolution of dependencies?

Don't get hung up on the grub issue as i know how to fix this, i just put it in so as to explain why i could boot into system, the main problem is the dpkg to many errors message.

cheers

---

### Post by mörgæs on 2010-08-12
I guess that you are taking the long road. A clean install of 10.04 takes one hour, and then you are sure that it all works. 

Doing an upgrade from a more or less damaged system is risky.

---

### Post by rollin on 2010-08-12
> **mörgæs said:**
> I guess that you are taking the long road. A clean install of 10.04 takes one hour, and then you are sure that it all works. 

Doing an upgrade from a more or less damaged system is risky.

+1 

I do appreciate you want to deal with the dpkg errors but I have to agree with mörgæs in that starting with a fresh installation will give you a much better foundation.

If it is literally a plain installation, you don't add any new packages, then perform an apt-get upgrade and install the security and recommended updates (includes the upgrade to kernel 2.6.32-24) then your system has all these issues afterwards... I'd  recommend adding a bug on launchpad. You can then get expert help at working on the installation on your hardware as they will know the steps to work through to get all the answers from your system. [https://launchpad.net/](https://launchpad.net/)

I think would have to be my ultimate recommendation, file the bug at launchpad, I expect you'll need to recreate the environment leading up to the errors, as mörgæs recommended with a fresh installation. Good luck with it and I hope you find a good long term solution this way.

---

### Post by carpman on 2010-08-12
Thanks for replies, i now have it booting and am seeing if salvageable. 

A clean install can appear the quicker, but when you take into account all the little changes you make it can end taken a lot longer.

It was never a hardware issue, just something that went wrong during upgrade. The kernel issue i have already encountered on another machine and believe that is a known bug.

thanks for help.

---

