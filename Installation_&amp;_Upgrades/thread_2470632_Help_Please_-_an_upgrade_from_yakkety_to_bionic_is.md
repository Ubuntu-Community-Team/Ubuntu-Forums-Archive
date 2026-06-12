---
title: "Help Please - an upgrade from yakkety to bionic is not supported by this tool"
date: 2022-01-06
forum: Installation &amp; Upgrades
---

### Post by benbart on 2022-01-06
Hi,

Can someone please help me with some instructions on how to do this upgrade?

Initially I get the message "Software Updates are no longer provided for 16.10. To stay secure, you should upgrade to Ubuntu 18.04.6 LTS"
Then when I choose to upgrade it say "an upgrade from 'yakkety' to 'bionic' is not supported with this tool"

I have checked on [https://help.ubuntu.com/community/BionicUpgrades](https://help.ubuntu.com/community/BionicUpgrades)
And there is only "Upgrade from 16.04 or 17.10 to 18.04"

From Google, I found [https://www.linuxbabe.com/ubuntu/upgrade-ubuntu-16-10-17-04-to-ubuntu-18-04](https://www.linuxbabe.com/ubuntu/upgrade-ubuntu-16-10-17-04-to-ubuntu-18-04)
I just want to know if maybe there is an official Ubuntu doc/instruction before I try the URL above. I hope I don't break anything as we have files all over the place too :(

Any advise will be much appreciated. A wee bit desperate.
The Ubuntu was installed from a USB and dual boot with Micro$oft Windows 10. I sincerely don't want to go back to using Windows 10.
The Ubuntu upgrade is also causing me not to be able to use some of the Google Apps as Firefox requires an upgrade to a newer version.
Thanks in advance.

---

### Post by Impavidus on 2022-01-06
The last upgrade for 16.10 was provided in July 2017, so that's over 4 years ago. The only direct upgrade from 16.10 that was ever supported was to 17.04, as 16.10 reached end of life before the release of any successor of 17.04. 17.04 is dead too, as is 17.10. There is a way to force an upgrade by simply changing the software sources, but as the changes between 16.10 and supported versions are large, the probability of success is small.

Make backups of all your important files and perform a clean install of 20.04. Upgrading this system is too much work with a very low chance of success.

Furthermore, it appears you've been using your 16.10 system, with all its known flaws, for long enough on the web to notice that your outdated Firefox no longer works with new websites. I wouldn't trust that computer any more.

---

### Post by tea for one on 2022-01-06
Very good advice from [COLOR="#0000FF"]Impavidus[/COLOR].

Especially the observations about backups and using 20.04 ([COLOR="#0000FF"]L[/COLOR]ong [COLOR="#0000FF"]T[/COLOR]erm [COLOR="#0000FF"]S[/COLOR]upport)

Also, if you are going to start from scratch, please use GPT and UEFI mode.

---

### Post by guiverc on 2022-01-06
This post is mostly links.

The *official* doc you're looking for is [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Ubuntu 16.10 reached EOL long ago as already discussed - [https://ubuntu-news.org/2017/07/20/ubuntu-16-10-yakkety-yak-end-of-life-reached-on-july-20-2017/](https://ubuntu-news.org/2017/07/20/ubuntu-16-10-yakkety-yak-end-of-life-reached-on-july-20-2017/)

It's inttended upgrade path was to 17.04 or the next release; so upgrades became much harder when 17.04 reached EOL ([Jan 13, 2018]("https://fridge.ubuntu.com/2018/01/17/ubuntu-17-04-zesty-zapus-reached-end-of-life-on-january-13-2018/")) though tools would still allow upgrade (*note: this is allow; not that it's recommend as it's not a QA or Quality Assurance tested path**, though CI testing of package connections takes place thus it's possible assuming no 3rd party packages are included*) to the next *supported* release which was 17.10, then 18.04 which is why you saw mention of it in 3rd party blogs. 

You didn't say if the machine was desktop or server, nor if internet connected (*ie. risk is significantly higher*), but for a desktop install I may consider an *upgrade via re-install* on it, but if a server that's not as good an option.  We can't know how much the box was on in its unsecured state, but the *upgrade via re-install* is just an install without format, allowing you to skip releases which causes
- *manually installed *packages to be noted
- system directories wiped (*as servers programs keep conf files in these directories this isn't as good with server installs*)
- new system is installed
- additional packages (*manually installed noted earlier*) are installed (*if available on new release*)
- no user file is touched (*unless format is selected*)
- user is asked to reboot

I'd suggest auditing the machine for problem packages etc. (it's a 2016-October release which was long ago & much has changed in the software world; that's Qt4 times, default DE was Unity 7, python2 etc., ie. many things that are no longer *supported* or *changed*) and removing any 3rd party packages prior to this install.

 Problems with it can be expected if audit was fast (*problem really is just a message that some packages cannot be re-installed - ie. not a big problem*), but I'd still expect an good result.  Again this may not be the safest decision given you were using EOL software for so long, but it's your choice (*esp. if box is off-line etc*)

Best advice was provided by others - BACKUP FIRST.

---

### Post by MAFoElffen on 2022-01-06
Good advice so far... To make things a bit easier, let me share what I do...

Personally, I migrate to new installations... Backup the data and configuration files. Start a migration plan. Get a list of any programs that I want to include as manually installed into the migration plan. Research if that installation plan makes sense... Modify the plan. Implement the plan. Test the results.

Since I "migrate"... I don't carry on any old problems that may be there, such as overlapping partition declares, filesystem problems, old boot problems, old technology dead ends, upgrade package plans that didn't make sense, etc, etc, etc. Also in that list is packages that were remove along the way that left pieces, such as dependencies that are no-longer required or needed. You don't know how often that results over years of service and upgrades. Since I migrate, I still have a copy of what was there, as default, for the fresh install, of what was the default package list...

Everyone tells people "to get a list of what is installed..." That is too much information, convoluted and very confusing. What you really need is: What was installed manually by you, beyond what was the base initial installation.
```

comm -23 <(apt-mark showmanual | sort -u) <(gzip -dc /var/log/installer/initial-status.gz | sed -n 's/^Package: //p' | sort -u) >> ~/manually_installed.txt

```
And then I use that to look at those packages and see what is currently available... Also use that list to make a plan  to retrieve the config files for those packages, to update for the new system...

EDIT:
You will be surprised, that once you see "that list", of how much less daunting and simpler things will seem, in how to get from Point A to Point B...

NOTE:
I also use that to look at current systems, to audit what was installed during the system's life-cycle, to see what is really used versus unused... to  remove things that were installed as a 'test' or 'trial' of something, to make decisions to remove unneeded packages that are no longer needed in the current system.

---

### Post by watchpocket on 2022-01-06
> **MAFoElffen said:**
> 

Everyone tells people "to get a list of what is installed..." That is too much information, convoluted and very confusing. What you really need is: What was installed manually by you, beyond what was the base initial installation.
```

comm -23 <(apt-mark showmanual | sort -u) <(gzip -dc /var/log/installer/initial-status.gz | sed -n 's/^Package: //p' | sort -u) >> ~/manually_installed.txt

```
And then I use that to look at those packages and see what is currently available... Also use that list to make a plan  to retrieve the config files for those packages, to update for the new system...

(I'm not the OP but) This is one of the most helpful things I've seen!  Thank you!

---

### Post by benbart on 2022-02-06
Thanks for all your replies and advices.
I'll work on doing an upgrade and create a new partition to do a new install of sort as a last resort :(
Most difficult part is working out where users have save their files :(

---

### Post by MAFoElffen on 2022-02-07
> **benbart said:**
> Thanks for all your replies and advices.
I'll work on doing an upgrade and create a new partition to do a new install of sort as a last resort :(
Most difficult part is working out where users have save their files :(
Migration should be your first choice... And it is not as daunting as you think.

Next, finding files owned by a user is also easy... 

Get list of Users:
```

compgen -u

```
Get a list of groups:
```

compgen -g

```
Then weed through those to find what "you created" as users and user groups... to find the files owned by users by using this format:
```

find {directory-start-location} -user {username} -group {groupname} -name {file-name}

```
For example:
```

sudo find / -user benbart
sudo find / -group humanresources

```
This works better if the user you are using in the query is not the loggged in user, as it will also list /proc processes as files... just saying... you will have to weed through it. You can do that by piping egrep exclusions...

---

### Post by Impavidus on 2022-02-07
> **benbart said:**
> Thanks for all your replies and advices.
I'll work on doing an upgrade and create a new partition to do a new install of sort as a last resort :(
I know that many less experienced users think a fresh install is hard. Maybe it is for those who lack experience, but upgrading such an old release and getting it to work again is harder.
> Most difficult part is working out where users have save their files :(
If the users have been behaving themselves, all their files should be in /home. They don't have permission to store their files anywhere else, unless you gave them that permission. You could simply copy all of /home (maybe skip cache directories), but just to be sure in the case of malware (you've been running an unsupported system connected to the web for a long time), it may be better to only backup the files of which you're sure that they are important (and are what they seem to be). I may be overly cautious here.

---

