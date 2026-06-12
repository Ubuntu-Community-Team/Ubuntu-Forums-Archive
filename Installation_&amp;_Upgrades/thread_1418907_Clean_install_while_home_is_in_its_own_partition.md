---
title: "Clean install while /home is in its own partition"
date: 2010-03-01
forum: Installation &amp; Upgrades
---

### Post by sideburn on 2010-03-01
Hello *buntu-ologist!

I guess it's time to move up to Ubuntu 9.10 from 9.04 ...unless you would advise me to stay with 9.04.  Either way,  I would like to do a clean install.  I managed to create a separate partition for /home almost a year ago ... now the only thing I want to keep inside /home is one big folder which I already had made a backup copy with several DVDs (larger than 4GB).  Besides that large folder,  I would like to start everything new.  This would be my second time installing and it has been quite awhile.  Here are my questions:

1. I know I have backup DVDs in hand.  But sometimes DVDs are funky.  I would restore my files with DVDs as last resort.  So, should I just delete all files and folders (including hidden ones) under /home except a large folder that I would like to keep?  If so,  can I do that while on a normal gnome session or am I better off doing it while on Live CD?

2. I see a suggestion that when installing Ubuntu,  I need to make sure to mount /home but NOT FORMAT IT.  Is there a visual tutorial or step-by-step guide showing how to do this?

3. Are there other gotchas like I need to "create" user name the exact same spelling as old user name that is already created under /home on my harddrive?

Thanks! :D

---

### Post by Silent Warrior on 2010-03-01
Holy cow, you're thorough! Have a :KS. Burning DVDs might have been overkill (at least, I haven't gone to that trouble yet), but it's definitely better to be safe than sorry. Just so you ABSOLUTELY know, when you create your separate /home-partition, you won't really have to worry about it during install besides setting the mount-point in the partitioner. As long as you don't format that partition by accident, the only "risk" is having a couple of configuration files overwritten.
But let's advance through your points.

1. If that's how you want to go about it, go ahead. 'Tis the Linux way, innit? :) One thing to look out for, though, is that you'll be removing any and all customizations - manually downloaded themes (themes installed with Synaptic will be upgraded if they're in the newer repositories, fear not) and icons, custom-tweakerized scripts and settings, browser-history, app-generated databases (Exaile and Amarok spring to mind)... I think the deletion can be done equally successfully in both LiveCD- and normal Gnome-environments, though it's noticeably less hassle booting without the LiveCD (then you'd have to manually mount the partition before accessing/deleting the files - which isn't to say it can't be done, it's just more difficult). The only catch about doing this from your default Gnome-install is that some basic configurations might or might not be auto-generated right back. I don't think that would cause a problem, but... just so you know. (But once the files are gone, consider logging out that very instant.)

2. There's bound to be several guides. But, as I mentioned at the top of my post, don't worry about your /home-partition (besides remembering which /dev/sdaX (or hdaX) it is) until you get to the partitioner. Set it to the mount-point /home, use the same filesystem as before so you aren't asked to format, and that's all the user-interaction you need to have your /home back after the installation.

3. Yes, exactly that - good spotting. Of course, even if you use a different user-name, you can most likely access the stuff as root and copy/move it over to your new user-directories. Messy, but the data would still be there. Besides that, I only know of left-over configuration-files causing unexpected behaviour. I mentioned the loss of user-downloaded themes and stuff - it seems you mean to delete the configuration-files where your desktop-settings are kept, so you'll have to set your desktop up again, but I guess that's exactly what you want.

Good luck.

---

### Post by sideburn on 2010-03-02
Thanks Silent Warrior!!!!! :D

Yeah,  I'm willing to lose all config settings and start over except to keep my data files such as documents.

I had another thought for deletion methods...boot up as CLI instead of gnome.  Orrrr login as a second user (I need to create one).  I think CLI is quicker...but not sure if either would work?

---

### Post by sideburn on 2010-03-05
Yahoo!

Does anyone knows if booting up CLI instead of gnome or logging in as another user is a better choice when deleting all unwanted files under home directory?

Happy weekend!

---

