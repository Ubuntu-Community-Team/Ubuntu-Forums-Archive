---
title: "Can I Roll Back/Re-Install 11.10 Without Losing Data?"
date: 2012-01-06
forum: Installation &amp; Upgrades
---

### Post by haon8 on 2012-01-06
Hey everyone,

Is it possible to either roll back from 11.10 to 10.04 without losing data, or if not, reinstall 11.10 without losing data?

My dad first started using Ubuntu at the 10.10 release, and seemed satisfied with it. He upgraded to 11.04, apparently without issue, however after 11.10 came out he began having a bunch of problems. These issues include (but are not limited to) icon pictures not displaying (or displaying as a default white page), volume and power-off controls not appearing on to top bar (which is constant), Banshee player associations not working with online radio and Banshee being associated with the Recycle Bin icon, amongst other things. I sorted out a few of these, but the bottom line is that it's inconvenient and annoying.

I was hoping we could just wait until 12.04, but these problems have just gotten out of hand. My original idea was to roll-back from 11.10 to 10.04, but from everything I read this is not possible without a total re-format. I'd now like to know if it's possible to reinstall 11.10 without losing data.

And before you tell me that it's a good idea to do a re-format every so often, don't. My father is a psychologist and has a ton of important files that he can't lose. While we can back them up, he also has e-mails, bookmarks, and other things which don't get carried over, not to mention some other files which inevitably get left behind.

If there is no way to do any of these things, is there at least an option to perform an installation repair or something? I find it both hard to believe and incredibly short-sighted for Ubuntu to release programs that cannot be easily fixed without losing data.

---

### Post by Buntumatic on 2012-01-06
Data what cannot be lost should be backed up. Amen.

Anyhow, if you create a new user, does this new user have all the same problems? I'm asking this because often upgraded programs do not work with old config files properly. Those conf files are stored in users home directory.

---

### Post by darkod on 2012-01-06
For this type of use I suggest you consider installing with a separate /home partition. That way you can do a clean install formatting the / partition if/when needed, but you still keep the /home partition with all the data inside his Home folder and program settings.

But the auto methods don't create this type of setup, you have to do a manual partitioning install.

As far as backing up your data is concerned. If his files are mainly documents, pdfs, etc, it's easy to copy them to an external HDD using ubuntu cd live mode.
For the favorites and emails it might be more complicated, or easy, depending which programs he uses.
If the browser is Firefox, simply copying the whole profile folder will do it. After the clean install, you copy it back and it works. Not only the favorites are there, even the browsing history, stored passwords, etc.
If the email program is Thunderbird, the same applies, just copy the whole profile folder. The setup, settings and emails are inside.

I have my TB profile on a network disk and can read the emails from TB from both windows and ubuntu, two different types of OS.

In any case, you should double check what's the best way to backup FF and TB before doing any clean install. Google has plenty of info and tutorials. For me and my experience copying the folder was enough.

You should also investigate about other programs he needs, if there are any.

Except for this, I have no other ideas. If you want help trying to solve the problems and keep the current 11.10, you will need to post more details about them. But it sounds like a new clean install is best for you. It all depends how easy/difficult your backup procedure will be.

---

### Post by haon8 on 2012-01-06
> **darkod said:**
> For this type of use I suggest you consider installing with a separate /home partition. That way you can do a clean install formatting the / partition if/when needed, but you still keep the /home partition with all the data inside his Home folder and program settings.

But the auto methods don't create this type of setup, you have to do a manual partitioning install.

As far as backing up your data is concerned. If his files are mainly documents, pdfs, etc, it's easy to copy them to an external HDD using ubuntu cd live mode.
For the favorites and emails it might be more complicated, or easy, depending which programs he uses.
If the browser is Firefox, simply copying the whole profile folder will do it. After the clean install, you copy it back and it works. Not only the favorites are there, even the browsing history, stored passwords, etc.
If the email program is Thunderbird, the same applies, just copy the whole profile folder. The setup, settings and emails are inside.

I have my TB profile on a network disk and can read the emails from TB from both windows and ubuntu, two different types of OS.

In any case, you should double check what's the best way to backup FF and TB before doing any clean install. Google has plenty of info and tutorials. For me and my experience copying the folder was enough.

You should also investigate about other programs he needs, if there are any.

Except for this, I have no other ideas. If you want help trying to solve the problems and keep the current 11.10, you will need to post more details about them. But it sounds like a new clean install is best for you. It all depends how easy/difficult your backup procedure will be.

Are ALL of the files saved in the Home folder? By that, I mean documents, music, emails, favorites, preferences, etc?

Is there any way to shrink the existing partition, and just create a new install in the free space (while having the new installation access the Home folder in the old partition)? Or can I just overwrite the old install with a new one and keep the files? I know that in terms of system files, a complete reinstall is best. However, if an overwrite works, that would be just fine.

What you said is great, but doesn't help me with the issue I have now of needing to reinstall without losing information. At the end of the day, if worse comes to worse, I can back up the information. But I'd like to try different ways before then.

---

### Post by Buntumatic on 2012-01-06
haon8,

an user has no rights to write anywhere besides his/her home directory. Thus there can be nothing that belongs to a particular user outside of home directory.

Edit: Did you ignore my hint about creating a new user?

---

### Post by darkod on 2012-01-06
No, you can't overwrite the installation but keep the data. At least I don't know of a way to guarantee you will not lose the data.
Also, making a second installation but letting it access the first Home will probably get you in trouble with permission, as already mentioned. I don't know how to do that to work.

In general, all data goes in the Home folder by default, unless you select otherwise. The docs go in Documents, downloads in Downloads, etc. Also software settings go into Home too usually in hidden folders starting with '.'

---

### Post by haon8 on 2012-01-06
> **Buntumatic said:**
> haon8,

an user has no rights to write anywhere besides his/her home directory. Thus there can be nothing that belongs to a particular user outside of home directory.

Edit: Did you ignore my hint about creating a new user?

Thanks.

Sorry. I didn't create a new user, but just logged in as Guest. I didn't check at length, but the volume control and system menu are present on the top bar (while they aren't in his normal account), so it seems like it's probably fine.

So, is there any way to shrink the existing installation and just create a new installation? If so, could I then copy over all of his files from the old installation to the new installation?

Is there anyway I could just try overwriting the installation while still keeping all of his files (and if that doesn't work, just do what I asked about above)?

EDIT: Ok, is there any way to shrink the old installation partition and create a new one (forgetting the idea of carrying over information for the moment)? At that point, I could just boot the original one and back up the data, and then just bring it over to the new one. While that wouldn't be much different from backing up the data and formatting the entire drive, this would ensure that the data is saved on the original installation in case something doesn't work.

---

### Post by darkod on 2012-01-06
I would recommend booting with the cd or usb stick in live mode (Try Ubuntu) first, and copy all the data you need to another disk (external, etc).
During the partition shrinking things could potentially go wrong, and if you have no copy of the data that's not something I would do right now.

To shrink it you would still need to use the cd and boot into live mode. Then open Gparted and shrink the root partition for at least 6-7GB to have enough to install a new ubuntu. Make sure you have enough unused space depending how much you try to shrink it.

But if you do make a copy of the data first, making a second install seems pointless. Just make a new install and put the data back. Up to you...

---

### Post by haon8 on 2012-01-06
> **darkod said:**
> I would recommend booting with the cd or usb stick in live mode (Try Ubuntu) first, and copy all the data you need to another disk (external, etc).
During the partition shrinking things could potentially go wrong, and if you have no copy of the data that's not something I would do right now.

To shrink it you would still need to use the cd and boot into live mode. Then open Gparted and shrink the root partition for at least 6-7GB to have enough to install a new ubuntu. Make sure you have enough unused space depending how much you try to shrink it.

But if you do make a copy of the data first, making a second install seems pointless. Just make a new install and put the data back. Up to you...

The entire reason that I don't want to delete the old installation prior to creating a new installation is because if the problems persist or if I forget to back up a certain piece of data, then it would be pretty pointless.

If I can create an entirely new installation and still have access to all of the files, then that would be great.

---

### Post by darkod on 2012-01-06
> **haon8 said:**
> The entire reason that I don't want to delete the old installation prior to creating a new installation is because if the problems persist or if I forget to back up a certain piece of data, then it would be pretty pointless.

If I can create an entirely new installation and still have access to all of the files, then that would be great.

OK, go for it. But still copy them somewhere else too before shrinking it, if possible.

---

### Post by Buntumatic on 2012-01-06
Correct me if I got it wrong, but you said guest has no problems? Then just delete your fathers obsoleted config and he'll be fine.

---

### Post by haon8 on 2012-01-06
> **Buntumatic said:**
> Correct me if I got it wrong, but you said guest has no problems? Then just delete your fathers obsoleted config and he'll be fine.

Yes, you're correct. However, I have no idea what you're referring to in terms of the "obsolete configuration."

---

### Post by Buntumatic on 2012-01-06
Well, you could create a new account for you father and copy all his files over. Or you could delete all his config files, don't worry new ones will be created as soon as he logs on.

---

### Post by haon8 on 2012-01-06
> **Buntumatic said:**
> Well, you could create a new account for you father and copy all his files over. Or you could delete all his config files, don't worry new ones will be created as soon as he logs on.

You'd have to tell me how to go about deleting the old configuration files.

---

### Post by haon8 on 2012-01-07
Can someone please tell me how to go about deleting the old configuration files?

---

### Post by darkod on 2012-01-07
Well, he probably meant that you can create a new user, just open User Account and create a new one. Log into that user and if all basic things work fine, you can plan copying over the data files. But I'm not sure how it would work for the favorits and emails, I guess the option to copy the profile folder would still work.

The main problem will be the permissions, only the old user will have permissions in his Home folder. You can try changing them, or giving a permission for everyone to work with those files, so you can copy them to the new user Home folder and work with them.

I'm not too experienced with permissions but to give a read/write access to all, it would be something like:

sudo chmod a+rw /home/old-username

That should set read/write permissions for all to the Home folder of the old user. After that you should be able to copy what you need. It's better not to copy the whole Home folder, just the stuff you need. That will avoid copying some broken configuration file.

---

### Post by haon8 on 2012-01-07
> **darkod said:**
> Well, he probably meant that you can create a new user, just open User Account and create a new one. Log into that user and if all basic things work fine, you can plan copying over the data files. But I'm not sure how it would work for the favorits and emails, I guess the option to copy the profile folder would still work.

The main problem will be the permissions, only the old user will have permissions in his Home folder. You can try changing them, or giving a permission for everyone to work with those files, so you can copy them to the new user Home folder and work with them.

I'm not too experienced with permissions but to give a read/write access to all, it would be something like:

sudo chmod a+rw /home/old-username

That should set read/write permissions for all to the Home folder of the old user. After that you should be able to copy what you need. It's better not to copy the whole Home folder, just the stuff you need. That will avoid copying some broken configuration file.

Thanks, but I was wondering how to go about deleting the old configuration files. If I can avoid needing to create a new account and copying everything over, that would be better.

---

### Post by darkod on 2012-01-07
> **haon8 said:**
> Thanks, but I was wondering how to go about deleting the old configuration files. If I can avoid needing to create a new account and copying everything over, that would be better.

We are starting to go in circles. If you delete important configuration files in user A, how do you plan to keep using user A since you are declining to create a new user B?

We gave you a suggestion what to do. I'm sorry, but this is not a wishing well, you can't say I don't want to do this but still achieve my goal. If user A is messed up there is very small possibility to make it work properly.

Either create user B and work with that, or copy data files to ext HDD and create a whole new installation.

I don't know of any other way. The choice is up to you.

---

### Post by haon8 on 2012-01-07
I was under the impression (based on what Buntumatic told me) is that if I deleted all of the configuration files, new ones would generate and probably fix the issues that I'm having (without the need to create a new account, format, or do any of that stuff).

If this is just not possible, then tell me. I didn't think he would give false information.

---

### Post by ottosykora on 2012-01-07
>The main problem will be the permissions, only the old user will have permissions in his Home folder. You can try changing them, or giving a permission for everyone to work with those files, so you can copy them to the new user Home folder and work with them.<

as I am for each new install transfering some of my essential data like thunderbirds mails and similar, I have kind of settled for following strategy:

Where ever I want get those files and configs from, I do it under the normal user, but copy all stuf to a fat32 formated usb stick.
(by that the permissions from the old computer were lost)

Then coming to the new install, using the user which the things are going to belong, I copy them to proper places in the home dir.
(the new user permissions are created, as this is the one who 'created' the files now)

So far this was may way in last few installs I did, some files like address book from thunderbird or the mail folder, I even copied from a portable windows thunderbird and all was fine.

---

### Post by darkod on 2012-01-07
> **haon8 said:**
> I was under the impression (based on what Buntumatic told me) is that if I deleted all of the configuration files, new ones would generate and probably fix the issues that I'm having (without the need to create a new account, format, or do any of that stuff).

If this is just not possible, then tell me. I didn't think he would give false information.

I saw that reply, but you will have to wait for him to reply I guess. If I'm not mistaken there is no single config file, and that makes things more complicated. You would have to go into many folders deleting files.

Personally it seems much easier creating a new user and just copying the files over. It would have already been done so far. But lets not start that all over again, I mentioned the option already earlier.

---

### Post by Buntumatic on 2012-01-07
Alright, sorry for late reply.
Anyhow, I cannot give precise advice how to go about that because I do not use Gnome myself. So you have to experiment a little.
If you do ```
ls -a
``` in home directory you'll see all hidden directories and files. I'd start renaming them, one at a time. The first suspect would be .gconf. Just do ```
mv .gconf .gconf.bak
``` and log off and back on. See if that helped. If not rename another directory and repeat logoff/on. Nothing will be lost really as you rename them to *.bak and you can rename them back any time you want to.

---

