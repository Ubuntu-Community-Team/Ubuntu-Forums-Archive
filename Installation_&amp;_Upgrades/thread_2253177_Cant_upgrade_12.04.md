---
title: "Cant upgrade 12.04"
date: 2014-11-17
forum: Installation &amp; Upgrades
---

### Post by maxyman3400 on 2014-11-17
Hello! I cant seem to upgrade from 12.04 version of unbuntu. I have tried over the past month on a bunch of different threads and forums and no one seems to have the problem I have. Ill show you what it shows in the update screen.
 imgur.com/XphCFeN
As you can see it doesnt even show the 14 version. When I try to update this happens.
 [http://imgur.com/RBBOxkp](http://imgur.com/RBBOxkp)
And now when I try sudo apt -get update this happens
[http://imgur.com/je3BaeT](http://imgur.com/je3BaeT)
I have also tried a bunch of other stuff but here is just some basic stuff of what is happening. PLEASE HELP

---

### Post by Bashing-om on 2014-11-17
maxyman3400; Hi ! Welcome to the forum.

a) Open the update manager, go to Settings, click to open.
Then go to the Updates tab and find the line for notify for new release, and change to "lts'
In your linked image you do not have the correct option checked.

b) The correct terminal commands for 'update':
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```
note there is no space in apt-get.

For best results put the install back to as close to defaults as possible, disable all 3rd party sources- that does include proprietary graphics drivers. And as well disable the screen saver. 

Prior Prudent Planning Prevents P*** Poor performance

[INDENT][INDENT][INDENT]then no luck to it , done and over with
[/INDENT][/INDENT][/INDENT]

Doing so I have never experienced a problem doing the on-line release upgrade.

---

### Post by maxyman3400 on 2014-11-17
Hey sorry I dont understand by what you mean by change to "Its" could you please clarify.

---

### Post by Bashing-om on 2014-11-17
maxyman3400; Sure;

One may make that change in the GUI update manager, but;
here is an alternate way:
edit the file
/etc/update-manager/release-upgrades
change the line from Prompt=normal to Prompt=lts.
As in:
> 
<snip>
#           the currently-running one.  Note that this option should not be
#           used if the currently-running release is not itself an LTS
#           release, since in that case the upgrader won't be able to
#           determine if a newer release is available.
Prompt=lts
sysop@1404mini:~$ 

where 'lts' is Long Term Support ; in this case 14.04.

Remember to always make a backup first of any file one edits, one can never know what might happen.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

