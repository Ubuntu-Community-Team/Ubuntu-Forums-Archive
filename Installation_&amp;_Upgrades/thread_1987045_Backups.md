---
title: "Backups"
date: 2012-05-25
forum: Installation &amp; Upgrades
---

### Post by LancerNZ on 2012-05-25
What tools are there to back up a system?

Please keep it simple.

I'm after a full system backup to the effect that if my install completely went down (e.g. graphics card clash with kernal etc) and I was unable to otherwise resolve the issues, I would be able to restore things to how they were. I know of dd... which would back up everything but it would be a massive biggish huge over the top thing in terms for the space of multiple versions and it would take... well forever really.

So what are the sensible options? Do I go for backing up selective directories? If I only back up the /home dir, then I'm out of luck if applications are relying on other locations for their configurations (would I even know?).

I've heard there are such a thing as patch back ups... where you make the initial backup and anything after that is smaller and faster because it basically backs up the changes. How does this work? Do I need to keep all 10 system backups with this method because each one chains to the next? Does each "image" only map to the first one making it "full" and a whole lot of "restore point from that one" versions?

I know there is a "backup" utility directly in Ubuntu. But how does it work? Is it rendered useless if the system goes down?

Please let me know what I should be doing, I've done format-and-reinstall a number of times in my Linux life (often after updates) and it's not fun.

P.S. I do not want to use online backup. I don't have the bandwidth for it.

---

### Post by darkod on 2012-05-25
I haven't used it but I have seen this mentioned as a good bare metal restore tool:
[http://redobackup.org/](http://redobackup.org/)

I guess that's what you are after.

It also depends whether you plan to make backups on the fly, with the system booted, because this redo solution seems to work from a live cd to make the backup which means you would have to shut down your OS.

But I didn't go into reading all the details.

---

### Post by drs305 on 2012-05-25
I'll start by mentioning an oft-forgotten gem called fsarchiver. It makes a single-file backup that can be restored to the same or any larger partition. 

Advantages are that it is very easy to use and the file can be restored to the same or any larger partition. Disadvantages are that it takes a while (15 minutes for me on a 6GB install), doesn't do incremental backkups, and must be run from another OS or a LiveCD.

It's great for backing up an OS just before upgrading to a new release, as you can go back to your old one at any time just by restoring the file.

Install fsarchiver (if running from a LiveCD, add the universe repository first), then:
```
fsarchiver savefs -z3 -v filename partition
fsarchiver savefs -z3 -v precise.backup.fsa /dev/sda5

To restore:
fsarchiver restfs -v /path/filename id=0,dest=/dev/sda5
```
Take a look at the MAN page for all the options (compression, etc)

---

### Post by darkod on 2012-05-25
I like fsarchiver too. If I may add, it can also restore to a smaller partition as long as the data fits. This can be useful in some situations.

---

### Post by LancerNZ on 2012-05-25
Those solutions look good. Thanks. :)

**redobackup** - I'm downloading this now. I take it the approach would be to use is as a "main snapshot" for "my system is fully working" restore state? I imagine it does not make incremental backups(?) so it might be good for "new install" and "upgraded and sure I'm happy install", with the regular backup from Ubuntu taking care of my day to day files on a more regular basis?

That way - I'd have full system restore (with a goal to be redone after major system updates) along with mini snapshots of essential files like /home etc. If the system completely fries, using the full restore then the mini would mean I'd pretty much have everything.

**fsarchiver**
This is kind of like dd except with compression and it doesn't mutilate destination partition size? So if I use the standard ISO file from Ubuntu as a rescue CD I could (while running) install the fsarchiver... would it let me? Or should I be making a custom Ubuntu with this preinstalled and export system as custom ISO?

---

### Post by drs305 on 2012-05-25
> **darkod said:**
> I like fsarchiver too. If I may add, it can also restore to a smaller partition as long as the data fits. This can be useful in some situations.

That's a good point, and an option I've used several times. I think that is how I stumbled upon it in the first place, as I used to use some other app that wouldn't let me do that. 

I should have mentioned it. I also wish every user doing an online upgrade would use it or something else before committing to an upgrade. Restoration is so easy!

---

### Post by darkod on 2012-05-26
Yes, you can add fsarchiver while running from the standard ubuntu cd. Of course, this will be a one time deal, you still has to do it next time, but it will do the job.

It is also included in the System Rescue CD, so if you download one of those for emergencies (has many tools), you can use it for fsarchiver.

Another option is creating an ubuntu live usb with persistence, then when you add fsarchiver it should stay added in the live usb because with persistence the changes can be saved (if there is enough space, depending on the change).

---

### Post by agillator on 2012-05-26
You might also look at rsnapshot for backups.  It has the advantage of small backup size and ease of reinstallation. It copies the individual files to a stated destination - another computer on a LAN, a different HD on the computer, or simply to another directory using rsync. The advantage of rsync is speed. It mirrors directories transferring only changes, so the first time it can take a bit for a huge source but only seconds for the next time. Rsnapshot then saves copies of the backups using hard links which means the only actual copies of files are those that have changed, in effect incremental though the difference between incremental and full is invisible to the user. I have an external USB drive I connect and forget. I keep a series of backups using only slightly more space than a single backup. I often find an individual file has become corrupted (operator error is a nasty thing, you know) and it is easy to replace/repair.

---

