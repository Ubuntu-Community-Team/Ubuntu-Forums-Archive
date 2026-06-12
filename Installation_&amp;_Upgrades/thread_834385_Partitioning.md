---
title: "Partitioning"
date: 2008-06-19
forum: Installation &amp; Upgrades
---

### Post by Codera123 on 2008-06-19
Alright, so I've finally decided to create a seperate home partition so each time I format, or add another linux operating system so I don't lose my documents. However, what would be the recommended partition scheme for this? What are the recommended partition sizes? And are there any partitions I don't necessarily need?

If somebody could help me out I'd appreciate it a lot.

Hard drive size: 160GB
Amount of RAM: 2GB

If somebody could also recommend the best filesystem type? I heard ResierFS to be the best.

---

### Post by pytheas22 on 2008-06-19
The only partitions you need to make are /, /home and swap.  Swap should be twice the size of RAM, so 4 gigabytes is good.  I use 20 gigabytes for / and it works fine.  If you're going to install an extraordinary amount of applications (which would fill up /usr/bin) or host big files in a web server (on /var/www), you might need more space.  But for normal desktop users, 20 gigabytes should be fine for /.  Actually you could probably do it with as few as 5 gigabytes if you wanted.  And then give what's left over to /home.  You can always readjust later if necessary.  Also for best performance it's good to put swap in the middle of the hard disk (i.e. between / and /home).

Personally I like reiserfs best.  It's gone through dozens of cold shutdowns and has always repaired itself without a problem.  ext3 is good, but I had major corruption with it once.  reiserfs is also supposed to be faster, especially for smaller files.  The only downside that I know of is that the reiserfs drivers for Windows are not as good, but if you don't have a dual-boot system, that shouldn't matter.

---

### Post by Codera123 on 2008-06-19
Ok, so I don't *really* need to create seperate /boot and /var partitions then? Will those automatically be created in /? 

Eww Windows :P, I don't plan on running windows anytime soon. The main reason for asking this is because I tend to format quite often, after various testing etc.. etc.. And I thought it'd be far easier to have a seperate home partition which can be used each and every time without having to connect to my network drives and get the data back from there.

20GB will be enough you say? I don't plan on installing a great deal of applications, however I will be hosting a web server, but surely even then 5GB is more than enough soley for a web server?


Edit: Should they all be primary or logical?

---

### Post by pytheas22 on 2008-06-19
No, there's definitely no need to keep /boot and /var on separate partitions.  If you are running a web server you might want to have /var on its own partition for the same reasons that you want /home on its own partition (i.e. to avoid having to rebuild it after every system reinstall), but you're not obligated.

5 gigabytes would be plenty for a web server if you're only going to be hosting mostly html/PHP pages.  If you have videos or a lot of high-resolution images, or large databases, maybe you would need more, but you could store thousands of html pages in 5 gigabytes.

I think all the partitions should be primary--mine are--but to be honest I don't really understand the difference, so you may want to research it more or ask someone who knows more than me.

---

### Post by Codera123 on 2008-06-19
Alright, final question.

I'm a pretty experienced linux user (have to be for work), however I've never manually partitioned a drive for linux before so sorry about the silly questions.

Just out of curiosity, if I were to create a seperate /opt partition etc.. would all of my applications be stored in there every time I formatted? (i.e. the applications installed, and the configuration of each, e.g. if I installed thunderbird and configured it to read my e-mail, would my settings be stored also?)

Again, thanks for the help.

---

### Post by pytheas22 on 2008-06-19
Most applications get installed in /usr/bin, so if you want to save them through reinstalls, you should put /usr/bin on its own partition.  Global configuration options for applications go in /etc, so you would need to do the same for that to save configurations.

However user-specific settings, like Thunderbird configurations for different email accounts or your desktop wallpaper, go in the /home directory of each user (look at the hidden folders inside your /home directory if you want to see them).  So they'll be preserved as long as /home is on its own partition.  /etc is just for system-wide settings that you probably will never change anyway, with the exception maybe of apt and X11, at least if you were me.

I think that Ubuntu doesn't really use /opt...some other distributions store applications there, but I think it's becoming deprecated and everything goes in /usr/bin now.  The only things that I've ever seen in /opt are [wicd]("http://wicd.sourceforget.net") which installs itself there for some obscure reason and Google's photo editor Picasa (which is not really a native Linux application anyway because it uses wine) which does the same thing.  So I wouldn't worry about backing it up.

And there's no such thing as silly questions--if I hadn't asked or read about partitioning before, I wouldn't understand it either.

---

### Post by Jacdeb6009 on 2008-06-20
Hi there,

This is all very useful information.  There is one question that I have for which I have not been able to find the answer, as follows.

I have /home on a separate partition.  I wish to re-install Feisty. I am quite happy with it and everything more or less works, however, being a n00b and prone to "playing" there are a couple of things that I have "changed" that I cannot change back and a clean install is probably a good idea anyway.

Question:

If I use the liveCD to re-install, and simply format the / partition and re-install Feisty there (same user, etc.), will the installation see the existing /home partition and leave it alone or will it create a new one as part of the / partition?  Worse still would it try to clear out the existing /home partition?

For safety of course everything will be backed up, but it would be nice to understand how to do this without having to restore the /home partition.

Some help would be appreciated!!

Thanks!

---

### Post by housam on 2008-06-20
Reinstalling FF will not touch your /home partition and will detect it. don't format anything for reinstalling, just choose the manual way during the installtion process and point the root ( / )partition (ex FF )to the installer.

---

### Post by meindian523 on 2008-06-20
The installer WILL see the existing /home.It will NOT create a separate /home if you tell it that the partition you have for /home is to be used as /home.If you do that,then be sure to uncheck the tickbox for Format,otherwise,your data would be lost.In short,tell the installer,I have a /home partition on there,you just use that,but don't format it.:)

---

### Post by pytheas22 on 2008-06-20
Yes, as others have said, /home will be automatically recognized and preserved; everything is going to happen the way you want.

The only I'll add is that you will probably not be able to log in to Gnome after the reinstallation before you'll get an error message along the lines of ".dmrc folder is not owned by user" (I forget the exact message but it mentions a .dmrc folder).  But this isn't a serious problem; just google the error message and the fix is obvious.  You just need to run a couple of chown commands.

Actually I think in Hardy this problem doesn't even occur, but in earlier versions of Ubuntu it's still an issue.

---

### Post by meindian523 on 2008-06-20
Actually,in a case of prevention is better than cure,when you install the new version,make sure that you use the same username and password you had on the old version,then there will be no problems.I speak from experience.;)

---

### Post by tubbygweilo on 2008-06-20
Before you install a new version of Ubuntu or indeed amend partitions in any way it is an idea to make a backup of data you would not wish to loose or data it would take an age to recreate. I have simple needs and make archives of .mozilla, .mozilla-thunderbird, .gnupg and Documents folders from my home directory to a cd or dvd. It takes me but a few moments but I know that if something unexpected happens I can reinstall Ubuntu and extract these archived files back into my home folder and carry on as if nothing untoward had happened.

---

