---
title: "Clean install &amp; /home-folder"
date: 2007-04-02
forum: Installation &amp; Upgrades
---

### Post by Roelski on 2007-04-02
Hi,

I've been reading a lot on upgrading vs. clean installing on these fora.  Although I upgraded smoothly from Dapper to Edgy this weekend, I am planning to do a fresh install once Feisty comes out.

That's for no particular reason other that I want to be sure I know how to do a clean install...  (say, in case my laptop's hardware breaks down suddenly, my house burns down, ... - oh no, definitely not because Ubuntu would let me down :-) )

What came to my mind is the following.  I have /home on separate partition, so I can easily wipe out my root partition without losing personal data.  But: how do I make sure that after a fresh install, I and all my other users have their own /home back - including all rights, settings, etc???

It can't be that easy just to add a user with the same username to the new configuration, can it?

I could not find the answer in the fora yet, so any reply would be greatly appreciated.



Roelski

---

### Post by nyinge on 2007-04-03
> **Roelski said:**
> 
It can't be that easy just to add a user with the same username to the new configuration, can it?
Roelski

Yes, as a matter of fact, it's that easy.  Make sure you use the same username and password (I think password matters too, but I've never tested it with a different one, since I'm afraid that I might not be able to access my home drive anymore :D  ).  In addition, when you're installing a fresh copy, point your new home directory to the existing /home partition, and do not choose to format it.  Things should go on smooth from there, hopefully.

---

### Post by heimo on 2007-04-03
I think the user id, UID and group id, GID need to be same as before. Backup your whole /etc and restore users from /etc/passwd and /etc/shadow after reinstall. Groups are in /etc/group. Don't forget to backup any other data you might need, typically under /var (mail spools, databases etc).

---

### Post by zvacet on 2007-04-03
You will be safe with your home directory.In the partition step of installing **do not format home partition.**

---

### Post by Roelski on 2007-04-03
> **heimo said:**
> I think the user id, UID and group id, GID need to be same as before. Backup your whole /etc and restore users from /etc/passwd and /etc/shadow after reinstall. Groups are in /etc/group. Don't forget to backup any other data you might need, typically under /var (mail spools, databases etc).

You wouldn't have a full-blown dummy-proof howto available somewhere, would you?  Am kinda new to Linux-Ubuntu...

Thx for all your comments, anyway.



Roelski

---

### Post by Roelski on 2007-04-03
> **nyinge said:**
> Yes, as a matter of fact, it's that easy. 

That's what I call "System Administration"!  Thx.

Roelski

---

### Post by Black Dog on 2007-04-03
But would the new versions of the applications in the new release conflict with the old application settings in the old home folder? For example, f-spot is a major upgrade from Dapper to Feisty, as is gthumb and so on. Can anyone enlighten me as to the best practise approach?

I suggest that the upgrade / reinstall process with an existing home folder is ripe for detailed official Ubuntu documentation, if Ubuntu is to be accepted by the masses and near-novices like me. I will be moving from Dapper to Feisty, but only if I have some assurance!

Cheers,
David

---

### Post by heimo on 2007-04-03
Sorry roelski, I don't have a howto handy for this. But basically, you'd make a compressed package under your home directory (which you'll NOT format during install) and then restore whole files or just parts of them after install (do not restore whole /etc tree).

This is totally untested. To backup (just) /etc, I'd do:
```
cd && sudo tar czvf etc.tar.gz /etc/
```
Make sure that after that, you have a etc.tar.gz file in your home directory and that you can extract files from it. You can just double-click on it to do that. Repeat for other directories, if neccessary. There might be easier way through graphical user interface, but I'm not familiar with it. ;)

Also check my reply to Black Dog.

---

### Post by heimo on 2007-04-03
> **Black Dog said:**
> But would the new versions of the applications in the new release conflict with the old application settings in the old home folder? For example, f-spot is a major upgrade from Dapper to Feisty, as is gthumb and so on. Can anyone enlighten me as to the best practise approach?


This is excellent point one has to keep in mind. Applications' config files can change from version to version. My approach to this is that when doing major upgrades or reinstalls, I move all the files and directories which begin with a dot in my home directory to a sub directory. After reinstall or major upgrade, I selectively restore some of the config files to my home directory - if neccessary. One of the files is your firefox bookmarks, which can also be backuped through its "manage bookmarks" window. This way you'll get fresh default settings for most of the programs and you can restore any specific settings if neccessary and see if it causes any conflicts. Definitely a good idea to let programs create new, fresh, default settings if you don't have any laborious self-made settings.

---

### Post by Roelski on 2007-04-03
> **Black Dog said:**
> 
I suggest that the upgrade / reinstall process with an existing home folder is ripe for detailed official Ubuntu documentation

Seems like a plan to me.  Who should we inform about this?

@Heimo: thanks for your comments.

Roelski

---

### Post by Black Dog on 2007-04-03
To be more precise, the ideal would be a clear seperation between user created data (for example f-spot's & gthumb's databases containing tags and such, opera mail, etc) and application configuration files. I can live with new config files and re-apply my preferences over time, but identifying and copying these user data files is tricky, and certainly not easy for the average user.

I'm think that I'll move all my documents, photos etc into a unique partition, identify the user created data files concealed in the various 'dot' directories, ready for copy to the new /home, then treat the old /home as disposable upon upgrade / new install.

Thanks to all for your input, and who should we address a documentation request to? In an open-source spirit we should do it ourselves, but I certainly don't have the required knowledge.

David

---

### Post by heimo on 2007-04-03
> **Black Dog said:**
> 
Thanks to all for your input, and who should we address a documentation request to? In an open-source spirit we should do it ourselves, but I certainly don't have the required knowledge.
David

You can politely suggest it to the voluntary Ubuntu Documentation team:
[https://wiki.ubuntu.com/DocumentationTeam](https://wiki.ubuntu.com/DocumentationTeam)

---

### Post by Roelski on 2007-04-03
Good suggestion !  See the email below  I sent out 5mins ago.

QUOTE:
[I][INDENT]Dear Ubuntu User Documentation Team,

Amongst a few users we've been discussing possible /home-folder issues during an upgrade vs. clean install.  A number of suggestions were given, including the suggestion to bring it to the attention of you, the Doc-Team, in an polite attempt to have the item covered in a manual or howto.

You can review the entire post here: 
[http://ubuntuforums.org/showthread.php?t=399412](http://ubuntuforums.org/showthread.php?t=399412)

Thanks for your ideas, comments and feedback.

Should you need any additional information, please contact me by email.

Best regards & keep up the good work


Roelski,[/INDENT][/I]

UNQUOTE

Let's see what happens in the next hours/days/releases... 

Great community work, though.

Regs,


Roelski

---

### Post by Black Dog on 2007-04-03
Excellent! Thankyou, Roelski and Heimo.

---

### Post by Roelski on 2007-04-05
Here's what I received back.  I will hide all personal data: 

[INDENT][I]Hi Roelski, 

I'm afraid it's too late to add this to the system documentation for 
Feisty, as we passed string freeze a few weeks ago. I think that the 
best place to start would be to **create a new wiki page **at 
help.ubuntu.com and document the procedure there. 

There would have to be separate instructions for GNOME and KDE I think, 
and it's not as simple as it sounds. GNOME stores several 
secret/encrypted files in ~/.gnome2 and ~/.gnome2_private IIRC, which 
can't be read after a fresh install, but aren't recreated if they 
already exist. This causes the user the be unable to log-in graphically. 
At least, this is what happened to me the last time I tried it. 

Thanks, 

PB 
[/I][/INDENT]

Anybody who knows how to set up such a wiki?

Meanwhile, I've been working on an own developed Howto - not ready for publishing yet.  @ BlackDog & Heimo: can I "PM" a draft of the howto to the both of you for review?

Best,


Roelski

---

### Post by heimo on 2007-04-05
> **Roelski said:**
> Heimo: can I "PM" a draft of the howto to the both of you for review?

Excellent! I won't have much time to test it, but I can browse through it. I'm not sure about current politics about documenting Ubuntu (as I understand, there has been couple different groups / projects), but these should get you near:

[http://doc.gwos.org/index.php/Main_Page](http://doc.gwos.org/index.php/Main_Page)

Or:

[https://wiki.ubuntu.com/UserPreferences](https://wiki.ubuntu.com/UserPreferences)
[https://launchpad.net/+login](https://launchpad.net/+login)

---

### Post by bodhi.zazen on 2007-04-05
> **Black Dog said:**
> To be more precise, the ideal would be a clear seperation between user created data (for example f-spot's & gthumb's databases containing tags and such, opera mail, etc) and application configuration files. I can live with new config files and re-apply my preferences over time, but identifying and copying these user data files is tricky, and certainly not easy for the average user.

I'm think that I'll move all my documents, photos etc into a unique partition, identify the user created data files concealed in the various 'dot' directories, ready for copy to the new /home, then treat the old /home as disposable upon upgrade / new install.

Thanks to all for your input, and who should we address a documentation request to? In an open-source spirit we should do it ourselves, but I certainly don't have the required knowledge.

David

Saw your post re :wiki

This is to explain the comment you received regarding "it is not so easy" (I did not make that comment, I am only trying to help you).

The problem is /home is used for BOTH user data and (user) system/application configuration (.dot) files.

Conflicts in the configuration files can be problematic if you share /home across distro's or if you save /home with an upgrade.

You solution is best and very easy.

Let each distro (or install) of Linux make a /home directory of the root partition.

Make a data partition, separate from any root partition(s)

Mount the data partition anywhere you like, say /media/data.

Now make some links :

```
ln -s /media/data/music ~/music
ln -s /media/data/pictures ~/pictures
ln -s /media/data/documents ~/documents
```

If you have multiple users :

```
ln -s /media/data/user_name/music /home/user_name/music
```

and on...

This strategy will accomplish two things :

1. It keeps configuration (.dot) files from conflicting across distro's or installs.

2. You keep all your user data across distros or installs.

HTH

---

### Post by Roelski on 2007-04-06
Good suggestion & thx for the code, but IMHO:

- quite complicated for a novice.
- additional partition leads to less optimal allocation of HDD-space

Btw: e.g. my evolution-mails are in .evolution, and I want to keep those as well... That problem is not solved with this solution, is it?

Additional suggestion for backing up data (say on a weekly basis) is *grsync*.  Simply install the package using Synaptic.  The shortcut is located in Applications>Internet.


Roelski
(I apologize for being a noob, but everybody has to start somwhere)

---

### Post by bodhi.zazen on 2007-04-06
> **Roelski said:**
> Good suggestion & thx for the code, but IMHO:

- quite complicated for a novice.
- additional partition leads to less optimal allocation of HDD-space

LOL separate home partition is the same as a /data partition, both in HD storage size and performance.

If you are talking about saving data in the event of a re-install you are talking a separate partition.

If you are talking backup, well back up to CD or what not, off the HD is fine.

It is not as complicated as it seems.

> Btw: e.g. my evolution-mails are in .evolution, and I want to keep those as well... That problem is not solved with this solution, is it?

Well, nothing prevents you from moving a few select .dot files to the data partition. In this case, .evolution.

If you want you can link : Move the data: ```
mv ~/.evolution /media/data/user_name
```Link the data in your home directory: ```
ln -s /media/data/user_name/.evolution ~/.evolution
```

FYI : ~ is short hand for /home/user_name (works in a terminal)

> Additional suggestion for backing up data (say on a weekly basis) is *grsync*.  Simply install the package using Synaptic.  The shortcut is located in Applications>Internet.


Roelski
(I apologize for being a noob, but everybody has to start somwhere)

NP, please ask away.

As I stated, backup is similar, but slightly different then preserving you data on a separate partition in the event of a re-installation.

You have several options for backup. Just keep your data off the HD (in the event of HD failure). You can back up the whole partition or just your user data, up to you.

---

### Post by Roelski on 2007-04-06
> **bodhi.zazen said:**
> LOL separate home partition is the same as a /data partition, both in HD storage size and performance.

Okay, you're right - I didn't see that through! Summing it up, that would mean:

- Partition 1: root, including /home
- Partition 2: /data, linked to /home in root (where as I would have made this /home & a 3rd partition for /data - complicated!)
- Swap

Makes sense...  Might try this later this weekend.  Thanks for the suggestion.



Roelski

PS: I also found this post on partitioning by you: [http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018) - Very helpful!

---

### Post by bodhi.zazen on 2007-04-06
> **Roelski said:**
> PS: I also found this post on partitioning by you: [http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018) - Very helpful!

You are most welcome, thanks for the feedback ;).

If you run into problems, questions, feel free to ask.

---

### Post by NewJack on 2007-04-06
I don't mean to hijack this thread, but rather than start a new one (since I am on topic re: clean install)....

I currently have Dapper installed and want to upgrade to Edgy (or eventually Feisty)

I have my partitions set up like this

Windows
/
/home - shared
swap

Now, how do I complete a clean install?  After installing the LIVE CD and choose to install the new version, when the partition screen comes up what do I do next?  Does it give me the option to leave my Windows & /home partition and then do I choose to format the / and swap partitions?  Sorry if this seems like a complete n00b question, but unfortunately I am a n00b :) 

Thanks!!
Joe

---

### Post by arito on 2007-04-06
> I have my partitions set up like this

Windows
/
/home - shared
swap

Now, how do I complete a clean install? After installing the LIVE CD and choose to install the new version, when the partition screen comes up what do I do next? Does it give me the option to leave my Windows & /home partition and then do I choose to format the / and swap partitions?

At least when you install Feisty there's a check box next to each partition. If you check the box, the partition will be formated. The partitioner defaults to no formating at least for the Windows partition.

> Sorry if this seems like a complete n00b question, but unfortunately I am a n00b  

A relative n00b here too - you have my full sympathy :-)

---

### Post by bodhi.zazen on 2007-04-06
> **NewJack said:**
> I don't mean to hijack this thread, but rather than start a new one (since I am on topic re: clean install)....

I currently have Dapper installed and want to upgrade to Edgy (or eventually Feisty)

I have my partitions set up like this

Windows
/
/home - shared
swap

Now, how do I complete a clean install?  After installing the LIVE CD and choose to install the new version, when the partition screen comes up what do I do next?  Does it give me the option to leave my Windows & /home partition and then do I choose to format the / and swap partitions?  Sorry if this seems like a complete n00b question, but unfortunately I am a n00b :) 

Thanks!!
Joe

That is how you would do a clean install. Boot the desktop (live CD) and install. On the partitioning page mount the home partition as /home and the windows where you are like.

format only root partition, NOT the home or windows partitions.

To update : [https://help.ubuntu.com/community/FeistyUpgrades](https://help.ubuntu.com/community/FeistyUpgrades)

---

### Post by NewJack on 2007-04-06
First, thanks for the replies.

@ bodhi.zazen, what do I do with the swap partition?  Do I format that too?
Thanks!!!

---

### Post by heimo on 2007-04-07
It's good to realize that clean install isn't always necessary as Debian package management (which Ubuntu uses) works really well in major upgrades. Actually my first install to Ubuntu was straight from Debian, a different distro. So it's definitely not needed to reinstall just to upgrade. But yeah, sometimes you have to.

I think the swap partition will be detected by its partition type. You don't need to format it.

---

### Post by Roelski on 2007-04-07
I received some nice feedback from the Ubuntu Documentation Team.  A brandnew wiki was started  !   Quote:

[I][INDENT]Hi Roelski,

I've created a new wiki page with some basic information [1], and have
linked to it where it seemed appropriate to do so. Please review it and
see if it meets your needs. Also, feel free to modify it if you find any
errors or omissions.

Thanks,

PB

[1] - [https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion](https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion)
[/INDENT][/I]

Kudos to the Doc-team!  I *love* Ubuntu...

I will do a clean install once Feisty comes out and try to document it all !  Have some patience. \\:D/  

Happy Easter.



Roelski

---

### Post by heimo on 2007-04-07
Hi Roelski! Thank You Very Much for this contribution. :) Documentation is essential part of any software, and extremely helpful for people on these forums - both those seeking for help and those who're trying to help others. 

:KS:KS:KS:KS:KS

---

