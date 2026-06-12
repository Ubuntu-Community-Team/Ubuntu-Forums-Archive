---
title: "Partitioning the home folders question"
date: 2007-06-01
forum: Installation &amp; Upgrades
---

### Post by Corfy on 2007-06-01
I recently got a new harddrive, and plan on backing up some files on my computer, wiping everything, and reinstalling everything on my computer from scratch (Windows and Ubuntu). 

(I'd like to get rid of Windows, but my wife won't let me yet, so I have to keep it for now. But that is another discussion.)

But I had a quick question. I don't see why it won't do this, but I don't want to try this only to find out that there was no possible way it would work.

The last time I installed Ubuntu, I did it across two partitions (not counting swap), one was for root, and the other was for /home.

I have a similar plan now, but I want to go a bit more specific.

I was thinking of setting up a partition for /home/corfy, but I wanted to make sure that when it came time to set up the user corfy (which is later in the install process on the Ubuntu LiveCD), that it would use that partition for the home folder. I don't see why it wouldn't, but I have been wrong before.

Actually, I want to set up three users with their own separate partitions. It may seem a bit overkill, I guess, but I think it would work better. Assuming it will work at all.

---

### Post by aysiu on 2007-06-01
The only difficulty I foresee is in matching up the user ID with the new user.

I don't know how difficult this is, since I typically set up only one user (who tends to be user ID 1000, I think).

---

### Post by Corfy on 2007-06-01
I may be wrong, but I don't think the user ID will come into play unless I want to move my user settings over from my old computer. But I won't be doing that, I will just move some files (documents, pictures, etc.). Otherwise, I am using this opportunity to wipe the slate clean.

Windows has been running on that computer for a long time, and I have gone through three different Linux distros (not counting updates, like from Edgy to Fiesty) with the same home partition. This seems like a good time to start over.

I just wanted to make sure that if I did set up a folder for a specific user before the user is created, then that folder is the one that will be used when I create the user. (Try saying that three times fast.)

---

### Post by Wim Sturkenboom on 2007-06-01
I think it will work (never tried it), but in what way will it work better?

Disadvantage of partitions is that it's often a waste of space Your home directory might be full while the other home directories are still empty.
And there will be no easy way to 'resize'; if course you can resize using a aprtition manager, but if it's worth the trouble? And the other users will not be amused if you detroy their data during the resize.

---

### Post by Corfy on 2007-06-01
I was just thinking that having our home folders in separate partitions might be a little safer than having them in the same partition, especially since I am very experimental and my wife is very conservative when it comes to computers. If worst came to worst and I had to wipe both the root directory and my home folder, I would prefer that my wife's home folder (and files) remain in tact.

But my wife and I are both used to partitions. It goes back to when we upgraded our harddrive from a 430 MB to 4.3 GB, only to learn that our motherboard couldn't handle larger than 2.1 GB. So we ended up partitioning it into three equal portions. And then later we added a 3.4 GB harddrive, which we had to partition in half. Ever since then, even though it isn't necessary, we have just always had a lot of partitions. And I figured this was a chance to wipe out all of the unneccessary partitions... or go crazy with them. I chose the latter.

---

### Post by dbbolton on 2007-06-01
EDIT: material that belongs elsewhere has been removed, so as to not distract other members.

---

### Post by Wim Sturkenboom on 2007-06-02
@corfy
If you're quite exoerimental, I would use a different approach. There is a chance that you blow the Ubuntu installation and both of you can not use it. So in that case I would do two Ubuntu installs; you can decide to share the home partition (I would do that) or have separate home partitions for each install.
I'm considering this approach at the moment for a similar reason: I'm very scared that an update will break the system or requires a re-install of video drivers. I do not always have the time to fix it and my wife will not be amused if she has to live more than one day without.

@dbbolton:
If you haven't installed any Ubuntu yet, just try it. I shared a home partition once between two distros and the distros kept interfering with each other with regards to GUI, so I would not do it. Solution is (in my opinion) to let each install have it's own home partition and have a partition wher you can share the data between the distros.

Further it's confusing when you hijack a thread. Problem is now that posters must indicate to who they reply and people who read the thread can not easily follow it. So next time, please start your own thread.

---

### Post by dbbolton on 2007-06-02
> **Wim Sturkenboom said:**
> 
Further it's confusing when you hijack a thread. Problem is now that posters must indicate to who they reply and people who read the thread can not easily follow it. So next time, please start your own thread.

hmm. i didn't realize you were a mod. but i think that's why there's a multiquote feature.

it was a related question, so i chose to post in here. Corfy, i'm sorry for "hijacking" your thread.

---

### Post by Wim Sturkenboom on 2007-06-02
I'm not a mod :) Hijacking irritates a lot of users on all kinds of forums and I just tried to add an explanantion why you should not do it. Even with quoting, it's still confusing.

Suppose you start your own thread. You follow it and see 'hey, new reply'. Look at it and find that somebody hijacked it. Next time again, but now it's a reply to the question of the 'hijacker'. Would you like it?

---

### Post by dbbolton on 2007-06-02
> **Wim Sturkenboom said:**
> I'm not a mod :) Hijacking irritates a lot of users on all kinds of forums and I just tried to add an explanantion why you should not do it. Even with quoting, it's still confusing.

Suppose you start your own thread. You follow it and see 'hey, new reply'. Look at it and find that somebody hijacked it. Next time again, but now it's a reply to the question of the 'hijacker'. Would you like it?
i was being sarcastic.

---

