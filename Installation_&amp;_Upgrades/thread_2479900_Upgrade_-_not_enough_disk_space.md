---
title: "Upgrade - not enough disk space"
date: 2022-10-12
forum: Installation &amp; Upgrades
---

### Post by shad2022 on 2022-10-12
Hi,

as my search showed I am not the first one with problems regarding disk space while trying to upgrade.

I tried everything I found to get more space, including erasing old kernel files by hand in the terminal and I still need to get around 40MB free additional space to upgrade.

So I hope there are other suggestions.

Another idea would be to change the partition size but I tried that in Ubuntu itself while running and was not able to change anything. So I guess I would need to boot another Ubuntu or something like that to do this while the system is not active?

Standard setup was used, including encryption. 

Of course I can do a clean install but I think that can not be the method to have in mind when there is an option to do an upgrade.

Thank you in advance.

---

### Post by QIII on 2022-10-12
Without knowing what you found and what you tried, it would be difficult for us to help without the possibility of giving you redundant suggestions.

Please be specific about the size of your partition, what you found and what you have tried.

As a simple start point, please provide the output of 
```
df -h
```
which will provide some very basic file/directory information in a human-readable form.

You can't change the size of mounted partitions, so yes, you would have to be booted to another system -- the usual method is to use your installation media and start a live session.  But let's get to what you have tried thus far first.

---

### Post by Paddy Landau on 2022-10-12
It might help to also post the output of
```
sudo parted --list
```

---

### Post by yancek on 2022-10-12
In addition to the suggestions above, a good place to look is in /var/log for unnecessary files.  Log files generally take up a lot of space if not set up correctly.

---

### Post by Dennis N on 2022-10-12
> I tried everything I found to get more space, including erasing old kernel files by hand in the terminal and I still need to get around 40MB free additional space to upgrade. So I hope there are other suggestions.
Well, you don't need much more. I've had the same problem in the past trying to do an in-place upgrade in a tight situation.
1) Trim the journal. This can release several GB if you haven't done that recently.
Example to delete all but 20MB of journal:
```
[dmn@Sydney ~]$ sudo journalctl --vacuum-size=20M
Vacuuming done, freed 764.4M of archived journals from /var/log/journal/53ed2694eba742b2adc8bfa9b37d010c.

``` 
2) Temporarily uninstall a big application, like LibreOffice. You can reinstall after the upgrade.

---

### Post by shad2022 on 2022-10-12
Ok, did already deinstall Libreoffice before and deinstalled other things like VLC etc. just yet, around 500 MB in total, also removed logs and I'm still getting the message that around 38 MB are missing?!

I think I will just do a full install instead of wasting more time on this (already spent several hours before).

---

### Post by Paddy Landau on 2022-10-12
> **shad2022 said:**
> I think I will just do a full install instead of wasting more time on this (already spent several hours before).
That won't be necessary. Answer our previous questions. The shortage of space is likely on your boot partition, not your root.

Until you answer our questions, we can't help you!

---

### Post by shad2022 on 2022-10-12
> **Paddy Landau said:**
> That won't be necessary. Answer our previous questions. The shortage of space is likely on your boot partition, not your root.

Until you answer our questions, we can't help you!

Sorry, I never posted file system structure information somewhere and will not do it in the future. Because I know nothing about it in Linux. 

I also don't know about how Ubuntu does upgrades. In fact nothing changed, nevertheless I deleted lots of stuff. And I don't understand why Ubuntu / Linux does this partition things at all. In fact it only leads to errors like this situation shows.

And I don't know what Ubuntu takes boot or root for. So for me the question is why does Ubuntu not take enough space in the first place, when it has a 500GB SSD which has more than enough space, regardless if boot and/or root has 2GB more ore less and what helps beside a clean install and getting this things right manually?

And honestly I don't understand the function of each partition at all. For me partitions are dinosaurs used in Windows in those times you had problems to use big disks in one partition. 

And no, this answer is not meant respect less towards people trying to help me with this problem.

---

### Post by Paddy Landau on 2022-10-12
> **shad2022 said:**
> Sorry, I never posted file system structure information somewhere and will not do it in the future. Because I know nothing about it in Linux.
OK, it's really easy. As you know nothing about Linux, I'll give you simple step-by-step instructions.

[LIST=1]
[*]Open a terminal. The easiest way to do this is to press Ctrl+Alt+T.
[*]In the terminal, type the following three lines, pressing Enter at the end of each line. Note that one of them will ask for your password. Enter your password (nothing will be displayed while you do that, so don't worry) and press Enter.
```
df -h
sudo parted --list
apt list --installed 'linux-image*'
```
[*]Now, use your mouse to highlight the results; then right-click and copy.
[*]In your post here in this forum, paste what you copied.
[*]Highlight what you pasted in the post, and press the "Code" button at the top; the button looks like a big hash sign. (This places "CODE" markers around your code.)
[*]Press "Preview Post" to see if you managed to paste everything correctly.
[/LIST]
This will let us see where, and maybe why, you are having problems, so that we can help you to fix it.
> **shad2022 said:**
> I also don't know about how Ubuntu does upgrades.
By default, Ubuntu will automatically install updates regularly. You don't have to do anything manual. Unlike in Windows, this also includes all of your installed applications such as Firefox.
> **shad2022 said:**
> I don't understand why Ubuntu / Linux does this partition things at all.
Linux isn't the only system that does this. Mac, Windows, and all other operating systems also do it.

The first partition is the EFI System Partition (ESP), which is there for security. Microsoft demands that computers use this with Windows, so unless you manually turn it off in your computer's BIOS, you have no choice but to have it. It isn't a foolproof system by any means, but it's better to have it than not.

The second partition is the Boot partition. That's there, because it can't be encrypted, otherwise your computer won't know how to boot!

The third partition is where your so-called root is. This is the encrypted partition, and holds your entire system: programs, data, preferences, etc.
> **shad2022 said:**
> In fact it only leads to errors like this situation shows.
No. Something happened to cause this. I have three computers running Ubuntu 22.04, one running 20.04, and I've had a multitude of computers running Ubuntu and Lubuntu over the years. I have had this problem exactly once, due to something that I did (it wasn't Ubuntu's fault). Two of my current computers have only 70 Gb space, so you see that your 500 Gb is plenty! You are one of the very few to have this problem.
> **shad2022 said:**
> the question is why does Ubuntu not take enough space in the first place
That's what we're trying to find out, and why we need you to post your results. When we have this, we can advise you better.
> **shad2022 said:**
> partitions are dinosaurs used in Windows in those times you had problems to use big disks in one partition.
No, that's incorrect. It's not possible to use a disk without using partitions. Even if it's just a data disk (e.g. an external USB drive), then you have one partition on the disk. You can't have a usable disk without a partition! Even most USB sticks use a partition (at least, the ones that I use do). But partitions are here to stay for the foreseeable future. The ESP is, as already explained, mandatory, as is the boot partition if you want an encrypted system. The encrypted partition is the final required partition.

Plus, if you dual-boot, you need separate partitions for each operating system.
> **shad2022 said:**
> this answer is not meant respect less towards people trying to help me with this problem.
That's fine, no disrespect taken. I can see that you are very new to Linux, and simply need some understanding.

If you reinstall from scratch, that might solve your problem, unless you repeat whatever it was that caused your problem in the first place. If you prefer to solve your problem without reinstalling, paste your results as I explained above.

---

### Post by Impavidus on 2022-10-12
Those partitions are a technical requirement. You have an encrypted system. That means that the filesystem is encrypted. Not just the files; the entire filesystem, or one could still see the number of files and their names, sizes and permissions. But before you can use an encrypted filesystem, it must be decrypted. The software used to decrypt the filesystem cannot be encrypted itself, or it would have to decrypt itself before being loaded. So, on an encrypted system, you have an encrypted root partition and a plain /boot partition. You pay for the encryption with some additional complexity.

BTW, modern Windows system use quite a lot of partitions too.

If you want to fix this and learn about the internals of Ubuntu, you have to share some information. If you don't, that's fine too. There's nothing wrong with a fresh install. It should only take half an hour.

I assume you've got excellent backups of your documents, right? Especially important on encrypted systems, as there's no recovery when something gets damaged.

/boot partition should be about 500MB, but you can make it twice that size just to be sure. The minimum you need slowly increases over time. For a root partition, about 30GB should be more than enough, but you can make it larger too for the same reason. It's not as if every gigabyte counts on modern harddrives.

---

### Post by Paddy Landau on 2022-10-12
> **Impavidus said:**
> /boot partition should be about 500MB, but you can make it twice that size just to be sure.
The OP is apparently a beginner, and so wouldn't know how to go about this. But, for information, my main system is just like the OP's: A standard encrypted full-disk installation on a 500Gb SSD. The installer reserved 511 MiB for the ESP, and 1,646 MiB for /boot. Only 12% and 17% respectively have been used. Thus, the OP must have done something (presumably unintentionally) to cause it to run out of space.

---

### Post by shad2022 on 2022-10-13
In fact I'm not a beginner. I used my first Suse Linux installation about 20 Years ago, rooted Android phones etc. But I'm just not used to the folder and file structure of Linux. Maybe I'm too lazy to get into that topic but on the other hand it just annoys me.

The funny thing is, that while using Linux I'm always on that side of the small number of users that have problems like mentioned in this topic (Raspian tends to crash itself at some point regulary, Mint had a similar problem with disk space etc.). And I mean I don't do something crazy with the machine this topic is about, I just install the updates that show up and mostly browse the web.

That is why I like the Apple stuff. It just works 99% of the time and using it over 10 years now I never had such problems while updating something.

So on topic: I deleted some files on the boot partition by hand that turned out to be relevant and it ended up in a kernel panic. So I finally did a full install. Expect it to work until the next release. ;)

Thank you.

---

### Post by Paddy Landau on 2022-10-13
> **shad2022 said:**
> That is why I like the Apple stuff…
Apple has total control over their hardware and software, so yes, it does tend to be more reliable. If you prefer Apple, it might be worth your while sticking with it. What is your use-case for using Linux — for fun, for work, for some other reason?

If you purchase hardware with Linux preinstalled from a vendor that explicitly supports Linux (I like Dell's products, but other vendors also support Linux), you generally will find it just as reliable.
> **shad2022 said:**
> I deleted some files on the boot partition by hand…
Oops! That is absolutely not the way to go! Don't ever manually do something in /boot unless you are sure of what you're doing (generally, only if you're messing with Grub's themes).
> **shad2022 said:**
> I finally did a full install. Expect it to work until the next release. ;)
If you have further problems, try following instructions instead of rushing off and deleting stuff. That hardly ever ends well!

Good luck with your new installation.

---

