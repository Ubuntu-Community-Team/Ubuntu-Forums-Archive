---
title: "Migrate, Copying all files, programs and settings, from 32 to 64-bit?"
date: 2009-12-18
forum: Installation &amp; Upgrades
---

### Post by Dr.Dixie on 2009-12-18
Hullo, there. I've been wondering for a while whether this sort of thing was possible, because I change computers/hardware a lot.

Basically, I want to know if there's a way to take all files that are different from a default install (or something like that), all programs that aren't installed by default, and all settings, even down to the panel settings and those in gconf-editor...and take them over to another system, possibly radically different. Right now, I'm trying to get rid of my former Ubuntu 32-bit installation so I can install Windows and see what this integrated GPU can do (fairly low-power stuff...BF2, FC, BFH, LSW1/2).

So, basically, I'd like to be able to make my desktop on 64-bit everything my 32 bit one was, while still taking advantage of 64-bit software, and whatever else can take advantage of it.

Obviously, I can't merely do a clone of my entire hard drive, and take advantage of the new power of my machine. I hope this explains everything...


!Dr.Dixie!

---

### Post by gadolinio on 2009-12-18
Your settings, documents, applications menu, panel, background, etc can be easily transfered by copying your user folder complete (including folders starting with ".") from the current to the new system.
Backup the entire folder, then install your new 64-bit ubuntu, log out and start a session with the root user, delete everything inside the recently created user, and paste the content of your backup there. For launchers and everything to work fine, the new user should be called the same as the old one.
Next time you log in with the new installation's home user, it should be a clone of the previous one.

Now, regarding non-default-software... I'm afraid all the packages you have downloaded for the 32-bit system can't be used in a 64-bit one. Only those which are architecture-independent are worth backing up and reinstalling in the new system. For the rest, i thing you'll have to download all again in their respective 64-bit versions.

Hope you find this useful...

---

### Post by Dr.Dixie on 2009-12-18
That, I'm afraid, I could have thought of/done myself.

I really need something that can do everything. I know I can't just copy the 32-bit programs from my former installation and use them in this one. I know I'll have to re-download and reinstall everything if I want a complete clone (differences in bits notwithstanding).

It'd be helpful if I could have detailed instructions on how to get the list of installed software on one installation, and then compare it with what I've already got on the other installation...*and then*, hopefully, to input that into apt-get or something to install all those packages one night.

I also want to be able to migrate all my themes, including emerald, GTK, icons...whatever. I just need to be able to make my new desktop like my old one in as many ways as possible...without, hopefully, more trouble than it's worth.

Thanks for trying to help!


!Dr.Dixie!

---

### Post by gadolinio on 2009-12-19
> **Dr.Dixie said:**
> That, I'm afraid, I could have thought of/done myself.

I really need something that can do everything. I know I can't just copy the 32-bit programs from my former installation and use them in this one. I know I'll have to re-download and reinstall everything if I want a complete clone (differences in bits notwithstanding).

It'd be helpful if I could have detailed instructions on how to get the list of installed software on one installation, and then compare it with what I've already got on the other installation...*and then*, hopefully, to input that into apt-get or something to install all those packages one night.

I also want to be able to migrate all my themes, including emerald, GTK, icons...whatever. I just need to be able to make my new desktop like my old one in as many ways as possible...without, hopefully, more trouble than it's worth.

Thanks for trying to help!


!Dr.Dixie!

Then, I'm afraid, you could have been more specific in your question ;)
You see, many people with no ability at all make questions here, and that's perfectly OK. There might be someone who doesn't know how to turn the computer on... and there also might be someone who doesn't know how to ask whay he wants and can't add what he already knows and be more specific about the question, in a polite way ;)
You might have also thought of a way of saving your <package selections list> and making the new system use it... 
Which part of being "able to migrate all my themes, including emerald, GTK, icons...whatever" is it that you can't think of? I mean, you know you can also copy those files... So what's missing then?

---

