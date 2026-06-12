---
title: "sudo apt-get install does not upgrade/install some packages"
date: 2015-09-29
forum: Installation &amp; Upgrades
---

### Post by oldefoxx on 2015-09-29
I've run into this situation a lot, and awhile back someone suggested a likely cause for it, but I can't find the link.

Anyway, here we go again:  I do the following commands in a terminal:
```

sudo apt-get -qq update; sudo apt-get -qq -y upgrade; sudo apt-get -qq -y autoremove; sudo /usr/bin/update-manager

```
Now this works very well.  Gets more updates than apt-get alone gets.  But apt-get will begin telling about some updates it isn't getting, but only the count, never what it is passing over or why.

Someone explained to me what was probably happening, but that's all I can remember.  I had a lot going on at the time, so it washed out of my mind.  Now I would like to find out for sure, and what can be done about it.

---

### Post by vasa1 on 2015-09-29
*dist-upgrade* instead of *upgrade* from help.ubuntu.com/community/AptGet/Howto

---

### Post by oldos2er on 2015-09-29
```
sudo apt-get update; sudo apt-get dist-upgrade
``` will upgrade more than ```
sudo apt-get update; sudo apt-get upgrade
``` alone. This is explained in the man pages: ```
dist-upgrade
           dist-upgrade in addition to performing the function of upgrade, also intelligently handles changing
           dependencies with new versions of packages; apt-get has a "smart" conflict resolution system, and it will
           attempt to upgrade the most important packages at the expense of less important ones if necessary. The
           dist-upgrade command may therefore remove some packages. The /etc/apt/sources.list file contains a list of
           locations from which to retrieve desired package files. See also apt_preferences(5) for a mechanism for
           overriding the general settings for individual packages.
``` I'm assuming this is what you're referring to when you say > But apt-get will begin telling about some updates it isn't getting, but only the count, never what it is passing over or why.

---

### Post by oldefoxx on 2015-10-02
Hey, I only resort to the man pages when I don't have example code to follow.  I've never seen sudo apt-get dist-update used before, so this is all news to me.  Thank you both for bringing it to my attention.  It is most appreciated.

Here is the script file I am currently using.  I just begin a new empty document named "Update" on the desktop, open it with the rext editor, paste this into it, then save it.  Then I right click on it with the mouse, click on Properties, select the center tab named Permissions, and put a check in the box between "Execute:" and "Allowing executing file as a program".  Then I click Close.  Now it's ready to be used.

Most readers know all this stuff already, but there is a percentage of people still learning, and I like to cover my bases.  And Yes, it is recommended that the extension of ".sh" be added. but that causes the label to be too long and lap the label next to it. so I shortened it a trifle.

Hereis the code:```
#!/bin/sh
#
echo "\n\n\n"
echo "                             SOFTWARE UPDATE SCRIPT"
echo "                               Please be patient."
echo "                          This will take a few minutes."
echo "                        To watch all the action. you can"
echo "                     Edit the script and remove the '-qq's.\n"
echo "                    Updates require root [sudo] priveleges, so" 
echo "                    enter your personal password to gain them."
echo "               (You won't be asked if already root or super user).\n"
printf "               "
sudo apt-get -qq update
sudo apt-get -qq -y dist-upgrade
sudo apt-get -qq -y autoremove
sudo /usr/bin/update-manager
sudo updatedb
```

Now it's not mentioned much, but the bash command of locate is really better at finding file names than the find command is.  And faster too, because it just looks in databases.  But the databases are not always current, and the last line ensures that the databases are brought up to date so that locate does a better job.

Locate acts like an InStr() command in Basic, in that you can string together any continuous group of characters that could make up part of a path/filename.ext combo, and it acts as though there were wild cards at either end, which is exactly what InStr() does.  But it does not allow actual wildcards in the string put together.  What it returns is the complete path for every file that matches that pattern, which can be a lot of returns unless you extend the search down to the specific file sought.  It does make a stipulation that the PATTERN employed could be a regex (regular expression), but I had problems running down examples of working with a PATTERN or regex as these might apply to Locate.  Locate is lower case when actually used.

Anyway, it's proven to be a handy tool, and I run Update daily, so my databases are kept current.

---

### Post by ian-weisser on 2015-10-02
> **oldefoxx said:**
> But apt-get will begin telling about some updates it isn't getting, but only the count, never what it is passing over or why.

Yes, -qq mutes a lot of information you might find useful...

---

