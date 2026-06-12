---
title: "Problems upgrading 14.04 to 16.04"
date: 2019-02-22
forum: Installation &amp; Upgrades
---

### Post by Ursus Maritimus on 2019-02-22
Hi,

Tried to find solution from older post's and google, but with out success.. These are the main probs, which I will get every time (even tried to solve them). First will say: 
A problem occurred during the update. 
This is usually some sort of network problem, 
please check your network connection and retry.

Even, everything works otherwise. 

2nd one comes as well, after the sudo apt-get update command. I had the same problem earlier, disappeared (by how, no idea), 
but came back and can't find a solution to get rid of it..

N: Ignoring file 'google-chrome.list.save.1' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
W: Failed to fetch [http://dl.google.com/linux/earth/deb/dists/stable/Release](http://dl.google.com/linux/earth/deb/dists/stable/Release)  
Unable to find expected entry 'main/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)
E: Some index files failed to download. They have been ignored, or old ones used instead.

I would be grateful of any help, thanks..

---

### Post by CatKiller on 2019-02-22
Removing third-party repositories from your list of software sources would be a good place to start.

---

### Post by Ursus Maritimus on 2019-02-22
> **CatKiller said:**
> Removing third-party repositories from your list of software sources would be a good place to start.

I believe you easily, but any kind of hints what to do, would be nice as well..

---

### Post by CatKiller on 2019-02-22
> **jukka_suikki said:**
> I believe you easily, but any kind of hints what to do, would be nice as well..

It depends what you're using, and what you're comfortable with.

Commenting out lines from in /etc/apt/sources.list and sources.list.d would be the way I'd do it. Others might be using Synaptic, and so change the repository settings there. Still others might use the Software Sources part of the Settings tool. It all does the same stuff.

Doing a search for "remove repositories" is still going to find you far more information than I'm willing to type out on a phone.

---

### Post by TheFu on 2019-02-22
If networking doesn't work, then everything dependent on that will also fail - like apt.

So a few questions:
Is the networking ok or not?  If not, where does it break?  
Is the problem with a wired connection or wifi?  
Is there a router involved or not?  
Is the correct driver loaded or not?

Follow these steps in order and report back:  [http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking)  Use the correct IP addresses for your network in that link.  If you don't know them, you can use these commands:
**ip addr**  # <---- provides the IP(s) for the current computer. Ignore any that begin with 127.x.x.x, those are loopback.
**route -n**  # <---- provides the IP for the "gateway", which should be the router in a home/small biz setup.

---

### Post by oneleded on 2019-02-22
what version are you up grading? i must have missed it.

---

### Post by Ursus Maritimus on 2019-02-24
Ubuntu 14.04 LTS Intel® Celeron(R) CPU 1007U @ 1.50GHz × 2 64-bit

Network is working well, but when I try to update, it will stop and tell:
[COLOR=#000000]A problem occurred during the update. [/COLOR][COLOR=#000000]This is usually some sort of network problem, [/COLOR][COLOR=#000000]please check your network connection and retry.
[/COLOR]Problem comes from wifi
It will tell the same with or without router
what do you mean by correct drivers?

---

### Post by Ursus Maritimus on 2019-02-24
Now I got the 16.04 installed, but when I was trying to update it, it stopped and said again: N: Ignoring file 'google-chrome.list.save.1' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionSo, how can I can fix that or delete it..?

---

### Post by Autodave on 2019-02-24
Is there any reason why you could not do a clean install of 18.04 instead of trying to upgrade what you have?  Upgrades generally (at least in my opinion) rarely go smoothly if at all.  I learned a long time ago to back up everything that I need to keep to an external source and just do a clean install.

---

### Post by rsteinmetz70112 on 2019-02-24
I'd create a directory somewhere safe and move the offending file there. The file is obviously related to google chrome, so you could try removng it and purging it then try the update again. The exact process depends on what package management system you use.

You could also try from a terminal

sudo dpkg --configure -a
sudo apt install -f  

It will clean up some things and may give you more information.

---

### Post by oneleded on 2019-02-26
i agree with Autodave.. why not install 18.04 lts.

---

### Post by TheFu on 2019-02-26
Everyone has different experiences and has had good and bad upgrades.

16.04 is fine and supported until 2021.  There are thousands and thousands of how-to guides known to work for almost anything in 16.04, but 18.04 has some newly introduced issues and there are few guides to handle some of the newer stuff and uncommon setups.  The new network config files in 18.04 still don't meet my needs well enough for my production use. There are other issues too.
[B]
Newer isn't always better.[/B]

As for .save files in for PPAs ---- those are what the _do-release-upgrade_ process does when moving to a new release as a way to minimize upgrade failures.  All 3rd party PPAs are made invalid, so the upgrade only depends on Canonical repos, which limits possible dependency and other issues tremendously.  If you only use a few PPAs and never installed .deb files directly, then upgrades between versions generally go fine on non-server systems. There are exceptions and only you can make the decision that fits your needs.

Before doing any upgrade, always, always make a know-you-can-restore backup, so if anything goes wrong, then you can put it back and try again or go in a different direction.

---

### Post by Ursus Maritimus on 2019-02-27
> **rsteinmetz70112 said:**
> I'd create a directory somewhere safe and move the offending file there. The file is obviously related to google chrome, so you could try removng it and purging it then try the update again. The exact process depends on what package management system you use.

You could also try from a terminal

sudo dpkg --configure -a
sudo apt install -f  

It will clean up some things and may give you more information.


I will try this and see, what will happen..

---

### Post by Ursus Maritimus on 2019-02-27
> **jukka_suikki said:**
> I will try this and see, what will happen..

N: Ignoring file 'google-chrome.list.save.1' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension

Was the result again and again.. Clean 18.04 install sounds interesting option, if I can't find a solution for this issue.. By clean, does is it mean installation on clear/empty disk? So everything I've got, should be saved on backup (common sense) and install them back later, or..? Making sure, that I did understand the meaning correctly..

---

### Post by mastablasta on 2019-02-28
> **TheFu said:**
> .  If you only use a few PPAs and never installed .deb files directly, then upgrades between versions generally go fine on non-server systems. There are exceptions and only you can make the decision that fits your needs.
Kubuntu 14.04 simply won't upgrade well to 16.04 which i found out the hard way.
more: [https://wiki.ubuntu.com/XenialXerus/ReleaseNotes/Kubuntu](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes/Kubuntu)



> **jukka_suikki said:**
> N: Ignoring file 'google-chrome.list.save.1' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension

Was the result again and again.. Clean 18.04 install sounds interesting option, if I can't find a solution for this issue.. By clean, does is it mean installation on clear/empty disk? So everything I've got, should be saved on backup (common sense) and install them back later, or..? Making sure, that I did understand the meaning correctly..

1. try to rename the file to for example [I]google-chrome.list.save.1.bak 
[/I]2. two option with clean install 
- overwrite the current install (this keeps current settings and files)
- reformat the drive - this erases all data
3. well everything in your home folder at least. as i was forced into fresh install i chose reformat. i had 2 partitions / and  /data, so i copied the home folder to data and reformated the root, then moved the data back to home (where needed). i just used the same user name and all worked like a sloppy upgrade :). well actually it all works well, just had to install a few apps.

---

### Post by TheFu on 2019-02-28
Just delete the google-chrome.list.save and google-chrome.list.save.1 files.

---

### Post by Ursus Maritimus on 2019-03-02
I tried some other methods and reply was this: 

N: Ignoring file 'google-chrome.list.save.1' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Skipping acquire of configured file 'main/binary-i386/Packages' as repository 'http://dl.google.com/linux/earth/deb stable InRelease' doesn't support architecture 'i386'

---

### Post by Ursus Maritimus on 2019-03-02
>  1. try to rename the file to for example google-chrome.list.save.1.bak 

How do I do that?

---

### Post by TheFu on 2019-03-02
Did Google end support for 32-bit Chrome?  I vaguely remember something about that. [https://www.omgubuntu.co.uk/2016/03/fix-failed-to-fetch-google-chrome-apt-error-ubuntu](https://www.omgubuntu.co.uk/2016/03/fix-failed-to-fetch-google-chrome-apt-error-ubuntu) yep.  Gone.  No need to keep the PPA around, if that is true. Just delete the file(s).

There is a work-around. Use chromium-browser instead of google-chrome browser.  Chromium is the F/LOSS project that google sponsors which feeds into their chrome browser. **sudo apt install chromium-browser** will install it. Don't do this install yet. Wait until the rest of APT is all good, clean, and working.

But cleaning up the old PPA and getting the package manager into a good state, is still necessary.

How to delete files is a basic task.  Any Unix/Linux training should teach that in the first few hours.  An understanding of Unix file permissions will make things easier, since file permissions are core of all Unix security.

To rename a file, use the 'mv' command.  Files stored outside your HOME directory will almost always be system owned, so your user account cannot rename or delete them. That's where **sudo** comes in.  Using sudo when it isn't necessary can be very harmful, so don't just use it all the time.

I wouldn't rename that PPA file. I would delete it. Actually, I would delete all the PPA files from google.  To do that, here are the steps:

```
sudo rm /etc/apt/sources.list.d/google-chrome*
sudo apt update
sudo apt upgrade
```
In theory, this should get APT into a good state. If you see any warnings or errors, STOP.  DO NOT run the next command. Post the command AND the output back here using _code tags_. See my example block.

---

### Post by him610 on 2019-03-03
> Did Google end support for 32-bit Chrome? 
Yes. One needs to install open-source 32-bit Chromium.

---

### Post by Ursus Maritimus on 2019-03-04
Result:

>  
N: Skipping acquire of configured file 'main/binary-i386/Packages' as repository 'http://dl.google.com/linux/earth/deb stable InRelease' doesn't support architecture 'i386'




That was after first line and update try..

---

### Post by TheFu on 2019-03-04
Please be much clearer. There are lots of commands above and we can't tell which you've decide to use. We cannot read minds.

---

### Post by Ursus Maritimus on 2019-03-06
I agree with that and I'm happy to be as clear as I can.. So, what should I show, cause I thought I've replied all the commands what has came & what have I tried..

---

### Post by TheFu on 2019-03-06
If you don't show the **command** _and_ the **output**, we are left guessing.

---

### Post by Ursus Maritimus on 2019-03-07
Ok. sudo apt-get update and answer today was: 
Reading package lists... Done
N: Skipping acquire of configured file 'main/binary-i386/Packages' as repository 'http://dl.google.com/linux/earth/deb stable InRelease' doesn't support architecture 'i386'

sudo apt-get upgrade works well, without comments..

---

### Post by monkeybrain20122 on 2019-03-07
> N: Skipping acquire of configured file 'main/binary-i386/Packages' as  repository 'http://dl.google.com/linux/earth/deb stable InRelease'  doesn't support architecture 'i386'

This is harmless.Kind of comes and goes.. If it bothers you [https://askubuntu.com/questions/741410/skipping-acquire-of-configured-file-main-binary-i386-packages-as-repository-x](https://askubuntu.com/questions/741410/skipping-acquire-of-configured-file-main-binary-i386-packages-as-repository-x)

---

### Post by Ursus Maritimus on 2019-03-07
Ok, thanks. It bothers me and I'm not totally sure, if the update would be done properly. I will check the link though..

edit.
I've seen it before and tried it, without success. It is on this format ```
(deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main) 
```So that ain't changing.

Tried this, with result:
```
To confirm you are using 64 bit ubuntu with multiarch enabled issue
dpkg --print-foreign-architectures
if it says
i386
then you have added 32 bit support, this will list your native arch ... issue
```

It tells that it can be fixed, but just temporary. But there is a option to do it regularly, but I'm not sure how to do it? 
```
To fix it once and for all, edit /etc/cron.daily/google-earth-pro.
Find this line:
REPOCONFIG="deb http://dl.google.com/linux/earth/deb/ stable main"
...and change it to:
REPOCONFIG="deb [arch=amd64] http://dl.google.com/linux/earth/deb/ stable main"
```

How about taking the whole Earth away and reinstall it? Would that solve the problem?

---

### Post by monkeybrain20122 on 2019-03-07
I have also seen this message from google's repositories (chrome and earth) I tried the link, it went away for a while then it appeared again, it is kind of harmless, I still got upgrades for earth and chrome (got earth upgrade just yesterday despite the message). I just don't bother any more.

---

### Post by TheFu on 2019-03-07
> **Ursus Maritimus said:**
> Ok. sudo apt-get update and answer today was: 
Reading package lists... Done
N: Skipping acquire of configured file 'main/binary-i386/Packages' as repository 'http://dl.google.com/linux/earth/deb stable InRelease' doesn't support architecture 'i386'

sudo apt-get upgrade works well, without comments..

And what about the prior commands I posted above - the ones that would actually clean up the PPA?

I know you are trying.  Someone else will need to step in.  Good luck.

---

### Post by DuckHook on 2019-03-07
@Ursus Maritimus

Please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar. Failing to do so adds unwanted URL tags to your posts. Please also refrain from using unusual colours and fonts. These are difficult to read on some devices and screens.

---

### Post by monkeybrain20122 on 2019-03-09
I have not done anything, but that message has disappeared on its own when when ran apt update tonight.  It has been like that, the error suddenly appears out of nowhere, lasts a few days, then gone, then  comes back all of a sudden for a few days, then gone again... But all the while I have no problem upgrading. So I just ignore it when it shows up.

---

### Post by Ursus Maritimus on 2019-03-09
> **TheFu said:**
> Did Google end support for 32-bit Chrome?  I vaguely remember something about that. [https://www.omgubuntu.co.uk/2016/03/fix-failed-to-fetch-google-chrome-apt-error-ubuntu](https://www.omgubuntu.co.uk/2016/03/fix-failed-to-fetch-google-chrome-apt-error-ubuntu) yep.  Gone.  No need to keep the PPA around, if that is true. Just delete the file(s).

[CODE]sudo rm /etc/apt/sources.list.d/google-chrome*


I tried the first one and result was: ** (gedit:3089): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-position not supported

2nd one gave: rm: cannot remove '/etc/apt/sources.list.d/google-chrome*': No such file or directory

---

### Post by Ursus Maritimus on 2019-04-06
Still having issues of sudo apt-get update or sudo apt-get upgrade via terminal or via show updates.. 

Via later option it tells: An error occurred, please run Package manager from the right-click menu or apt-get in terminal to see what is wrong. The error message was 'Error:BrokenCount> 0' This usually means that your installed packages have unmet dependencies, before the update try..

Then it will show the update list, but will stop by saying:


Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f
Transaction failed: The package system is broken
The following packages have unmet dependencies:
snapd-xdg-open: Depends: snapd (= 2.37.4ubuntu0.1) but 2.37.1~14.04 is installed

I have tried to correct them with what I've found from this forum and from google, different terminal commands, unsuccessfully. 
Tried 'software&updates' > ubuntu software > download from > select best server, no help.

---

