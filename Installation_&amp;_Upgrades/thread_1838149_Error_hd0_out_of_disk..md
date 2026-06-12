---
title: "Error: hd0 out of disk."
date: 2011-09-03
forum: Installation &amp; Upgrades
---

### Post by creata.physics on 2011-09-03
First off, I want to say that I know this topic has been posted about 100 times, but in the topics I've searched there is no actual fix for my issue.

I'm using 11.04, when I did an 'upgrade' the issue was gone, after I had done an update a restart was required, grub also had an update which was applied.

After the update, I got the error again.

When it gives me the error, the only option is to "Press any key to continue", which I do, and Ubuntu loads fine.

I guess the problem isn't severe because Ubuntu does load, it's just rather annoying, and I'd like to have a system that doesn't initially start with an error, I'd like it to just boot up normally.

Grub is installed, I have the option to load from which ever OS I want, windows xp pro also loads fine.  Is there any fix for this? Where I can make the first option load hd0 or whatever it needs to load so I can avoid this error?

Thanks in advance
/Matt

---

### Post by dino99 on 2011-09-03
- clean the system:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

- force a fsck on next reboot:

sudo shutdown -r now

reboot on recovery mode and select "repair packages"

---

### Post by creata.physics on 2011-09-03
I have done all that you've recommended and the issue still persists, any other ideas?

---

### Post by Hakunka-Matata on 2011-09-03
**EDIT:  Oh  yeah, hi, welcome to the forum**
Can read your RESULTS.txt file easily using gedit.  Would you mind editing the post and posting your RESULTS.txt file in a different way?

[LIST]
[*] Paste the entire text into the reply area,
[*]highlight the entire text..
[*]click on code tags, the # icon.
[*]preview and post it.
[/LIST]
Thanks,

Please download, run, **boot_info_script** and post resulting file RESULTS.txt between code tags.

---

### Post by Rubi1200 on 2011-09-03
+1 to the suggestion to post the results of the boot info script.

It will give us a much better idea of what is going on and will make offering solutions easier.

---

### Post by creata.physics on 2011-09-03
RESULTS.txt has been added as an attachment so you guys can check it out.

Thanks a bunch

/Matt

---

### Post by Hakunka-Matata on 2011-09-03
Please state what the *error *is exactly:  Grub boots and the first and only thing you see is "**Press any key to continue"**?

---

### Post by creata.physics on 2011-09-03
My apologies, posting the error itself as the thread title was not the best idea.

The exact error message I get is:

"Error: hd0 out of disk.
Press any key to continue"

---

### Post by Hakunka-Matata on 2011-09-03
your RESULTS.txt file looks OK to me, but I'm the first to admit I'm still an apprentice with boot_info_scripts output.  Found a link that you might find useful:
[http://www.anty.info/2011/06/22/solution-for-error-hd0-out-of-disk/](http://www.anty.info/2011/06/22/solution-for-error-hd0-out-of-disk/)

I'm still thinking but don't see anything obviously out of place yet.

---

### Post by creata.physics on 2011-09-03
Yeah, I thought it would have to do with the configuration since it tries to load hd0 which doesn't seem to exist? I'm not sure, I'm still a novice to Ubuntu and Linux in general, so I'm clueless on how to fix this.

I've reformatted and updated / re-installed everything so many times I would like to avoid erasing everything just to fix this, so thanks for your help.

---

### Post by Hakunka-Matata on 2011-09-03
what is your hardware?, have you stated that already in this thread.  Anyway, are you going to check and see if there is a BIOS update available for your BIOS?

---

### Post by creata.physics on 2011-09-03
I have 2GB of ram, pentium 4 HT 3.2 ghz, and i'm not sure about the graphics card.

I've done a bios upgrade a while back on windows, it's currently at it's most recent version, and I don't think there'll be anymore updates for that.

I'll wait a while more for some other responses, but I may just toss in the towel soon and do a full erase and re-install.

---

### Post by Hakunka-Matata on 2011-09-03
ok

---

### Post by oldfred on 2011-09-03
Are you shutting down abnormally?

This says the error should have been fixed many versions ago.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Out_Of_Disk](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Out_Of_Disk)

Relates to grub writing an error. Fix will not directly work as line numbers have changed a lot. And I do not know details.

Just a suggestion with no guarantees. You can try uninstalling grub & reinstalling it. You can do it from your install, but if you do not get it reinstalled, you will then need liveCD to fix it.

HOWTO: Purge and Reinstall Grub 2 from the Live CD 
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

