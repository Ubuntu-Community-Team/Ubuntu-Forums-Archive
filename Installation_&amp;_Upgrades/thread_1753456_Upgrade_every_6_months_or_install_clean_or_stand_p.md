---
title: "Upgrade every 6 months or install clean or stand pat?"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by brad1138 on 2011-05-09
Sometimes I upgrade, sometimes I do a full clean install. But the more I customize and install programs, the more of a pain it is to do a full wipe and full clean install. 

I have read that it is better to do a clean install. For those that upgrade, how many upgrades have you done without reinstalling? In the past, upgrading commonly caused problems, I think it is getting better now though. 

Of course I could just stick with LTS releases, but not having the newest features bugs me for some reason.

I am not sure if I actually have a question or not in there. I guess I am just curious if anyone else goes through this dilemma every 6 months?

Thanks,
Brad

---

### Post by akand074 on 2011-05-09
I used to upgrade. I upgraded from 8.10 to 9.04 to 9.10. I always do a clean install now. With the new PPA system it actually takes less time to do a full clean install and reinstall everything the way I want it than an upgrade. I have a separate /home partition too so most of my configurations remain usually untouched so when I reinstall the applications they are right back where I left them. Just a matter of a few sudo add-apt-repository and sudo apt-get install and done.

---

### Post by MSwal2846 on 2011-05-09
I do a reinstall also.  Why?

[LIST=1]
[*]Did an upgrade (yes, it was years ago, now) and had problems so was forever scared
[*]cleans everything out
[*]allows one to take advantage of new options that an upgrade won't permit (e.g., this time I encrypted by home directory)
[*]really is relatively fast
[/LIST]

Hope that helps....

---

### Post by Hey338Too on 2011-05-09
I hope it is OK if I ask a follow up to this question.  If you have your /home directory on a separate partition and use the same user name and password during the reinstall, do you need to reset the permissions in the /home partition so that everything works properly?  Thanks in advance and I hope that I have not hijacked this thread.  Michael

---

### Post by manzdagratiano on 2011-05-09
For Lucid -> Maverick -> Natty, upgrades have worked flawlessly for me. I manually clean out my /home for obsolete directories/files. I did clean installs for Karmic and Lucid, and getting all back up to the way ot was is just a headache.

The rule of thumb I follow is this: if an upgrade is going to make major system changes (Karmic -> Lucid brought grub2, ext4 as default etc etc), it is safer to do a clean install. If the changes are not major on the underlying base system, an upgrade should be fine. With Lucid -> Maverick, there were no such critical changes. With Maverick -> Natty, the major change was the miracle 2.6.38 kernel and Unity, but nothing too critical about underlying system design. Therefore, using your intuition would tell you what would be the best way.

I do not keep a separate home partition; rather, I keep a separate data partition, since I do not like to have my data files be mixed up with application configuration files. I just manually back up required files from /home in the event of a reinstall.

In the event of a reinstall, since my data partition was ext4, I indeed had to reset permissions (chown -R <user>:<group> <target>). /home may have a different story since if you point the installer to that partition, the installer may end up recreating permissions for you - some of the old files may need to be 'chowned' again, but in either case, it is a trivial task.

---

### Post by mörgæs on 2011-05-09
My advise is doing a clean install once a year, skipping every other release of Ubuntu. It takes an hour or less.

I always keep a true back up on an external hard drive, so there is no need for a separate /home.

---

### Post by akand074 on 2011-05-09
> **Hey338Too said:**
> I hope it is OK if I ask a follow up to this question.  If you have your /home directory on a separate partition and use the same user name and password during the reinstall, do you need to reset the permissions in the /home partition so that everything works properly?  Thanks in advance and I hope that I have not hijacked this thread.  Michael

No you don't have to do anything. Should work exactly as you left it before you reinstalled (generally).

---

### Post by akand074 on 2011-05-09
> **manzdagratiano said:**
> I do not keep a separate home partition; rather, I keep a separate data partition, since I do not like to have my data files be mixed up with application configuration files. I just manually back up required files from /home in the event of a reinstall.

I'm considering this for the sake of cleanliness.

---

### Post by RikardSvenningsen on 2011-05-09
I have made an upgrade sins 5.04 every half year, only to times it went wrong and I was left with a crashed computer. It's annoying when it doesn't work but anyway I don't know any operating system so easy to upgrade.
I have now a 11.04 and that upgrade didn't work, so now I am running on a clean install.

---

### Post by Hey338Too on 2011-05-09
Thank you for the fast responses.  Michael

---

