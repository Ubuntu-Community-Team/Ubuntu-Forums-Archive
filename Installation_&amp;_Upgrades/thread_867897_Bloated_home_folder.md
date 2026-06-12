---
title: "Bloated home folder"
date: 2008-07-23
forum: Installation &amp; Upgrades
---

### Post by realn on 2008-07-23
Hello all,
 
Installed HH. Went into my ~
What do I see? "Templates", "Pictures", "Videos" and some other folders.
WTF IS THIS ? I HATE THAT
Could someone please stop this horror? 

very :mad:

---

### Post by Pumalite on 2008-07-23
Post:
df -h
top

---

### Post by realn on 2008-07-23
Thank you for your kind answer, Pumalite. Could you please develop a little bit more on the idea?
 I don't remember if at install time I was asked to create and/or mount them, I don't care if they are created as symlinks or samba/sshfs/nfs shares. I simply just don't want those folders to be created in my $HOME. Because otherwise, I will start to get suspicious and look in some other places for things that are not supposed to be there. Please let me know if any user/admin with more than 2 years of contact with Linux considers that those folders "are supposed to be there". I think it's just a matter of habit - I can admit that. But I would like to say just this: Windows used to and still does drive me crazy everytime I used to open/save/edit some doc/pic/video and it went in "My\ Documents". Let's face it, everytime it does that i feel like  my balls are cut. I never bothered to see if I can replace this behaviour with want I want and I never will. I'm just hoping I won't get the same feeling in the future when using Ubuntu. 
 Am I the only one, please let me know ...

---

### Post by realn on 2008-11-19
Please, can someone confirm if this behavior "has been fixed" on the Ibex?

---

### Post by MikeSho on 2008-11-19
The bloated folder you are referring to are just hidden files. Just press Ctrl H and all will vanish and ctrl H again to see the hidden files.
:)

---

### Post by snova on 2008-11-19
I don't get it... there isn't even anything in them. They're just empty folders. Remove them...

And yes, they existed on my fresh install of Intrepid, though not for long.

---

### Post by cariboo on 2008-11-19
WHy would you call empty directories bloat, they take up very little room, and if you don't want them, just delete them. Ubuntu is produced for a large crossection of users, some of whom like the idea of precreated folders.

Jim

---

### Post by Wolki on 2008-11-20
Don't just delete them, they might be coming back if you do.

Various programs will use these folders as their default so that it's quicker for the user to select the correct directory. If you want the directories to have different names, edit the file "~/.config/user-dirs.dirs". If you absolutely do not want these directories, set them to "$HOME". I would advise that you do not do this for "Templates" however, as this folder has a special meaning (all files in it will be available in the "Create Document" menu in nautilus". Instead, create an empty hidden folder and set XDG_TEMPLATES_DIR to point there.

---

### Post by realn on 2010-07-20
I see that this didn't change with latest releases. I still consider this as bloated home folder and I still have to delete them by hand. Fallback to Kubuntu Hardy Heron waiting for a real LTS release and thread marked as solved.

---

